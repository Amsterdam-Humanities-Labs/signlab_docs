# Motion capture

Problems with Vicon captures: syncing files from the Vicon PC, viconDashboard, the mocap studio page, FBX post-processing, blendbaking, the GLB viewers and the SAM 3D body queue.

!!! tip "Traffic lights in viconDashboard"
    Green means all five required parts arrived. Yellow means they arrived but files are still growing: the upload is still running. Red means a required part is really missing.

### Mocap files from today are not on the server yet {#mo-not-synced}

**Type:** both · **Who can fix:** you

**Likely cause:** the Vicon sync runs once a day at night. Captures from today only arrive after the next run, unless someone starts it by hand.

**Try this:**

1. Open the mocap studio page.
2. Click **Manual Sync**.
3. Wait for the status line to show "idle — last run N downloaded, N errors".

**Still stuck?** Send the capture date, the take name and the status text.

### Sync says "Vicon PC unreachable" {#mo-vicon-unreachable}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the Vicon PC is off, not logged in, or not on the lab network. After a Windows reinstall the PC gets a new network name, and the sync has to find it again.

**Try this:**

1. Check that the Vicon PC is on and logged in.
2. Click **Manual Sync** again.
3. If the Vicon PC was reinstalled recently, tell the administrator.

**Still stuck?** Send the time and the full text after "Vicon PC unreachable:".

### Sync finished with "Sync completed with N error(s)" {#mo-sync-errors}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** some files failed to download or convert. The rest synced.

**Try this:**

1. Check in viconDashboard which takes are red.
2. Start **Manual Sync** once more.
3. Report it if the same takes stay red.

**Still stuck?** Send the date, the error count and the take names.

### Manual Sync shows "Error (HTTP …)" or "Network error" {#mo-manual-sync-error}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** "Network error" is a problem between your browser and SignCollect. "Error (HTTP …)" means the sync service did not answer.

**Try this:**

1. Reload the page and click **Retry**.
2. If "Error (HTTP …)" returns, report it.

**Still stuck?** Send the time and the full error text.

### "Mocap sync started, but Blackmagic trigger failed" {#mo-bm-trigger}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the mocap files sync as normal, but the Blackmagic video copy on the Vicon PC did not start.

**Try this:**

1. Let the mocap sync finish.
2. Report the Blackmagic part.

**Still stuck?** Send the time. See also [Blackmagic cameras](blackmagic.md).

### The sync status says "stopped auto-refresh" {#mo-stopped-refresh}

**Type:** user error · **Who can fix:** you

**Likely cause:** this is not an error. The page stopped checking, but the sync continues in the background.

**Try this:**

1. Reload the page later to see the result.

**Still stuck?** Not needed.

### A corrected FBX on the Vicon PC was not copied again {#mo-fbx-not-updated}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the sync compares files by size. If your corrected FBX has the same size as the old one, the sync skips it.

**Try this:**

1. Tell the administrator which FBX files you changed.

**Still stuck?** Send the take names and the date you changed them. An administrator can force a full re-sync.

### My viconDashboard row stays red {#mo-row-red}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** at least one of the five required parts (OBS video, Shogun Live, Unreal, Livelink, metadata) is missing. It was not recorded, or it has not synced yet.

**Try this:**

1. Wait for the next sync, or start **Manual Sync**.
2. Check on the Vicon PC whether the part was recorded.
3. If it exists on the Vicon PC but stays red, report it.

**Still stuck?** Send the capture date, the take name and the missing column.

### A file shows as present in viconDashboard but has no download link {#mo-no-download}

**Type:** user error · **Who can fix:** you

**Likely cause:** some files stay on the Vicon PC by design: Livelink CSV, metadata JSON, the Unreal CC and Vicon folders, and Shogun post-processing files.

**Try this:**

1. Get the file from the Vicon PC.

**Still stuck?** Not needed.

### viconDashboard shows "Error loading captures" {#mo-dashboard-error}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the dashboard could not read its data from the server. It keeps showing the last list it had.

**Try this:**

1. Reload after a minute.
2. Check whether other pages work (see [Server and system](system.md)).

