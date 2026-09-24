# Troubleshooting

This section lists problems that SignCollect users run into, and what to do about them. Some are handling mistakes you can fix yourself. Others are system errors that only an administrator can fix.

## How to use this section

1. Do the [first checks](#first-checks) below. They solve many problems in a minute.
2. Pick the area of your problem in the [table of areas](#areas).
3. Find your symptom. Headings are written the way you would say the problem, or they quote the error message. Use the search box at the top to search for an exact message.
4. Follow **Try this** step by step.
5. If it still fails, follow **Still stuck?** and send that information to an administrator.

Every issue has the same parts:

- **Type**: *user error* (something in how the tool was used), *system error* (something broke on a server or machine), or *both*.
- **Who can fix**: *you*, or an *administrator*.
- **Likely cause**, **Try this** and **Still stuck?**.

Each issue has its own link. Click the ¶ sign next to a heading to copy it, and paste that link in your message to the administrator.

## First checks {#first-checks}

- **Reload the page.** Force-reload with `Ctrl+Shift+R` (`Cmd+Shift+R` on a Mac). See [Browser cache](browser.md#br-cache).
- **Log in again.** Many errors ("not logged in", "Unauthorized", 401) mean your session expired. See [Login and accounts](login.md).
- **Check the address.** Use `signcollect.nl` and open tools from the menu. Demo hosts miss the studio and AI features. Old bookmarks may point to renamed tools.
- **Try a second page.** If unrelated pages fail too, it is a server problem. See [Server and system](system.md).
- **Use Chrome or Edge on a desktop computer.** Several tools need features other browsers lack. See [Browser problems](browser.md).
- **Wait for the schedule.** Videos, mocap files and syncs arrive by scheduled jobs, not instantly. The studio PC uploads the day's recordings at the end of the day, so a recording from today may only appear tomorrow.
- **Do not close a tab that says saving failed.** Your changes only live there.
- **In the studio: check cables, power and batteries** before anything else. See [Recording sessions](recording.md).

## What to send an administrator {#what-to-send}

A good report saves a lot of time. Include:

- the page address (copy it from the address bar);
- the date and time the problem happened;
- the exact error text (copy it, or make a screenshot);
- the sentence ID, take ID, gloss name or capture date involved;
- what you already tried from this section.

Never send passwords or upload tokens.

## Areas {#areas}

| Area | Covers | Issues |
|---|---|---|
| [Login, accounts and the menu](login.md) | Wrong password, blocked account, login loops, roles, datasets, menu links | 12 |
| [Glosses and Signbank sync](glosses.md) | Saving, hiding and batch-adding glosses, labels, notes, push and pull to Signbank, the Signbank export | 16 |
| [Sentence annotation and EAF files](annotation.md) | The sentence (zin) overview, EAF upload and download, ZIP, status, overwritten edits | 13 |
| [Annotation editors](editors.md) | subBeta8 and 3DAnn3: loading, saving, Smart Search, Segment and Spot, sync | 15 |
| [Annotation tool](annotation-tool.md) | v3, webcam and clusters modes, autosave, video conversion, spotting, Smart Search | 15 |
| [Recording sessions](recording.md) | FX30 cameras, Camera Control, batteries, overheating, QR codes, downloading clips | 18 |
| [Video processing and studio archive](video-processing.md) | Crops and the Crop Fix Manager, green screen to blue, thumbnails, missing angles, the DRS pipeline | 18 |
| [Motion capture](mocap.md) | Vicon sync, viconDashboard, the mocap studio page, FBX post-processing, GLB viewers, blendbaking, SAM 3D body queue | 23 |
| [Blackmagic cameras](blackmagic.md) | Camera control, recording settings, copies to the research drive | 9 |
| [Uploads, tokens, API and patient-info](uploads.md) | Video uploads, upload tokens, API errors, patient-info texts | 11 |
| [Monitoring and alerts](monitoring.md) | The client monitor dashboard, heartbeats, disk, mount and database alerts | 11 |
| [Server and system](system.md) | Site down, database down, disk full, certificate, slow pages, stopped jobs | 14 |
| [Browser problems](browser.md) | Cache, autoplay, codecs, pop-ups, camera access, WebGL | 8 |

**Total: 183 issues.**
