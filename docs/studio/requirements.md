# Studio requirements

A checklist of what a SignCollect recording studio needs, and why.
**Required** items are needed for the pipeline to work. **Recommended** items
make the studio reliable or easier to run.

## Hardware

| Item | Required? | Why |
|---|---|---|
| 3 to 5 Sony FX30 cameras | Required (3 minimum) | The camera server only connects to FX30s. The pipeline renders and crops the left, middle and right cameras (`L`, `M`, `R`). Cameras `A` and `B` are extra angles: they are converted and uploaded, but not rendered or cropped |
| USB-C cable per camera, direct to the Mac or a powered hub | Required | The cameras are controlled and downloaded over USB. Use data cables, not charge-only cables |
| Spare batteries or mains power for the cameras | Recommended | Downloading at the end of the day needs a battery of at least 50% |
| Memory card per camera | Required | Clips are recorded on the camera and downloaded afterwards |
| Studio Mac (Mac mini or macOS laptop), Apple Silicon | Required | Runs the camera server, DaVinci Resolve Studio and the pipeline. The pipeline calls `/opt/homebrew/bin/ffmpeg`, the Homebrew path on Apple Silicon |
| External disk named `cacheDisk` | Required | Camera downloads go to `/Volumes/cacheDisk/fx30_staging`, and the rclone cache to `/Volumes/cacheDisk/rclone` (allowed to grow to 4000 GB). Plan several terabytes |
| Three screens | Required | One for the operator (Camera Control), one for the QR code facing the cameras, one for the signer. See [physical setup](physical-setup.md#screens) |
| Foot pedal(s) that send key presses | Recommended | The operator or signer starts and stops takes hands-free. Camera Control listens to the **B** and **A** keys |
| Elgato HD60 (HDMI capture) | Recommended | Camera Control uses it for its live view and to check at start-up that the QR screen is visible. Without it, the page uses the Mac's default camera |
| Speakers | Required | Camera Control plays a beep at the start and end of each take and waits for it (*Wachten op piep*). Set the volume to 60% or more |
| Green screen | Required | DaVinci Resolve keys out the green background and puts the signer on the studio blue (the Fusion composition in `config/Settings.setting`) |
| Studio lights | Required | Even light on the green screen gives a clean key; light on the signer keeps hands sharp for cropping |
| Wired network (ethernet) | Required | The pipeline uploads large files. `network_manager.py` watches the ethernet port `en0` and restarts it when it fails |

## Software

| Item | Required? | Why |
|---|---|---|
| macOS 12.1 or later | Required | The camera server is built for macOS 12.1 and later |
| Xcode (the full app) and Homebrew | Required | To build the camera server (`cmake -GXcode`) and install ffmpeg, Python 3.13, zbar and build tools |
| DaVinci Resolve **Studio** (paid) | Required | The pipeline drives Resolve through its external scripting API, which the free version does not offer. Buy a licence from Blackmagic Design |
| Tailscale | Required | The SignCollect server reaches the camera server on the Mac over Tailscale (`fx30proxy.php`) |
| Google Chrome | Required | The controller app opens Camera Control and the QR screen in Chrome |
| rclone (official build) and macFUSE | Recommended | Mounts the research drive. See [research drive](#research-drive) |
| The setup script `scripts/setup-drs.sh` | Required | Installs the rest. See [Install the DRS Mac](install-drs.md) |

## Accounts and access

| Item | Required? | Why |
|---|---|---|
| A SignCollect server | Required | Camera Control and the QR page (`opnameLR.html`; both in signlab_camera-control), the studioSupport websocket and the upload endpoints (`videoProc/upload2.php`, `videoProc/upload_post.php`, `renderServer`, `drs_ep/api.php`, `qr/qrResultReceiver.php`) all run there. The pipeline's server address is set with `SIGNCOLLECT_URL` |
| SignCollect login for the operator | Required | Camera Control asks for a login |
| SignCollect accounts for signers | Required | Camera Control lists glosses per signer (the gloss owner) |
| Database credentials (`DB_*` in `.env`) | Optional | Only for the repair tools `services/qrConvert.py` and `tools/check_studiofiles.py` |
| A tailnet shared with the server | Required | See Tailscale above |
| Research drive account | Recommended | See below |

!!! warning "The QR link runs through signcollect.nl"
    Camera Control and the QR page connect to `wss://signcollect.nl/studioSupport/`.
    Demo hosts have no studioSupport server, so the QR screen does not work
    there. A studio that uses a different server needs that server and those
    two pages changed.

## Research drive

A research drive (for example a WebDAV drive) connected with rclone is not
mandatory, but it is recommended: it keeps every raw clip safe off the Mac,
and it is how the current pipeline works. The controller app copies clips to
the remote `signcollect:`, and the pipeline reads and writes
`~/signCollect/AIHR-FGW-TEST-SIGNLAB (Projectfolder)/studioFiles` on the rclone
mount.

!!! note "Without a research drive"
    `startupScript.py` always tries to start the rclone mount, and the
    pipeline paths point into the mount. Running without a research drive
    needs code changes in `startupScript.py` today. The setup script warns
    about this.

## Related

- [Setting up a recording studio](index.md)
- [Physical setup](physical-setup.md)
- [Install the DRS Mac](install-drs.md)
