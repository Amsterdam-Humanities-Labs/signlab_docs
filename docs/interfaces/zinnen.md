# Zinnen interface

The Zinnen interface (zinnen-annotation) is where annotators work on signed
sentences (*zinnen*). It lists every sentence with its studio videos, the
status of each annotation layer, its motion-capture takes and its Signbank
glosses. From here you open a video in an
[annotation editor](annotation-editors.md), and you download or upload its
EAF file.

- **Who uses it:** annotators, every day.
- **Address:** <https://signcollect.nl/zin/zinnen.html>
- **Login:** yes.

## Open it

- On the start page after login, click **Zinnen interface**, or
- in the [gloss management](main-menu.md) menu, choose **Zinnen Interface**.

<!-- screenshot: Zinnen interface with filters and first sentence rows, page /zin/zinnen.html -->

## The screen

### Top buttons

- **View Logs:** the action log (who did what, and when). You can filter it.
- **Upload EAF:** upload an EAF file that is not tied to a row yet.
- **Overzicht:** statistics on all sentences.

### Filters

| Filter | What it does |
|---|---|
| Filter by Thema | Show one theme |
| Search Sentences | Words in the Dutch sentence |
| Search glosses | A gloss in the Signbank gloss tier |
| Search Gebaar-voor-Gebaar | Text in the sign-by-sign tier |
| Status Video Controle | *Niet Klaar*, *Klaar*, empty, or *Niet voor app, verplaatsen naar Signbank* |
| Status Nederlands | Dutch translation: *Niet Klaar*, *Klaar*, empty, *Controle nodig* |
| Status Glossen | Gloss tier: *Niet Klaar*, *Klaar*, empty, *NVT* |
| Status Gebaar voor Gebaar | Sign-by-sign tier: *Niet Klaar*, *Klaar*, empty, *Check nodig* |
| Motion Capture | Has or has no motion capture |
| MCP statuses | Post-processing and time annotation of the mocap take |

**Reset Filters** clears them all.

!!! warning "Buttons that change many rows"
    **Apply** next to *Video controle* sets a status for every video in the
    chosen theme. **Reset All Status to empty** clears statuses. Only use these
    when you have agreed it with your coordinator.

### A sentence row

Each row shows the sentence and one block per video. You can correct the
sentence text in place; it saves when you leave the field. A video block has:

- The videos (click to play; **Play All Videos** plays the angles together).
- A table with the three EAF tiers: **EAF Signbank Glossen**, **EAF
  Nederlands** and **EAF Gebaar voor Gebaar**.
- Buttons:
    - **Bewerk EAF (AI):** open the video in the subBeta8
      [annotation editor](annotation-editors.md).
    - **Bewerk Motion Capture:** open the mocap take in the 3DAnn3 editor. It
      is greyed out until *Status Nederlands*, *Status Glossen* and *Status
      Gebaar voor Gebaar* are all *Klaar*.
    - **Download EAF (MP4):** download the EAF file.
    - **Download:** download the video angles of this take as a ZIP file.
    - **Upload EAF:** replace the annotation with an EAF file from your
      computer, for example one you edited in ELAN.
    - **Verplaatsen naar nieuwe zin:** move this video to a new sentence.
    - **Delete video**.
- The status drop-downs for this sentence, and a comments field.

## Common tasks

### Find your next sentence

1. Choose your theme in **Filter by Thema**.
2. Set **Status Nederlands** (or the tier you work on) to *Niet Klaar* or
   empty.
3. Pick the first row.

### Annotate a sentence

1. Click **Bewerk EAF (AI)** on the video.
2. Annotate in the editor. It saves by itself.
3. Click **Go back to Zinnen**.
4. Set the status of the tier you finished to *Klaar*.

The full workflow is in [Annotate a sentence and save the EAF](../guides/annotate-sentence.md).

### Work on an EAF in ELAN

1. Click **Download EAF (MP4)** and **Download**.
2. Unzip the videos. Open the EAF in ELAN, with the video, and edit.
3. Click **Upload EAF** on the same video and choose your file. *EAF file
   uploaded successfully* confirms it.

### Record why a sentence is not done

Type in the comments field of the row. It saves when you leave the field.

## Related

- [Annotation editors](annotation-editors.md)
- [Annotate a sentence and save the EAF](../guides/annotate-sentence.md)
- [Export and download annotations](../guides/export-annotations.md)
- [Troubleshooting](../troubleshooting/index.md)
