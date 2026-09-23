# Getting started

SignCollect is the system the UvA SignLab uses to collect Sign Language of the
Netherlands (NGT). It covers the whole path of a recording:

1. A signer is recorded in the studio with five Sony FX30 cameras, or in the
   Visualisation Lab with Vicon motion capture.
2. The videos are rendered, cropped and uploaded to signcollect.nl
   automatically.
3. Annotators add time-aligned annotation (ELAN EAF files) to the videos.
4. Glosses are managed in one list and kept in step with Signbank.

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
3. Pick an interface on the start page. Most people start in the
   [gloss management interface](../interfaces/main-menu.md). Its menu links to
   every other part of SignCollect.
4. Follow the [how-to guide](../guides/index.md) for your task.

!!! tip "Words you do not know"
    SignCollect uses Dutch and English terms side by side: *glos* and gloss,
    *zin* and sentence, *opname* and take. The [glossary](../glossary.md)
    explains them.

## Something not working?

See [Troubleshooting](../troubleshooting/index.md).
