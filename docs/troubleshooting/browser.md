# Browser problems

Many SignCollect pages do their work in your browser: playing and stepping through video, saving files, recording from a webcam. Use a recent **Chrome or Edge on a desktop computer**. Other browsers miss features that some tools need.

### I still see the old version of a page {#br-cache}

**Type:** user error · **Who can fix:** you

**Likely cause:** your browser shows a stored copy of the page or its scripts.

**Try this:**

1. Force-reload: `Ctrl+Shift+R` on Windows or Linux, `Cmd+Shift+R` on a Mac.
2. If that does not help, clear the site data for `signcollect.nl` in your browser settings.

!!! warning
    Clearing site data also resets saved filters, the annotation tool's autosave folder and its cached converted videos. Your saved EAF files are not affected.

**Still stuck?** Send the page address and what you expected to change.

### A preview video does not start playing {#br-autoplay}

**Type:** user error · **Who can fix:** you

**Likely cause:** your browser blocked autoplay. Gloss previews start muted and loop, but some browsers still block them.

**Try this:**

1. Click play on the video.
2. Allow autoplay for `signcollect.nl` in the site settings.

**Still stuck?** Send the page, the browser and the gloss.

### The video plays, but the timeline stays empty or frame stepping does not work {#br-codec}

**Type:** user error · **Who can fix:** you

**Likely cause:** frame stepping decodes the video in the browser. If your browser does not support the video's codec, the timeline stays empty without a visible error.

**Try this:**

1. Use Chrome or Edge.
2. For your own videos, convert them to MP4 with H.264.

**Still stuck?** Send the video name, the browser and version.

### Pop-ups are blocked {#br-popups}

**Type:** user error · **Who can fix:** you

**Likely cause:** some buttons open a new tab, for example "open 2D video" in 3DAnn3. Your browser blocks it.

**Try this:**

1. Click the pop-up icon in the address bar.
2. Choose to always allow pop-ups from `signcollect.nl`.
3. Click the button again.

**Still stuck?** Send the page and the button.

### The site asks for the camera, or the camera does not work {#br-camera}

**Type:** user error · **Who can fix:** you

**Likely cause:** camera access only works on `https://` pages and only after you allow it. Another app can hold the camera.

**Try this:**

1. Check that the address starts with `https://`.
2. Allow the camera in the site settings.
3. Close video calls or recording software.
4. Reload the page.

**Still stuck?** See [webcam mode](annotation-tool.md#at-webcam-access).

### Autosave to a folder does not work in Firefox or Safari {#br-file-access}

**Type:** user error · **Who can fix:** you

**Likely cause:** only Chrome and Edge can save to a folder on your computer.

**Try this:**

1. Use Chrome or Edge, or export by hand. See [autosave needs Chrome/Edge](annotation-tool.md#at-autosave-browser).

**Still stuck?** Not needed.

### The 3D avatar does not appear {#br-webgl}

<!-- TODO: confirm — hardware-acceleration step is general browser advice, not from the SignCollect code. -->

**Type:** user error · **Who can fix:** you

**Likely cause:** the 3D viewers need WebGL. It is off, or your computer's graphics are too weak.

**Try this:**

1. Use Chrome or Edge on a desktop computer.
2. Turn on hardware acceleration in the browser settings.
3. Close other heavy tabs.

**Still stuck?** Send the browser, the computer and the take name.

### The page is blank or buttons do nothing {#br-blank}

<!-- TODO: confirm — general browser advice, not traced to a specific SignCollect error. -->

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** a script failed to load, often because of a browser extension (ad or script blocker) or a cached old version.

**Try this:**

1. Force-reload (see [cache](#br-cache)).
2. Turn off ad blockers and script blockers for `signcollect.nl`.
3. Try a private window.
4. If it still fails, open the browser console (`F12`) and copy the red error lines.

**Still stuck?** Send the page address, the browser, and the red console lines.
