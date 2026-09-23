# Add or edit a gloss and sync with Signbank

This guide shows how to add a gloss to SignCollect, edit it, and keep it in
step with [Signbank](https://signbank.cls.ru.nl). You work in the
[gloss management page](../interfaces/main-menu.md).

SignCollect keeps its own gloss list. Syncing with Signbank is one gloss at a
time, and you start it yourself.

## 1. Check whether the gloss exists

1. Open <https://signcollect.nl/menu_beta/>.
2. Open the menu and choose **Glos Wizard**.
3. Type the word or gloss and click **Zoeken** (Search).
4. If a match is the sign you mean, use that gloss. Do not add a second one.

!!! tip "Many words at once"
    Paste one word per line in **Glos lijst** (gloss list) and click **Batch
    activeren** (start batch). Click **Volgende** (next) to go through them.

## 2. Add the gloss

1. In the wizard, click **Als nieuwe glos toevoegen** (add as new gloss). Or
   close the wizard and click **Nieuwe glos**.
2. Fill in the gloss and the English gloss. Both are required.
3. Choose a theme and add the Dutch and English senses.
4. Click **Aanmaken** (Create). *Gloss created* confirms it.

## 3. Edit the gloss

1. Search for the gloss.
2. Click in the field you want to change and type. It saves by itself.
3. For the hand shape and other form features, open the row menu **⋮** and
   choose **Phonology**.
4. Leave a note for colleagues with **⋮** > **Notes**. **Logbook** shows who
   changed what.

## 4. Push the gloss to Signbank

1. Switch the header to **Signbank**. Only glosses in the Signbank view can be
   pushed. If you do not see the switch, ask an administrator to give your
   account access to both views.
2. Find the gloss and open its row menu **⋮**.
3. Choose **Push to Signbank**.
4. Confirm *Push gloss "…" to Signbank?* with **Ja, doorgaan**.
5. The window shows a timeline and a result per field:
    - *Push: completed:* everything arrived.
    - *Push: partially succeeded:* some fields failed. The failed ones are
      listed. Click **Opnieuw verzenden** (resend).
    - *Push: failed:* nothing arrived. See
      [Troubleshooting](../troubleshooting/index.md).

After a push, the row menu shows the Signbank number of the gloss, for example
**Compare with Signbank (#1234)**.

<!-- screenshot: Push to Signbank result window with timeline, page /menu_beta/ -->

## 5. Compare and sync an existing Signbank gloss

1. In the Signbank view, open **⋮** > **Compare with Signbank (#…)**.
2. The table shows each field in SignCollect and in Signbank, marked *match*
   or *mismatch*. It also shows both videos.
3. Choose one:
    - **Push differences:** send only the fields that differ to Signbank.
    - **Push all → Signbank:** overwrite Signbank with all SignCollect fields.
    - **Pull all ← Signbank:** overwrite SignCollect with the Signbank fields.
    - **Open in Signbank:** look at the gloss on the Signbank website.
4. Confirm.

!!! warning "Push all and Pull all overwrite"
    Both replace every field on the other side. Use **Push differences** unless
    you are sure.

## Unlink a gloss from Signbank

Open **⋮** > **Disconnect from Signbank (#…)** and confirm. The gloss stays in
SignCollect, but the linked gloss on Signbank is archived.

!!! warning
    Only disconnect when the Signbank gloss should no longer be used.

## New Signbank glosses in the gloss search

The gloss search in the annotation editors uses a copy of the Signbank gloss
list. An administrator refreshes it in the
[Signbank connector](../interfaces/signbank-connector.md), by hand or on a
schedule. A gloss you just pushed shows up there after the next refresh.

## Related

- [Main menu and gloss management](../interfaces/main-menu.md)
- [Signbank connector](../interfaces/signbank-connector.md)
- [Troubleshooting](../troubleshooting/index.md)
