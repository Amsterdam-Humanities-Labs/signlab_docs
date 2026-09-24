# Installing a demo host

A demo host is a complete, separate copy of the SignCollect web interface on a
server of your own. Use it to try out changes, test a pull request or show the
system, without touching production. The install builds everything from
GitHub. It copies nothing from the production server.

This page covers the install *on the host itself*, as a normal user. The full
reference, including installing from your workstation over ssh, is
[install.md](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack/blob/main/docs/install.md)
in the stack repository.

## What you get

- Apache, PHP, MySQL and a TLS certificate, installed and configured.
- All component repositories (about twenty) cloned into the web root, `/web`.
- The database schema and its migrations, a demo login (`gomer` / `123`) and
  twenty real studio recordings with their video.
- The job scheduler (pythonCron) installed as a service.
- Every network path from the host to production cut off.

## Prerequisites

1. **Ubuntu 24.04.** Other versions are not tested.
2. **A normal user with passwordless sudo.** Every privileged step runs
   without a prompt. If `sudo` stops to ask for a password, the install stops
   half way. To set it up, run this as root (replace `gomer` with the user):

    ```bash
    echo 'gomer ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/gomer
    chmod 440 /etc/sudoers.d/gomer
    ```

3. **Tailscale, joined and logged in** (`sudo tailscale up`). The host's name
   and its TLS certificate both come from Tailscale. For a public name
   instead, see [A public name instead of a tailnet one](#public-name).
4. **Outbound HTTPS to github.com.** The host clones the repositories itself.
   They are all public, so you need no GitHub account or login.
5. **Room:** at least 3 GB free disk (5 GB is comfortable) and about 1 GB of
   RAM. With less memory, MySQL often does not start.

The installer sets up everything else: Apache, PHP, MySQL, Composer and the
firewall.

## Install

1. Open a terminal on the host.
2. Install git:

    ```bash
    sudo apt update && sudo apt install -y git
    ```

3. Clone the deploy toolchain:

    ```bash
    git clone https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack ~/signcollect-deploy
    cd ~/signcollect-deploy/interface_deploy
    ```

4. Check the host. This changes nothing:

    ```bash
    scripts/preflight.sh --local
    ```

    Every line should say `ok`, and the last line `preflight passed.` A
    failed check prints the command that fixes it.

5. Optional: see what the install would change. This also changes nothing:

    ```bash
    scripts/install.sh --local --dry-run
    ```

    It lists the eleven steps and what each would do, for example
    `all packages present` or `20 of 20 components already checked out`.

6. Run the install:

    ```bash
    scripts/install.sh --local
    ```

    It runs the preflight checks again and changes nothing until they pass.
    On a bare host it takes a few minutes. At the end it prints the result
    and `log in as gomer / 123`. On a desktop it also opens the site in the
    browser.

7. Open `https://<host>.<tailnet>.ts.net` in a browser and log in as
   `gomer` / `123`.

!!! note "What `--local` deploys"
    `--local` installs exactly what is on GitHub. A change you committed on
    your workstation but did not push yet is not included. To deploy that,
    install from the workstation over ssh (`scripts/install.sh --host
    gomer@<host>`); see the full reference.

### If it stops half way

Run the install again (step 6). Every step can be repeated safely: a second
run finishes the job instead of doing it twice. A failure names the step it
stopped at and the command to retry, for example:

```text
=== install FAILED at step 5/11: bootstrap - clone ... components, rewrite URLs, place vendored files ===
```

### Update a running demo host

1. `cd ~/signcollect-deploy && git pull`
2. `cd interface_deploy && scripts/install.sh --local`

Each component is reset to the latest version on GitHub. Demo data and the
database password are kept.

## Check the result

`verify` checks that the pages answer, that secrets and data files are not
served, that production cannot be reached, and that the demo login works.
`test` runs the end-to-end suites: the interface and role separation, the
shared library, the mocap portal, the path resolver, the scheduler and the
Signbank connector.

1. Install make. The installer does not install it:

    ```bash
    sudo apt install -y make
    ```

2. Run the checks from the toolchain folder:

    ```bash
    cd ~/signcollect-deploy/interface_deploy
    make verify
    make test
    ```

    `make verify` ends with `ALL CHECKS PASSED`. `make test` prints one line
    per suite, such as `passed 98   failed 0`. A failure names its log file
    in `/tmp`.

!!! note "The scheduler suite needs ssh"
    `pythoncron-test.sh` inspects the host over ssh. Run on the host itself,
    it reports `FAILED`. To run it, use a workstation with ssh access:
    `make test HOST=gomer@<host>` from a clone of the toolchain.

The tests write data and clean it up afterwards. They refuse to run against
production.

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
    Some features need machines that only production can reach:

    - The camera panel in Camera Control stays empty.
    - AI segmentation and gloss suggestions in the annotation editors do not
      answer.
    - **Manual Sync** on the Motion Capture Studio page answers
      `Error (HTTP 502)`: there is no Vicon sync.
    - Background Fix shows "Could not load date list".
    - The client monitor dashboard is not installed.

    Everything else works with the demo data.

## A public name instead of a tailnet one {#public-name}

For a server with a public name (for example `test.signcollect.nl`):

1. Point the name's DNS A record at the server.
2. Keep port 80 open. Let's Encrypt uses it to check the name.
3. Run the installer with your e-mail address. It gets a free Let's Encrypt
   certificate that renews itself:

    ```bash
    LETSENCRYPT_EMAIL=you@uva.nl ~/signcollect-deploy/interface_deploy/scripts/install.sh --local --domain test.signcollect.nl
    ```

## Related

- [For administrators](index.md)
- [Troubleshooting](../troubleshooting/index.md)
