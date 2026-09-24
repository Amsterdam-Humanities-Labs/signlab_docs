# Run a recording session

This guide takes you through a studio session with the Sony FX30 cameras:
what must exist first, getting ready, recording, and what happens to the
videos afterwards. You work in [Camera Control](../interfaces/camera-control.md)
on the studio computer.

The studio works with three to five cameras. They are connected by USB to
[DRS](../glossary.md), the studio Mac, which downloads, renders, crops and
uploads the videos. What the studio needs and how it is set up is in
[Recording studio](../studio/index.md) and
[Requirements](../studio/requirements.md).

## First: put the items in SignCollect

Camera Control only shows items that already exist. For glosses:

1. In the [gloss management page](../interfaces/main-menu.md), click
   **Nieuwe glos** and fill in the gloss, its **Thema** (theme) and at least
   one label.
2. Record a selfie video for it: open the row menu and choose
   **Zelfopname maken**. Camera Control plays this video as the example for
   the signer.

The gloss now shows in Camera Control under its theme (**Glos**) and its
labels (**Labels**), for the signers who own it. Camera Control lists only
the glosses of the signer you choose in **Welke gebruiker ben je?** (theme
**ALLES** excepted), and a new gloss is owned by whoever created it. So add
the signer under **Owners** on the gloss if someone else created it. Sentences, NMM items and health texts come from their own
interfaces.

## Before the session

1. Charge the camera batteries and check that the memory cards have room.
2. Turn on all cameras you use today.
3. Check that the QR screen (the second or third monitor) shows the QR page
   and that every camera can see it
   ([physical setup](../studio/physical-setup.md)). *Why:* for each take this
   screen shows a QR code with the item's ID. The cameras film it, and DRS
   later reads it to know which item each video belongs to.
4. Turn on the sound of the studio computer, at 60% volume or more. Camera
   Control plays a beep at the start and end of each take and listens for it.
5. Check that DRS is running its pipeline. If you are not sure, ask an
   administrator.
   <!-- DRS checks (startup script, storage mount, one camera controller) are in the drs-pipeline operator manual; admin level -->
6. Open <https://signcollect.nl/studio_beta/opnameView.html>.
7. Wait until *Wachten op qR desktop* disappears. It stays until the QR page
   is connected.
8. In **Wat wil je opnemen?**, choose what you record, for example **Glos**
   or **Zin**.
9. In **Welke gebruiker ben je?**, choose the signer's account.
10. In **Welke thema wil je opnemen?**, choose the theme (or the label, for
    **Labels**). **ALLES** takes every theme.
11. Click **Beginnen**. The card shows the first item that is not recorded yet.
12. Check the top bar: **Cameras online: n/5** must count every camera you
    use. The page compares against the five cameras set up at installation
    ([install DRS](../studio/install-drs.md)). With fewer online, the count
    turns red, a warning bar shows and each take asks you to confirm (see
    below). A studio can run with three.

<!-- screenshot: Camera Control top bar with the camera count, page /studio_beta/opnameView.html -->

If a camera you use is missing, open **Instellingen** > **Camera Tabel
(Probleemoplossing)**, or see [FX30 troubleshooting](../studio/troubleshooting-fx30.md).

## During the session

The **Timer** is on by default. Then each take runs by itself: a 3-2-1
countdown, then the cameras record for the number of seconds on the timer
(5 by default), then they stop.

1. Let the signer read the item on the card and watch the example video.
2. Press **B**. After the countdown the card turns red while the cameras
   record.
3. With the timer on, wait until the take stops by itself. Press **C** first
   if the signer needs one second more. With the timer off, press **B** again
   when the signer is done; a take is at least 3 seconds.
4. Press **A** for the next item, or **O** to skip one.
5. Repeat. **Overzicht** shows what is still to do.

Keep an eye on the messages:

- *Niet alle cameras online!* Fewer than five cameras are online. If that is
  your setup today, click **Toch opnemen**. If a camera you use dropped out,
  fix it first: without it you lose that angle for this take.
- *Let op, weinig geheugen of lage batterij!* Change the battery or card.
- *Scan of bestandslijst bezig, even wachten...* The cameras are being
  scanned. Wait until it passes.

!!! warning "Leave DRS alone during a session"
    Do not open DaVinci Resolve on DRS by hand, and do not start a second
    camera program. Only one program can hold the cameras.

## After the session

1. Open **Instellingen** > **Vandaag Opgenomen (Review)**. Check that every
   take is listed. Click **Bekijk** to watch one.
2. Check that every camera battery is at least 50% full.
3. Click **Start Downloaden Video's**. The download starts at once.
4. Keep the cameras connected while *Bezig met downloaden....* shows.
5. Open **Vandaag Opgenomen (Review)** again. Every take should now show
   **✓ alles gedownload**.
6. Only if you need empty cards for the next session: click **Starten
   Formatten**. **Ja, formatteren** only appears when every clip is
   downloaded. Formatting erases all cards and cannot be undone.

## What happens next

After the download, everything runs by itself on DRS:

1. The clips are copied from DRS to the research drive on the server.
2. The QR scanner reads the QR code in each clip and links the clip to its
   item.
3. DaVinci Resolve renders the clips (every hour).
4. Each video is cropped around the signer and uploaded to signcollect.nl
   (every 15 minutes).

The finished videos appear over the next hours in the
[studio archive](../interfaces/studio-archive.md) and under **Studio video's**
in the gloss management page. If a crop cuts off part of a sign,
[fix the crop](fix-crop.md).

## The next day

[Check that the day's recordings are complete](check-day-complete.md).

## Related

- [Camera Control](../interfaces/camera-control.md)
- [Recording studio workflow](../studio/workflow.md)
- [Studio archive](../interfaces/studio-archive.md)
- [Troubleshooting](../troubleshooting/index.md)
