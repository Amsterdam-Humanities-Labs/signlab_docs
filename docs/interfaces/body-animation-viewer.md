# Body-animation viewer

The body-animation viewer (body-animation-viewer, **GLB Viewer**) plays 3D
body animations that were reconstructed from studio videos. You search by
gloss or file name, and the matching animations play on an avatar. You can
also line signs up into a sentence.

!!! warning "Experimental"
    This viewer is a research prototype. It has no login and no tests, and no
    other page links to it. Expect rough edges.

- **Who uses it:** researchers.
- **Address:** <https://signcollect.nl/s3b_glb/>
- **Login:** no.

## Open it

| Page | Address | What it shows |
|---|---|---|
| GLB Viewer | `/s3b_glb/index.html` | Search all reconstructed animations. Each clip plays trimmed to the sign |
| Gebarenstrand | `/s3b_glb/gebarenstrand.html` | A fixed set of about 5,400 animations with readable names. Clips play in full |

The old address `/s3b_glb/gs.html` sends you to Gebarenstrand.

<!-- screenshot: GLB Viewer with avatar and gloss search, page /s3b_glb/index.html -->

## The screen

- **3D view** with the avatar in the middle.
- **Search gloss...** (Gebarenstrand: **Search filename or gloss...**): type
  to find animations. Up to 100 results show.
- **Sentence panel** (✍ button, *Zin naar Gebaar*): type a Dutch sentence in **Typ een Nederlandse
  zin...**. Word cards appear. Click **▶ Afspelen** (play) to play the signs one
  after the other.
- **Queue:** drop animation files on **Drop animation files here** to play them
  in a row. You can name the queue.
- **☰** opens and closes the side panel **GLB Files**, which holds the search
  field, the results and your **Saved Queues**.
- The timeline at the bottom plays, pauses and scrubs the current animation.
- A drop-down switches the avatar between **Default (no texture)** and
  **Textured**.

## Common tasks

### Watch a sign

1. Click **☰** to open **GLB Files**.
2. Type the gloss in **Search gloss...**.
3. Click a result. It plays on the avatar.

### Play a sentence

1. Click **✍** to open the sentence panel.
2. Type a Dutch sentence in **Typ een Nederlandse zin...**. A word card
   appears for each word.
3. Click **▶ Afspelen**. The signs play one after the other.

!!! note "First visit after an update"
    The first page load after an update rebuilds the search lists. It can take
    a while. Later loads are fast.

## Related

- [blendBaking](blendbaking.md)
- [Troubleshooting](../troubleshooting/index.md)
