# Annotate a sentence and save the EAF

This guide takes one sentence video from *not started* to *Klaar*. You pick
the sentence in the [Zinnen interface](../interfaces/zinnen.md), annotate it
in the subBeta8 [annotation editor](../interfaces/annotation-editors.md), and
set its status. The editor saves the EAF file on the server for you.

A sentence annotation has three tiers:

- **Nederlands:** the Dutch translation.
- **Signbank ID glossen:** one Signbank gloss per sign, timed to the video.
- **Gebaar-voor-Gebaar:** a sign-by-sign description.

**Before you start:** log in to SignCollect. The editor saves only for a
logged-in user.

## 1. Pick a sentence

1. Open <https://signcollect.nl/zin/zinnen.html>, or choose **Zinnen
   Interface** in the menu.
2. Choose your theme in **Filter by Thema**.
3. Set the status filter of your tier, for example **Filter by Status
   Nederlands**, to **Niet Klaar**.
   *Leeg/Empty* is the default and means "no filter": it shows every sentence.
4. Pick a row. Play the video first to see the whole sentence.

## 2. Open the editor

1. Click **Bewerk EAF (AI)** on the video.
2. The editor opens in the same tab. It shows the sentence, the video and the
   three tiers. Earlier work on this video is loaded.

<!-- screenshot: subBeta8 with the three tiers filled, page /annotation-editors/subBeta8/zin/subBeta8.html -->

## 3. Segment the signs (optional)

The AI buttons only work on `signcollect.nl`.

1. Click **Segment + Spot**.
2. Wait for the progress window to close. The *Signbank ID glossen* tier is
   replaced by one empty segment per detected sign.
3. Hover over or select a segment to see the 10 most likely glosses. Click a
   gloss to fill it in.
4. Check every segment. Fix the edges and pick or type the right gloss.

If the result is worse than what was there, click **Revert to Original
Segments**. This button only works until you leave the page.

## 4. Annotate

1. To add an annotation, move the mouse over an empty spot on a tier. A **+**
   appears. Click where the sign starts, then click where it ends.
   **Esc** cancels.
2. Double-click the annotation (or select it and press **Enter**) and type the
   text. Press **Esc** when done.
3. Fine-tune the timing, one frame at a time:
    - **←** / **→**: the left edge.
    - **Shift** + arrow: the right edge.
    - **Ctrl** (Cmd on Mac) + arrow: the whole annotation.
4. Press **Tab** to go to the next annotation on the same tier.
5. Use **P** to play and pause, and **1** to **4** for the speed.

The editor saves about one second after each change. *Saving successful*
appears at each save, and the save button keeps saying **Autosave Enabled**.
If it says **Save Failed!** or **Save Error!**, your changes are not saved.
Keep the tab open and see [Annotation editors](../troubleshooting/editors.md#ed-save-failed).

## 5. Set the status

The status drop-downs are in the button bar above the timeline:
**Nederlands:**, **Glossen:** and **GvG:**.

1. Set the drop-down of the tier you finished to **Klaar**. The status is
   saved at once.
2. If someone should check your work, choose **Controle nodig**
   (Nederlands) or **Check nodig** (GvG) instead.
3. Wait for *Saving successful* after your last edit.
4. Click **Go back to Zinnen**.

!!! warning "If you see *Opslaan is mislukt. Toch de pagina verlaten?*"
    Your last changes were not saved. Click **Cancel** to stay on the page.
    Make a small change, wait for *Saving successful*, then leave.

## 6. Check the result

1. In the Zinnen interface, find the row again.
2. The tier table of the video (**EAF Signbank Glossen**, **EAF Nederlands**,
   **EAF Gebaar voor Gebaar**) shows *Aantal items:* with the number of
   annotations per tier.
3. The status of the tier shows **Klaar**.
4. To keep a copy, click **Download EAF (MP4)**. See
   [Export and download annotations](export-annotations.md) to open it in ELAN.

## Where the EAF is saved

The editor saves one EAF file per video on the server, plus one SRT subtitle
file per tier. Before each save it keeps a dated copy of the old files, so an
administrator can restore an earlier version. The Dutch text, glosses and GvG
also go to the sentence database at once. You do not need to download
anything to save your work.

## Next: motion capture

The **Bewerk Motion Capture** button only appears when the sentence has a
mocap take that has been post-processed. It stays greyed out as
**Motion Capture blocked** until *Status Nederlands*, *Status Glossen* and
*Status Gebaar voor Gebaar* are all *Klaar*. It opens the same annotation on
the mocap take in 3DAnn3. See
[Get mocap from Vicon to a baked animation](mocap-to-animation.md).

## Related

- [Zinnen interface](../interfaces/zinnen.md)
- [Annotation editors](../interfaces/annotation-editors.md)
- [Troubleshooting](../troubleshooting/index.md)
