# Camera Control

Camera Control (camera-control) is the page the recording operator keeps open
during a studio session. It shows what to sign next, starts and stops all
Sony FX30 cameras at once, and logs every take. It also downloads the clips
from the cameras at the end of the day.

The page talks to the camera controller on DRS, the studio Mac that the
cameras are connected to. The studio runs with three to five cameras. The page
expects the cameras in its camera list, set at installation (five by default;
see [Install the DRS Mac](../studio/install-drs.md#camera-control-and-the-server)).

- **Who uses it:** recording operators, in the studio.
- **Address:** <https://signcollect.nl/studio_beta/opnameView.html>
- **Login:** yes.

!!! note "Only in the studio"
    The cameras are only reachable from the studio network. Elsewhere, and on
    demo hosts, the camera panel stays empty.

## Before you open it

- **The items exist.** Camera Control only lists glosses that are in the
  [gloss management page](main-menu.md), with a theme and labels. The
  selfie video (**Zelfopname maken**) is the example video the signer sees.
- **The QR screen is on.** A second or third monitor shows the QR page. For
  each take it shows a QR code with the item's ID. The cameras must see it:
  DRS reads the code from the video later to link each clip to its item. See
  [physical setup](../studio/physical-setup.md).
- **Sound is on,** at 60% volume or more. The page plays a beep at the start
  and end of each take and checks it hears the beep.

## Open it

1. Open <https://signcollect.nl/studio_beta/opnameView.html> on the studio
   computer.
2. Wait while *Wachten op qR desktop* shows. It closes when the QR page is
   connected.
3. Wait while *Waiting for QR on display...* shows. It closes when the page
   sees a QR code in the studio camera image.
4. The start window asks **Wat wil je opnemen?** (what do you want to record?).

<!-- screenshot: start window "Wat wil je opnemen?" with the type buttons, page /studio_beta/opnameView.html -->

![Start window "Wat wil je opnemen?" with the type buttons](../assets/screenshots/camera-control.png)


## The screen

### Start window

1. **Wat wil je opnemen?** Choose the type: **Glos** (gloss), **Zin**
   (sentence), **NMM**, **OC**, **Extern**, **Tekst** (health text),
   **Labels**, **Begrippen** (glossary terms) or **Vrij opnemen** (free: you
   type what you will record).
2. **Welke gebruiker ben je?** Choose the signer's account.
3. **Welke thema wil je opnemen?** Choose the theme. **ALLES** takes every
   theme. For **Labels** this list shows labels instead.
4. Click **Beginnen** (start). The card shows the first item not recorded yet.

### Top bar

- **Cameras online: n/5**. It turns red when fewer cameras are online than
  the camera list expects (five by default), and a red warning bar (*LET OP: slechts n van de 5 cameras
  online!*) shows below it.
- **Menu:** back to the start window.
- **Overzicht:** what is still to record (*Nog te gaan*) and what is done
  (*Opgenomen*) in the current list.
- **Live View:** live images from the cameras. **Draai 90°** rotates the view.
- **Instellingen:** opens the side panel.

### Main area

The card in the middle shows the item to sign, with its example video when
there is one. Below it:

- **Vorige** (previous), **Opnemen (B)** (record), **Volgende** (next).
- **Timer** checkbox and slider: the length of a take, 1 to 10 seconds
  (5 by default). With the timer on, **B** gives a 3-2-1 countdown and the
  take stops by itself after that time. With the timer off, you stop the take
  with **B**.

<!-- screenshot: recording card with Opnemen (B) button and timer, page /studio_beta/opnameView.html -->

### Keyboard

| Key | Action |
|---|---|
| B | Start the take. With the timer off, press again to stop |
| A | Next item. Also sets the timer back to 5 s |
| O | Skip this item |
| C | Take one second longer (after 10 s it goes back to 1 s) |
| Q | Download the clips, after a confirmation |

### Side panel (Instellingen)

| Section | Buttons |
|---|---|
| Camera | **Camera Tabel (Probleemoplossing)** (camera table, for troubleshooting), **Live Streams Aan/Uit** |
| Opnames | **Vandaag Opgenomen (Review)**, **Starten Formatten** (format cards), **Start Downloaden Video's**, **Start Auto-Press B (20s)** (presses **B** every 20 seconds until you stop it) |
| Timer | **Timer inschakelen** (on by default) |

## Common tasks

### Record a take

1. Check the top bar: every camera you use today is online.
2. Let the signer read the card and watch the example video.
3. Press **B**. The countdown runs, then the card turns red while the cameras
   record.
4. Wait until the take stops by itself. With the timer off, press **B** again
   to stop. A stop within the first seconds is delayed: you see *Je hebt te
   snel op stop knop gedrukt* and the take stops by itself.
5. Press **A** for the next item.

### Record when a camera is missing

If fewer cameras are online than the camera list expects, **B** shows *Niet alle cameras
online!* with *Slechts n van de 5 cameras online. Toch opnemen?*

- If the missing camera is not in use today, click **Toch opnemen** (record
  anyway).
- If a camera you use dropped out, click **Annuleren** and fix it first. See
  [FX30 troubleshooting](../studio/troubleshooting-fx30.md).

The next take asks again.

### Review today's takes

1. Open **Instellingen** and click **Vandaag Opgenomen (Review)**.
2. Click **Bekijk** to watch a take. **✓ alles gedownload** means all clips of
   the take were downloaded from the cameras. *n/m gedownload* lists each clip
   with ✓ or ✗.

### Download the clips at the end of the day

1. Check that every camera battery is at least 50% full.
2. Open **Instellingen** and click **Start Downloaden Video's**. The download
   starts at once. (Pressing **Q** asks for confirmation first: **Ja,
   DOWNLOADEN**.)
3. Keep the cameras connected while *Bezig met downloaden....* shows.

When a memory card is almost full, the page starts a download by itself and
shows *Geheugen bijna vol, bezig met automatische upload*.

After the download, DRS copies, renders, crops and uploads the videos by
itself. See [what happens next](../guides/recording-session.md#what-happens-next).

### Format the cards

1. Open **Instellingen** and click **Starten Formatten**.
2. Read the download status. **Ja, formatteren** only appears when every clip
   is downloaded. Otherwise you see *n van m video's nog NIET gedownload —
   eerst downloaden!*
3. Click **Ja, formatteren**, and again under **LAATSTE KANS**.

!!! danger "Formatting cannot be undone"
    **Starten Formatten** erases the memory cards of all cameras.

The full session checklist is in
[Run a recording session](../guides/recording-session.md).

## Messages you may see

| Message | Meaning |
|---|---|
| Wachten op qR desktop | The QR page on the QR screen is not connected yet. Check that it is open |
| Waiting for QR on display... | The page does not see a QR code in the camera image yet. Check the QR screen and the capture device |
| Downloaden bezig, opnemen kan niet... | A download is running. Wait until it ends |
| Scan of bestandslijst bezig, even wachten... | The controller is scanning for cameras. Cameras disappear for a moment; wait |
| Cameras nemen al op (extern gestart) | The cameras were started from somewhere else. Stop them there first |
| Een van de camera's reageert niet | A camera stopped answering. All takes were stopped. Check the cables and that the cameras are on |
| Let op, weinig geheugen of lage batterij! | A card is nearly full, a battery is below 10%, or a camera is too hot |
| LET OP: CAMERA OVERVERHIT | A camera is too hot. Pause and let it cool down |
| Wachten op piep. | Waiting for the start beep. If it stays over 10 seconds, check that sound is on, at 60% volume or more |
| Controller niet bereikbaar — formatteren geblokkeerd. | The page cannot reach the camera controller on DRS, so it cannot check the downloads |

## Related

- [Run a recording session](../guides/recording-session.md)
- [Recording studio](../studio/index.md)
- [Check that a day's recordings are complete](../guides/check-day-complete.md)
- [Troubleshooting](../troubleshooting/index.md)