**Still stuck?** Send the time and the full message.

### The mocap studio page turned red {#mo-studio-red}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the page lost its connection to the Unreal relay. It tries again every 5 seconds. The relay is started by hand.

**Try this:**

1. Wait 10 seconds.
2. If it stays red, ask an administrator to start the relay.

**Still stuck?** Send the time.

### The mocap studio page shows no sentence or video {#mo-studio-no-video}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** reference videos for the sentences are missing or broken. Messages include "Failed to find a valid video after N attempts" and "No valid sentences found".

**Try this:**

1. Click to try again.
2. Pick another theme.
3. Report the theme or sentence.

**Still stuck?** Send the theme, sentence ID and exact message.

### The mocap studio skips items in a theme {#mo-theme-skip}

**Type:** user error · **Who can fix:** you

**Likely cause:** "No video found for this capture. Skipping to next..." means one item has no reference video. "No uncaptured captures found for theme" means the theme is complete.

**Try this:**

1. Pick another theme if it is complete.
2. Note skipped items and report them.

**Still stuck?** Send the theme and the skipped items.

### The FBX file manager asks me to log in or hides dates {#mo-pp-access}

**Type:** user error · **Who can fix:** you / administrator

**Likely cause:** you need a SignCollect session. If you are not an administrator, you only see the recording dates assigned to you.

**Try this:**

1. Log in on `signcollect.nl`.
2. Ask an administrator to assign the dates you need.

**Still stuck?** Send your account name and the dates.

### The FBX upload failed {#mo-pp-upload}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the file could not be stored, or the ZIP is damaged ("Failed to open ZIP file"). "Skipped system file" is not an error.

**Try this:**

1. Check that the ZIP opens on your computer.
2. Upload again.
3. If "Failed to save file" returns, report it.

**Still stuck?** Send the file name, size and exact message.

### A file is not marked "MCP Klaar" or "+EAF" {#mo-pp-klaar}

**Type:** user error · **Who can fix:** you

**Likely cause:** "Klaar" needs the post-processing status set and the Gloss field set to "Klaar". "+EAF" also needs an EAF for this take. An EAF for the whole broadcast does not count.

**Try this:**

1. Set both fields.
2. Make sure the take has its own EAF.

**Still stuck?** Send the file name.

### The avatar faces the wrong way or disappears when played {#mo-avatar-wrong}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** a direction correction was not applied to the animation, or a viewer does not handle the way the animation is attached to the skeleton. 3DAnn3 handles it; other viewers may not.

**Try this:**

1. Try the take in 3DAnn3.
2. Report the take and the viewer.

**Still stuck?** Send the take name and the page where it looks wrong.

### The avatar GLB is missing for one take {#mo-glb-missing}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** converting the FBX to a GLB failed, often because the skeleton only partly matched. The sync keeps going; an hourly job tries again.

**Try this:**

1. Wait an hour.
2. Report the take if it is still missing.

**Still stuck?** Send the take name and capture date.

### The GLB viewer rejects my upload or shows "Failed to load file list." {#mo-glb-viewer}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** only `.glb` files are accepted, and empty files are refused. "Failed to load file list." means the server did not answer.

**Try this:**

1. Check that the file ends in `.glb` and is not empty.
2. Reload the viewer.

**Still stuck?** Send the file name and the message.

### Blendbaking shows an old list or "Upstream-aanvraag mislukt" {#mo-blendbaking}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** lists are cached for 10 minutes. "Upstream" messages mean the sentence service it depends on failed. "Geen geldige SRT-bestanden gevonden." means no subtitle files were found.

**Try this:**

1. Wait 10 minutes, or add `refresh=1` to the address.
2. If an "Upstream" message stays, report it.

**Still stuck?** Send the address and the message.

### The SAM 3D body queue refuses a job {#mo-sam3d}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the worker needs an upload token ("Invalid or missing X-Api-Token"). "This file is already being processed" means another worker holds it. A take with a stuck lock is never offered again.

**Try this:**

1. Check that the worker has its token.
2. Report takes that stay locked.

**Still stuck?** Send the take name and message. See also [Uploads and tokens](uploads.md).
