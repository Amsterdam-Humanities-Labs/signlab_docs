# Main menu and gloss management

The gloss management page (signCollect-v2) is the centre of SignCollect. It
shows every gloss in one table. You can search and filter it, edit glosses in
place, record a selfie video and watch the studio recordings of a gloss. Its
navigation menu links to all other interfaces.

- **Who uses it:** everyone. Editing glosses is mostly done by researchers.
- **Address:** <https://signcollect.nl/menu_beta/>
- **Login:** yes.

## Open it

1. [Log in](../getting-started/login.md).
2. On the start page, click **signCollect interface (nieuw)**.

The page shows in Dutch or English, depending on the language an administrator
set for your account.

<!-- screenshot: gloss table with filter bar and header, page /menu_beta/ -->

## The screen

### Header

- **Menu button** (three lines, top left): opens the navigation menu.
- **Signbank / Signio switch:** shows glosses from one of two sources. *Signio*
  is the default. You only see the switch if your account may use both.
- **Your user name** and the **log-out** icon, top right.

### Navigation menu

| Section | Items |
|---|---|
| Hoofdmenu (main) | Glos Wizard, Video Crop fix, Studio Videos, Motion Capture, Zinnen Interface, NMM Site, Health Holland Interface, Video Downloader |
| Beheer (manage) | Labels toevoegen (add labels), Batch toevoegen (add glosses in bulk), Themas Aanpassen (edit themes) |
| Admin | Gebruikers Beheren (manage users), Signbank koppeling (Signbank connector). Only administrators see this section |
| Statistieken | Gebruikersactiviteit (user activity). Only some accounts see this section |
| Account | Uitloggen (log out) |

### Filter bar

- **Search:** type part of a gloss, the English gloss or a sense.
- **Eigenaar** (owner), **Sortering** (sort order), **Thema** (theme),
  **Labels**.
- **Status:** tick one or more, for example *Geen zelfopname* (no selfie
  video), *Heeft studio opname* (has a studio recording) or *Verborgen*
  (hidden).
- **Nieuwe glos** (new gloss) and **Reset filters**.

The table shows 50 glosses per page. Scroll past the top or bottom of the page
to go to the previous or next page.

### A gloss row

Each row shows the gloss, the English gloss, the theme, labels, senses (Dutch
and English), owners and a **Checked** toggle (*klaar* / *niet klaar*). It
also shows a thumbnail of the selfie video and, when there are any, a **Studio video's** button.

The **⋮** button on the right opens the row menu:

- **Record selfie video**
- **Phonology**
- **Notes** and **Logbook** (who changed what)
- **Hide / show**
- **Delete all selfie videos** (only when there are any)
- **Delete**
- In the Signbank view only: **Push to Signbank**, **Compare with Signbank**
  and **Disconnect from Signbank**. See [Add or edit a gloss](../guides/gloss-signbank.md).

## Common tasks

### Find a gloss

1. Type part of the gloss in the search field.
2. Narrow the list with **Thema**, **Labels** or **Status**.
3. Click **Reset filters** to start again.

### Edit a gloss

1. Click in the field you want to change, for example the English gloss or a
   sense.
2. Type the new text.

Changes save on their own while you type. A short *Saved* message confirms
it. If you see *Save failed*, your change was not stored; try again.

### Add a gloss

1. Click **Nieuwe glos**.
2. Fill in the gloss and the English gloss (both required), and optionally the
   theme and senses.
3. Click **Aanmaken** (Create).

To check first whether a sign already exists, use **Glos Wizard** in the menu:
type a word, click **Zoeken** (Search), then **Als nieuwe glos toevoegen**
(Add as new gloss) if nothing fits.

### Record a selfie video

1. Open the row menu and choose **Record selfie video**, or click the empty
   thumbnail.
2. Allow the browser to use your camera.
3. Click **Start recording** (*Opname starten*) and sign.
4. Click **Stop & save**. The video uploads by itself. *Selfie video uploaded*
   confirms it.

### Watch the studio recordings

1. Click **Studio video's** in the row. The button only shows when the gloss has studio recordings.
2. The **Studio recordings** window shows the left, centre and right camera of
   each take.

## Related

- [Add or edit a gloss and sync with Signbank](../guides/gloss-signbank.md)
- [Signbank connector](signbank-connector.md)
- [Troubleshooting](../troubleshooting/index.md)
