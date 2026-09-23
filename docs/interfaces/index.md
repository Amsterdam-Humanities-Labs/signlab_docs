# Interfaces

Every SignCollect interface is a web page. The address column gives the path
after `https://signcollect.nl`, unless a full address is given. All pages need
a [login](../getting-started/login.md), except where the page says otherwise.

| Interface | What it is for | Who uses it | Where it lives |
|---|---|---|---|
| [Main menu and gloss management](main-menu.md) | The gloss list: search, edit, selfie videos, studio videos. Its menu links to everything else | everyone | `/menu_beta/` |
| [Signbank connector](signbank-connector.md) | Settings for the link with Signbank: API key, gloss file, refresh schedule | administrators | `/menu_beta/signbank.php` |
| [Zinnen interface](zinnen.md) | The list of signed sentences with their videos, statuses and EAF files | annotators | `/zin/zinnen.html` |
| [Annotation editors](annotation-editors.md) | subBeta8 (annotate a sentence video) and 3DAnn3 (annotate a mocap take in 3D) | annotators | opened from the Zinnen interface |
| [Annotation tool](annotation-tool.md) | A general EAF editor for any video, with webcam and cluster-review modes | annotators, researchers | `/annotation-tool/` |
| [Camera Control](camera-control.md) | Starts and stops the five studio cameras and logs each take | recording operators | `/studio_beta/opnameView.html` |
| [Studio archive](studio-archive.md) | Every studio take by date, all camera angles, and a completeness check | operators, researchers | `/studioIndex/` |
| [Crop fix manager](crop-fix-manager.md) | A work queue for takes where the automatic crop cut off the sign | researchers, operators | `/videoFix/` |
| [Patient-info texts](patient-info.md) | Dutch health texts linked to NGT recordings (dormant project) | researchers | `/hh/` |
| [Mocap portal](mocap-portal.md) | Start page with links to the motion-capture tools | mocap team | `https://mocap.signcollect.nl` |
| [Motion Capture Studio](mocap-studio.md) | The page used during a Vicon recording session | recording operators | `/mocapStudio/capture.html` |
| [Vicon dashboard](vicon-dashboard.md) | Which Vicon recordings arrived and whether their files are complete | mocap team | `/viconDashboard/` |
| [blendBaking](blendbaking.md) | Gloss SRTs and gloss timings for the baked mocap sentences | researchers | `/blendBaking/` |
| [Body-animation viewer](body-animation-viewer.md) | Plays 3D body animations reconstructed from studio video (experimental) | researchers | `/s3b_glb/` |
| [Client monitor](client-monitor.md) | Which lab machines and background jobs are alive | administrators | `/client_monitor_dashboard/` |

!!! tip "Open the page, not the folder"
    Use the full address from the table. Some folders, such as `/mocapStudio/`,
    have no start page and show an error when you open the bare folder.

## Where the menu takes you

The navigation menu of the [gloss management page](main-menu.md) links to most
of these interfaces. The [mocap portal](mocap-portal.md) links to the
motion-capture tools.

## Related

- [How-to guides](../guides/index.md)
- [Troubleshooting](../troubleshooting/index.md)
