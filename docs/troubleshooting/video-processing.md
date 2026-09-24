# Video processing and studio archive

At the end of the capture day, the studio Mac (DRS) downloads the clips from the cameras and copies them to the research drive. It then renders them, crops them, makes thumbnails and uploads the results to SignCollect. Problems here show up later, as a video that is missing, cut off, or has the wrong background.

For how the DRS pipeline is set up, see [Installing DRS](../studio/install-drs.md) and [Studio workflow](../studio/workflow.md).

!!! tip "Processing is not instant"
    Clips younger than 10 minutes wait for the next copy run (every 15 minutes). Rendering runs every hour; cropping and converting every 15 minutes. Today's clips may not be visible until later today.

### The video is not cropped correctly: the sign is cut off {#vp-bad-crop}

**Type:** system error · **Who can fix:** you / administrator

**Likely cause:** the automatic crop placed the frame too tight, so a hand leaves the picture.

**Try this:**

1. Open the [Crop Fix Manager](../interfaces/crop-fix-manager.md) from the menu.
2. Add the take.
3. Mark which edges the sign crosses: top, left, right or bottom.
4. To queue every take labelled "GEBAAR UIT DE BEELD" at once, click **Populate from "GEBAAR UIT DE BEELD"**.

**Still stuck?** Send the take ID and the edges. The re-crop service on the studio Mac is started by hand; ask an administrator if the queue does not move. See also [Fix a crop](../guides/fix-crop.md).

### The video was not cropped at all {#vp-no-crop}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the crop step found no person in the frame (`pose_detection_failed`). It retries every run, but the same clip keeps failing.

**Try this:**

1. Check the raw video. If the signer is outside the frame or the picture is dark, the take may need to be recorded again.
2. Report the take.

**Still stuck?** Send the take ID and the recording date.

!!! tip "Usually a trial video"
    "No person detected" almost always means the clip was a trial recording,
    made to test the capture. Those clips can be ignored.

### Crop Fix Manager: "Crop fix already requested for this file" {#vp-crop-duplicate}

**Type:** user error · **Who can fix:** you

**Likely cause:** someone already added this take to the queue.

**Try this:**

1. Find the take in the queue list.
2. Wait for it to be processed.

**Still stuck?** Not needed.

### Crop Fix Manager: "m_file not found" or "No valid files found" {#vp-crop-not-matched}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** crop fixes are keyed on the middle-camera file of a take. The take is not matched to its clips yet, or you typed the name in the wrong format ("Invalid m_file format").

**Try this:**

