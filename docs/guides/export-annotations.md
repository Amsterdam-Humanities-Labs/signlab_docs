# Export and download annotations

SignCollect stores annotations as ELAN EAF files, with an SRT subtitle file
per tier. This guide lists where to download them, one at a time or in bulk.

| You need | Where | Section |
|---|---|---|
| The EAF of one sentence video | Zinnen interface | [One sentence](#one-sentence) |
| The subtitles of what you are editing now | subBeta8 or 3DAnn3 | [From the editor](#from-the-editor) |
| Your own video with its annotations | Annotation tool | [From the annotation tool](#from-the-annotation-tool) |
| EAF/SRT of many mocap recordings | File Manager | [Many mocap recordings](#many-mocap-recordings) |
| Gloss SRTs of the baked mocap sentences | blendBaking | [Gloss SRTs and timings](#gloss-srts-and-timings) |

## One sentence

1. Open the [Zinnen interface](../interfaces/zinnen.md) and find the sentence.
2. On the video, click **Download EAF (MP4)**. You get the `.eaf` file, named
   after the sentence text. If the video has no EAF yet, you get an empty one
   with the three tiers.
3. To open it in ELAN with the video, also click **Download**. You get a ZIP
   with the camera angles (`midden_…`, `links_…`, `rechts_…`) and one SRT file
   per tier.
4. Unzip, then open the `.eaf` in ELAN.
5. ELAN cannot find the video, because the EAF points to the server. When
   ELAN asks, choose the `midden_….mp4` file from the ZIP.

To put an edited file back:

1. Save it in ELAN under the same file name. The upload refuses a file whose
   name differs from the sentence (*EAF bestandsnaam verschilt van huidige
   bestandsnaam!*).
2. Click **Upload EAF** on the same video, choose the file and click
   **Upload**.
3. *EAF file uploaded successfully.* confirms it. The server keeps the old
   EAF as a dated backup.

## From the editor

In [subBeta8 or 3DAnn3](../interfaces/annotation-editors.md), click **Download
Subtitles**. You get one WebVTT subtitle file (`.vtt`) per tier that has
annotations. Your browser may ask to allow several downloads at once. For the
EAF, use **Download EAF (MP4)** in the Zinnen interface.

!!! warning "Check the tier in subBeta8 files"
    In subBeta8 the file names of the *Nederlands* and *Gebaar-voor-Gebaar*
    files are swapped. Check the content before you use them.

## From the annotation tool

In the [annotation tool](../interfaces/annotation-tool.md):

- **Download Video + EAF** saves `<video name>.eaf` and the video as `.mp4`.
- **Download Subtitles** saves the annotations as WebVTT subtitle files
  (`.vtt`), one per tier.
- In Chrome or Edge, the tool also autosaves `<video name>.eaf` to the folder
  you chose. That file is your export.

## Many mocap recordings

1. Open the mocap portal and choose **Motion Capture File Manager**. See the
   [mocap portal](../interfaces/mocap-portal.md).
2. Set **MCP Status** to **MCP Klaar + EAF beschikbaar**.
3. Tick the recordings you need. You can take at most 100 at a time.
4. Click **Download Selected (EAF)**.
   You get one ZIP with the EAF and SRT files per recording. A list inside
   the ZIP names any recording that was left out, and why.

## Gloss SRTs and timings

1. Open [blendBaking](../interfaces/blendbaking.md):
   <https://signcollect.nl/blendBaking/>.
2. In **SRT bestanden**, filter and search.
3. Click **Download geselecteerde als ZIP** for the ones you ticked, or
   **Download alles (huidige filter)** for all of them.

For gloss lists, use the **Glossen** tab: **Exporteer CSV** or **Exporteer
JSON**. For use in other software, the **API** tab explains the gloss timings
API.

## Cluster labels

On the sign clusters page, **Download cluster_labels.json** saves the labels
you gave. See [Review clusters](review-clusters.md).

## Related

- [Annotate a sentence and save the EAF](annotate-sentence.md)
- [Troubleshooting](../troubleshooting/annotation.md)
