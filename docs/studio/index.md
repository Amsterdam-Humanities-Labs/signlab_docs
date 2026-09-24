# Setting up a recording studio

This section explains how to build a SignCollect recording studio: the
hardware, the studio Mac (DRS) and how a recording day runs from gloss list
to finished video. It is for IT staff who set up a studio and for the
operators who run it.

A studio records each item with three to five Sony FX30 cameras at the same
time. A QR code on a separate screen tells the pipeline which item each take
belongs to. After the session the videos are processed on the studio Mac and
uploaded to the SignCollect server by themselves.

![The recording studio seen from above: signer in front of the green screen, 3 to 5 FX30 cameras, the QR screen in their view, the signer and operator screens, and DRS uploading to the server](../assets/studio/studio-layout.svg)

## The pieces

| Piece | What it does | Where |
|---|---|---|
| Sony FX30 cameras (3 to 5) | Record every take from several angles: left (`L`), middle (`M`), right (`R`), and optionally `A` and `B` | Studio, on USB to DRS |
| DRS, the studio Mac | Runs the camera server, the camera controller app and the video pipeline | Studio |
| Camera server (`fx30MultiRecord`) | Starts and stops all cameras at once and downloads the clips. Listens on port 8080 | DRS |
| Camera controller app (**FX30 Multi-Camera Bediening**) | Starts the camera server, opens the QR screen and uploads the clips to the research drive | DRS |
| [Camera Control](../interfaces/camera-control.md) | The web page the operator records with | Browser on DRS, served by the SignCollect server |
| QR screen (`opnameLR.html`) | Shows a QR code for the item being recorded. The cameras film it | Second or third screen on DRS, facing the cameras |
| Video pipeline (signlab_drs-pipeline) | Renders the green screen in DaVinci Resolve Studio, crops, converts and uploads to the server | DRS |
| Research drive (optional, recommended) | Stores all raw and processed clips, mounted with rclone | Network storage |
| SignCollect server | Gloss lists, Camera Control, take records, finished videos | For example `signcollect.nl` |

## From gloss to finished video

1. **Enter the glosses.** A researcher adds the glosses in the
   [gloss management page](../interfaces/main-menu.md) (menu_beta), with a
   theme or labels, and makes the signer an owner.
2. **Record a quick reference video.** In the same page, **Zelfopname
   maken** (Record selfie video) records a short webcam video of the gloss.
   Camera Control shows it to the signer as the example.
3. **Pick the list in Camera Control.** The operator chooses the type, the
   signer and the theme or label. The items of that list appear one by one.
4. **Record.** For each item the QR screen shows a code, and the operator
   starts and stops all cameras at once with **B** or a foot pedal.
5. **Upload at the end of the day.** The operator downloads the clips from
   the cameras. The controller app copies them to the research drive, and the
   pipeline renders, crops and uploads them to the server over the next
   hours.
6. **Link each take to its item.** The QR scanner on DRS reads the QR code
   in each clip and tells the server which item the take belongs to.
7. **Review and fix.** The finished videos appear in the
   [studio archive](../interfaces/studio-archive.md) and under **Studio
   video's** in the gloss table. Bad crops go to the
   [crop fix manager](../interfaces/crop-fix-manager.md); leftover green
   background is fixed with Background Fix.

The step-by-step version for operators is in
[the capture day](workflow.md).

## Who does what

| Role | Tasks |
|---|---|
| IT staff or developer | Build the studio, [install DRS](install-drs.md), keep the pipeline running, [fix camera connections](troubleshooting-fx30.md) |
| Researcher | Enter glosses, themes and labels; record reference videos; check and fix the results |
| Recording operator | Run the session in Camera Control, download the clips at the end of the day |
| Signer | Signs the items in front of the cameras |

## In this section

- [Requirements](requirements.md): what to buy and install.
- [Physical setup](physical-setup.md): cameras, green screen, lights, screens and pedals.
- [Install the DRS Mac](install-drs.md): the setup script and the manual steps.
- [The capture day](workflow.md): the operator's workflow.
- [Troubleshooting FX30 connections](troubleshooting-fx30.md): for developers and IT.

## Related

- [Run a recording session](../guides/recording-session.md)
- [Camera Control](../interfaces/camera-control.md)
- [Studio archive](../interfaces/studio-archive.md)
- [Glossary](../glossary.md)
