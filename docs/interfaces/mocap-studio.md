# Motion Capture Studio

The Motion Capture Studio page (mocapStudio, **3D Studio**) is used during a
Vicon motion-capture session. It shows the signer the next item, starts and
stops the recorder in Unreal, and logs every recording. It can also start the
copy of the day's recordings to the server.

- **Who uses it:** recording operators in the Visualisation Lab.
- **Address:** <https://signcollect.nl/mocapStudio/capture.html>
- **Login:** yes.

!!! tip "Use capture.html"
    Open `capture.html`. The older page `3dOpname.html` still exists but is not
    the one in use. The bare folder `/mocapStudio/` has no start page.

## Open it

- Go to <https://signcollect.nl/mocapStudio/capture.html>, or
- on the [mocap portal](mocap-portal.md), click **3D Studio**.

<!-- screenshot: mode selection with Glosses, HH, Sentences, BAK and Capture List, page /mocapStudio/capture.html -->

## The screen

### Select capture mode

| Mode | What you record |
|---|---|
| Glosses | Single glosses, by video gloss, image gloss or topic |
| HH | Health texts |
| Sentences | Sentences (*zinnen*) |
| BAK | Items from the BAK label lists |
| Capture List | The list of what still needs recording, per theme. You can pick an item, record a whole theme, or mark an item as captured |

<!-- TODO: confirm what BAK stands for -->

### Recording screen

- **Back:** return to mode selection.
- **Manual Sync:** copy the recordings to the server now (see below).
- Operator buttons: **Close UE**, **Broadcast Gloss**, **Export LSN**,
  **Custom Gloss**, **Custom Command**. These send commands to Unreal. Use them
  only when the session lead asks you to.
- Counters: how many items are left, and how many were recorded today.
- **Duration** slider (3 to 15 seconds): the countdown before a capture.
- The large text in the middle is the item to sign.
- A 3D preview of the reference animation.

### Keyboard

| Key | Action |
|---|---|
| A | Start the capture. Press again to stop |
| B | Save the capture and go to the next item |
| C | Skip this item |
| X | Leave theme batch mode |

## Common tasks

### Record an item

1. Choose a mode and an item.
2. Press **A**. The countdown runs, then the capture starts.
3. Press **A** again when the signer is done.
4. Press **B** to save and go to the next item, or **C** to skip.

### Copy today's recordings to the server now

The server copies new recordings from the Vicon PC every night. To do it
straight after a session:

1. Click **Manual Sync**.
2. Click **Yes, sync now**.
3. The window shows *Triggering sync...* and then *Syncing...* with live
   status. It keeps checking for about ten minutes.
4. Check the result on the [Vicon dashboard](vicon-dashboard.md).

## Related

- [Get mocap from Vicon to a baked animation](../guides/mocap-to-animation.md)
- [Vicon dashboard](vicon-dashboard.md)
- [Troubleshooting](../troubleshooting/index.md)
