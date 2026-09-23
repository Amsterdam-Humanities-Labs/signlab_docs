# Annotation editors (subBeta8 and 3DAnn3)

Two editors open from the [Zinnen interface](zinnen.md). Both show a video or
animation above a timeline with three tiers:

| Tier | What goes in it |
|---|---|
| Nederlands | The Dutch translation of the sentence |
| Signbank ID glossen | One Signbank gloss per sign |
| Gebaar-voor-Gebaar | A sign-by-sign description |

Both editors save your work on the server as an EAF file, one per video.

| Editor | What it is for | Opened with |
|---|---|---|
| subBeta8 | Annotate a studio video of a sentence, with AI help for segmenting and glossing | **Bewerk EAF (AI)** |
| 3DAnn3 | Time the annotation on the motion-capture take, shown as a 3D avatar | **Bewerk Motion Capture** |

- **Who uses them:** annotators.
- **Address:** opened from the Zinnen interface; you do not type the address.
- **Login:** yes for subBeta8.
<!-- TODO: confirm; the repo README says 3DAnn3 has no login check of its own -->

## subBeta8

<!-- screenshot: subBeta8 editor with video, tier timeline and toolbar, page /annotation-editors/subBeta8/zin/subBeta8.html -->

### The screen

- **Video** at the top, with the side camera angles next to it. **Hide Side
  Videos** hides them.
- **Playback:** **(P) Play**, speed buttons **0.25x (1)** to **Normal (4)**,
  and zoom **-** / **+**.
- **Toolbar:**
    - **+ Add Subtitle:** add a short, empty annotation at the start of the
      first tier (*Nederlands*). Drag it into place and type its text.
    - **Regex:** help for the search patterns.
    - **Download Subtitles:** save each tier as a WebVTT subtitle file
      (`.vtt`).
    - **Autosave Enabled:** shows the save state (see below).
    - **Disable Autoloop:** while the video plays, hovering over an
      annotation replays it. This button turns that off.
    - **Segment**, **Spot**, **Segment + Spot:** the AI helpers (see below).
    - **⌨ Keyboard Controls:** the list of shortcuts.
- **Status drop-downs** for *Video*, *Nederlands*, *Glossen* and *GvG*. These
  are the same statuses as in the Zinnen interface.
- **Go back to Zinnen:** saves, then returns to the list.

### Saving

The editor saves by itself about one second after each change. You do not
have to press anything.

- **Autosave Enabled** means your last change is stored.
- **Save Failed!** or **Save Error!** means it is not. You also get an alert
  such as *Upload failed due to a network error. Your changes have NOT been
  saved.*
- **Go back to Zinnen** shows *Opslaan...* and then *Opgeslagen!*. If it shows
  *Opslaan mislukt!*, you are asked whether to leave anyway. Choose to stay,
  and see [Troubleshooting](../troubleshooting/index.md).

### AI helpers

| Button | What it does |
|---|---|
| Segment | Splits the video into signs and fills the *Signbank ID glossen* tier with empty segments |
| Spot | Suggests the ten most likely glosses for each segment |
| Segment + Spot | Both, one after the other |

The helpers run on a GPU server behind signcollect.nl. Check every suggestion
before you accept it.

### Keyboard

| Key | Action |
|---|---|
| P | Play / pause |
| 1 2 3 4 | Speed 0.25x, 0.5x, 0.75x, 1x |
| + / - | Zoom in / out |
| Tab / Shift+Tab | Next / previous annotation on the same tier |
| Enter or double-click | Edit the text of the selected annotation |
| Esc | Stop editing |
| ← / → | Move the left edge by one frame |
| Shift+← / → | Move the right edge by one frame |
| Ctrl+← / → (Cmd on Mac) | Move the whole annotation by one frame |

An annotation stops when it meets its neighbour on the same tier. Neighbours
are never pushed or overlapped.

## 3DAnn3

3DAnn3 shows the motion-capture take as a 3D avatar instead of video. You use
it to set the timing of the annotation on the mocap take.

<!-- screenshot: 3DAnn3 with avatar, timeline and sync buttons, page /annotation-editors/3DAnn3/zin/3DAnn3.html -->

### The screen

- **3D view** with the avatar. **Hand L**, **Hand R** and **Reset view** move
  the camera.
- The same playback, speed and zoom controls as subBeta8.
- **Shift all:** **-1s**, **-0.1s**, **+0.1s**, **+1s** move every annotation
  at once.
- **Status drop-downs** for the three MCP statuses: *Status Postprocessing*,
  *Status Tijd Annotatie Gloss* and *Status Tijd annotatie Gebaar voor
  Gebaar/Nederlands*.
- **Auto-Segment** re-times the *Signbank ID glossen* tier to the take.
  **Revert Autoseg** undoes it. **View 2D Video** opens the studio video in a
  new tab.
- **Sync van mp4:** copy one tier (**Nederlands**, **Gebaar-voor-Gebaar** or
  **Signbank ID glossen**) from the studio-video annotation into this take.
  Then click **Save Sync**, or **Revert Sync** to undo.

If you leave with a sync that is not saved, the editor asks what to do:
**Sync opslaan** (save), **Sync verwerpen** (discard) or **Op deze pagina
blijven** (stay).

### When it does not open

The Zinnen interface shows one of these alerts instead:

- *No motion capture file found for this video.* There is no mocap take for
  this sentence.
- *This capture has not been through the FBX-to-GLB conversion yet …* The take
  exists but has no 3D version yet. The conversion runs every hour on the
  server. Try again later, or ask an administrator.

## Common tasks

- [Annotate a sentence and save the EAF](../guides/annotate-sentence.md)
- [Get mocap from Vicon to a baked animation](../guides/mocap-to-animation.md)

## Related

- [Zinnen interface](zinnen.md)
- [Troubleshooting](../troubleshooting/index.md)
