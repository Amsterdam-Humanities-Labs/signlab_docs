# For administrators

This section is for the people who look after SignCollect: accounts, the
Signbank link, the servers and the studio machines. Most of your work happens
in a few admin pages. The technical documentation is in the repositories on
GitHub.

## What administrators do

| Task | Where |
|---|---|
| Create accounts, reset passwords, unblock users, set language, role and access | **Gebruikers Beheren** in the [gloss management](../interfaces/main-menu.md) menu (`/menu_beta/users.html`) |
| Keep the Signbank link working: API key, gloss-list refresh | [Signbank connector](../interfaces/signbank-connector.md) |
| Watch that machines and background jobs are alive | [Client monitor](../interfaces/client-monitor.md) |
| Help when something breaks | [Troubleshooting](../troubleshooting/index.md), then the runbook (below) |
| Set up a demo or test server | [Installing a demo host](install.md) |

## Manage users

Only users with the role *Admin* see this page.

1. Open the [gloss management page](../interfaces/main-menu.md), open the
   menu and click **Gebruikers Beheren** under **Admin**.
2. To add a user, click **Gebruiker toevoegen**.
3. Fill in the user name (**Gebruikersnaam**) and password (**Wachtwoord**).
4. Set the access fields:
    - **Taal:** Nederlands or English. The gloss management page uses it.
    - **Rol:** *User* or *Admin*. Only admins see the Admin menu and the
      Signbank connector.
    - **Datasets:** which datasets the user may open, and the default one.
      Tick at least one.
    - **Signio / Signbank:** which gloss views the user may use, and the
      default one. Tick at least one.
5. Click **Toevoegen**. The user appears in the list.

To change a user later:

1. Click **Bewerken** in the user's row.
2. To reset the password, type the new one in **Nieuw wachtwoord**. Leave it
   empty to keep the old one.
3. Click **Opslaan**.

To unblock a user, click **Deblokkeren** in the row. *Gebruiker
gedeblokkeerd* confirms it. **Blokkeren** blocks a user.

!!! note "Automatic blocking"
    An account that has not been used for more than 60 days is blocked at its
    next password login. Unblock it here.

## Technical documentation

All repositories are public, in the
[Amsterdam-Humanities-Labs](https://github.com/orgs/Amsterdam-Humanities-Labs/repositories?q=signlab_)
organisation on GitHub. Their names start with `signlab_`.

Start with the index repository,
[signlab_signcollect-stack](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack).
Its `docs/` folder has:

| Document | Read it when you want to know |
|---|---|
| [architecture.md](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack/blob/main/docs/architecture.md) | How the repositories fit together |
| [machines.md](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack/blob/main/docs/machines.md) | What runs on each machine |
| [runbook.md](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack/blob/main/docs/runbook.md) | What to do when something breaks |
| [production.md](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack/blob/main/docs/production.md) | How the production server is laid out and updated |
| [install.md](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack/blob/main/docs/install.md) | Full install reference for a demo or test host |
| [deploy.md](https://github.com/Amsterdam-Humanities-Labs/signlab_signcollect-stack/blob/main/docs/deploy.md) | How a deploy works, and how to add a component |

Each component repository has a README with what it does, where it runs and
how to deploy it. The studio Mac (DRS) has its own operator manual in
[signlab_drs-pipeline](https://github.com/Amsterdam-Humanities-Labs/signlab_drs-pipeline/blob/main/docs/manual.md).
For setting up the studio itself (cameras, DRS, the QR screen), see
[The studio](../studio/index.md).

!!! warning "Production is hands-off"
    Do not test changes on signcollect.nl. Use a demo host: see
    [Installing a demo host](install.md).

## Related

- [Installing a demo host](install.md)
- [The studio](../studio/index.md)
- [Troubleshooting](../troubleshooting/index.md)
