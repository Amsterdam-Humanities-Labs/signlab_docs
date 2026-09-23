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
2. On the video, click **Download EAF (MP4)**. You get the `.eaf` file.
3. To open it in ELAN with the video, also click **Download**. You get the
   camera angles as a ZIP.
4. Unzip, then open the `.eaf` in ELAN.

To put an edited file back, click **Upload EAF** on the same video.

## From the editor

In [subBeta8 or 3DAnn3](../interfaces/annotation-editors.md), click **Download
Subtitles**. You get one WebVTT subtitle file (`.vtt`) per tier that has
annotations. For the EAF, use **Download EAF (MP4)** in the Zinnen interface.

## From the annotation tool

In the [annotation tool](../interfaces/annotation-tool.md):

- **Download Video + EAF** saves the video and the annotations.
- **Download Subtitles** saves the annotations as WebVTT subtitle files
  (`.vtt`), one per tier.
- In Chrome or Edge, the tool also autosaves `<video name>.eaf` to the folder
  you chose. That file is your export.

## Many mocap recordings

1. Open the File Manager from the [mocap portal](../interfaces/mocap-portal.md).
2. Filter on *MCP Klaar*.
3. Select the recordings and download their EAF/SRT files. You can download
   at most 100 recordings at a time.

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
- [Troubleshooting](../troubleshooting/index.md)
