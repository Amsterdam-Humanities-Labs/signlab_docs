# Annotation tool

The annotation tool (annotation-tool, version 3) is a general editor for
annotating any NGT video on a timeline with several tiers. It reads and writes
ELAN EAF files. Unlike the [annotation editors](annotation-editors.md), it is
not tied to the sentence list: you bring your own video, and the EAF is saved
on your own computer. Use it for videos that are not in SignCollect, or to
try out annotation.

It has three modes:

| Mode | Address | What it is for |
|---|---|---|
| Default | `/annotation-tool/` | Drop a video, annotate, autosave the EAF to a folder on your computer |
| Webcam | `/annotation-tool/v3/?mode=webcam` | Record yourself with the webcam, then annotate that recording |
| Clusters | opened from the cluster pages | Review and correct automatic sign segmentations; saves on the server |

- **Who uses it:** annotators and researchers.
- **Address:** <https://signcollect.nl/annotation-tool/>
- **Login:** not for the default and webcam modes. Clusters mode needs a login.

!!! warning "Use Chrome or Edge"
    Autosave needs a browser feature that Firefox and Safari lack. In those
    browsers the tool works, but you must download your EAF by hand.

## Open it

1. Open Chrome or Edge.
2. Go to <https://signcollect.nl/annotation-tool/>.

You now see *Drop a video (.mp4) and optionally an EAF (.eaf)*, with a file
picker.

<!-- screenshot: annotation tool with a video loaded and two tiers, page /annotation-tool/v3/ -->

![Annotation tool with a video loaded and two tiers](../assets/screenshots/annotation-tool.png)


## The screen

- **Video** at the top. The browser decodes it frame by frame, so you can step
  one frame at a time.
- **Playback:** **(P) Play**, speed buttons **0.25x (1)** to **Normal (4)**,
  and zoom **-** / **+**.
- **Tiers:** you start with one tier, *Tier 1*.
    - **+ Tier** adds a tier.
    - Double-click a tier name to rename it.
    - **×** deletes a tier with its annotations. One tier always remains.
- **Toolbar:**
    - **Drop EAF:** load an EAF file. It replaces the current tiers and
      annotations.
    - **Regex:** help for the patterns you can type in the gloss search field.
    - **Download Subtitles** (one subtitle file per tier) and **Download
      Video + EAF:** save your work by hand.
    - **Autosave Enabled:** the save state.
    - **Auto Segmentation**, **Revert to Original Segments**.
    - **Hide Side Videos**.
- **Gloss suggestions:** under a new segment, a list of the ten most likely NGT
  glosses. Click one to use it, or click **↻** to ask again.

## Common tasks

### Annotate a video

1. Drop an `.mp4` on the page, or use the file picker. To continue earlier
   work, drop its `.eaf` together with the video.
2. Wait while the video is converted and loads. A new video without
   annotations is split into sign segments automatically, and each segment
   gets gloss suggestions.
   You now see the video above the timeline.
3. Add a box on the timeline and type its text. Drag a box to move it, drag its
   edges to resize it, and drag it up or down to move it to another tier.
4. On your first change the browser asks for a folder. Choose one and allow
   access. From then on the tool writes `<video name>.eaf` there about one
   second after each change. It also copies the video into that folder, so
   you can pick up the session later.

!!! note "Your video is uploaded for the AI features"
    For conversion, segmentation and gloss suggestions, the video is sent to
    the signcollect.nl servers. The limit is 3 minutes and 200 MB. Uploads are
    deleted within 24 hours. The EAF itself stays on your computer.

### Continue later

1. Open the tool again, in the same browser.
2. The tool asks *Restore last session from <file>.eaf?*. Click **OK**.
   It loads the most recent `.eaf` in your folder, and the video with the
   same name if it is there.
3. If the video is not in the folder, drop it on the page.

If the browser no longer has access to the folder, there is no question.
Drop the `.eaf` and the video together instead (see above).

### Record with the webcam

1. Open <https://signcollect.nl/annotation-tool/v3/?mode=webcam>.
2. Allow the browser to use your camera.
3. Click **● Record** and sign. Click **■ Stop** when you are done.
4. Check the recording, then click **Use this → segment & spot**, or
   **Re-record** to try again.

The recording is converted, segmented and given gloss suggestions, as with a
dropped video. Webcam mode does not offer to restore a session.

### Review a cluster video

Clusters mode opens from the cluster review pages. It saves on the server, not
in a local folder. At the top you set the status (**Niet klaar** or **Klaar**)
and click **Volgende ▶** to save and go to the next video that is not *Klaar*.
See [Review clusters](../guides/review-clusters.md).

## Related

- [Review clusters](../guides/review-clusters.md)
- [Export and download annotations](../guides/export-annotations.md)
- [Troubleshooting](../troubleshooting/index.md)
