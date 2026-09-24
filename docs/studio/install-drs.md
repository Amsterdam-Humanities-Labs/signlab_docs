# Install the DRS Mac

This page installs the studio Mac (DRS): the Sony camera server, the camera
controller app and the video pipeline. The setup script
`scripts/setup-drs.sh` in
[signlab_drs-pipeline](https://github.com/Amsterdam-Humanities-Labs/signlab_drs-pipeline)
does most of it. The steps it cannot do are listed below.

- **Who does this:** IT staff or a developer, with admin rights on the Mac.
- **Time:** half a day, plus downloads.

!!! note "Script status"
    The setup script is new and has only been tested as a dry run. Until
    [pull request #32](https://github.com/Amsterdam-Humanities-Labs/signlab_drs-pipeline/pull/32)
    is merged, it is on the branch `setup-script`.

## Before you start

1. Create a macOS user named `signlab` and log in as that user. The pipeline
   paths are fixed to `/Users/signlab`.
2. Connect the external disk and name it `cacheDisk`, so it mounts at
   `/Volumes/cacheDisk`.
3. Install Xcode from the App Store, open it once, and run
   `sudo xcode-select -s /Applications/Xcode.app`.
4. Install [Homebrew](https://brew.sh).
5. Install DaVinci Resolve Studio (see [below](#davinci-resolve-studio)).
6. Decide which SignCollect server the studio uploads to, for example
   `https://signcollect.nl`.

## Run the setup script

1. Clone the pipeline to its fixed place:

    ```bash
    git clone https://github.com/Amsterdam-Humanities-Labs/signlab_drs-pipeline.git /Users/signlab/drs
    cd /Users/signlab/drs
    ```

2. Run the script without options. This is a dry run: it checks the Mac and
   prints what it would do, and changes nothing.

    ```bash
    scripts/setup-drs.sh
    ```

3. Read the warnings. Fix what the script cannot fix, then run it again.
4. Run it for real. Use your server, number of cameras and the name of the QR
   screen. Leave out `--rclone` if you do not use a research drive.

    ```bash
    scripts/setup-drs.sh --apply --server https://signcollect.nl --cameras 3 --display-screen PHL --rclone
    ```

5. Answer the questions of `rclone config` (only with `--rclone`). Name the
   remote exactly `signcollect`. The password is stored in the `signlab`
   user's rclone config, never in git.
6. Read the list of manual steps at the end, and do them (see below).

The script is safe to run again. Each step checks first and skips what is
already done. `scripts/setup-drs.sh --help` shows all options.

### What the script does

| Step | Details |
|---|---|
| Checks | macOS 12.1 or later, Apple Silicon, user `signlab`, checkout at `/Users/signlab/drs`, Xcode |
| Homebrew packages | cmake, autoconf, automake, libtool, ffmpeg, python@3.13, zbar; Tailscale and Google Chrome if missing |
| Python | Service packages for `/usr/bin/python3` (what `startupScript.py` runs); a venv in the repo root for the QR scanner; copies `qr_scanner/` to `qr/` |
| Folders | `logs`, `import`, `export`, `temp`; `/Volumes/cacheDisk/fx30_staging/inbox` and `/Volumes/cacheDisk/rclone` |
| `.env` | Created from `.env.example`, mode 600, with `SIGNCOLLECT_URL` set to `--server` |
| Camera server | Clones [signlab_Sony-SDK-MACOS-API](https://github.com/Amsterdam-Humanities-Labs/signlab_Sony-SDK-MACOS-API) to `/Users/signlab/signlab_Sony-SDK-MACOS-API` and builds `fx30MultiRecord` as its README says |
| Controller app | A venv with PyQt6, and `pyqtController/config.json` if there is none |
| rclone (`--rclone`) | Official rclone build in `/Users/signlab/rclone` (Homebrew's rclone cannot mount on macOS), checks macFUSE, runs `rclone config` |
| sudo rule | `/etc/sudoers.d/signlab-network`, so `network_manager.py` can restart ethernet and Tailscale |
| Start at login | A LaunchAgent `nl.signcollect.drs-startup` that starts `startupScript.py` at login, unless it already runs |

### Configuration

| Setting | Where | Default |
|---|---|---|
| Server the pipeline uploads to | `SIGNCOLLECT_URL` in `/Users/signlab/drs/.env` | `https://signcollect.nl` |
| Database credentials (repair tools only) | `DB_HOST`, `DB_USER`, `DB_PASSWORD`, `DB_NAME` in `.env` | Empty password |
| Camera server, staging, rclone, QR screen | `pyqtController/config.json` in the SDK clone | Written by the script |
| Research drive | rclone remote `signcollect:` in the `signlab` user's rclone config | None |
| Mouse keep-awake | `/Users/signlab/drs/mouse_config.json` (optional) | See `config/mouse_config.json.example` |

!!! warning "Never commit secrets"
    `.env` and the rclone config hold passwords. Both stay on the Mac and are
    not in git.

## Manual steps

### DaVinci Resolve Studio

1. Buy and install DaVinci Resolve **Studio** from Blackmagic Design. The
   free version has no external scripting, and the pipeline needs it.
2. Open Resolve and go to **Preferences** > **System** > **General**.
3. Set **External scripting using** to **Local**.
4. Restart Resolve.
5. Create a project named `lala6`. `services/batch_queue.py` loads it by
   that name. Copy its settings from the current DRS; they are not in git.
6. Close Resolve. The pipeline opens and closes it by itself, every hour.

!!! warning
    Do not use Resolve by hand on DRS. The batch step kills Resolve at the
    start and end of every batch.

### Camera settings

Do this on each FX30:

1. Set the USB connection mode to remote shooting. In Sony's SDK guide this
   is **Remote Shoot (PC Remote)** under **Setup** > **USB** > **USB
   Connection Mode**; the exact menu path on the FX30 may differ, see the
   FX30 help guide under "PC Remote".
2. Set the clip name so files start with the camera's position letter and the
   date: `L`, `M`, `R` (and `A`, `B` for extra cameras), for example
   `M20251001_2313.MP4`. The pipeline only accepts this pattern.
3. Insert a memory card with free space.
4. Connect the camera by USB and turn it on.

### Camera Control and the server

These files are in
[signlab_camera-control](https://github.com/Amsterdam-Humanities-Labs/signlab_camera-control)
on the server. A new studio needs them changed:

1. **Camera serials.** `opnameView.html` lists the serials of the five
   current cameras in `CAMERA_MAP` (and again in `cameraArray` in the **O**
   key handler). The number of entries is the number of cameras the page
   expects. With other cameras or only three, every take warns *Niet alle
   cameras online!*. List exactly your cameras. Read the serials with
   `curl -s localhost:8080/api/status`: the ID in brackets in `"model"`, for
   example `ILME-FX30 (D4DA001EC952)`.
2. **Camera server address.** `fx30proxy.php` reaches the camera server at
   `signlabs-mini.taila8bdbd.ts.net:8080`. Change `$DEFAULT_HOST` to your
   Mac's Tailscale name, or open Camera Control with
   `?camhost=<name>:8080`.
3. **Capture log.** `fx30capturelog.php` copies the expected clip names to
   the Mac over ssh, to a fixed address and key. Change them, and turn on
   **Remote Login** on the Mac.

### macOS

1. Log in to Tailscale on the same tailnet as the SignCollect server.
2. **System Settings** > **Privacy & Security**: give Terminal and
   `/usr/bin/python3` **Accessibility** and **Input Monitoring** (for
   `mouse.py` and `keyboard_monitor.py`), and allow **Automation** of System
   Events (the batch step hides Resolve).
3. Allow the macFUSE system extension, if you use rclone.
4. Set the Mac never to sleep. `mouse.py` also keeps it awake.
5. Allow Chrome to use the camera and microphone for Camera Control.

### Research drive

With `--rclone`, create on the research drive:

1. The folder `AIHR-FGW-TEST-SIGNLAB (Projectfolder)/studioFiles`.
2. The empty marker file
   `AIHR-FGW-TEST-SIGNLAB (Projectfolder)/do_not_remove_for_rclone`.
   `startupScript.py` uses it to check that the mount is healthy.

## Start and verify

1. Log out and in again, or run
   `launchctl kickstart gui/$(id -u)/nl.signcollect.drs-startup`.
2. Check that the pipeline runs:

    ```bash
    ps -p $(cat ~/drs/startup.pid)
    tail ~/drs/startup.log
    ```

3. Check the mount (with a research drive):
   `ls "$HOME/signCollect/AIHR-FGW-TEST-SIGNLAB (Projectfolder)/do_not_remove_for_rclone"`.
   The mount check waits 30 minutes after rclone starts.
4. Start the controller app:
   `/Users/signlab/signlab_Sony-SDK-MACOS-API/pyqtController/run.sh`. It
   starts the camera server and opens the QR screen.
5. Open <http://localhost:8080>. Every camera should be listed as connected.
6. Open Camera Control on the server and check the camera count in the top
   bar.
7. Open the [client monitor](../interfaces/client-monitor.md). The `drs-*`
   clients (for example `drs-converter`, `drs-batch-queue`) should send
   heartbeats.
8. Record one test take and follow it through [the capture day](workflow.md).

Service logs are in `~/drs/logs/<service>.log`. More checks are in the
pipeline's operator manual (`docs/manual.md` in signlab_drs-pipeline).

## Related

- [Requirements](requirements.md)
- [Physical setup](physical-setup.md)
- [Troubleshooting FX30 connections](troubleshooting-fx30.md)
- [Installing a demo host](../admin/install.md)
