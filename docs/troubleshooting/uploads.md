# Uploads, tokens, the API and patient-info

Problems with uploading your own videos, with upload tokens for capture machines, with the SignCollect API, and with the patient-info texts.

### "Camera-toegang geweigerd" or "Kon niet starten" when I record in the browser {#up-camera-denied}

**Type:** user error · **Who can fix:** you

**Likely cause:** you blocked camera access, or your browser cannot record WebM video.

**Try this:**

1. Click the camera or lock icon in the address bar and allow the camera.
2. Close other apps that use the camera.
3. Use Chrome or Edge, and reload the page.

**Still stuck?** Send your browser name and the gloss you tried to record.

### My video upload fails {#up-video-failed}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the error code says why:

- `upload_failed`: the file did not arrive, usually because it is too large.
- `gloss_not_found`: the gloss was deleted or hidden while you recorded.
- `bad_extension`: a capture machine sent a file type that is not allowed. This only happens with machine uploads (LSM studio videos), which accept mp4, webm, mov, m4v and mkv.
- `uploads_dir_unwritable` or `move_failed`: the server cannot write to its uploads folder.

**Try this:**

1. For `upload_failed`: record a shorter video and upload again.
2. For `gloss_not_found`: reload the gloss page and check that the gloss still exists.
3. For `bad_extension`: convert the file to mp4 on the capture machine.
4. Report `uploads_dir_unwritable` and `move_failed` to an administrator.

**Still stuck?** Send the file name, size, the gloss and the error code.

### Uploads from a capture client are refused with a token error {#up-token}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** mocap packages, SAM 3D body jobs and the segmentation service need an upload token. The token on the client is missing, wrong, or was changed on the server ("Invalid or missing X-Api-Token", "Invalid or missing API token").

**Try this:**

1. Check whether the token was changed recently, for example after an update.
2. Ask an administrator for the current token. Never send tokens by open chat or email.

**Still stuck?** Send the client name, the time and the message (without the token).

### The API returns "Search query is required" {#up-api-query}

**Type:** user error · **Who can fix:** you

**Likely cause:** the search call was sent without a search term. When you send several words, all of them must match.

**Try this:**

1. Add a search term.
2. Use fewer words if you get no results.
3. Results come in pages of 8 by default, and at most 100.

**Still stuck?** Send the full request (without any key).

### Autocomplete returns nothing {#up-api-autocomplete}

**Type:** user error · **Who can fix:** you

**Likely cause:** autocomplete needs at least 3 characters.

**Try this:**

1. Type at least 3 characters.

**Still stuck?** Not needed.

### The API says "No video data found" or "Invalid type parameter" {#up-api-video}

**Type:** user error · **Who can fix:** you

**Likely cause:** the type must be one of `zin`, `glos`, `nmm` or `sb`, and an ID is required. "No video data found for sentence ID" means that sentence has no video.

**Try this:**

1. Check the type and the ID in your request.
2. Check in the sentence overview that the sentence has a video.

**Still stuck?** Send the request and the answer.

### The theme list or random video from the API is out of date {#up-api-cache}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** both are cached for 24 hours.

**Try this:**

1. Wait a day, or ask an administrator to clear the cache.

**Still stuck?** Send what you expected to see.

### The submit form says "Missing required fields" or "Invalid email format" {#up-submit}

**Type:** user error · **Who can fix:** you

**Likely cause:** a required field is empty, or the email address is not valid.

**Try this:**

1. Fill in every field the message names.
2. Check the email address for typos.

**Still stuck?** Send the message.

### Patient-info: "Not authenticated — log in" {#up-hh-auth}

**Type:** user error · **Who can fix:** you

**Likely cause:** your SignCollect session is missing, expired, or your account is blocked.

**Try this:**

1. Log in on `signcollect.nl`.
2. Open patient-info from the menu again.

**Still stuck?** See [Login and accounts](login.md).

### Patient-info: setting status "Opnieuw" deleted the videos {#up-hh-opnieuw}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** status "Opnieuw" always marks all videos of that text for deletion. The page asks to confirm first ("Let op: status "Opnieuw" zet alle gekoppelde video's op DELETE"). After you click **OK**, the message says how many ("N video(s) op DELETE gezet").

**Try this:**

1. Ask an administrator to undo it. Send the text ID.
2. Next time, click **Cancel** in the confirmation if you want to keep the videos. The status then stays as it was.

**Still stuck?** Send the text ID and the time.

!!! note "For the administrator"
    The undelete page in the Zinnen interface does not cover patient-info videos. Reset them in the database: `UPDATE matched_transcriptions SET added = '1' WHERE m_transcription = <text ID> AND zOg = 'tekst' AND added = 'DELETE';`. Check the row count first with a `SELECT`, because this also restores videos that were deleted on purpose earlier.

### Patient-info shows "Configuration error" {#up-hh-config}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the shared library that patient-info needs (signcollect-lib, in `/web/lib`) is not installed on this host. The full message is "Configuration error: signcollect-lib is not installed.".

**Try this:**

1. Report it.

**Still stuck?** Send the address and the time.
