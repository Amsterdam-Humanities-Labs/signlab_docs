# The capture day

The whole workflow of a recording day, from entering glosses to fixing the
finished videos. The session itself is described in detail in
[Run a recording session](../guides/recording-session.md); this page puts it
in order with what comes before and after.

<video controls preload="metadata" width="100%" poster="../../assets/studio/studio-workflow-poster.png">
  <source src="../../assets/studio/studio-workflow.mp4" type="video/mp4">
  Your browser cannot play this video. <a href="../../assets/studio/studio-workflow.mp4">Download it (MP4, 90 seconds)</a>.
</video>

*Video (90 seconds, no sound): a gloss from menu_beta to Camera Control and on to the
finished video, recorded on a SignCollect test server.*

## 1. Enter the glosses

Done by a researcher, before the recording day, in the
[gloss management page](../interfaces/main-menu.md)
(<https://signcollect.nl/menu_beta/>).

1. Add each gloss with **Nieuwe glos**, or many at once with **Batch
   toevoegen** in the menu.
2. Give each gloss a **Thema** (theme), or labels, so it lands in the right
   recording list.
3. Make the signer an owner of the gloss (**Wie** / *Owners* in the row).
   Camera Control only lists the glosses of a theme that belong to the signer
   chosen at the start.
4. Check that the gloss is not hidden. Hidden glosses are not listed.

## 2. Record a quick reference video

For each gloss, record a short example in the same page. Camera Control shows
it on the card, so the signer knows what to sign.

1. Open the row menu (**⋮**) and choose **Zelfopname maken** (Record selfie
   video), or click the empty thumbnail.
2. Click **Opname starten**, sign, and click **Stoppen & opslaan** (*Stop & save*).

## 3. Prepare the studio

1. Turn on the lights and all cameras. Check batteries and cards.
2. Check that the controller app **FX30 Multi-Camera Bediening** is open on
   DRS. It lists every camera and shows **QR-scherm: ● open**.
3. Check that the QR screen shows the white QR page, full screen.
4. Turn the sound on, at 60% volume or more.

## 4. Open the list in Camera Control

1. Open [Camera Control](../interfaces/camera-control.md):
   <https://signcollect.nl/studio_beta/opnameView.html>.
2. Wait until *Wachten op qR desktop* goes away. The page is waiting for the
   QR screen to answer.
3. In **Wat wil je opnemen?**, click **Glos** to record by theme, or
   **Labels** to record by label.
4. In **Welke gebruiker ben je?**, choose the signer.
5. In **Welke thema wil je opnemen?**, choose the theme (or label).
6. Click **Beginnen**.
7. Check the top bar: all cameras must be online.

## 5. Capture

1. Let the signer watch the card and its reference video. The QR screen now
   shows the code for this item.
2. Press **B** (or the pedal) to start. The card turns red while the cameras
   record.
3. Press **B** again when the signer is done.
4. Press **A** for the next item, or **O** to skip one.
5. Repeat until the list is done. **Overzicht** shows what is still to do.

The details, messages and what to do when a camera drops out are in
[Run a recording session](../guides/recording-session.md#during-the-session).

## 6. Upload at the end of the day

1. In Camera Control, open **Instellingen** > **Vandaag Opgenomen (Review)**
   and check that every take is listed.
2. Check that every camera battery is at least 50% full.
3. Click **Start Downloaden Video's** and confirm with **Ja, DOWNLOADEN**.
4. Keep the cameras on and connected until the download is done.

From here everything runs by itself, as long as the controller app and the
pipeline run on DRS:

| When | What happens | Where |
|---|---|---|
| Right after the download | The controller app sorts the clips by date and copies them to the research drive | `studioFiles/<date>/raw/` |
| Every 15 minutes | Each clip is converted to H.264 with a thumbnail and uploaded | `videoProc/upload2.php` |
| Every 15 minutes | The QR scanner reads the QR code in each thumbnail and links the take to its item | `qr/qrResultReceiver.php` |
| Every hour | DaVinci Resolve renders the `L`, `M` and `R` clips: green screen replaced with studio blue | `post_noncropped/` |
| Every 15 minutes | Rendered clips are cropped around the signer and uploaded | `videoProc/upload_post.php` |

The server address comes from `SIGNCOLLECT_URL` on DRS (see
[Install the DRS Mac](install-drs.md#configuration)).

!!! danger "Format only when everything is downloaded"
    **Starten Formatten** erases all camera cards. Only use it when every take
    shows **✓** in **Vandaag Opgenomen (Review)**.

## 7. Review and fix

Processing takes a few hours. The next day:

1. [Check that the day's recordings are complete](../guides/check-day-complete.md)
   in the [studio archive](../interfaces/studio-archive.md).
2. Watch the takes. In the gloss table, **Studio video's** in a row shows the
   left, middle and right camera of each take.
3. If the crop cut off part of a sign,
   [fix the crop](../guides/fix-crop.md) in the
   [crop fix manager](../interfaces/crop-fix-manager.md).
4. If green background is left in a video, paint it out with Background Fix
   (<https://signcollect.nl/videoBackgroundFix/>). See
   [the green screen was not replaced](../troubleshooting/video-processing.md#vp-green-screen).

## Related

- [Run a recording session](../guides/recording-session.md)
- [Camera Control](../interfaces/camera-control.md)
- [Check that a day's recordings are complete](../guides/check-day-complete.md)
- [Fix a badly cropped take](../guides/fix-crop.md)
- [Studio archive](../interfaces/studio-archive.md)
- [Recording troubleshooting](../troubleshooting/recording.md)
