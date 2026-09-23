# Get mocap from Vicon to a baked animation

This guide follows a motion-capture recording from the Vicon session to a
finished, annotated 3D animation. It touches six tools. Each step names the
tool and what to check before you move on.

```
Record (Motion Capture Studio)
  → copy to server (nightly, or Manual Sync)
  → check arrival (Vicon dashboard)
  → clean up (File Manager)
  → 3D conversion to GLB (automatic, hourly)
  → time annotation (Zinnen interface, 3DAnn3)
  → baked take with gloss timings (blendBaking, Avatar Player)
```

A *baked* take is one that has been converted to a GLB animation file.

## 1. Record

1. Open the [Motion Capture Studio](../interfaces/mocap-studio.md):
   <https://signcollect.nl/mocapStudio/capture.html>.
2. Choose the mode, for example **Sentences**.
3. For each item: press **A** to start, **A** to stop, then **B** to save and
   go to the next item. Press **C** to skip.

## 2. Copy the recordings to the server

The server copies new recordings from the Vicon PC every night. To have them
straight away:

1. In the Motion Capture Studio, click **Manual Sync**.
2. Click **Yes, sync now** and wait for the status to finish.

## 3. Check that everything arrived

1. Open the [Vicon dashboard](../interfaces/vicon-dashboard.md):
   <https://signcollect.nl/viconDashboard/>.
2. Click the session date in **Date Overview**.
3. Every row should be green. Yellow means still copying: wait. Red means a
   part is missing: note the recording name and the missing column, and tell
   an administrator.

## 4. Clean up the animation

1. Open the File Manager from the [mocap portal](../interfaces/mocap-portal.md).
2. Filter on recordings that are not processed yet.
3. Download the FBX, or the ZIP with the reference video.
4. Clean the animation up in Unreal.
5. Upload the result under **Upload Processed Files**.
6. Mark the recording as approved, or as needs review with a comment.

## 5. Wait for the 3D conversion

<!-- TODO: confirm whether the GLB is built from the cleaned FBX (step 4) or from the raw CC export; viconSync cc_pipeline converts CC exports hourly -->
The server converts the character exports to GLB files every hour. The **GLB**
column of the Vicon dashboard shows when a recording has one.

Until then, **Bewerk Motion Capture** in the Zinnen interface says *This
capture has not been through the FBX-to-GLB conversion yet*.

## 6. Annotate the timing on the take

1. Open the [Zinnen interface](../interfaces/zinnen.md) and find the sentence.
   The studio-video annotation must be done first: **Bewerk Motion Capture**
   only works when *Status Nederlands*, *Status Glossen* and *Status Gebaar
   voor Gebaar* are all *Klaar*.
2. Click **Bewerk Motion Capture**. The take opens in
   [3DAnn3](../interfaces/annotation-editors.md#3dann3).
3. Under **Sync van mp4**, copy the tiers from the studio video: click
   **Nederlands**, **Gebaar-voor-Gebaar** and **Signbank ID glossen**.
4. Click **Save Sync**.
5. Shift the timing to match the avatar: use **-1s** to **+1s** for the whole
   annotation, or **Auto-Segment** for the gloss tier, and fix single
   annotations by hand.
6. Set **MCP - Status Tijd Annotatie Gloss** and **MCP - Status Tijd
   annotatie Gebaar voor Gebaar/Nederlands** to *Klaar*.
7. Click **Go back to Zinnen**.

## 7. Use the baked take

- [blendBaking](../interfaces/blendbaking.md) lists every baked take with a
  gloss SRT. Download the SRTs, or query gloss timings through its API.
- The **Avatar Player** on the [mocap portal](../interfaces/mocap-portal.md)
  plays the animations on an avatar.
- The File Manager downloads the EAF/SRT files of up to 100 finished
  recordings at once.

## Related

- [Motion Capture Studio](../interfaces/mocap-studio.md)
- [Vicon dashboard](../interfaces/vicon-dashboard.md)
- [Troubleshooting](../troubleshooting/index.md)
