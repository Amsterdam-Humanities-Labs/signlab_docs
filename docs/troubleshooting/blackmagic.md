# Blackmagic cameras and research-drive copies

Problems with the Blackmagic Studio Camera 6K Pro in the motion-capture studio: remote control, recording, and the copies of its clips on the research drive. A control service on the Vicon PC (`bmcam serve`) talks to the camera over the studio network.

### Every Blackmagic command fails with "not found" (404) {#bm-404}

**Type:** user error · **Who can fix:** you

**Likely cause:** Web Media Manager and the REST API are switched off in the camera settings.

**Try this:**

1. On the camera, open **Setup**, then **Network**.
2. Switch on **Web Media Manager** and **REST API**.
3. Try the command again.

This is a one-time setting. It can also be set in Blackmagic Camera Setup (tick **Web Media Manager** and **REST Camera Control**).

**Still stuck?** Send the time and the command you used.

### The camera does not respond to control at all {#bm-no-response}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the control service on the Vicon PC is not running. It is started by hand and stops when its window closes. Nothing restarts it. Or the camera is off or off the network.

**Try this:**

1. Check that the camera is on and connected to the network.
2. Ask an administrator to start the control service.

**Still stuck?** Send the time and the exact message.

### Control requests are refused with "invalid or missing X-API-Key" {#bm-api-key}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the control service requires an API key in the `X-API-Key` header, and the caller does not send it or sends an old one.

**Try this:**

1. In the web inspector (the control service's own page), enter the key when it asks. It keeps it in a cookie.
2. For other tools, report it. You cannot set the key yourself.

!!! note "For the administrator"
    The key is `BMCAM_API_KEY` when `bmcam serve` starts. The research-drive copy sends the same variable, so both must match.

**Still stuck?** Send the time and the tool that sent the request.

### Recording stops by itself after a few seconds {#bm-recording-stops}

**Type:** user error · **Who can fix:** you

**Likely cause:** the USB disk cannot keep up with BRAW 8:1 at 6K and 50 fps.

**Try this:**

1. Switch the codec to BRAW 12:1.
2. Or lower the resolution or frame rate.
3. Record a short test take.

**Still stuck?** Send the camera settings and the disk you used.

### There is no live preview from the Blackmagic camera {#bm-no-preview}

**Type:** user error · **Who can fix:** you

**Likely cause:** the camera firmware offers no network live view.

**Try this:**

1. Use the HDMI or SDI output for a picture.

**Still stuck?** Not needed.

### Blackmagic clips are not on the research drive {#bm-not-copied}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the copy to the research drive is experimental. It runs on the Vicon PC, started by hand, and then repeats every 12 hours. **Manual Sync** on the [Motion Capture Studio](../interfaces/mocap-studio.md) page also starts one run. A run is skipped when the camera service or the research drive is not reachable.

**Try this:**

1. Leave the clips on the camera disk. Do not format it.
2. On the Motion Capture Studio page, click **Manual Sync**, then **Yes, sync now**.
3. Check the status line: "Blackmagic: idle — last cycle N uploaded, N deleted, N failed".
4. If clips are still missing, report the date.

**Still stuck?** Send the date and clip names. An administrator can run the copy once by hand; steps that already finished are skipped.

### I find a .braw file instead of an .mp4 {#bm-braw}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** converting the clip failed, so the copy stored the original BRAW file instead.

**Try this:**

1. Open the BRAW in DaVinci Resolve if you need it now.
2. Report the clip name.

**Still stuck?** Send the clip name and date.

### The compressed "Mini" copies from last night are missing {#bm-mini}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the nightly compression (04:00, on the core server) did not run, or it failed for that clip. A clip that keeps failing is parked after several tries. Nothing is lost: the originals stay on the server.

**Try this:**

1. Wait for the next night.
2. Report it if the same clip stays missing.

**Still stuck?** Send the date and clip names.

### A clip was deleted from the camera before it reached the drive {#bm-deleted-early}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the copy removes clips from the camera after it checks the upload. It only checks that the file reached the research drive itself when an rclone remote is configured. Without that setting, a clip can be removed before the upload has finished.

**Try this:**

1. Stop using the camera disk for new takes.
2. Report it at once.

**Still stuck?** Send the date and clip names.

!!! note "For the administrator"
    Check the clip in the local staging folder (`E:\BlackmagicTemp`) on the Vicon PC; it may still be there. Before the next run, set `RCLONE_REMOTE` (for example `signcollect:`), or set `NO_DELETE_SOURCE=1` to keep clips on the camera.