1. Copy the file name from the studio archive instead of typing it.
2. If the take has no middle-camera clip in the archive, wait for processing or see [missing angles](#vp-missing-angle).

**Still stuck?** Send the take ID and the exact error text.

### Crop Fix Manager gives a 500 error, "Unexpected end of JSON input" or "Failed to write crop fixes file" {#vp-crop-500}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the page cannot read its database settings, or cannot write its data file on the server. "Unexpected end of JSON input" means the server answered with an error instead of data.

**Try this:**

1. Reload once.
2. Report it.

**Still stuck?** Send the time and the exact text.

!!! note "For the administrator"
    Check that `videoFix/mysql_config.php` exists in the web root and that `videofix_data/crop_fixes.json` is writable by the web server. On a demo host, running the install again recreates the link.

### My crop fix stays "unresolved" {#vp-crop-unresolved}

**Type:** both · **Who can fix:** administrator

**Likely cause:** a fix is only marked resolved when the studio Mac reports the new crop back. Each angle (left, middle, right) has its own status. The re-crop service is not started automatically.

**Try this:**

1. Check which angle is still open.
2. Ask an administrator to run the re-crop service.

**Still stuck?** Send the take ID and the angle.

### The green screen was not replaced with blue {#vp-green-screen}

**Type:** both · **Who can fix:** you

**Likely cause:** part of the background was not covered by the automatic replacement.

**Try this:**

1. Open Background Fix at `signcollect.nl/videoBackgroundFix/`. It is not in the menu.
2. Pick the date and camera.
3. Draw mask boxes over the parts that must become blue. The default colour is the studio blue.
4. Preview the result.
5. Run the batch. It ends with "Batch complete: X done, Y error".
6. Check the result. If it looks wrong, restore the original.

**Still stuck?** Send the date, camera, take ID and the batch summary ("Batch complete: X done, Y error").

!!! note
    Background Fix also widens the video to a width of 1.15 times its height, padding the sides with blue. If it cannot find the signer, it centres on the middle of the frame. It needs the studio file service, so on a demo host it only shows "Could not load date list".

### Background Fix shows "render failed", "source missing" or "no backup" {#vp-bgfix-errors}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:**

- "Date must be YYYYMMDD": the date is typed wrong.
- "source missing": the original clip is not there.
- "no backup" (on restore): there is no original to go back to.
- "render failed" or "probe failed": processing the file failed.

**Try this:**

1. Type the date as eight digits, for example `20260923`.
2. Only studio clip names are accepted; pick files from the list.
3. For "render failed" or "source missing", report it.

**Still stuck?** Send the date, camera, file name and message.

### Background Fix says "Could not load date list" {#vp-bgfix-dates}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** Background Fix could not reach the service that lists recording dates. On a demo host this is expected.

**Try this:**

1. Reload after a minute.
2. Report it if it continues.

**Still stuck?** Send the time and the exact message.

### The video has the wrong shape after cropping {#vp-aspect}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the target shape is a width of 1.15 times the height (1440 × 1252). A clip that ends up with a different shape is listed in a dimension report (`dimension_issues.json`).

**Try this:**

1. Report the take IDs.

**Still stuck?** Ask an administrator to reprocess the clips from the dimension report.

### A camera angle is missing, or I see a grey placeholder {#vp-missing-angle}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the archive shows the processed image, then the raw thumbnail, and otherwise a placeholder. "Missing" means the take was logged but no clip was matched to it: the clip was not downloaded, or its QR code was not read (for example because the QR screen was not in view of the cameras). With three or four cameras, the angles of the cameras you did not use are always empty.

**Try this:**

1. Open the studio archive and pick the date.
2. Look at the date status panel ("Missing: N") and at the gloss ("N missing").
3. Check whether the clips were downloaded (see [clip has a ✗](recording.md#rec-not-downloaded)).
4. Report the date if clips were downloaded but are still missing.

**Still stuck?** Send the date, the glosses marked missing and the camera angles.

### The cropped video or thumbnail is missing on the website {#vp-upload-missing}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the studio Mac processed the clip, but the upload to SignCollect failed ("Upload failed" in the crop log). The crop step does not retry uploads, so waiting does not help.

**Try this:**

1. Report the date.

**Still stuck?** Send the date and take IDs.

!!! note "For the administrator"
    On the studio Mac, in `~/drs`, run `python3 tools/backfill_post_uploads.py <YYYY-MM-DD> --dry-run`. Check the list, then run it again without `--dry-run`.

### Thumbnails are missing or wrong for a whole date {#vp-thumbnails}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** conversion or thumbnail creation failed for that date, or the thumbnail upload failed.

**Try this:**

1. Report the date.

**Still stuck?** Ask an administrator to send the thumbnails again for that date.

!!! note "For the administrator"
    On the studio Mac, in `~/drs`: `python3 tools/backfill_post_uploads.py <YYYY-MM-DD> --thumbs-only --dry-run`, then without `--dry-run`.

### A clip was never rendered {#vp-never-rendered}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the render step marked the clip to skip, with a reason such as "Failed to create timeline", or the clip is in the wrong date folder ("date mismatch"). Clips older than 62 days are no longer picked up.

**Try this:**

1. Do not open DaVinci Resolve on the studio Mac yourself. The batch closes it by force and your work is lost.
2. Report the clip.

!!! note "For the administrator"
    The reason is in `post_noncropped/<clip>.skip` for that date. Fix the cause, delete the `.skip` file and wait for the next hourly run.

**Still stuck?** Send the date, take ID and camera.

### A clip is on the studio Mac but not on the research drive {#vp-not-copied}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** clips younger than 10 minutes wait for the next 15-minute run. Empty (zero-byte) clips are never copied. When the research drive is not mounted on the studio Mac, copying pauses.

**Try this:**

1. Wait 30 minutes and check again.
2. If it is still missing, report it.

**Still stuck?** Send the date, take ID and camera.

### Nothing from today's session is being processed {#vp-pipeline-stopped}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the pipeline supervisor on the studio Mac (`startupScript.py`) is not running, or a step crashed five times in five minutes and restarts are paused for 15 minutes.

**Try this:**

1. Check that the capture day has ended: the automatic download starts then.
2. Wait 15 minutes.
3. If nothing moves, report it.

!!! note "For the administrator"
    On the studio Mac: `ps -p $(cat ~/drs/startup.pid)` must show `startupScript.py`. If a single service stopped, `grep "Disabling restarts" ~/drs/startup.log` names it.

**Still stuck?** Send the date and when the session ended.

### The studio archive shows "Network Error" or "No videos found" {#vp-archive-empty}

**Type:** both · **Who can fix:** you

**Likely cause:** your connection dropped, or there are no processed videos for the date you picked.

**Try this:**

1. Check your network and reload.
2. Check the date. Processing can take hours after a session.

**Still stuck?** Send the date and the time you tried.
