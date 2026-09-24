# Studio archive

The studio archive (studio-archive, **Studio Index**) lets you browse every
studio take by date. Each take shows the gloss or sentence and its camera
angles (three to five, depending on how many cameras recorded). Use it the day
after a recording session to check that all takes arrived and were processed.

The archive only reads. You cannot change or delete takes here.

- **Who uses it:** recording operators and researchers.
- **Address:** <https://signcollect.nl/studioIndex/>
- **Login:** yes.

## Open it

- Go to <https://signcollect.nl/studioIndex/>, or
- in the [gloss management](main-menu.md) menu, choose **Studio Videos**.

You now see the takes of the latest recording day, with its status line.

<!-- screenshot: Studio Index with date filter, status line and take cards, page /studioIndex/ -->

![Studio Index with date filter, status line and take cards](../assets/screenshots/studio-archive.png)


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
   You now see the status line under the filters.
2. Compare **CameraRecords** with **Matched**. A big gap means takes were
   logged in Camera Control but their videos are not on the server.
3. Compare **Matched** with **PostProcessed**. A big gap means videos arrived
   but are not rendered and cropped yet.
4. Look for both confirmation messages.

The full check is in
[Check that a day's recordings are complete](../guides/check-day-complete.md).

### Look at all angles of a take

1. Set **Video Display** to **5 Videos (All)**.
2. Find the take and play the angles.

!!! tip "Processing takes time"
    The studio Mac (DRS) uploads the videos at the end of the capture day, and
    processing follows after that. On the day of recording, *Matched* and
    *PostProcessed* are often lower than *CameraRecords*. Check again the next
    day.

## Related

- [Camera Control](camera-control.md)
- [Crop fix manager](crop-fix-manager.md)
- [Check that a day's recordings are complete](../guides/check-day-complete.md)
- [Troubleshooting](../troubleshooting/index.md)
