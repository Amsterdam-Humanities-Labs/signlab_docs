# Glosses and Signbank sync

Problems when you add, edit, label or hide glosses, and when you push or pull glosses to and from Signbank. The gloss management page is in Dutch by default; English labels are in brackets. See also [Add or edit a gloss and sync with Signbank](../guides/gloss-signbank.md).

### "Opslaan mislukt" when I save a gloss {#gl-save-failed}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the server refused the change. The gloss was removed in the meantime, the input was invalid, your session expired, or none of the fields you changed can be edited.

**Try this:**

1. Reload the page. Log in if asked.
2. Find the gloss again and make the change once more.
3. If it still fails, report it.

**Still stuck?** Send the gloss name, the field you changed and the time. "Geen wijzigingen" (No changes) means nothing changed; that is not an error.

### I deleted a gloss, but it still exists {#gl-hidden}

**Type:** user error · **Who can fix:** you

**Likely cause:** **Verwijderen** (Delete) only hides a gloss (*Glos "…" verbergen?*). The data stays, so it can be restored.

**Try this:**

1. Set the **Status** filter to **Verborgen** (Hidden). Hidden glosses appear.
2. To restore one, open its row menu **⋮** and choose **Zichtbaar maken** (Show).

**Still stuck?** Send the gloss name.

### The wizard says the gloss already exists and adds a letter {#gl-suffix}

**Type:** user error · **Who can fix:** you

**Likely cause:** a gloss with that name exists. The wizard proposes the same name with the first free letter, for example *Glos bestaat al. Laatste letter toegevoegd: HUIS-A. Aanmaken?*

**Try this:**

1. Check the search results under the message: is the existing gloss the sign you mean?
2. If it is, use it instead of making a new one.
3. If it is a different sign, click **Bevestig** (Confirm) to create the name with the letter.

**Still stuck?** "Alle achtervoegsels A t/m Z zijn al in gebruik" means all 26 letters are taken. Ask an administrator.

### Batch add refuses my list {#gl-batch-add}

**Type:** user error · **Who can fix:** you

**Likely cause:** "Please select a thema or enter a custom thema before adding words." means no theme is chosen. A word with other characters than letters, digits, spaces and hyphens is skipped. "(all suffixes A-Z are already used)" means every letter is taken for that name.

**Try this:**

1. Select a theme, or type a custom theme, before you add words.
2. Remove accents and punctuation from the words.
3. Remove duplicate lines. Existing glosses are not duplicated; they only get the new labels.

**Still stuck?** Send the list and the message.

### A label cannot be added {#gl-label}

**Type:** user error · **Who can fix:** you

**Likely cause:** "Label cannot be empty", "This label already exists", or "Invalid color format. Please use hex format (#RRGGBB)".

**Try this:**

1. Use a new, non-empty name. If the label exists, use that one.
2. Enter the colour as `#RRGGBB`, for example `#316CA4`.

**Still stuck?** Send the label name and the message.

### My note is not saved {#gl-note}

**Type:** user error · **Who can fix:** you

**Likely cause:** "Plaatsen mislukt: empty_note" means the note is empty. "note_too_long" means it is longer than 5000 characters.

**Try this:**

1. Shorten the note, or split it in two.

**Still stuck?** Send the gloss name.

### "Push naar Signbank" is not in the row menu {#gl-no-push}

**Type:** user error · **Who can fix:** you / administrator

