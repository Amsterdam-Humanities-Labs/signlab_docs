# Sentence annotation and EAF files

Problems in the sentence (zin) overview: statuses, uploading and downloading EAF files, and opening the editors. For problems inside the editors, see [Annotation editors](editors.md).

!!! warning "The last save wins"
    Two people can open the same sentence. There is no lock: whoever saves last overwrites the other. Agree who works on which sentence.

### "Invalid EAF file type." when I upload an EAF {#an-invalid-eaf}

**Type:** user error · **Who can fix:** you / administrator

**Likely cause:** the file is not an EAF (XML) file. Because of a known bug, the old EAF is set aside before the check, so the sentence may now have no EAF.

**Try this:**

1. Save the file again from ELAN as `.eaf`.
2. Upload it again.
3. If the sentence now shows no EAF and you have no good copy, ask an administrator to restore the backup.

**Still stuck?** Send the sentence ID and the time of the failed upload.

### The upload worked, but subtitles are wrong or missing {#an-srt}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** after upload, each tier becomes a subtitle file. "Failed to parse EAF file." means the EAF is damaged. "Failed to write SRT file for tier" is a server problem.

**Try this:**

1. Open the EAF in ELAN and check that it loads.
2. Save and upload again.
3. Report "Failed to write SRT file".

**Still stuck?** Send the sentence ID, the tier name and the message.

### My colleague's edits disappeared {#an-overwritten}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** you both edited the same sentence. The last save won. Each save keeps a dated backup first.

**Try this:**

1. Agree who works on the sentence.
2. Ask an administrator to restore the backup from before your save.

**Still stuck?** Send the sentence ID and both save times.

### The downloaded EAF has an odd or empty file name {#an-filename}

**Type:** user error · **Who can fix:** you

**Likely cause:** the file name is made from the sentence text. Spaces become `_`, and all other characters are removed, including letters with accents.

**Try this:**

1. Rename the file on your computer.

**Still stuck?** Not needed.

### ELAN cannot find the video of a downloaded EAF {#an-elan-media}

**Type:** user error · **Who can fix:** you

**Likely cause:** the EAF points to the video on `signcollect.nl`, not to a file on your computer.

**Try this:**

1. Download the video too, or use the ZIP download.
2. In ELAN, relink the media file to your local copy.

**Still stuck?** Send the sentence ID.

### EAF download fails {#an-download-failed}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** "MEDIA_DESCRIPTOR not found in EAF file." or "Failed to parse existing EAF file." means the stored EAF is damaged. "Failed to create EAF directory." is a server problem.

**Try this:**

1. Try the ZIP download.
2. Report the message.

**Still stuck?** Send the sentence ID and the message.

### The ZIP download fails {#an-zip}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** "No files found" means the sentence has no video or EAF yet. "Cannot create ZIP file" is a server problem.

**Try this:**

1. Check that the sentence has a video.
2. Report "Cannot create ZIP file".

**Still stuck?** Send the sentence ID.

### I deleted an EAF, and now I need it back {#an-eaf-deleted}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** delete keeps a copy on the server, so it can be recovered.

**Try this:**

1. Ask an administrator to restore it.

**Still stuck?** Send the sentence ID and when you deleted it.

### "Failed to save Status Annotatie" (or Glos, GvG) {#an-status}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the status did not reach the server, often because the session expired or the connection dropped.

**Try this:**

1. Reload the page and log in if asked.
2. Set the status again.

**Still stuck?** Send the sentence ID, the status and the time.

### "No motion capture file found for this video." {#an-no-mocap}

**Type:** both · **Who can fix:** administrator

**Likely cause:** there is no mocap capture linked to this sentence, or it has not been converted to GLB yet.

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
