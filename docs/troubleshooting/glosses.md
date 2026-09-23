# Glosses and Signbank sync

Problems when you add, edit, label or hide glosses, and when you push or pull glosses to and from Signbank.

### "Opslaan mislukt" when I save a gloss {#gl-save-failed}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** the server refused the change. The gloss was removed in the meantime, the input was invalid, or none of the fields you changed can be edited.

**Try this:**

1. Reload the page.
2. Find the gloss again and make the change once more.
3. If it still fails, report it.

**Still stuck?** Send the gloss name, the field you changed and the time. "Geen wijzigingen" means nothing changed; that is not an error.

### I deleted a gloss, but it still exists {#gl-hidden}

**Type:** user error · **Who can fix:** you

**Likely cause:** deleting a gloss only hides it ("Glos … verbergen?"). The data stays, so it can be restored.

**Try this:**

1. Check the filter for hidden glosses.
2. Ask an administrator if you need it restored.

**Still stuck?** Send the gloss name.

### The wizard says the gloss already exists and adds a letter {#gl-suffix}

**Type:** user error · **Who can fix:** you

**Likely cause:** a gloss with that name exists. The wizard proposes the same name with the next letter, for example `HUIS-B`.

**Try this:**

1. Check whether the existing gloss is the sign you mean.
2. If it is, use it instead of making a new one.
3. If it is a different sign, accept the name with the letter.

**Still stuck?** Not needed.

### Batch add refuses my list {#gl-batch-add}

**Type:** user error · **Who can fix:** you

**Likely cause:** you did not pick a theme, the list has duplicates, or all letters A to Z are used for a name.

**Try this:**

1. Select a theme, or type a custom theme, before you add words.
2. Remove duplicate lines.
3. Existing glosses are not duplicated; they only get the new labels.

**Still stuck?** Send the list and the message.

### A label cannot be added {#gl-label}

**Type:** user error · **Who can fix:** you

**Likely cause:** the name is empty, the label already exists, or the colour is not a hex code.

**Try this:**

1. Use a new, non-empty name.
2. Enter the colour as `#RRGGBB`, for example `#316CA4`.

**Still stuck?** Send the label name and the message.

### My note is not saved {#gl-note}

**Type:** user error · **Who can fix:** you

**Likely cause:** the note is empty or longer than 5000 characters.

**Try this:**

1. Shorten the note, or split it in two.

**Still stuck?** Send the gloss name.

### Pushing to Signbank says "Already connected to Signbank" {#gl-already-connected}

**Type:** user error · **Who can fix:** you

**Likely cause:** this gloss is already linked to Signbank. You cannot create it there twice.

**Try this:**

1. Use **Push** to send changes, or **Pull** to get Signbank's version.

**Still stuck?** Not needed.

### Push fails with "Mislukt — HTTP …" {#gl-push-failed}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** Signbank refused the gloss, or the Signbank API key is not valid.

**Try this:**

1. Note the HTTP number.
2. Try another gloss. If every push fails, the key is the likely cause.
3. Report it.

**Still stuck?** Send the gloss name, the HTTP number and the time. An administrator can test the key on the Signbank admin page.

### "This gloss is not connected to Signbank." {#gl-not-connected}

**Type:** user error · **Who can fix:** you

**Likely cause:** fetch, push, pull and delete only work on glosses that are linked to Signbank.

**Try this:**

1. Create the gloss on Signbank first, with the Signbank button.
2. Then use push or pull.

**Still stuck?** Send the gloss name.

### Signbank sync says the dataset is not synced {#gl-dataset-not-synced}

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

**Likely cause:** the annotation tools and patient-info read a Signbank export that is rebuilt on a schedule (off, hourly or daily). A "sample" refresh does not publish.

**Try this:**

1. Wait for the next scheduled refresh.
2. Ask an administrator to run a full refresh on the Signbank admin page.

**Still stuck?** Send the gloss name and when it was added to Signbank.

### Signbank refresh says "a refresh is already running" or "every gloss request failed" {#gl-refresh-errors}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** "already running" means another refresh is busy. "every gloss request failed - check the API key" means the key is wrong or expired.

**Try this:**

1. Wait for the running refresh to finish.
2. Test the API key on the Signbank admin page.
3. Enter the daily time as HH:MM.

**Still stuck?** Send the exact message and the time.

### Gloss counts or recorded status look out of date {#gl-stale}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** gloss, lemma and GvG data are updated by scheduled jobs (hourly or daily). If the scheduler stopped, nothing updates.

**Try this:**

1. Wait an hour.
2. If it is still stale, see [scheduler stopped](system.md#sys-scheduler-stopped).

**Still stuck?** Send the gloss and what you expected to see.
