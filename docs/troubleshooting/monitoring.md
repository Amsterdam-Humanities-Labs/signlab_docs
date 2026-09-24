# Monitoring and alerts

The [client monitor](../interfaces/client-monitor.md) dashboard shows which machines and background jobs still report in. Each job sends a [heartbeat](../glossary.md). Server alerts go to Discord; the disk alert also goes by email. The dashboard runs only on `signcollect.nl`, not on demo hosts.

!!! note "A missing heartbeat is not lost data"
    The dashboard only knows that it heard nothing. The job may still be running. Monitoring never stops a job.

### A job shows "Warning" or "Offline" on the dashboard {#mon-offline}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the job did not send a heartbeat in time. It is online up to 1.5 times its interval, warning up to 2 times, and offline after that. The job did not run, crashed, or runs but cannot reach the server.

**Try this:**

1. Check when it was last seen.
2. Check whether the data the job makes is still updating (for example new videos or synced glosses).
3. Report it.

**Still stuck?** Send the job name as shown, its status and the "last seen" time.

### Every job is offline at once {#mon-all-offline}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the web server is down, so no heartbeat arrives. The jobs themselves may be fine.

**Try this:**

1. See [The whole site is down](system.md#sys-webserver-down).

**Still stuck?** Send the time the dashboard turned red.

### The dashboard says "Not logged in" {#mon-not-logged-in}

**Type:** user error · **Who can fix:** you

**Likely cause:** the dashboard has its own login, separate from the SignCollect login, and that session expired.

**Try this:**

1. Open `signcollect.nl/client_monitor_dashboard/`.
2. Log in on the **Client Monitor** page with your user name and password.
3. If the login is refused, ask an administrator for access.

**Still stuck?** See [Login and accounts](login.md).

### The dashboard says "Connection failed" {#mon-connection-failed}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the dashboard cannot reach its database.

**Try this:**

1. Check whether other pages work.
2. Report it.

**Still stuck?** Send the time and the message.

### The dashboard lists odd jobs, such as an email queue or thumbnail generator {#mon-sample-rows}

**Type:** user error · **Who can fix:** you

**Likely cause:** these are old sample entries that match nothing real.

**Try this:**

1. Ignore them.

**Still stuck?** Not needed.

### Dashboard numbers do not change {#mon-stale-metrics}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the service that collects the dashboard metrics (`client-monitor-metrics`, reports hourly) stopped. The charts show the last week, so a gap appears after an hour or more.

**Try this:**

1. Report it with the time of the last update you see.

**Still stuck?** Send the time.

### Alert: "Low Disk Space" or email "Disk space is below 30%" {#mon-disk-alert}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the server disk is filling up. The Discord alert "Low Disk Space" means less than 10% is free. The email is sent earlier, when less than 30% is free; the current percentage is in the email.

**Try this:**

1. Stop large uploads until the administrator confirms there is space.
2. See [Saving fails everywhere](system.md#sys-disk-full).

**Still stuck?** Forward the alert.

### Alert: "Rclone Mount Timeout" or "mount BROKEN" {#mon-mount-alert}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the research-drive connection on the server hangs: a test write and read did not finish within 15 seconds. Studio videos and mocap files cannot be read.

**Try this:**

1. Expect videos to be missing until it is fixed.
2. Forward the alert.

**Still stuck?** See [Pages are slow, or videos are missing](system.md#sys-research-drive).

### Alert: "MySQL Connection Failed" or "MySQL Timeout" {#mon-mysql-alert}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the database did not answer within 30 seconds, or not at all.

**Try this:**

1. Stop saving work.
2. Forward the alert.

**Still stuck?** See [Every page and the API are down](system.md#sys-everything-down).

### The same alert keeps coming, then "Recovered: …" {#mon-alert-repeat}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** a check that keeps failing alerts again, at most once an hour. "Recovered: …" means it passes again.

**Try this:**

1. After "Recovered", check that the affected pages work.

**Still stuck?** Forward both alerts with their times.

### A scheduled job ran twice or never ran {#mon-job-twice}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** on the core server, most jobs are defined in both schedulers (pythonCron's `scheduler_v2` and the per-job services) until the move to one scheduler, so they run twice. A job whose script is missing is skipped. A run is skipped while the previous run is still busy. A job that runs too long is stopped.

**Try this:**

1. Do not start the job by hand.
2. Report the job name.

**Still stuck?** Send the job name and the times you saw it run.
