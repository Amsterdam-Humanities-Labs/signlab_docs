# Server and system

Problems that come from the core server at `signcollect.nl` itself: the database, the web server, the disk, the certificate and the scheduled jobs. You cannot fix these yourself. Your job is to notice them, stop making things worse, and give an administrator a good report.

!!! tip "One outage, many symptoms"
    When the database or the web server stops, every page breaks at once. If several unrelated pages fail at the same moment, report one outage instead of many small problems.

### Every page and the API are down {#sys-everything-down}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the database has stopped. Every page, API call and background job reads from it, so everything breaks at once.

**Try this:**

1. Open two unrelated pages, for example the menu and a gloss page. If both fail, it is a server outage.
2. Stop saving or uploading work until the site is back.
3. Tell your colleagues, so the administrator gets one report instead of ten.

**Still stuck?** Send the administrator the time the problem started, two page addresses that fail, and the exact error text on the screen.

### The whole site is down and the monitoring dashboard shows every job offline {#sys-webserver-down}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the web server or PHP has stopped. Heartbeats from jobs also go through the web server, so the dashboard shows every job as offline even if the jobs still run.

**Try this:**

1. Check whether `signcollect.nl` loads at all. A browser message such as "cannot connect" points to the web server.
2. Do not assume data is lost. The jobs may still be running.
3. Report it.

**Still stuck?** Send the time, the exact browser message, and whether other SignCollect addresses (for example the API) also fail.

!!! note "For the administrator"
    Run the web server's configuration test first and fix the file and line it names. Reload before you restart. After a full outage, start services in this order: database, research-drive mount, PHP, web server, Vicon sync, scheduler, job wrappers, the rest.

### Pages load, but everything that saves or queries data fails {#sys-php-down}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** PHP has stopped, while plain files are still served. Or the database is down (see [Every page and the API are down](#sys-everything-down)).

**Try this:**

1. Reload the page once.
2. If a static page loads but a page with data does not, report it.

**Still stuck?** Send the address of one page that works and one that fails, with the time.

### Saving fails everywhere and uploads stop halfway {#sys-disk-full}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the server disk is full. The database will not start on a full disk. Scheduled-job logs do not rotate and can fill the disk over time.

**Try this:**

1. Stop uploading. Every new upload makes the problem worse.
2. Keep your unsaved work open in the browser tab, or copy text you typed somewhere safe.
3. Report it.

**Still stuck?** Send the time, what you were saving or uploading, and the error text.

!!! note "For the administrator"
    Check free space and free inodes. Truncate large job logs; never delete an open log, because it keeps its space. A log clean-up script exists but is not scheduled. Never delete the scheduler state, the database files, or anything on the research drive. Afterwards, check for failed services and start the database first.

### My browser says the certificate is not valid or has expired {#sys-certificate}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the TLS certificate for `signcollect.nl`, `api.signcollect.nl` or `avatar.signcollect.nl` was not renewed in time.

**Try this:**

1. Do not click through the warning, and do not log in on that page.
2. Check the date and time of your own computer. A wrong clock also causes certificate warnings.
3. Report it, with the full address that shows the warning.

**Still stuck?** Send the address, a copy of the browser warning text, and the time.

### Pages are slow, or videos and studio files are missing {#sys-research-drive}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the connection from the core server to the research drive dropped. Almost every video, studio and mocap page reads files through it. This connection drops now and then.

**Try this:**

1. Reload the page after a minute.
2. Check a second video on another page. If both are missing, it is not your recording.
3. Report it.

**Still stuck?** Send the page address, one take or sentence ID that is missing, and the time.

### Recordings are no longer linked to sentences, and glosses look out of date {#sys-scheduler-stopped}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the scheduler that runs the background jobs has stopped. Matching recordings to sentences, gloss, lemma and EAF syncs, and database backups all stop. Nobody gets an error; the data just stops changing.

**Try this:**

1. Note which data looks stale and since when (for example: "yesterday's takes have no sentence").
2. Look at the [monitoring dashboard](monitoring.md) for jobs that stopped reporting.
3. Report it.

**Still stuck?** Send the page, the date of the last data that did arrive, and one example ID that should have been updated.

!!! note "For the administrator"
    Restart the job wrappers and then the watchdog. Never delete the scheduler state, or every job runs at once.

### A page shows "500 Internal Server Error" {#sys-500}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** often you opened a bare folder address that has no start page. Otherwise a script failed on the server.

**Try this:**

1. Open the page from the [menu](login.md#login-menu) instead of a bookmarked or typed address.
2. If you typed the address, remove anything after the last `/` and try the menu link again.
3. If the menu link also gives 500, report it.

**Still stuck?** Send the full address, the time, and what you clicked just before.

### A tool says it cannot connect to the database {#sys-db-credentials}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the tool cannot read its database settings on the server, or the database is down.

**Try this:**

1. Check whether other pages work. If they do, only this tool is affected.
2. Report it with the exact message.

**Still stuck?** Send the tool name, its address, the exact error text and the time.

!!! note "For the administrator"
    Check that the tool's configuration file exists and that the web server user can read it.

### Nightly results are missing this morning {#sys-nightly-jobs}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** some nightly jobs (video counts, the daily 3D render, the annotation backup, the video cache) run from a separate schedule. If that schedule is broken, the night's output is missing.

**Try this:**

1. Wait until the next morning; one missed night is often a temporary problem.
2. If it is missing two nights in a row, report it.

**Still stuck?** Send which result is missing (for example "no new 3D renders"), and the dates.

### A job appears twice, or something runs double {#sys-duplicate-jobs}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** some jobs are scheduled in two places during the move to one scheduler. The Vicon sync is one known case.

**Try this:**

1. Do not start the job again by hand.
2. Report which job you saw twice and where.

**Still stuck?** Send the job name as shown on the dashboard, and the time of both runs.

### A fix was announced, but I still see the old behaviour {#sys-fix-not-live}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the fix is in the code repository but was not deployed to `signcollect.nl` yet. Or your browser shows a cached copy.

**Try this:**

1. Force-reload the page (see [Browser cache](browser.md#br-cache)).
2. Ask the administrator whether the update was deployed.

**Still stuck?** Send the page address and the issue or change you expected to see.

### Uploads from a capture machine are refused after an update {#sys-upload-tokens}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** uploads of mocap packages and 3D body jobs now need an upload token. After an update, the new token was not set on the server or on the capture machine.

**Try this:**

1. Check whether the refusal started right after an update.
2. Report it; you cannot set tokens yourself.

**Still stuck?** Send the machine name, the time of the refused upload and the error text. See also [Uploads and tokens](uploads.md).

### Is there a backup of my work? {#sys-backup}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** a scheduled job makes a database backup. If that job stops, no new backups are made and nobody gets a warning.

**Try this:**

1. If you are about to do a large clean-up or bulk change, ask an administrator to confirm that the latest backup is recent.
2. Keep your own copy of EAF files you downloaded.

**Still stuck?** Ask the administrator for the date of the last backup, and which data you need back.
