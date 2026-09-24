# Main menu and gloss management

The gloss management page (signCollect-v2, `menu_beta`) is where every gloss
starts. You add glosses here before they can be recorded: a gloss with a theme
and a label shows up in [Camera Control](camera-control.md) under that theme or
label. The page shows every gloss in one list. You can search and filter it,
edit glosses in place, record a selfie video (*snelle opname*) and watch the
studio recordings of a gloss. Its navigation menu links to all other
interfaces.

- **Who uses it:** everyone. Adding and editing glosses is mostly done by
  researchers.
- **Address:** <https://signcollect.nl/menu_beta/>
- **Login:** yes.

## Open it

1. [Log in](../getting-started/login.md).
2. On the start page, click **signCollect interface (nieuw)**.

You now see the gloss list, filtered on your own glosses (**Eigenaar** is set
to you).

The labels are in Dutch or English, depending on the language an
administrator set for your account. This page gives the Dutch label, with the
English one in brackets where it differs.

<!-- screenshot: gloss table with filter bar and header, page /menu_beta/ -->

![Gloss table with filter bar and header](../assets/screenshots/gloss-list.png)


## The screen

### Header

- **Menu button** (**☰**, top left): opens the navigation menu.
- **Signbank / Signio switch:** shows glosses from one of two views. Which
  view opens first is set per account; without a setting it is *Signio*. You
  only see the switch if your account may use both.
- **Your user name** and the **log-out** icon, top right.

### Navigation menu

| Section | Items |
|---|---|
| Hoofdmenu (*Main menu*) | Glos Wizard, Video Crop fix, Studio Videos, Motion Capture, Zinnen Interface, NMM Site, Health Holland Interface, Video Downloader |
| Beheer (*Manage*) | Labels toevoegen (add labels), Batch toevoegen (add glosses in bulk), Themas Aanpassen (edit themes) |
| Admin | Gebruikers Beheren (manage users), Signbank koppeling ([Signbank connector](signbank-connector.md)). Only administrators see this section |
| Statistieken (*Statistics*) | Gebruikersactiviteit (user activity). Only one lab account sees this section |
| Account | Wachtwoord wijzigen (change password), Uitloggen (log out) |

What each item opens: [Where to find what](../getting-started/where-to-find-what.md).

### Filter bar

- **Search:** type part of a gloss, the English gloss or a sense.
- **Eigenaar** (*Owner*): whose glosses you see. It starts on you; choose
  **Iedereen** (*Everyone*) to see all.
- **Sorteren** (*Sort*), **Thema** (*Theme*), **Label**.
- **Status:** tick one or more, for example *Geen zelfopname* (no selfie
  video), *Met studio-video* (has a studio recording) or *Verborgen*
  (hidden).
- **Nieuwe glos** (*New gloss*) and **Reset filters**.

The list shows 50 glosses per page. Use the page buttons at the bottom, or
keep scrolling past the top or bottom of the page to go to the previous or
next page.

### A gloss row

- **Left:** a video thumbnail (the studio recording if there is one,
  otherwise your selfie video), and the buttons **Fonologie** (*Phonology*),
  **Notities** (*Notes*) and **Logboek** (*Logbook*: who changed what). Below
  them is the gloss ID, and **SB #…** if the gloss is linked to Signbank.
- **Middle:** **Glos NL**, **Glos EN**, **Thema**, **Labels** and the senses
  (**Betekenissen**, Dutch and English). **Studio video's** appears when the
  gloss has studio recordings.
- **Right:** **Wie** (*Owners*) and **Gecontroleerd** (*Checked*), a toggle
  between *klaar* (done) and *niet klaar* (not done).

The **⋮** button on the right opens the row menu:

- **Zelfopname maken** (*Record selfie video*)
- In the Signbank view only: **Push naar Signbank**, or for a linked gloss
  **Vergelijken met Signbank** and **Loskoppelen van Signbank**. See
  [Add or edit a gloss](../guides/gloss-signbank.md).
- **Alle zelfopnames verwijderen** (*Delete all selfie videos*), only when
  there are any
- **Verbergen / tonen** (*Hide / show*)
- **Verwijderen** (*Delete*)

!!! note "Delete hides"
    **Verwijderen** does not remove the gloss from the database. It hides it
    and writes *Glos verborgen* in the logbook. To find it again, tick
    **Status** → *Verborgen*.

## Common tasks

### Find a gloss

1. Set **Eigenaar** to **Iedereen**, unless you only want your own glosses.
2. Type part of the gloss in the search field.
3. Narrow the list with **Thema**, **Label** or **Status**.
4. Click **Reset filters** to start again.

### Edit a gloss

1. Click in the field you want to change, for example **Glos EN** or a sense.
2. Type the new text.

Changes save on their own while you type. *Opgeslagen* (*Saved*) confirms
it. If you see *Opslaan mislukt* (*Save failed*), your change was not stored;
try again.

### Add a gloss

Add the gloss before it is recorded. Camera Control lists glosses by theme and
label, so a gloss without them cannot be found there.

1. Click **Nieuwe glos**.
2. Fill in every field: **Glos NL**, **Glos EN**, **Thema**, at least one
   **Label**, and at least one sense in **Senses NL** and **Senses EN**.
3. Click **Aanmaken** (*Create*).

You now see *Glos aangemaakt* (*Gloss created*) and the new row.

!!! warning "All fields are required"
    Only **Glos NL** and **Glos EN** carry a `*`, but the form refuses to
    create the gloss until every field is filled. It shows a short message,
    *Vul eerst alle velden in: …*, that lists the missing fields.

To check first whether a sign already exists, use **Glos Wizard** in the menu:

1. Type a word in **Glos** and click **Zoeken** (*Search*).
2. If nothing fits, click **Als nieuwe glos toevoegen** (*Add as new gloss*).
   If the gloss name is taken, the wizard proposes the next free letter
   suffix.

### Record a selfie video (snelle opname)

A selfie video is a quick webcam reference of how the sign looks. Record one
for each new gloss before the studio session.

1. Open the row menu (**⋮**) and choose **Zelfopname maken**, or click the
   empty thumbnail.
2. Allow the browser to use your camera.
3. Click **Opname starten** (*Start recording*) and sign.
4. Click **Stoppen & opslaan** (*Stop & save*).

The video uploads by itself. *Zelfopname geüpload* (*Selfie video uploaded*)
confirms it, and the thumbnail shows the new video.

### Watch the studio recordings

1. Click **Studio video's** in the row. The button only appears when the gloss
   has studio recordings.
2. The **Studio-opnames** window shows the left, middle and right camera
   (**Links**, **Midden**, **Rechts**) of each take.

## Related

- [Add or edit a gloss and sync with Signbank](../guides/gloss-signbank.md)
- [Signbank connector](signbank-connector.md)
- [Troubleshooting](../troubleshooting/index.md)
