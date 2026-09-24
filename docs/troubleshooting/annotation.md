# Sentence annotation and EAF files

Problems in the sentence (zin) overview: statuses, uploading and downloading EAF files, and opening the editors. For problems inside the editors, see [Annotation editors](editors.md).

!!! warning "The last save wins"
    Two people can open the same sentence. There is no lock: whoever saves last overwrites the other. Agree who works on which sentence.

### "Invalid EAF file type." when I upload an EAF {#an-invalid-eaf}

**Type:** user error · **Who can fix:** you / administrator

**Likely cause:** the file is not an EAF (XML) file. Because of a known bug, the old EAF is set aside as a backup before the check, so the sentence may now have no EAF.

**Try this:**

1. Open the file in ELAN and save it again as `.eaf`.
2. Upload it again with **Upload EAF**.
3. If the sentence now shows no EAF and you have no good copy, ask an administrator to restore the backup (`<video>_backup_<date>.eaf`).

**Still stuck?** Send the sentence ID and the time of the failed upload.

### The upload worked, but subtitles are wrong or missing {#an-srt}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** after an upload, each tier becomes a subtitle file. "Failed to parse EAF file." means the EAF is damaged. "Failed to write SRT file for tier '…'." is a server problem.

**Try this:**

1. Open the EAF in ELAN and check that it loads.
2. Save it and upload it again.
3. If you see "Failed to write SRT file for tier", report it.

**Still stuck?** Send the sentence ID, the tier name and the message.

### My colleague's edits disappeared {#an-overwritten}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** you both edited the same sentence, and the last save won. Every save first keeps a dated copy of the old EAF, and a nightly job backs up all EAF and SRT files.

**Try this:**

1. Stop editing the sentence, so no newer save pushes the good version further back.
2. Ask an administrator to restore the copy from before the second save.
3. Agree who works on the sentence from now on.

**Still stuck?** Send the sentence ID and both save times.

### Upload says "EAF bestandsnaam verschilt van huidige bestandsnaam!" {#an-filename}

**Type:** user error · **Who can fix:** you

**Likely cause:** the upload only accepts a file whose name matches the sentence text: spaces become `_`, and all other characters are removed, including letters with accents. The name you get from **Download EAF (MP4)** is the right one. A renamed file is refused. Text in brackets, such as ` (1)` from a second download, is ignored.

**Try this:**

1. Give the file back the name it had when you downloaded it.
2. Upload it again.

**Still stuck?** Send the sentence ID and the file name.

### ELAN cannot find the video of a downloaded EAF {#an-elan-media}

**Type:** user error · **Who can fix:** you

**Likely cause:** the EAF points to the video on the server, not to a file on your computer.

**Try this:**

1. Click **Download** on the same video. You get a ZIP with the video.
2. Unzip it.
3. When ELAN asks for the media file, choose `midden_….mp4` from the ZIP.

**Still stuck?** Send the sentence ID.

### EAF download fails {#an-download-failed}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** "MEDIA_DESCRIPTOR not found in EAF file." or "Failed to parse existing EAF file." means the stored EAF is damaged. "Failed to create EAF directory." is a server problem.

**Try this:**

1. Open the sentence in the editor (**Bewerk EAF (AI)**) and check whether the annotations are there.
2. Report the message.

**Still stuck?** Send the sentence ID and the message.

### The ZIP download shows "Failed to create ZIP archive." {#an-zip}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** **Download** builds the ZIP on the server. The server could not build it, for example because the `zip` program is missing. The browser then shows this text instead of a download.

**Try this:**

1. Go back to the overview.
2. Use **Download EAF (MP4)** for the annotations in the meantime.
3. Report it.

**Still stuck?** Send the sentence ID and the page address.

### I deleted an EAF, and now I need it back {#an-eaf-deleted}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** **Delete EAF** renames the file to `.bak` on the server, so it can be recovered. A second delete of the same video overwrites that copy.

**Try this:**

1. Do not delete the EAF of that video again.
2. Ask an administrator to restore it.

**Still stuck?** Send the sentence ID and when you deleted it.

### "Failed to save Status Annotatie. Please try again." (or Glos, GvG) {#an-status}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the status did not reach the server, often because the session expired or the connection dropped.

**Try this:**

1. Reload the page and log in if asked.
2. Set the status again.

**Still stuck?** Send the sentence ID, the status and the time.

### "No motion capture file found for this video." {#an-no-mocap}

**Type:** both · **Who can fix:** administrator

**Likely cause:** there is no mocap capture linked to this sentence. "This capture has not been through the FBX-to-GLB conversion yet" means the capture exists but has no GLB for 3DAnn3 yet.

**Try this:**

1. Check in viconDashboard whether the take exists (see [Motion capture](mocap.md)).
2. Report it if it exists but has no GLB.

**Still stuck?** Send the sentence ID and capture date.

### The edit buttons give "404 Not Found" {#an-editors-404}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the annotation editors are not installed on this host.

**Try this:**

1. Use `signcollect.nl` instead of a demo host.
2. Report it if it happens on `signcollect.nl`.

**Still stuck?** Send the address of the button.

### New studio videos or sentences are not in the overview yet {#an-late}

**Type:** system error · **Who can fix:** you / administrator

**Likely cause:** scheduled jobs add them. Video conversion runs every 12 hours, file moves every 6 hours, and the EAF sync every hour.

**Try this:**

1. Wait up to a day after the recording.
2. If it is later, see [scheduler stopped](system.md#sys-scheduler-stopped).

**Still stuck?** Send the recording date and take IDs.

### Going back to the overview shows different filters {#an-filters}

**Type:** user error · **Who can fix:** you

**Likely cause:** the overview remembers your filters in your browser. Another browser or cleared site data starts fresh.

**Try this:**

1. Set the filters again.

**Still stuck?** Not needed.
