# Annotate a sentence and save the EAF

This guide takes one sentence video from *not started* to *Klaar*. You pick
the sentence in the [Zinnen interface](../interfaces/zinnen.md), annotate it
in the subBeta8 [annotation editor](../interfaces/annotation-editors.md), and
set its status. The editor saves the EAF file on the server for you.

A sentence annotation has three tiers:

- **Nederlands:** the Dutch translation.
- **Signbank ID glossen:** one Signbank gloss per sign, timed to the video.
- **Gebaar-voor-Gebaar:** a sign-by-sign description.

## 1. Pick a sentence

1. Open <https://signcollect.nl/zin/zinnen.html>.
2. Choose your theme in **Filter by Thema**.
3. Set the status filter for your tier, for example **Status Nederlands**, to
   *Niet Klaar* or *Leeg/Empty*.
4. Pick a row. Play the video first to see the whole sentence.

## 2. Open the editor

1. Click **Bewerk EAF (AI)** on the video.
2. The editor opens with the video, the side angles and the three tiers.
   Earlier work on this video is loaded.

<!-- screenshot: subBeta8 with the three tiers filled, page /annotation-editors/subBeta8/zin/subBeta8.html -->

## 3. Segment the signs (optional)

1. Click **Segment + Spot**.
2. Wait. The video is split into signs, and the *Signbank ID glossen* tier
   fills with segments. Each segment gets a list of likely glosses.
3. Check every segment. Fix the edges and pick or type the right gloss.

If the result is worse than what was there, click **Revert to Original
Segments**.

## 4. Annotate

1. To add an annotation, move the mouse over an empty spot on a tier. A **+**
   appears. Click where the sign starts, then click where it ends.
2. Double-click the annotation (or select it and press **Enter**) and type the
   text. Press **Esc** when done.
3. Fine-tune the timing with the arrow keys: **←** / **→** move the left edge,
   **Shift** + arrow the right edge, **Ctrl** (Cmd on Mac) + arrow the whole
   annotation, one frame at a time.
4. Use **P** to play and pause, and **1** to **4** for the speed.

The editor saves about one second after each change. Watch the button that
says **Autosave Enabled**. If it turns into **Save Failed!** or **Save
Error!**, stop and see [Troubleshooting](../troubleshooting/index.md).

## 5. Set the status

1. At the top of the editor, set the drop-down of the tier you finished to
   **Klaar**. Use **Controle nodig** or **Check nodig** if someone should
   check it.
2. Click **Go back to Zinnen**. Wait for *Opgeslagen!*.

!!! warning "If you see *Opslaan mislukt!*"
    Your last changes were not saved. Choose to stay on the page, wait a
    moment and make a small change to trigger a new save. Leave only after
    **Autosave Enabled** shows again.

## 6. Check the result

1. In the Zinnen interface, find the row again.
2. The tier table of the video (**EAF Signbank Glossen**, **EAF Nederlands**,
   **EAF Gebaar voor Gebaar**) shows your text.
3. To keep a copy, click **Download EAF (MP4)**. The file opens in ELAN.

## Where the EAF is saved

The editor saves one EAF file per video on the server, plus one SRT subtitle
file per tier. You do not need to download anything to save your work. To edit
in ELAN instead, see [Export and download annotations](export-annotations.md).

## Next: motion capture

When *Status Nederlands*, *Status Glossen* and *Status Gebaar voor Gebaar* are
all *Klaar*, the **Bewerk Motion Capture** button becomes active. It opens the
same annotation on the mocap take in 3DAnn3. See
[Get mocap from Vicon to a baked animation](mocap-to-animation.md).

## Related

- [Zinnen interface](../interfaces/zinnen.md)
- [Annotation editors](../interfaces/annotation-editors.md)
- [Troubleshooting](../troubleshooting/index.md)
