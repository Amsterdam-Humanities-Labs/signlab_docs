# Run a recording session

This guide takes you through a studio session with the five Sony FX30
cameras: getting ready, recording, and what to do afterwards. You work in
[Camera Control](../interfaces/camera-control.md) on the studio computer.

The cameras are connected by USB to DRS, the studio Mac. DRS renders, crops
and uploads the videos by itself after the session.

## Before the session

1. Charge the camera batteries and check the memory cards have room.
2. Turn on all five cameras.
3. Turn on the sound of the studio computer, at 60% volume or more. Camera
   Control plays a beep at the start and end of each take.
4. Check that DRS is running its pipeline. If you are not sure, ask an
   administrator to check it before you start.
   <!-- DRS checks (startup script, storage mount, one camera controller) are in the drs-pipeline operator manual; admin level -->
5. Open <https://signcollect.nl/studio_beta/opnameView.html>.
6. In **Wat wil je opnemen?**, choose what you record, for example **Glos**
   or **Zin**.
7. In **Welke gebruiker ben je?**, choose the signer's account.
8. In **Welke thema wil je opnemen?**, choose the theme or list.
10. Click **Beginnen**.
11. Check the top bar: all five cameras must be online. If one is missing,
    open **Instellingen** > **Camera Tabel (Probleemoplossing)**.

<!-- screenshot: Camera Control top bar with the camera count, page /studio_beta/opnameView.html -->

!!! tip "Use the countdown"
    Turn on **Timer inschakelen** in **Instellingen**. The signer then gets a
    countdown before each take. Press **C** to make it one second longer.

## During the session

1. Let the signer read the item on the card. Play its reference video if
   there is one.
2. Press **B** to start. The card turns red while the cameras record.
3. Press **B** again when the signer is done. Do not press it too fast: a take
   needs a few seconds.
4. Press **A** for the next item, or **O** to skip one.
5. Repeat.

Keep an eye on the messages:

- *Niet alle cameras online!* A camera dropped out. Fix it before you record.
  Click **Toch opnemen** only if you accept losing that angle for this take.
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
3. Click **Start Downloaden Video's** and confirm with **Ja, DOWNLOADEN**.
4. Keep the cameras connected until the download is done.
5. Open **Vandaag Opgenomen (Review)** again. Every take should now show
   **✓** (downloaded).
6. Only then, if you need empty cards for the next session, click **Starten
   Formatten**. This erases all cards and cannot be undone.

DRS now processes the takes. Rendering runs every hour and cropping every 15
minutes, so the processed videos appear over the next hours.

## The next day

[Check that the day's recordings are complete](check-day-complete.md) in the
studio archive.

## Related

- [Camera Control](../interfaces/camera-control.md)
- [Studio archive](../interfaces/studio-archive.md)
- [Troubleshooting](../troubleshooting/index.md)
