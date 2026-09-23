# Signbank connector

The Signbank connector (**Signbank koppeling**) is the settings page for the
link between SignCollect and [Signbank](https://signbank.cls.ru.nl), the
online NGT lexicon. It holds the Signbank API key, refreshes the local copy of
the Signbank gloss list, and sets how often that copy is refreshed.

The gloss list it downloads is used across SignCollect: the gloss search in
the annotation editors and the annotation tool reads it.

- **Who uses it:** administrators only. Other users see *Deze pagina is alleen
  voor beheerders*.
- **Address:** <https://signcollect.nl/menu_beta/signbank.php>
- **Login:** yes, with the admin role.

## Open it

1. Open the [gloss management page](main-menu.md).
2. Open the menu and choose **Signbank koppeling** under **Admin**.

<!-- screenshot: Signbank koppeling page with the four sections, page /menu_beta/signbank.php -->

## The screen

### Verbinding (connection)

Shows the status, the Signbank server, the dataset and whether an API key is
set. **Verbinding testen** (test connection) checks that Signbank answers with
the current key.

### API-sleutel vervangen (replace API key)

Paste a new Signbank API key and click **Opslaan** (save). The new key works at
once. The page never shows the stored key again.

### Glossenbestand (gloss file)

Shows when the local gloss list was last refreshed, how many glosses it holds,
its size and the result of the last run.

- **Nu verversen** (refresh now) downloads the full list from Signbank.
- **Testronde (40 glossen)** (test run) downloads only 40 glosses. Use it to
  check the connection without waiting for a full run.

### Automatisch verversen (automatic refresh)

Choose **Uit** (off), **Elk uur** (every hour) or **Dagelijks** (daily, at the
time you set), then click **Opslaan**. The scheduler on the server runs the
refresh. Without it, only **Nu verversen** works.

## Common tasks

### Replace an expired API key

1. Get a new API key from your Signbank account.
2. Paste it under **API-sleutel vervangen** and click **Opslaan**.
3. Click **Verbinding testen** to check it.

### Get new Signbank glosses into SignCollect now

1. Click **Nu verversen**.
2. Wait until **Laatste run** shows the new result and the gloss count.

## Related

- [Main menu and gloss management](main-menu.md)
- [Add or edit a gloss and sync with Signbank](../guides/gloss-signbank.md)
- [Troubleshooting](../troubleshooting/index.md)
