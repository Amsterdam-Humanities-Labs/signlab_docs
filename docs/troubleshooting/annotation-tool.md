# Annotation tool (v3, webcam and clusters)

Problems in the annotation tool v3 and its modes: the default mode for your own videos, **webcam** mode, and **clusters** mode. The old v1, v2, webcam and clusters addresses now redirect to v3.

!!! note "Where the tool works"
    The default mode runs in your browser. It has no login and uploads nothing to your account. The AI features (segmenting, spotting, Smart Search) and the fast server conversion only work on `signcollect.nl`. On a demo host, segmenting fails with "Auto-segmentation failed: segment HTTP 404", and video conversion falls back to the slower conversion in your browser.

### "Autosave needs Chrome/Edge (File System Access API)." {#at-autosave-browser}

**Type:** user error · **Who can fix:** you

**Likely cause:** Firefox and Safari cannot save to a folder on your computer.

**Try this:**

1. Open the tool in Chrome or Edge on a desktop computer.
2. Or keep your browser and use the download button to export your EAF by hand, often.

**Still stuck?** Not needed; this is how the browsers work.

### The autosave button stays on "Autosave: pick folder" or shows "Save Error!" {#at-autosave-folder}

**Type:** user error · **Who can fix:** you

**Likely cause:** you did not choose a folder yet, or the browser forgot the permission. Clearing site data also forgets the folder.

**Try this:**

1. Click the autosave button.
2. Choose the folder again and allow access.
3. Check that the button changes to a saving state.

**Still stuck?** Send your browser name and the exact text on the button.

### The tool does not work when I open it from a file on my computer {#at-file-url}

**Type:** user error · **Who can fix:** you

**Likely cause:** the tool must be opened from a web address. An address that starts with `file://` is not supported.

**Try this:**

1. Open the tool from the SignCollect menu instead.

**Still stuck?** Send the address you used.

### "This video would need about … GB of memory to load" {#at-video-memory}

**Type:** user error · **Who can fix:** you

**Likely cause:** the video is too long or too large for the browser to hold in memory.

**Try this:**

1. Cut the video into shorter clips.
2. Load one clip at a time.

**Still stuck?** Send the video length, resolution and the number in the message.

### "Video conversion failed" or "converter library failed to load" {#at-conversion-failed}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** videos that are not 25 frames per second, or larger than 1080p, are converted first. The server tries, then your browser. Both failed. "converter library failed to load" means the converter is missing on the server.

**Try this:**

1. Convert the video yourself to MP4 (H.264), 25 fps, 1080p or smaller.
2. Load the converted file.
3. If you see "converter library failed to load", report it.

**Still stuck?** Send the file's format, frame rate, size and the full error text.

### My upload is refused or conversion is very slow {#at-upload-limits}

**Type:** user error · **Who can fix:** you

**Likely cause:** uploads for conversion are limited to 3 minutes and 200 MB. Files near that limit are converted in your browser, which is slow. Uploads are removed after 24 hours.

**Try this:**

