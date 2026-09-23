# Fix a badly cropped take

After rendering, each studio video is cropped automatically around the signer.
Sometimes the crop cuts off a hand or part of the sign. This guide puts such a
take in the queue to be cropped again with a wider frame.

## 1. Find the file name

1. Find the take in the [studio archive](../interfaces/studio-archive.md) or
   the [Zinnen interface](../interfaces/zinnen.md).
2. Note the name of the middle-camera file. It starts with `M` and the date,
   for example `M20251001_2313`.

## 2. Queue the fix

1. Open the [crop fix manager](../interfaces/crop-fix-manager.md):
   <https://signcollect.nl/videoFix/>.
2. Type the file name, or part of it, in the search field and click
   **Search**.
3. Find the row in **Search Results**.
4. If the sign also leaves the frame at the bottom, tick **OOB: Bottom**. The
   top, left and right are always widened.
5. Click **Fix Crop**. The button changes to **Pending**, and the take appears
   under **Unresolved**.

<!-- screenshot: crop fix row with OOB Bottom checkbox and Fix Crop button, page /videoFix/ -->

![Crop fix row with OOB Bottom checkbox and Fix Crop button](../assets/screenshots/crop-fix-manager.png)


## 3. Wait for the new crop

The studio pipeline picks up the queue, crops the left, middle and right
videos again, and reports each one back. When all three are done, the take
moves to **Resolved** and the button shows **Fixed**.

## 4. Check the result

1. Open the take in the studio archive again.
2. Check that the whole sign is now in the frame.
3. If it is still cut off, go back to the crop fix manager, click **Reset** on
   the take and queue it again.

!!! tip "Many takes at once"
    Researchers mark glosses that are out of frame with the label *GEBAAR UIT
    DE BEELD*. **Populate from "GEBAAR UIT DE BEELD"** adds all of them to the
    queue in one go.

!!! note "Sentence videos"
    For sentence videos you can also use **zinCrop**
    (<https://signcollect.nl/zin/zinCrop/>). It adds fixes to the same queue.

## If a fix stays Pending

If a take stays **Pending** for more than a day, the pipeline may not be
running. In the [client monitor](../interfaces/client-monitor.md), check the
client **DRS Crop Fix**. If it is **Offline**, tell an administrator.

## Related

- [Crop fix manager](../interfaces/crop-fix-manager.md)
- [Troubleshooting](../troubleshooting/index.md)
