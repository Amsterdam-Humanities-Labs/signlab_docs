# Studio archive

The studio archive (studio-archive, **Studio Index**) lets you browse every
studio take by date. Each take shows the gloss or sentence and up to five
camera angles. For a chosen date it also checks whether all recordings arrived
and were processed.

The archive only reads. You cannot change or delete takes here.

- **Who uses it:** recording operators and researchers.
- **Address:** <https://signcollect.nl/studioIndex/>
- **Login:** yes.

## Open it

- Go to <https://signcollect.nl/studioIndex/>, or
- in the [gloss management](main-menu.md) menu, choose **Studio Videos**.

<!-- screenshot: Studio Index with date filter, status line and take cards, page /studioIndex/ -->

## The screen

### Filters

- **Filter by Date:** one recording day, or **All Dates**. The page opens on
  the latest date.
- **Video Display:** **1 Video (Center)**, **3 Videos (L-M-R)** (the default)
  or **5 Videos (All)**.

### Date status

When you choose a date, a status line appears:

| Field | Meaning |
|---|---|
| CameraRecords | Takes that Camera Control logged that day |
| Matched | Video takes on the server for that day, linked to a gloss or sentence |
| Validated | Logged takes that have a matching video, counted per gloss or sentence |
| Missing | Logged takes that have no matching video yet |
| PostProcessed | Takes that are rendered and cropped |
| Files — L / M / R / A / B | For each camera angle, how many of the matched takes have a file |

Two messages confirm a good day:

- *Alle videobestanden aanwezig op signcollect server:* all video files are on
  the server.
- *Alles gerendered:* everything is rendered.

Small differences, up to five takes, still count as complete.

### Take cards

One card per take, with the gloss or sentence and the video players. The
thumbnail is the processed (cropped) version when it exists, otherwise the raw
video. Takes are listed 100 per page.

## Common tasks

### Check a recording day

1. Choose the date in **Filter by Date**.
2. Read the status line. Compare **CameraRecords** with **Matched**, and
   **Matched** with **PostProcessed**.
3. Look for both confirmation messages.

The full check is in
[Check that a day's recordings are complete](../guides/check-day-complete.md).

### Look at all angles of a take

1. Set **Video Display** to **5 Videos (All)**.
2. Find the take and play the angles.

!!! tip "Processing takes time"
    New takes are rendered about every hour and cropped about every 15
    minutes. On the day of recording, *PostProcessed* is often lower than
    *Matched*. Check again the next day.

## Related

- [Camera Control](camera-control.md)
- [Crop fix manager](crop-fix-manager.md)
- [Check that a day's recordings are complete](../guides/check-day-complete.md)
- [Troubleshooting](../troubleshooting/index.md)