**Likely cause:** the option only shows in the **Signbank** view, for glosses that are not linked yet. A gloss created in the **Signio** view stays in that view and can never be pushed. A linked gloss shows **Vergelijken met Signbank (#…)** instead.

**Try this:**

1. Switch the header to **Signbank**.
2. Search for the gloss. If it shows **SB #…**, it is already linked.
3. If the gloss is not in the Signbank view, it was made in Signio. Ask an administrator to move it, or create it again while the Signbank view is on.

**Still stuck?** Send the gloss name and ID (the number under the thumbnail).

### Pushing to Signbank says "Already connected to Signbank" {#gl-already-connected}

**Type:** user error · **Who can fix:** you

**Likely cause:** this gloss is already linked to Signbank. You cannot create it there twice.

**Try this:**

1. Open **⋮** > **Vergelijken met Signbank (#…)**.
2. Use **Push verschillen** to send changes, or **Pull alles ← Signbank** to get Signbank's version.

**Still stuck?** Not needed.

### Push fails with "Mislukt — HTTP …" {#gl-push-failed}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** Signbank refused the gloss, or the Signbank API key is missing or not valid. "no Signbank API key configured" means no key is set on this server.

**Try this:**

1. Read the red banner (*Signbank gaf een fout*) and note the HTTP number.
2. Click **Opnieuw verzenden** (Resend) once.
3. Try another gloss. If every push fails, the key is the likely cause.
4. Report it.

**Still stuck?** Send the gloss name, the HTTP number and the time. An administrator can test the key with **Verbinding testen** on the **Signbank koppeling** page.

### My edit to a linked gloss is not on Signbank {#gl-autosync}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** edits to a linked gloss are sent to Signbank when you save them. If that send fails, the page does not say so; the edit is only saved in SignCollect.

**Try this:**

1. Open **⋮** > **Vergelijken met Signbank (#…)**.
2. If the field shows *verschillend* (mismatch), click **Push verschillen**.
3. If that fails too, see [Push fails](#gl-push-failed).

**Still stuck?** Send the gloss name and the field.

### "This gloss is not connected to Signbank." {#gl-not-connected}

**Type:** user error · **Who can fix:** you

**Likely cause:** compare, push, pull and disconnect only work on glosses that are linked to Signbank. The link may have been removed in the meantime.

**Try this:**

1. Reload the page.
2. In the **Signbank** view, open **⋮** > **Push naar Signbank** to create the gloss on Signbank first.
3. Then use compare, push or pull.

**Still stuck?** Send the gloss name.

### Signbank sync says "dataset_not_synced" {#gl-dataset-not-synced}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** this dataset, for example LSM, is not set up for Signbank sync.

**Try this:**

1. Check that you are in the right dataset (see [dataset switch](login.md#login-dataset)).
2. Ask an administrator whether this dataset should sync.

**Still stuck?** Send the dataset and gloss name.

### "Geen verschillen om te pushen" {#gl-nothing-to-push}

**Type:** user error · **Who can fix:** you

**Likely cause:** the gloss in SignCollect and on Signbank are the same.

**Try this:**

1. Nothing to do.

**Still stuck?** If you expected a difference, send the gloss name and the field.

### New Signbank glosses do not show up in the annotation tools {#gl-export-stale}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the annotation tools, the Glos Wizard and patient-info read a copy of the Signbank gloss list. It is rebuilt on the schedule set on the **Signbank koppeling** page: **Uit**, **Elk uur** or **Dagelijks**. **Testronde (40 glossen)** only tests; it does not publish.

**Try this:**

1. Wait for the next scheduled refresh.
2. Ask an administrator to click **Nu verversen** on the **Signbank koppeling** page. A full refresh takes a few minutes.

**Still stuck?** Send the gloss name and when it was added to Signbank.

### Signbank refresh says "a refresh is already running" or "every gloss request failed" {#gl-refresh-errors}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** "already running" means another refresh is busy. "every gloss request failed - check the API key" means the key is wrong or expired. "daily_time must be HH:MM" means the daily time is not valid.

**Try this:**

1. Wait for the running refresh to finish.
2. Test the key with **Verbinding testen**.
3. Enter the daily time as HH:MM.

**Still stuck?** Send the exact message and the time.

### Gloss counts or recorded status look out of date {#gl-stale}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** gloss, lemma and GvG data are updated by scheduled jobs (hourly or daily). If the scheduler stopped, nothing updates.

**Try this:**

1. Wait an hour.
2. If it is still stale, see [scheduler stopped](system.md#sys-scheduler-stopped).

**Still stuck?** Send the gloss and what you expected to see.
