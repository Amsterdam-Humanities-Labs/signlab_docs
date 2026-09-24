# Mocap portal

The mocap portal (mocap_site, **Motion Capture Portal**) is the start page
for the motion-capture tools. It has four links.

- **Who uses it:** the mocap team: operators, post-processing engineers and
  researchers.
- **Address:** <https://mocap.signcollect.nl>
- **Login:** yes. Without a login it sends you to the login page.

## Open it

- Go to <https://mocap.signcollect.nl>, or
- in the [gloss management](main-menu.md) menu, choose **Motion Capture**.

<!-- screenshot: mocap portal with its four tiles, page https://mocap.signcollect.nl -->

![Mocap portal with its four tiles](../assets/screenshots/mocap-portal.png)


## The screen

| Link | Goes to | What it is for |
|---|---|---|
| **Motion Capture File Manager** | `/animMIDI/public/index.php` | Post-processing: download FBX recordings, clean them up, upload them again (see below) |
| **3D Studio Capture Site** | `/mocapStudio/capture.html` | The [Motion Capture Studio](mocap-studio.md) page used during a session |
| **signCollect Avatar Player** | `https://avatar.signcollect.nl/blendAnims/` | Plays the finished animations on an avatar. Not on demo hosts |
| **Vicon Dashboard Sync** | `/viconDashboard/` | The [Vicon dashboard](vicon-dashboard.md): which recordings arrived |

## File Manager (post-processing)

The File Manager (mocap-postprocessing, **Motion Capture File Manager**) is
where engineers clean up mocap recordings. It lists the recordings by date.
The counters at the top show how many are **Unprocessed** and **Processed**.

- **Filters:** **Search**, **Processing Status** (**Unprocessed Only**,
  **Processed Only**, **All Files**), **Filter by Date**, **Label** (BAK, ZNN,
  HH, Sencity), **MCP Status** and **Files per page**. Click **Apply Filter**.
  **MCP Klaar + EAF beschikbaar** shows only recordings that are *MCP Klaar*
  and have an EAF. A recording is *MCP Klaar* when, in the Zinnen interface,
  *MCP - Status Postprocessing* and *MCP - Status Tijd Annotatie Gloss* are
  both *Klaar*.
- **Download:** one FBX, or a ZIP with the FBX and the reference video.
  **Download Selected** downloads the ticked recordings.
- **Download Selected (EAF):** the EAF/SRT annotation files of the ticked
  recordings. Only recordings marked *MCP Klaar*, at most 100 per download.
- **Upload Processed Files:** upload cleaned FBX files, by drag and drop or as
  a ZIP.
- **Review:** mark a recording as approved, needs review or rejected, and add a
  comment.
- **Toewijzingen** (in the header; page **Capture Toewijzingen**): assign
  recording dates to users.
- **Statistieken** (in the header): downloads, uploads and activity per user
  and over time.

<!-- screenshot: File Manager recording list with filters, page /animMIDI/public/index.php -->

![File Manager recording list with filters](../assets/screenshots/mocap-file-manager.png)


### Clean up a recording

1. Set **Processing Status** to **Unprocessed Only** and click **Apply
   Filter**.
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
