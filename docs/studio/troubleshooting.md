# Studio troubleshooting

Start here when something in the recording studio does not work. The first
table sends you to the right page. The rest of this page covers problems
while **setting up** a studio.

## What is wrong?

| What you see | Go to |
|---|---|
| A camera is missing, offline or not responding | [Troubleshooting FX30 connections](troubleshooting-fx30.md) (IT), or [Recording: cameras offline](../troubleshooting/recording.md#rec-cameras-offline) (operator) |
| *Camera controller niet bereikbaar* | [Recording: controller unreachable](../troubleshooting/recording.md#rec-controller-unreachable) |
| Camera Control stays on *Wachten op qR desktop* | [The QR screen does not open](#studio-qr-screen) below |
| Camera Control stays on *Wachten op piep* | [Recording: waiting for the beep](../troubleshooting/recording.md#rec-waiting-beep) |
| Battery, card or overheating warnings | [Recording: battery](../troubleshooting/recording.md#rec-battery), [overheating](../troubleshooting/recording.md#rec-overheat) |
| A take is not downloaded (✗), or not linked to its gloss | [Recording: not downloaded](../troubleshooting/recording.md#rec-not-downloaded), [QR not linked](../troubleshooting/recording.md#rec-qr-not-linked) |
| Nothing from today is processed or uploaded | [Video processing: pipeline stopped](../troubleshooting/video-processing.md#vp-pipeline-stopped) |
| Videos are cropped badly, or the green screen is still green | [Video processing](../troubleshooting/video-processing.md#vp-bad-crop) |
| Clips are not on the research drive | [Video processing: not copied](../troubleshooting/video-processing.md#vp-not-copied) |
| A problem while installing the studio | The sections below |

## Setting up the studio

These entries follow the order of [Install the DRS Mac](install-drs.md).

### The setup script warns or stops {#studio-setup-script}

**Who can fix:** administrator

**Likely cause:** something the script needs is missing on the Mac. The
script names it in a line that starts with `warn`.

**Try this:**

1. Run the script without `--apply`. It then only reports and changes
   nothing:

    ```bash
    cd /Users/signlab/drs && scripts/setup-drs.sh
    ```

2. Fix each warning, then run it again. The common ones:

    | Warning | Fix |
    |---|---|
    | Xcode is missing | Install the full Xcode app from the App Store, open it once and accept the licence |
    | Homebrew is not installed | Install Homebrew, see <https://brew.sh> |
    | DaVinci Resolve Studio is not installed | Install the **Studio** (paid) edition, see below |
    | Tailscale is not installed | Install Tailscale and log in to the server's tailnet |
    | Google Chrome is not installed | Install Chrome |
    | `cacheDisk` is not mounted | See [the external disk](#studio-cachedisk) below |
    | no rclone remote `signcollect:` | See [the research drive](#studio-research-drive) below |
    | `VIDEOFIX_TOKEN` is not set | Run the script as `VIDEOFIX_TOKEN=<token> scripts/setup-drs.sh --apply`, with the token from the server's `.env` |

3. When the report is clean, run it with `--apply`.

**Still stuck?** Send the full output of the script.

### DaVinci Resolve does not render {#studio-resolve}

**Who can fix:** administrator

**Likely cause:** the pipeline drives Resolve through its scripting
interface. That needs the Studio edition, scripting switched on, and the
project the pipeline expects.

**Try this:**

1. Check that the installed edition is DaVinci Resolve **Studio**. The free
   edition has no external scripting.
2. Open Resolve > **Preferences** > **System** > **General** and set
   **External scripting using** to **Local**. Restart Resolve.
3. Check that a project named `lala6` exists. The pipeline opens it by name.
4. Close Resolve. The pipeline starts and stops it by itself every hour, and
   a Resolve you opened by hand gets killed mid-work.
5. Read `~/drs/logs/batch.log` for the error.

**Still stuck?** Send the last 50 lines of that log.

### The QR screen does not open, or opens on the wrong screen {#studio-qr-screen}

**Who can fix:** administrator

**Likely cause:** the controller app opens the QR page on the screen whose
macOS name contains the `display_screen` text in its `config.json`. If that
screen is mirrored, or the name does not match, it has nowhere to go.
Camera Control then stays on *Wachten op qR desktop*.

**Try this:**

1. Open **System Settings** > **Displays** and set the QR screen to
   **extend** the desktop, not mirror it.
2. Note part of that screen's name, for example `PHL` for a Philips monitor.
3. Put it in `display_screen` in
   `~/signlab_Sony-SDK-MACOS-API/pyqtController/config.json`.
4. Restart the controller app, or click **🖥 QR-scherm openen** in it. The
   status next to the button shows **QR-scherm: ● open**.
5. Check that the cameras can see the screen and that the code is sharp in
   the camera image.

**Still stuck?** The QR page reaches Camera Control through the
studioSupport service on the SignCollect server. Ask the server's
administrator whether that service is running.

### Camera Control warns "Niet alle cameras online" with every camera on {#studio-camera-list}

**Who can fix:** administrator

**Likely cause:** Camera Control counts against its camera list. Without a
`cameras.json` it expects the lab's five cameras, by serial number.

**Try this:**

1. On the Mac, read the serials: `curl -s localhost:8080/api/status`. The
   serial is the ID in brackets in `"model"`.
2. On the server, create `cameras.json` next to `opnameView.html` with
   exactly your cameras. See
   [Install the DRS Mac](install-drs.md#camera-control-and-the-server).
3. Reload Camera Control. The top bar now counts against your cameras.

### Camera Control cannot reach the cameras of a new studio {#studio-camera-server}

**Who can fix:** administrator

**Likely cause:** the server reaches the camera server on the Mac over
Tailscale, at a fixed name.

**Try this:**

1. On the Mac, open <http://localhost:8080>. If no page loads, the camera
   server is not running: start the controller app.
2. Check that the Mac and the server are in the same tailnet
   (`tailscale status` on both).
3. Open Camera Control with `?camhost=<the Mac's Tailscale name>:8080`. If
   that works, set that name as `$DEFAULT_HOST` in `fx30proxy.php` on the
   server.

**Still stuck?** Follow
[Troubleshooting FX30 connections](troubleshooting-fx30.md) from step 3.

### The external disk is not found {#studio-cachedisk}

**Who can fix:** administrator

**Likely cause:** camera downloads and the rclone cache go to
`/Volumes/cacheDisk`. The disk is not connected, or has another name.

**Try this:**

1. Connect the external disk and check it shows in Finder.
2. Rename it to exactly `cacheDisk` (Finder > select the disk > Return).
3. Check: `ls /Volumes/cacheDisk`.
4. Run `scripts/setup-drs.sh --apply` again. It creates the folders on the
   disk.

### The research drive is not mounted {#studio-research-drive}

**Who can fix:** administrator

**Likely cause:** the rclone remote is missing, macFUSE is not allowed, or
the mount is still starting. The pipeline needs this mount: all its paths
are under it.

**Try this:**

1. Check the remote exists: `rclone listremotes` must list `signcollect:`.
   If not, run `scripts/setup-drs.sh --apply --rclone`.
2. Open **System Settings** > **Privacy & Security** and allow the macFUSE
   system extension. Restart the Mac if it asks.
3. Check the mount:

    ```bash
    ls "$HOME/signCollect/AIHR-FGW-TEST-SIGNLAB (Projectfolder)/do_not_remove_for_rclone"
    ```

4. If the file is not there, wait. The health check only starts 30 minutes
   after rclone starts.
5. Check that the marker file `do_not_remove_for_rclone` and the folder
   `studioFiles` exist on the research drive itself.

**Still stuck?** Send `~/drs/startup.log`.

### The pipeline does not start after logging in {#studio-pipeline-start}

**Who can fix:** administrator

**Likely cause:** the start-up job did not run, or it stopped on the mount
check above.

**Try this:**

1. Start it by hand:

    ```bash
    launchctl kickstart gui/$(id -u)/nl.signcollect.drs-startup
    ```

2. Check that it runs: `ps -p $(cat ~/drs/startup.pid)`.
3. Read `tail -50 ~/drs/startup.log` for the reason.
4. Open the [client monitor](../interfaces/client-monitor.md). The `drs-*`
   clients should send heartbeats within a few minutes.

### Takes are recorded but never arrive on the server {#studio-no-upload}

**Who can fix:** administrator

**Likely cause:** the pipeline uploads to the address in `SIGNCOLLECT_URL`.
It is wrong, or the pipeline is not running.

**Try this:**

1. Check the address: `grep SIGNCOLLECT_URL ~/drs/.env`.
2. Check the Mac reaches it: `curl -sI "$(grep SIGNCOLLECT_URL ~/drs/.env | cut -d= -f2)" | head -1`.
3. Check that the pipeline runs, see
   [above](#studio-pipeline-start).
4. Follow one take: see
   [Video processing: nothing is processed](../troubleshooting/video-processing.md#vp-pipeline-stopped)
   and [a clip was never rendered](../troubleshooting/video-processing.md#vp-never-rendered).

## Related

- [Install the DRS Mac](install-drs.md)
- [Troubleshooting FX30 connections](troubleshooting-fx30.md)
- [Troubleshooting: recording sessions](../troubleshooting/recording.md)
- [Troubleshooting: video processing](../troubleshooting/video-processing.md)
