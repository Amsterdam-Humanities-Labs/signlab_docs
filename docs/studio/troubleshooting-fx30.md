# Troubleshooting FX30 connections

For developers and IT staff: how to find out why a Sony FX30 does not connect
to the camera server on DRS. Operators should start with
[Recording troubleshooting](../troubleshooting/recording.md).

## How the connection works

1. Each FX30 is connected to DRS by USB, in remote-shooting mode.
2. The camera server `fx30MultiRecord` (from
   [signlab_Sony-SDK-MACOS-API](https://github.com/Amsterdam-Humanities-Labs/signlab_Sony-SDK-MACOS-API))
   uses the Sony Camera Remote SDK to find the cameras. It only takes cameras
   whose model contains `FX30` (USB vendor `0x054c`, product `0x0e10`).
3. At start-up it resets the FX30 USB devices, waits, and connects to each
   camera. A failed connect is retried 3 times, with a USB reset in between.
4. It serves a dashboard and a REST API on port 8080.
5. The controller app (**FX30 Multi-Camera Bediening**) starts the server and
   polls it. Camera Control on the server reaches it through `fx30proxy.php`
   over Tailscale.

Only one process can hold the cameras. Never run two `fx30MultiRecord`s.

## Step 1: is the camera on the USB bus?

1. Turn the camera on.
2. On DRS, count the FX30s that macOS sees:

    ```bash
    ioreg -p IOUSB | grep -c ILME-FX30
    ```

3. If a camera is missing here, the problem is below the SDK:
    - Try another USB-C cable. Charge-only cables do not carry data.
    - Plug the camera straight into the Mac instead of a hub, or use a
      powered hub.
    - Check the camera's USB connection mode (step 2).
    - Close other apps that may claim the camera, such as Image Capture,
      Photos or Sony's own apps (general advice, not from the code).

## Step 2: check the camera settings

1. The USB connection mode must be remote shooting (**Remote Shoot (PC
   Remote)** in Sony's SDK guide). If the camera asks which USB mode to use
   when you plug it in, choose that one.
2. The camera must not be in a menu or playback screen.
3. Check the battery. A camera that is about to turn off drops out.
4. Check that the camera is not overheating. The server reports
   `heatState`; the controller shows *BIJNA OVERVERHIT* or *OVERVERHIT*.

## Step 3: is the camera server running?

1. Check for exactly one server:

    ```bash
    pgrep -fl fx30MultiRecord
    ```

2. Ask for its status:

    ```bash
    curl -s http://localhost:8080/api/status | python3 -m json.tool
    ```

3. Read the result:

| Field | Meaning |
|---|---|
| `cameras[].model` | Model and ID, for example `ILME-FX30 (D4DA001EC952)`. The ID in brackets is what Camera Control's `CAMERA_MAP` uses |
| `cameras[].connected` | `true` when the SDK is connected |
| `scanning`, `scanStatus` | A scan is running, and what it is doing |
| `downloading`, `listing` | Busy with a download or file list. Cameras disappear from the page meanwhile; that is normal |

If `curl` gets no answer, the server is not running. Start the controller app
(`pyqtController/run.sh`), or click **Sony SDK herstarten (hard)** in it.

## Step 4: rescan or reset

Every POST needs a JSON body; a bare POST gets HTTP 400.

1. Scan again for missing cameras:

    ```bash
    curl -s -X POST -H 'Content-Type: application/json' -d '{}' http://localhost:8080/api/scan
    ```

2. If that does not help, reset the USB devices and scan:

    ```bash
    curl -s -X POST -H 'Content-Type: application/json' -d '{}' http://localhost:8080/api/reset
    ```

3. Wait about 30 seconds and check the status again.
4. If a camera still does not connect, turn it off and on.
5. As a last step, restart the server: **Sony SDK herstarten (hard)** in the
   controller app. It kills `fx30MultiRecord` and starts it again.

The controller app has the same actions as buttons: **Opnieuw scannen**,
**USB-reset (zacht)** and **Sony SDK herstarten (hard)**. While only some
cameras are connected, it rescans every 5 seconds by itself.

!!! warning "Not during a take or a download"
    A scan, reset or restart drops the cameras for a while. Do not do it while
    recording or downloading.

## Step 5: read the logs

| Log | Where | What to look for |
|---|---|---|
| Event log | `pyqtController/capture_logs/events-<date>.log` when the controller started the server; `capture_logs/` next to the binary when you started it by hand | `SCAN_ENUMERATED` (FX30s seen on USB), `CONNECTED`, `CONNECT_FAILED`, `DISCONNECTED after …s`, `RECONNECTED`, `SCAN_RESULT` |
| Server output | Only when you run it in a terminal (the controller discards it) | See the table below |
| Camera Control debug log | `logs/fx30_debug.log` on the server | Browser and controller events. Off with `?fxdebug=0` |

To see the server output, quit the controller app, then run the server by
hand:

```bash
pkill -f fx30MultiRecord
cd /Users/signlab/signlab_Sony-SDK-MACOS-API/simpleCli/build/Release
./fx30MultiRecord --port 8080 --download-path /Volumes/cacheDisk/fx30_staging/inbox
```

Stop it with Ctrl-C and start the controller app again when you are done.

## Test one camera

1. Quit the controller app and stop the server (`pkill -f fx30MultiRecord`).
2. Unplug all cameras but one.
3. Run the server by hand (see above) and watch the output.
4. Open <http://localhost:8080>. The dashboard shows the camera and its
   settings.
5. Click **Start Recording**, wait a few seconds, and click **Stop Recording**.
   The dashboard also has **Scan** and **USB Reset**.
6. Repeat for each camera. A camera that fails alone has a camera, cable or
   settings problem; if each works alone but not together, suspect the hub or
   USB power.

## Messages

### Server output

| Message | Likely cause | What to do |
|---|---|---|
| `Failed to initialize Sony Camera Remote SDK.` | The SDK libraries are not next to the binary | Rebuild: the build copies `external/crsdk` into `Release/` and `CrAdapter` into `Release/Contents/Frameworks/`. Run the binary from `build/Release` |
| `No cameras found.` | No Sony camera answered on USB | Step 1 and 2 |
| `Skipping non-FX30: …` | Another Sony model is connected | Only FX30s are used |
| `Attempt n/3 failed for …` / `connection error for …` | The camera refused or dropped the connection | Check USB mode, cable, battery; the server resets USB and retries |
| `Failed to connect … after 3 attempts.` | All retries failed | Turn the camera off and on, then rescan |
| `Camera(s) disconnected for Ns...` | A connected camera dropped out | After 20 s the server resets and reconnects by itself |
| `No new FX30 cameras found.` | A scan found nothing new | Normal if all are already connected |

### API errors

| Error | Meaning |
|---|---|
| `Download in progress`, `Listing in progress` | Wait for the download or file list to finish |
| `Scan already in progress` | Wait for the running scan |
| `Busy` | Formatting or listing is blocked while another action runs |
| `No preset file found at …` | `--preset` points to a missing file |
| `Controller unreachable: …` (from `fx30proxy.php`) | The server cannot reach port 8080 on DRS: DRS is off, Tailscale is down, the camera server does not run, or `$DEFAULT_HOST` / `?camhost=` is wrong |

### Controller app banners

| Banner | What to do |
|---|---|
| *Alle camera's staan UIT* | No FX30 on USB. Turn the cameras on |
| *camera('s) REAGEREN NIET* | On USB but not connected. Turn all cameras off and on, or use **USB-reset (zacht)** / **Sony SDK herstarten** |
| *Slechts X van Y camera's verbonden* | Some cameras are missing. The app rescans every 5 s; turn the missing ones off and on |

### Camera Control

| Message | Cause |
|---|---|
| *Niet alle cameras online! Slechts N van de 5 cameras online.* | Fewer cameras than listed in `CAMERA_MAP`. With a studio of three cameras, `CAMERA_MAP` must list only those three (see [Install the DRS Mac](install-drs.md#camera-control-and-the-server)) |
| *Camera controller niet bereikbaar...* | See `Controller unreachable` above |

## Related

- [Install the DRS Mac](install-drs.md)
- [Recording troubleshooting](../troubleshooting/recording.md)
- [Camera Control](../interfaces/camera-control.md)
- [Client monitor](../interfaces/client-monitor.md)
