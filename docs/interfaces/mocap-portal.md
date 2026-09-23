# Mocap portal

The mocap portal (mocap_site) is the start page for the motion-capture tools.
It has four links.

- **Who uses it:** the mocap team: operators, post-processing engineers and
  researchers.
- **Address:** <https://mocap.signcollect.nl>
- **Login:** yes. Without a login it sends you to the login page.

## Open it

- Go to <https://mocap.signcollect.nl>, or
- in the [gloss management](main-menu.md) menu, choose **Motion Capture**.

<!-- screenshot: mocap portal with its four tiles, page https://mocap.signcollect.nl -->

## The screen

| Link | Goes to | What it is for |
|---|---|---|
| File Manager | `/animMIDI/public/index.php` | Post-processing: download FBX recordings, clean them up, upload them again (see below) |
| 3D Studio | `/mocapStudio/capture.html` | The [Motion Capture Studio](mocap-studio.md) page used during a session |
| Avatar Player | `https://avatar.signcollect.nl/blendAnims/` | Plays the finished animations on an avatar |
| Vicon Dashboard | `/viconDashboard/` | The [Vicon dashboard](vicon-dashboard.md): which recordings arrived |

## File Manager (post-processing)

The File Manager (mocap-postprocessing) is where engineers clean up mocap
recordings. It lists the recordings by date.

- **Filters:** processing status, *MCP Klaar* and whether an EAF exists. A
  recording is *MCP Klaar* when, in the Zinnen interface, *MCP - Status
  Postprocessing* is *Klaar* and *MCP - Status Tijd Annotatie Gloss* is
  *Klaar*.
- **Download:** one FBX, or a ZIP with the FBX and the reference video.
- **Download EAF/SRT:** the annotation files of many recordings at once. Only
  recordings marked *MCP Klaar*, at most 100 per download.
- **Upload Processed Files:** upload cleaned FBX files, by drag and drop or as
  a ZIP.
- **Review:** mark a recording as approved, needs review or rejected, and add a
  comment.
- **Capture Toewijzingen** (assignments): assign recording dates to users.
- **Statistieken:** activity per user and over time.

<!-- screenshot: File Manager recording list with filters, page /animMIDI/public/index.php -->

### Clean up a recording

1. Filter on recordings that are not processed yet.
2. Download the FBX, or the ZIP with the reference video.
3. Clean the animation up in Unreal.
4. Upload the processed FBX under **Upload Processed Files**.
5. Mark the recording as approved, or as needs review with a comment.

The whole path from recording to animation is in
[Get mocap from Vicon to a baked animation](../guides/mocap-to-animation.md).

## Related

- [Motion Capture Studio](mocap-studio.md)
- [Vicon dashboard](vicon-dashboard.md)
- [Troubleshooting](../troubleshooting/index.md)
