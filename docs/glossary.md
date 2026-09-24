# Glossary

SignCollect mixes Dutch and English terms. This page explains both. Where the
interface uses a Dutch word, it is given in brackets.

## A–E

**3DAnn3**: The [annotation editor](interfaces/annotation-editors.md#3dann3) for motion-capture takes. It shows the take as a 3D avatar.

**Angle** (camera angle): One of the studio cameras. The studio records with three to five cameras, so a take has three to five video files, one per angle. File names start with the angle letter: `L` (left), `M` (middle), `R` (right), and `A` and `B` when those cameras are used, followed by the date and a number, for example `M20251001_2313`. The middle file names the take.

**Annotation**: A piece of text linked to a stretch of time in a video, on one tier.

**Baked take**: A motion-capture take that has been converted to a GLB animation file. [blendBaking](interfaces/blendbaking.md) lists them.

**Client** (monitoring): A machine, script or background job that reports to the [client monitor](interfaces/client-monitor.md) with heartbeats.

**Cluster**: A group of automatically found sign segments that look alike. Each cluster should be one sign. See [Review clusters](guides/review-clusters.md).

**Crop**: After rendering, each studio video is cut down automatically to the area around the signer. When the crop cuts off part of a sign, it can be redone in the [crop fix manager](interfaces/crop-fix-manager.md).

**DRS**: The studio Mac that the Sony FX30 cameras (three to five) are connected to. It runs the camera controller and the video pipeline: render, crop, convert and upload to signcollect.nl. At the end of the capture day it uploads the videos by itself.

**EAF**: The file format of ELAN (`.eaf`). It holds the tiers and their time-aligned annotations, and a link to the video. SignCollect stores one EAF per video.

**ELAN**: The free desktop program for annotating video, from the Max Planck Institute for Psycholinguistics. SignCollect's EAF files open in it.

## F–L

**FBX**: A 3D animation file format. Vicon and Unreal export motion capture as FBX. Engineers clean FBX files up in the File Manager.

**FX30**: The Sony FX30 cameras in the studio. Three to five of them record every take; the camera list is set once at installation.

**Gebaar-voor-Gebaar** (GvG): "sign by sign". The annotation tier that describes a sentence one sign at a time.

**GLB**: A compact 3D file format for the web. Mocap takes are converted from FBX to GLB so they can play in the browser, for example in 3DAnn3 and the [body-animation viewer](interfaces/body-animation-viewer.md).

**Gloss** (glos): A label in capitals that stands for one sign, for example `HUILEN`. The gloss list is managed in the [gloss management page](interfaces/main-menu.md). The *English gloss* is its English label. A *base gloss* is the gloss without variant markers.

**Green screen, studio background**: The signer stands in front of a green screen. When DRS renders a take, DaVinci Resolve keys out the green and puts the signer on the studio background colour ("studio blue"). Background that is left over can be masked with the background-fix tool.

**Heartbeat**: A short "I am alive" message that a machine or job sends to the server at a fixed interval. If heartbeats stop, the [client monitor](interfaces/client-monitor.md) shows the client as *Warning* and then *Offline*.

**HH** (Health Holland): The project that recorded Dutch patient-information texts in NGT. See [patient-info](interfaces/patient-info.md).

**Klaar / Niet Klaar**: "Done" / "not done". The main status values in the Zinnen interface and the editors. Other values are *Controle nodig* or *Check nodig* (needs a check), *NVT* (not applicable) and empty (*Leeg*).

**Label**: A tag on a gloss, for example *GEBAAR UIT DE BEELD*. A gloss can have several. [Camera Control](interfaces/camera-control.md) lists glosses by theme or label, and the Video Downloader filters on them. Labels are managed under **Labels toevoegen** in the [gloss management page](interfaces/main-menu.md).

**LiveLink**: Data that Unreal records during a mocap session, stored as CSV files. The [Vicon dashboard](interfaces/vicon-dashboard.md) shows them in the *livelink* column.

## M–R

**MCP**: Motion capture (in status names). *MCP - Status Postprocessing* and *MCP - Status Tijd Annotatie* track a mocap take through cleanup and time annotation. *MCP Klaar* means both are *Klaar*.

**Mocap** (motion capture): Recording movement in 3D with markers and cameras. SignCollect uses a Vicon system in the Visualisation Lab. See [Get mocap from Vicon to a baked animation](guides/mocap-to-animation.md).

**NGT**: Nederlandse Gebarentaal, Sign Language of the Netherlands.

**NMM**: Non-manual markers: meaning carried by the face, head and body instead of the hands. Camera Control can record NMM items.

**Opname**: Dutch for recording. See *take*.

**Phonology** (fonologie): The form of a sign: hand shape, location, movement. Stored per gloss.

**QR code**: A code shown on the second or third studio screen, in view of the cameras. It identifies each take, so the DRS can link every video clip to its gloss or sentence. The cameras must point at it.

## S–Z

**Segment**: A stretch of video that holds one sign. The AI helpers find segments automatically; annotators correct them.

**Selfie video** (zelfopname, *snelle opname*): A quick reference video of a gloss, recorded with your own webcam in the [gloss management page](interfaces/main-menu.md) (**Zelfopname maken**). Camera Control plays it as the example for the signer.

**Sense** (betekenis): A meaning of a gloss, in Dutch and English.

**Sentence** (zin, plural zinnen): A signed sentence. Sentences are annotated in the [Zinnen interface](interfaces/zinnen.md).

**Signbank**: The online NGT lexicon at <https://signbank.cls.ru.nl>. SignCollect can push glosses to it and pull them from it. See [Add or edit a gloss and sync with Signbank](guides/gloss-signbank.md).

**Signio**: The second gloss view in the gloss management page, next to Signbank. It is the default view unless an administrator sets another for your account.

**Snelle opname**: "Quick recording". See *selfie video*.

**Spotting**: Suggesting which glosses a sign segment most likely is. The editors show the ten most likely glosses.

**SRT**: A plain subtitle file format (`.srt`). SignCollect writes one SRT per tier next to each EAF. [blendBaking](interfaces/blendbaking.md) downloads gloss SRTs.

**Take**: One recording of one item: all camera angles of a single start and stop. In Dutch: *opname*.

**Zelfopname**: See *selfie video*.

**Theme** (thema): A group of glosses or sentences on one topic. Recording lists and filters are organised by theme.

**Tier**: One row of annotations on the timeline, such as *Nederlands*, *Signbank ID glossen* or *Gebaar-voor-Gebaar*. An EAF file holds several tiers.

**Unreal**: Unreal Engine. The [Motion Capture Studio](interfaces/mocap-studio.md) page starts and stops recording in Unreal, and engineers use Unreal to clean up FBX files.

**Vicon**: The motion-capture system in the Visualisation Lab. The *Vicon PC* runs it. Recordings are copied from it to the server every night.

**WebVTT**: A subtitle file format (`.vtt`). **Download Subtitles** in the editors saves one per tier.
