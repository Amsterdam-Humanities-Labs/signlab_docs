# Getting started

SignCollect is the system the UvA SignLab uses to collect Sign Language of the
Netherlands (NGT). This page shows how a sign travels through the system and
which part of SignCollect you will use.

## How a recording travels through SignCollect

1. **Enter the glosses.** In the
   [gloss management page](../interfaces/main-menu.md) (`/menu_beta/`), add
   each gloss with a theme and at least one label.
2. **Make a quick reference video.** For each gloss, record a *snelle opname*
   with your webcam (**Zelfopname maken** in the gloss row).
3. **Record in the studio.** The glosses now appear in
   [Camera Control](../interfaces/camera-control.md), listed per theme or
   label. The signer is filmed with three to five Sony FX30 cameras. A QR code
   on the second or third screen identifies each take; the cameras must point
   at it. Motion capture with Vicon happens separately, in the Visualisation
   Lab.
4. **Upload.** At the end of the capture day, the studio Mac (DRS) uploads the
   videos to signcollect.nl by itself.
5. **Processing.** The video pipeline renders and crops the videos. Later, the
   finished videos appear in the interfaces, for example in the
   [studio archive](../interfaces/studio-archive.md). A take with a bad crop
   goes to the [crop fix manager](../interfaces/crop-fix-manager.md).
6. **Annotate.** Annotators add time-aligned annotation (ELAN EAF files) to the
   sentence videos.
7. **Sync with Signbank.** Glosses are kept in step with
   [Signbank](../interfaces/signbank-connector.md).

Everything runs in the browser at <https://signcollect.nl>. You need an
account; see [Logging in](login.md).

## Who uses what

The lab has four kinds of users. SignCollect itself only knows two account
roles, *user* and *admin*. The roles below describe what you do, not what the
system calls you.

| Role | What you do | Interfaces you use most |
|---|---|---|
| Annotator | Annotate sentence videos: Dutch translation, glosses, sign-by-sign timing | [Zinnen interface](../interfaces/zinnen.md), [annotation editors](../interfaces/annotation-editors.md), [annotation tool](../interfaces/annotation-tool.md) |
| Recording operator | Run studio and mocap recording sessions | [Camera Control](../interfaces/camera-control.md), [Motion Capture Studio](../interfaces/mocap-studio.md), [studio archive](../interfaces/studio-archive.md), [Vicon dashboard](../interfaces/vicon-dashboard.md) |
| Researcher | Manage glosses, review recordings, download data | [main menu and gloss management](../interfaces/main-menu.md), [studio archive](../interfaces/studio-archive.md), [blendBaking](../interfaces/blendbaking.md), [crop fix manager](../interfaces/crop-fix-manager.md) |
| Administrator | Manage accounts, the Signbank link and the servers | [Signbank connector](../interfaces/signbank-connector.md), [client monitor](../interfaces/client-monitor.md), [For administrators](../admin/index.md) |

The full list of interfaces, with their addresses, is on the
[Interfaces](../interfaces/index.md) page.

## Your first session

1. Ask an administrator for an account. See [Logging in](login.md).
2. Log in at <https://signcollect.nl/login.html>.
   You now see the start page, **Kies een interface**.
3. Click **signCollect interface (nieuw)** for glosses, or **Zinnen interface**
   for sentences. The menu (**☰**) of the gloss page links to every other part
   of SignCollect; see [Where to find what](where-to-find-what.md).
4. Follow the [how-to guide](../guides/index.md) for your task.

!!! tip "Words you do not know"
    SignCollect uses Dutch and English terms side by side: *glos* and gloss,
    *zin* and sentence, *opname* and take. The [glossary](../glossary.md)
    explains them.

## Something not working?

See [Troubleshooting](../troubleshooting/index.md).
