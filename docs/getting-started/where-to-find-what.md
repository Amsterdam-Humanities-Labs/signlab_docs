# Where to find what

This page maps every part of SignCollect to where you open it. Everything
starts at **signcollect.nl**. After you log in, the start page
(**Kies een interface**) offers two tiles:

| Tile | Opens | Use it for |
|---|---|---|
| **signCollect interface (nieuw)** | `/menu_beta/` | Glosses, and the menu to every other tool |
| **Zinnen interface** | `/zin/zinnen.html` | Sentences (zinnen): status, videos, annotation |

Labels on the gloss page follow the language of your account. Below, the Dutch
label comes first, the English one in brackets.

## The gloss page and its menu

The gloss list is the main screen. The **☰** button at the top left opens the
menu with every other tool. Your user name and the log-out icon are at the top
right.

![The gloss list](../assets/screenshots/gloss-list.png)

![The navigation menu](../assets/screenshots/navigation-menu.png)

| Section | Menu item | What you find there | Who uses it |
|---|---|---|---|
| Hoofdmenu | **Glos Wizard** | Check whether a sign exists, then create the gloss | Researchers |
| Hoofdmenu | **Video Crop fix** (*Video crop fix*) | Queue of takes where the automatic crop cut off the sign | Researchers, operators |
| Hoofdmenu | **Studio Videos** (*Studio videos*) | The studio archive by date, all camera angles | Everyone |
| Hoofdmenu | **Motion Capture** (*Motion capture*) | The motion-capture portal | Mocap team |
| Hoofdmenu | **Zinnen Interface** (*Sentences interface*) | The Zinnen interface | Annotators |
| Hoofdmenu | **NMM Site** (*NMM site*) | Glosses still to record for non-manual markers (NMM) and OC | Recording team |
| Hoofdmenu | **Health Holland Interface** | Patient-information texts linked to NGT recordings | Health Holland project |
| Hoofdmenu | **Video Downloader** (*Video downloader*) | Download videos by theme and/or label | Researchers |
| Beheer (*Manage*) | **Labels toevoegen** (*Add labels*) | Create and manage labels | Researchers |
| Beheer (*Manage*) | **Batch toevoegen** (*Batch add*) | Add many glosses at once, one per line | Researchers |
| Beheer (*Manage*) | **Themas Aanpassen** (*Manage themes*) | The list of themes | Researchers |
| Admin | **Gebruikers Beheren** (*Manage users*) | Add users, set role and language, block and unblock | Administrators only |
| Admin | **Signbank koppeling** | The link with Signbank: test, API key, refresh the gloss list | Administrators only |
| Statistieken (*Statistics*) | **Gebruikersactiviteit** (*User activity*) | Who did what, and the busiest pages | One lab account only |
| Account | **Wachtwoord wijzigen** (*Change password*) | Change your own password | Everyone |
| Account | **Uitloggen** (*Log out*) | End your session | Everyone |

Details: [Main menu and gloss management](../interfaces/main-menu.md).

## Sentences (Zinnen interface)

The buttons at the top lead to the sentence tools; the coloured counters show
how many sentences are in each state. Filters narrow the list; **Reset
Filters** clears them.

![Zinnen interface: buttons, counters and filters](../assets/screenshots/sentences-interface.png)

| Button | Opens |
|---|---|
| **ZNN App** | A sign-language browser: Dutch, sign-by-sign (Gebaar voor Gebaar) and gloss |
| **View Logs** | The action log |
| **Upload EAF** | Upload an ELAN annotation file that is not tied to a row yet |
| **Nieuwe Zinnen** | Add new sentences in batch |
| **Statistieken** | Activity timeline and statistics |
| **All Videos** | All sentence videos |
| **Overzicht** | Statistics on all sentences (*Overzicht Statistieken*) |

Each sentence has **View Videos**, **Delete Sentence** and **Logboek**. Each of
its videos has **Bewerk EAF (AI)**, **Download EAF (MP4)**, **Download**,
**Upload EAF** and more. Details: [Zinnen interface](../interfaces/zinnen.md).

## Recording (studio)

| Page | Opens | For |
|---|---|---|
| **Camera Control** | `/studio_beta/opnameView.html` | The operator during a recording session with the FX30 cameras |
| **Studio Videos** | `/studioIndex/` | Checking a day's recordings: every take, every camera angle |
| **Video Crop fix** | `/videoFix/` | Takes whose crop cut off the sign |

![Camera Control, waiting for the QR desktop](../assets/screenshots/camera-control.png)

!!! warning "Camera Control settings"
    The settings menu contains **Starten Formatten**, which erases *all* cameras.
    Only use it after the day's videos are safely off the cameras and uploaded.

![Studio videos: date filter and completeness check](../assets/screenshots/studio-archive.png)

![Crop Fix Manager](../assets/screenshots/crop-fix-manager.png)

## Motion capture

The **Motion Capture** menu item opens the portal (`/mocap_site/`) with four
tiles.

![Motion capture portal](../assets/screenshots/mocap-portal.png)

| Tile | For |
|---|---|
| **Motion Capture File Manager** | Download unprocessed recordings, upload cleaned (post-processed) files |
| **3D Studio Capture Site** | Live capture sessions: choose Glosses, HH, Sentences, BAK or the Capture List |
| **signCollect Avatar Player** | Play baked avatar animations |
| **Vicon Dashboard Sync** | See whether every Vicon capture arrived complete |

For the dataset as a whole, and to find or download animation files in bulk,
open **`/mocapOverview/`** ([Mocap overview and file API](../interfaces/mocap-overview.md)).

![Motion Capture File Manager](../assets/screenshots/mocap-file-manager.png)

![Motion Capture Studio](../assets/screenshots/mocap-studio.png)

![Vicon Capture Dashboard](../assets/screenshots/vicon-dashboard.png)

In the Vicon dashboard, **green** means a capture is complete (all five parts arrived),
**yellow** means it is still uploading, and **red** means parts are missing.

## Annotation tool

`/annotation-tool/` is a browser editor for any video with ELAN (EAF)
annotation. Drop a video (and optionally an EAF) on the page, or choose files.
It needs **Chrome or Edge** for autosave. Two other modes:
`?mode=webcam` and `?mode=clusters`. Details:
[Annotation tool](../interfaces/annotation-tool.md).

![Annotation tool, waiting for a video](../assets/screenshots/annotation-tool.png)

## Health Holland

Menu item **Health Holland Interface** (`/hh/`). Details:
[Patient-info texts](../interfaces/patient-info.md).

![Health Holland contents](../assets/screenshots/patient-info.png)

## Signbank link (administrators)

Menu item **Signbank koppeling** under **Admin**. Details:
[Signbank connector](../interfaces/signbank-connector.md).

![Signbank link](../assets/screenshots/signbank-link.png)
