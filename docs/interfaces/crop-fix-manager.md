# Crop fix manager

The crop fix manager (crop-fix-manager, **VideoFix**) is a work queue for
studio takes where the automatic crop cut off part of the sign. You add a take
to the queue; the studio pipeline then crops that take again with a wider
frame and marks it as fixed.

A fix always covers three camera angles of a take: left (L), middle (M) and
right (R). Each angle has its own status. The take is named after its middle
camera file, for example `M20251001_2313`.

- **Who uses it:** researchers and recording operators.
- **Address:** <https://signcollect.nl/videoFix/>
- **Login:** yes.

## Open it

- Go to <https://signcollect.nl/videoFix/>, or
- in the [gloss management](main-menu.md) menu, choose **Video Crop fix**.

<!-- screenshot: Crop Fix Manager with search box and the three tabs, page /videoFix/ -->

## The screen

- **Search:** type part of a file name, for example `M20251001_2313`. Partial
  names match.
- **Populate from "GEBAAR UIT DE BEELD":** adds every gloss that carries the
  label *GEBAAR UIT DE BEELD* (sign out of frame) to the queue.
- Three tabs, each with a count:
    - **Search Results**
    - **Unresolved:** fixes that wait for the pipeline.
    - **Resolved:** fixes that are done.
- Each row shows the file name, the three files (L / M / R) and a button:

| Button | Meaning |
|---|---|
| **Fix Crop** | No fix requested yet. Click to add the take to the queue |
| **Pending** | A fix is requested and at least one angle is not re-rendered yet |
| **Fixed** | All three angles are re-rendered |

Before you click **Fix Crop**, tick **OOB: Bottom** if the sign also goes out
of the frame at the bottom. Top, left and right are always widened. **Reset**
removes a requested fix, so you can submit it again.

## Common tasks

### Queue a badly cropped take

1. Search for the take by its file name.
2. Tick **OOB: Bottom** if the hands leave the frame at the bottom.
3. Click **Fix Crop**. The button changes to **Pending**.
4. Check back later. When all three angles are done, the take moves to
   **Resolved** and the button shows **Fixed**.

The full workflow is in [Fix a badly cropped take](../guides/fix-crop.md).

### Sentence videos

For sentences, the Zinnen side page **zinCrop** (<https://signcollect.nl/zin/zinCrop/>)
lists sentence videos with their crop-fix status and adds fixes to the same
queue.

## Related

- [Fix a badly cropped take](../guides/fix-crop.md)
- [Studio archive](studio-archive.md)
- [Troubleshooting](../troubleshooting/index.md)
