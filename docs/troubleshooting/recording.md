# Recording sessions and camera control

Problems during a studio session with the five Sony FX30 cameras: the Camera Control page, QR codes, card handling and downloading clips. The cameras are driven by a controller program on the studio Mac (DRS).

!!! warning "When in doubt, do not record"
    A take recorded with a camera missing cannot be repaired later. Fix the camera first, then record.

### "LET OP: slechts N van de 5 cameras online! Niet opnemen" {#rec-cameras-offline}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** fewer than five cameras are connected to the studio Mac. A camera is off, its USB cable is loose, or its battery is empty.

**Try this:**

1. Do not record.
2. Check that every camera is switched on and has a charged battery.
3. Check the USB cable at both ends of each camera.
4. Wait a few seconds for the banner to update.
5. If a camera stays missing, ask an administrator to rescan the cameras and reset USB.

**Still stuck?** Send the time, how many cameras the banner shows, and which camera position is missing.

### Cameras disappear from the page while downloading or scanning {#rec-cameras-hidden}

**Type:** user error · **Who can fix:** you

**Likely cause:** this is normal. While the controller scans, downloads or lists files, the camera banner is hidden on purpose.

**Try this:**

1. Wait until the scan or download finishes.
2. Check the banner again.

**Still stuck?** If cameras are still missing after the operation, see [only N of 5 cameras online](#rec-cameras-offline).

### "Camera controller niet bereikbaar" {#rec-controller-unreachable}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the camera controller program on the studio Mac is not running, or the studio Mac is off the network. Nothing restarts the controller automatically.

**Try this:**

1. Check that the studio Mac is on.
2. Reload the Camera Control page.
3. Ask an administrator to start the controller. Only one copy may run: two controllers fight over the cameras.

**Still stuck?** Send the time and the exact message, for example "Controller unreachable: …".

### "Een van de camera's reageert niet — Alle opnames zijn gestopt" {#rec-camera-not-responding}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** one camera stopped answering during a take. To keep the takes in sync, all recordings stop.

**Try this:**

1. Check that every camera is on and connected.
2. Look at the camera screens for an error or a full card.
3. Record the take again.
4. If it happens again, ask an administrator to rescan the cameras.

**Still stuck?** Send the time, the theme and gloss you were recording, and which camera showed a problem.

### I cannot start recording: "Download in progress" or "Listing in progress" {#rec-busy}

**Type:** user error · **Who can fix:** you

**Likely cause:** the cameras are busy with a download or file listing. You cannot record at the same time.

**Try this:**

1. Wait until the download or listing finishes.
2. Start recording again.

**Still stuck?** If the download never finishes, send the time and the progress shown.

### "Kan niet formatten" {#rec-format-blocked}

**Type:** user error · **Who can fix:** you / administrator

**Likely cause:** formatting the cards is blocked while a scan, download or file listing runs, or while the controller is unreachable.

**Try this:**

1. Wait until the scan or download finishes.
2. Make sure every clip is downloaded (no ✗ in the take list) before you format.
3. If the message says "Controller niet bereikbaar", see [controller unreachable](#rec-controller-unreachable).

**Still stuck?** Send the time and the exact message.

### "Let op, weinig geheugen of lage batterij!" {#rec-battery}

**Type:** user error · **Who can fix:** you

**Likely cause:** a camera's card is almost full or its battery is low.

**Try this:**

1. Swap the battery or the card.
2. After a battery swap, redo the Charuco calibration. The warning says so because the camera may have moved.

**Still stuck?** Not needed.

### "LET OP: CAMERA OVERVERHIT" {#rec-overheat}

**Type:** user error · **Who can fix:** you

**Likely cause:** a camera reports that it is too hot, or about to be.

**Try this:**

1. Pause recording.
2. Let the camera cool down. Improve the air flow around it if you can.
3. Continue when the warning is gone.

**Still stuck?** Send the time and which camera position overheats.

### The page stays on "Wachten op piep" {#rec-waiting-beep}

**Type:** user error · **Who can fix:** you

**Likely cause:** the page listens for the start beep. The sound is off or too quiet.

**Try this:**

1. Turn the sound on.
2. Set the volume to at least 60%.
3. Try the take again.

**Still stuck?** Send the time and which computer you used.

### The QR preview shows the wrong camera {#rec-wrong-webcam}

**Type:** user error · **Who can fix:** you

**Likely cause:** the page looks for the Elgato HD60 capture device. It did not find it, so it uses the default camera.

**Try this:**

1. Connect the Elgato.
2. Reload the page.
3. Allow camera access if the browser asks.

**Still stuck?** Send the time and the browser you used.

### "Error loading themas - check console" {#rec-themes}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the page could not load the list of themes from the server.

**Try this:**

1. Reload the page.
2. Check whether other SignCollect pages work (see [Server and system](system.md)).

**Still stuck?** Send the time and the exact message.

### "Error: Unable to save the video." {#rec-save-take}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the server could not store the take record.

**Try this:**

1. Note the theme and gloss of the take.
2. Record the take again.
3. Report it.

**Still stuck?** Send the time, theme and gloss.

### The Camera Control page says "not logged in" {#rec-not-logged-in}

**Type:** user error · **Who can fix:** you

**Likely cause:** your SignCollect session expired.

**Try this:**

1. Log in again on `signcollect.nl`.
2. Reload the Camera Control page.

**Still stuck?** See [Login and accounts](login.md).

### There is no camera panel on the Camera Control page {#rec-no-camera-panel}

**Type:** user error · **Who can fix:** you

**Likely cause:** you are on a demo host. Demo hosts have no link to the studio cameras.

**Try this:**

1. Use `signcollect.nl` in the studio.

**Still stuck?** If `signcollect.nl` also shows no panel, see [controller unreachable](#rec-controller-unreachable).

### A clip has a ✗ in the take list {#rec-not-downloaded}

**Type:** user error · **Who can fix:** you

**Likely cause:** the clip has not been downloaded from the camera yet.

**Try this:**

1. After the session, download all clips.
2. Download them to the staging area, never straight to the research drive.
3. Do not format the cards until every ✗ is gone.

**Still stuck?** Send the date and the take IDs that stay on ✗.

### The QR code was read, but the take is not linked to its gloss {#rec-qr-not-linked}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the QR scanner on the studio Mac could not reach SignCollect when it read the code, or it did not recognise the code (for example, the code was partly cut off by the monitor edge).

**Try this:**

1. Check the studio archive for that date (see [missing angles](video-processing.md#vp-missing-angle)).
2. Report the date.

**Still stuck?** Send the recording date, the theme and the gloss or take IDs that are not linked.

!!! note "For the administrator"
    The DRS pipeline has tools to replay stored QR results for a date and to re-read QR codes, including partly cut-off ones. Run them with the dry-run option first.

### The list of expected clips for today is incomplete {#rec-capture-log}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** "capture log failed" means the page could not write the list of clips it expected. Matching takes to clips later becomes harder.

**Try this:**

1. Note the time and the takes you recorded after the message.
2. Report it the same day.

**Still stuck?** Send the date, time and the takes involved.

### A gloss is marked as recorded, but I need to record it again {#rec-rerecord}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** once a take is saved, the gloss counts as recorded for that signer and theme.

**Try this:**

1. Ask an administrator to clear the recorded markers for that signer and theme.

**Still stuck?** Send the signer's account name, the theme and the glosses to redo.
