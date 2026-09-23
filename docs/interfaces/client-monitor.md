# Client monitor

The client monitor dashboard (client_monitor_dashboard, **Client Monitor**)
shows which lab machines, scripts and background jobs are alive. Each of them
sends a regular signal, a *heartbeat*, to the server. When the heartbeats stop,
the dashboard shows it. It also has a live feed of studio recordings.

- **Who uses it:** administrators, and anyone who wants to check that the
  studio pipeline is running.
- **Address:** <https://signcollect.nl/client_monitor_dashboard/>
- **Login:** yes, on its own login page. Use your SignCollect user name and
  password.

## Open it

1. Go to <https://signcollect.nl/client_monitor_dashboard/>.
2. Enter your **Username** and **Password** and log in.

This login is separate from the SignCollect login. It lasts one year on that
browser.

<!-- screenshot: Client Monitor with status counters and client cards, page /client_monitor_dashboard/view.php -->

## The screen

### Counters

**Total Clients**, **Online**, **Warning** and **Offline**.

### Monitored Clients

- Filter buttons: **All**, **Online**, **Warning**, **Offline**.
- View buttons: **Grid** (cards, grouped by machine) or **Table**. The page
  remembers your choice.
- **Refresh**. The page also refreshes by itself every 30 seconds.

In the table view each client has: **Status**, **Client Name**,
**Description**, **Last Seen**, **Heartbeat Interval**, **IP Address** and
**Actions** (edit, delete).

In the grid view, each machine card also shows charts of CPU use, I/O wait and
disk use over the last week, if the machine sends them.

### Status

| Status | Meaning |
|---|---|
| Online | The last heartbeat came within 1.5 times the expected interval |
| Warning | The last heartbeat is late: between 1.5 and 2 times the interval |
| Offline | No heartbeat for more than 2 times the interval |

These are the default limits. A client can have its own.

### Studio recordings

- **Recent Camera Records:** the newest takes logged by
  [Camera Control](camera-control.md), with today's count and the latest take.
- **Transcription Stats:** takes per day.

## Common tasks

### Check that the studio pipeline is running

1. Click **Offline**.
2. Look for the studio Mac (DRS) jobs, such as the file mover, batch queue,
   crop processor, converter and file lister.
3. If one is offline, tell an administrator. Recordings from that day will not
   be processed until it runs again.

### Remove a machine that no longer exists

1. Switch to **Table**.
2. Click delete in the **Actions** column of that client.
3. Confirm. Its metrics are deleted too.

## Related

- [Check that a day's recordings are complete](../guides/check-day-complete.md)
- [Troubleshooting](../troubleshooting/index.md)