1. Trim the video to under 3 minutes.
2. Or convert it yourself (see [conversion failed](#at-conversion-failed)).

**Still stuck?** Send the file size and duration.

### The tool uses an old version of my converted video {#at-cached-video}

**Type:** user error · **Who can fix:** you

**Likely cause:** the message "Using previously converted video (cached)" means the tool reuses a copy it stored in your browser.

**Try this:**

1. Give the new video a different file name, or
2. Clear the site data for the tool (see [Browser cache](browser.md#br-cache)). This also forgets your autosave folder.

**Still stuck?** Not needed.

### "Could not parse EAF" or "Invalid EAF XML" {#at-eaf-parse}

**Type:** user error · **Who can fix:** you

**Likely cause:** the file is not a valid ELAN EAF file, or it is damaged. "Please drop an .eaf file" means you dropped another file type.

**Try this:**

1. Open the file in ELAN and save it again.
2. Drop the saved `.eaf` file on the tool.
3. Tiers without time-aligned annotations load empty. That is expected.

**Still stuck?** Send the EAF file and the full error text.

### Auto-segmentation finds nothing or fails {#at-segmentation}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** "No video loaded to segment." means no video is open. "No segments detected in the video." means the segmenter found no signs. "Auto-segmentation failed: segment HTTP …" means the segmenter on the server failed or is not there. "Segmentation is already in progress. Please wait." means an earlier run is still busy.

**Try this:**

1. Load a video first and let it play.
2. If a run is busy, wait until the progress window closes.
3. Check that you are on `signcollect.nl`, not a demo host.
4. If you see an HTTP code on `signcollect.nl`, report it.

**Still stuck?** Send the video name, the HTTP code and the time.

### A box shows "spotting failed" {#at-spotting-failed}

**Type:** system error · **Who can fix:** you / administrator

**Likely cause:** the upload to the spotter or the spotting itself failed for this box.

**Try this:**

1. Click the ↻ button next to the message to retry.
2. If many boxes fail, report it.

**Still stuck?** Send the video name, the time and how many boxes failed.

### "Smart search requires a video filename (not available in standalone mode)." {#at-smart-search}

**Type:** user error · **Who can fix:** you

**Likely cause:** Smart Search (handshape search) only works on studio videos the server knows. It does not work on a video you dropped from your own computer, or when you are offline.

**Try this:**

1. Use the normal gloss search for local videos.
2. For studio videos, open the sentence from the sentence overview instead.

**Still stuck?** If it fails on a studio video with "Handshape recognition failed", see [Handshape recognition failed](editors.md#ed-handshape-failed).

### "Restore last session from …?" {#at-restore-session}

**Type:** user error · **Who can fix:** you

**Likely cause:** the tool kept your last annotations. After a restore it asks you to drop the matching video.

**Try this:**

1. Click to restore.
2. Drop the same video file you used last time.

**Still stuck?** Not needed. Webcam mode has no session restore.

### Webcam mode: "Could not access the webcam" or "This browser has no webcam access" {#at-webcam-access}

**Type:** user error · **Who can fix:** you

**Likely cause:** you blocked camera access, another app is using the camera, or the page is not on HTTPS.

**Try this:**

1. Use Chrome or Edge, and make sure the address starts with `https://`.
2. Click the camera or lock icon in the address bar and allow the camera.
3. Close other apps that use the camera (video calls, OBS).
4. Reload the page.

**Still stuck?** Send your browser name and the full message. "Recording is not supported here" means your browser cannot record video at all; try Chrome.

### Clusters mode: "Opslaan mislukt!" or "save HTTP 401" {#at-clusters-save}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the save button shows "Opslaan mislukt!" when a save fails; the status drop-down shows "Status opslaan mislukt: save HTTP …". 401 means your SignCollect session expired. Saving also only works on the same site: a link copied to another domain cannot save. Other codes mean the server could not store the review.

**Try this:**

1. Keep the tab open.
2. Log in again on `signcollect.nl` in another tab.
3. Back in the tool, make a small edit. The button should change to **Opgeslagen op server**.
4. For the next video, open it with **open ▶** on the [Segmented videos page](../guides/review-clusters.md#3-correct-the-segments-of-each-video), not from a copied link.
5. If you see anything other than 401, report it.

**Still stuck?** Send the video name, the exact toast text and the time.

### Cluster segment view: "Missing ?video= or ?eaf= param." or "Failed to load EAF" {#at-segview}

**Type:** user error · **Who can fix:** you

**Likely cause:** the segment view (`/annotation-tool/clusters/segview.html`) shows the pipeline's own segments of one video. No page links to it, so the address must be typed in full, with both parts. "Failed to load EAF" means the `eaf=` part points to a file that does not exist.

**Try this:**

1. Use this address, with the video name in both places:
   `segview.html?video=/annotation-tool/clusters/vid/<video>.mp4&eaf=/annotation-tool/clusters/out/eaf/<video>.eaf`
2. To look at and correct a video, use **open ▶** on the Segmented videos page instead.

**Still stuck?** Send the address you used.
