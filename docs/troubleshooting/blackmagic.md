# Blackmagic cameras and research-drive copies

Problems with the Blackmagic camera in the motion-capture studio: remote control, recording, and the copies of its clips on the research drive. A control service on the Vicon PC talks to the camera.

### Every Blackmagic command fails with "not found" (404) {#bm-404}

**Type:** user error · **Who can fix:** you

**Likely cause:** Web Media Manager and the REST API are switched off in the camera settings.

**Try this:**

1. On the camera, open the network setup menu.
2. Switch on **Web Media Manager** and the **REST API**.
3. Try the command again.

**Still stuck?** Send the time and the command you used.

### The camera does not respond to control at all {#bm-no-response}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the control service on the Vicon PC is not running. It is started by hand and stops when its window closes. Or the camera is off or off the network.

**Try this:**

1. Check that the camera is on and connected to the network.
2. Ask an administrator to start the control service.

**Still stuck?** Send the time and the exact message.

### Control requests are refused with "invalid or missing X-API-Key" {#bm-api-key}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the control service now requires an API key, and the caller does not send it.

**Try this:**

1. Report it. You cannot set the key yourself.

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

**Likely cause:** the copy to the research drive is experimental and started by hand. It runs every 12 hours and skips a run when the camera service or the drive is not reachable.

**Try this:**

1. Leave the clips on the camera disk. Do not format it.
2. Report the date.

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

**Likely cause:** the nightly compression did not run, or the GPU machine that does it was down. A clip that keeps failing is parked after several tries. Nothing is lost: the originals stay on the server.

**Try this:**

1. Wait for the next night.
2. Report it if the same clip stays missing.

**Still stuck?** Send the date and clip names.

### A clip was deleted from the camera before it reached the drive {#bm-deleted-early}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the copy removes clips from the camera after it checks the upload. If that check is not configured, a clip can be removed too early.

**Try this:**

1. Stop using the camera disk for new takes.
2. Report it at once.

**Still stuck?** Send the date and clip names. The administrator should check the copy settings before the next run.
