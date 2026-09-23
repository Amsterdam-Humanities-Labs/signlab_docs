# Installing a demo host

A demo host is a complete, separate copy of the SignCollect web interface on a
server of your own. Use it to try out changes, test a pull request or show the
system, without touching production. The install builds everything from
GitHub; it copies nothing from the production server.

This page covers the install *on the host itself*, as a normal user. The full
reference, including installing from your workstation over ssh, is
[install.md](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack/blob/main/docs/install.md)
in the stack repository (private).

## What you get

- Apache, PHP, MySQL and a TLS certificate, installed and configured.
- All component repositories cloned into the web root.
- The database schema and its migrations, a demo login and twenty real studio
  recordings with their video.
- The job scheduler (pythonCron) installed as a service.
- Every network path from the host to production cut off.

## Prerequisites

1. **Ubuntu 24.04.** Other versions are not tested.
2. **A normal user with passwordless sudo.** Every privileged step runs
   without a prompt. If `sudo` stops to ask for a password, the install stops
   half way.
3. **Tailscale, joined and logged in** (`sudo tailscale up`). The host's name
   and its TLS certificate both come from Tailscale.
4. **Outbound HTTPS to github.com.** The host clones about twenty public
   repositories from Amsterdam-Humanities-Labs. No GitHub account is needed.
5. **Room:** at least 3 GB free disk (5 GB is comfortable) and about 1 GB of
   RAM. With less memory, MySQL often does not start.

## Install

Open a terminal on the host and run these three lines:

```bash
sudo apt update && sudo apt install -y git
git clone https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack ~/signcollect-deploy
~/signcollect-deploy/interface_deploy/scripts/install.sh --local
```

1. Line 1 installs git.
2. Line 2 clones the deploy toolchain.
3. Line 3 runs the install. It first checks everything it needs, and changes
   nothing until those checks pass. On a bare host it takes a few minutes.

The site is then served at the host's Tailscale name, over HTTPS.

!!! note "A repository that is still private"
    The installer checks every repository anonymously. If one is private, it
    names it and asks for a GitHub login (`gh auth login`) at step 3.

!!! tip "See what it would do first"
    Add `--dry-run` to the last line. It reports what each step would change,
    and changes nothing.

### If it stops half way

Run the last line again. Every step can be repeated safely: a second run
finishes the job instead of doing it twice. A failure names the step it
stopped at and the command to retry. Running the install again is also how you
update a running demo host.

## Check the result

From the `interface_deploy/` folder of the clone, run:

```bash
cd ~/signcollect-deploy/interface_deploy
make verify
make test
```

- `make verify` checks that the pages answer, that secrets and data files are
  not served, that production cannot be reached, and that the demo login
  works.
- `make test` runs the end-to-end test suites: the interface and role
  separation, the shared library, the mocap portal, the path resolver, the
  scheduler, and the Signbank connector. Each prints one line; a failure
  points to its log file.

The tests write data, so they refuse to run against production.

## Isolated from production

The demo host cannot reach production:

- Production URLs in the deployed code are rewritten to the demo's own
  address before the first request is served.
- The host blocks production by DNS and by firewall rules. Your own ssh
  connection is not affected.
- Nothing is copied from the production server, and production does not need
  to be reachable during the install.

So a demo host can never write to the production database or media.

!!! note "What does not work on a demo host"
    Some features need machines that only production can reach. The camera
    panel in Camera Control stays empty, and the AI segmentation and gloss
    suggestions in the annotation editors do not answer. Everything else
    works with the demo data.

## Related

- [For administrators](index.md)
- [Troubleshooting](../troubleshooting/index.md)

## A public name instead of a tailnet one

For a server with a public name (for example `test.signcollect.nl`):

1. Point the name's DNS A record at the server.
2. Keep port 80 open.
3. Run the installer with your e-mail address. It gets a free Let's Encrypt certificate that renews itself:

```bash
LETSENCRYPT_EMAIL=you@uva.nl ~/signcollect-deploy/interface_deploy/scripts/install.sh --local --domain test.signcollect.nl
```
