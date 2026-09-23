# Annotation editors (subBeta8 and 3DAnn3)

Problems in the two sentence editors: **subBeta8**, the video and EAF editor with AI suggestions, and **3DAnn3**, the editor for 3D motion-capture animations. Both open from the sentence (zin) overview. For the overview itself, see [Sentence annotation](annotation.md).

!!! warning "Never close a tab that says saving failed"
    Both editors save automatically. If a save fails, your changes live only in the open tab. Keep it open until you see a successful save.

### The editor sends me to the login page {#ed-login-redirect}

**Type:** user error · **Who can fix:** you

**Likely cause:** subBeta8 checks that you are logged in to SignCollect before it opens. Your session expired, or you opened the link in a new browser.

**Try this:**

1. Log in on `signcollect.nl`.
2. Open the sentence again from the sentence overview.

**Still stuck?** Send the editor address and the time. See also [Login and accounts](login.md).

### "Could not load video file" {#ed-video-not-found}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the editor looks for the studio video first among processed videos and then among raw videos. It found it in neither place.

**Try this:**

1. Check the file name in the address bar. It must match the take you meant to open.
2. Open the sentence again from the overview instead of a copied link.
3. If the name is right, report it.

**Still stuck?** Send the sentence ID, the file name from the popup and the time.

### The header says "Error loading sentence." {#ed-sentence-load}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the editor could not fetch the sentence from the server.

**Try this:**

1. Reload the page.
2. Open a different sentence. If that works, only this sentence is affected.

**Still stuck?** Send the sentence ID, the address and the time.

### "Autosave failed" or "Save failed", and my changes are not saved {#ed-save-failed}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the server refused the save. The popup shows its reason after the colon.

**Try this:**

1. Do not close the tab.
2. Copy the error text after "Autosave failed:".
3. Make a small edit to trigger a new save. Wait for "Saving successful".
4. If it fails again, report it and keep the tab open.

**Still stuck?** Send the sentence ID, the full error text and the time.

### "Network error - changes NOT saved!" {#ed-network-error}

**Type:** user error · **Who can fix:** you

**Likely cause:** your computer lost the connection while the editor was uploading the file.

**Try this:**

1. Check your Wi-Fi or network cable.
2. When the connection is back, make a small edit. This triggers a new save.
3. Wait for "Saving successful" before you leave the page.

**Still stuck?** If other sites work but saving keeps failing, send the sentence ID and the time.

### Leaving the page asks "Opslaan is mislukt. Toch de pagina verlaten?" {#ed-leave-warning}

**Type:** both · **Who can fix:** you

**Likely cause:** the last save failed. The editor tries one final save when you leave, but that last attempt may not arrive.

**Try this:**

1. Click **Cancel** to stay on the page.
2. Fix the connection or wait a moment.
3. Make a small edit and wait for "Saving successful". Then leave.

**Still stuck?** See [Autosave failed](#ed-save-failed).

### Handshape search says "No video filename found" {#ed-no-filename}

**Type:** user error · **Who can fix:** you

**Likely cause:** the editor was opened without a video name in its address, for example from a shortened or edited link.

**Try this:**

1. Go back to the sentence overview.
2. Open the sentence from there.

**Still stuck?** Send the address you used.

### "Handshape recognition failed" {#ed-handshape-failed}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the handshape recognition service failed or could not be reached.

**Try this:**

1. Wait a few minutes and try again.
2. Use the normal gloss search in the meantime.

**Still stuck?** Send the sentence ID, the full error text and the time.

### "No glosses match the detected handshapes and sentence words." {#ed-no-gloss-match}

**Type:** user error · **Who can fix:** you

**Likely cause:** this is not an error. The combination of detected handshapes and words in the sentence is too narrow.

**Try this:**

1. Use the normal gloss search instead.

**Still stuck?** Not needed.

### Auto-segmentation shows an error dialog {#ed-segmentation-error}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the dialog names the reason. "No video loaded yet." means you clicked too early. "No segments detected in the video." means the segmenter found nothing. "No “Signbank ID glossen” segments to spot." means you ran Spot before Segment.

**Try this:**

1. Wait until the video plays.
2. Run **Segment** first, then **Spot**.
3. If you see "Segmentation failed: …" or "Could not upload video to the spotter: …", report it.

**Still stuck?** Send the sentence ID and the exact dialog text.

### "WebSocket connection error. Make sure ISS Server is running." {#ed-websocket}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** auto-segmentation uses a live connection to a service on the server. That service is down, or your network blocks this kind of connection.

**Try this:**

1. Try again once.
2. If you are on a guest or company network, try another network.
3. If it still fails, report it.

**Still stuck?** Send the time, your network (for example "UvA Wi-Fi"), and the exact message.

### "Segmentation is already in progress. Please wait." {#ed-segmentation-busy}

**Type:** user error · **Who can fix:** you

**Likely cause:** you clicked Segment again while the first run is still busy.

**Try this:**

1. Wait until the progress dialog closes.

**Still stuck?** If the progress dialog does not close after several minutes, reload the page and send the sentence ID.

### 3DAnn3: "Please wait for base character to load first" {#ed-3d-loading}

**Type:** user error · **Who can fix:** you

**Likely cause:** the 3D avatar is a large file and is still loading. Your browser also needs WebGL.

**Try this:**

1. Wait until the avatar appears.
2. On a slow connection, give it a minute.
3. If nothing appears, try Chrome or Edge on a desktop computer.

**Still stuck?** Send the address and your browser name.

### 3DAnn3: "Error loading animation" or "No animation found in GLB" {#ed-3d-glb}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the 3D animation file for this take is missing or broken, or the link points to the wrong file.

**Try this:**

1. Open the sentence again from the overview.
2. Check in the [GLB viewer](mocap.md#mo-glb-viewer) whether the animation exists.

**Still stuck?** Send the sentence ID, the take ID and the error text.

### 3DAnn3: "Let op: opgeslagen bestand wijkt af van editor!" {#ed-3d-mismatch}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** after saving, the editor reads the file back. The saved file differs from what you see in the editor.

**Try this:**

1. Keep the tab open.
2. Save again.
3. Report it, even if the second save works.

**Still stuck?** Send the sentence ID and the time of both saves.

### 3DAnn3: Sync says "Geen mp4-annotatie gevonden" or "niets gesynct" {#ed-3d-sync}

**Type:** both · **Who can fix:** you

**Likely cause:** Sync copies annotations from the video annotation of the same sentence. That annotation does not exist yet, or the tier you sync from is empty. "… nog niet opgeslagen" means the sync worked but is not saved yet.

**Try this:**

1. Annotate the video version of the sentence first, in subBeta8.
2. Try Sync again.
3. After a successful sync, wait until the editor saves.

**Still stuck?** Send the sentence ID and the exact toast text.

### 3DAnn3: nothing happens when I click to open the 2D video {#ed-3d-popup}

**Type:** user error · **Who can fix:** you

**Likely cause:** the video opens in a new tab, and your browser blocked the pop-up.

**Try this:**

1. Allow pop-ups for `signcollect.nl` (see [Pop-ups are blocked](browser.md#br-popups)).
2. Click the button again.

**Still stuck?** If the new tab says "No 2D studio video found for this animation", send the sentence ID.
