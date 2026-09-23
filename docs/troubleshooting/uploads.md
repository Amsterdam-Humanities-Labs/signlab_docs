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

**Likely cause:** the file type is not allowed ("bad_extension"), the file is too large ("upload_failed"), or the gloss no longer exists ("gloss_not_found"). Errors about the uploads folder are server problems.

**Try this:**

1. Use one of these types: mp4, webm, mov, m4v, mkv.
2. Make the file smaller: trim it or lower the resolution.
3. Reload the gloss page to check that the gloss still exists.
4. Report errors that mention the uploads folder.

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

**Likely cause:** with the delete option ticked, status "Opnieuw" marks the videos for deletion. The message says how many ("N video(s) op DELETE gezet").

**Try this:**

1. Ask an administrator to undo it on the undelete page.
2. Next time, leave the delete option unticked if you want to keep the videos.

**Still stuck?** Send the text ID and the time.

### Patient-info shows "Configuration error" {#up-hh-config}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** a shared component that patient-info needs is not installed on this host.

**Try this:**

1. Report it.

**Still stuck?** Send the address and the time.
