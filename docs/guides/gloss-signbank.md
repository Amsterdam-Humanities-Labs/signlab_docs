# Add or edit a gloss and sync with Signbank

This guide shows how to add a gloss to SignCollect, edit it, and keep it in
step with [Signbank](https://signbank.cls.ru.nl). You work in the
[gloss management page](../interfaces/main-menu.md) (`/menu_beta/`).

SignCollect keeps its own gloss list. A gloss is linked to Signbank one at a
time, and you start that yourself. Once a gloss is linked, your edits to it go
to Signbank automatically.

!!! note "Labels in Dutch or English"
    The page is in Dutch by default. Your language is set per account
    (**Taal** in the user settings). This guide gives the Dutch label with the
    English one in brackets.

## 1. Check whether the gloss exists

1. Open <https://signcollect.nl/menu_beta/>.
2. Open the menu (☰) and choose **Glos Wizard** (Gloss Wizard).
3. Type the word or gloss and click **Zoeken** (Search).
   The results show glosses from SignCollect and from Signbank. Hover over a
   card to play its video.
4. If a SignCollect match is the sign you mean, use that gloss. Do not add a
   second one.
5. If only Signbank has it, click **Overnemen** (Adopt) on that card. This
   adds the gloss to SignCollect, already linked to Signbank.

!!! tip "Many words at once"
    Paste one word per line in **Glos lijst** (Gloss list) and click **Batch
    activeren** (Start batch). The wizard searches the first word. Click
    **Volgende** (Next) to go to the next one.

## 2. Add the gloss

**Decide first where the gloss belongs.** The header has a switch with two
views: **Signbank** and **Signio**. A new gloss lands in the view you are in,
and only glosses in the **Signbank** view can be pushed to Signbank. Switch to
**Signbank** now if the gloss should go there.

1. Close the wizard and click **Nieuwe glos** (New gloss).
2. Fill in every field. The form refuses to save until all are filled:
    - **Glos NL** and **Glos EN**: the gloss names.
    - **Thema**: the theme.
    - **Labels**: at least one label.
    - **Senses NL** and **Senses EN**: at least one meaning in each language.
3. Click **Aanmaken** (Create).
   *Glos aangemaakt* (Gloss created) confirms it, and the gloss appears in
   the list.

Theme and labels matter for recording: Camera Control lists glosses per theme
and label.

!!! note "Adding from the wizard"
    In the wizard, **Als nieuwe glos toevoegen** (Add as new gloss) takes two
    clicks. The first checks the name: *Glos bestaat nog niet. … aanmaken?*,
    or it adds a letter if the name is taken. The second click, on
    **Bevestig** (Confirm), creates it. The wizard only fills in the name and
    senses, and puts the gloss in your default view. Fill in the other fields
    in the list afterwards.

## 3. Edit the gloss

1. Search for the gloss in the list.
2. Click in the field you want to change and type. Click outside the field to
   save. *Opgeslagen* (Saved) confirms it.
3. For the hand shape and other form features, click **Fonologie**
   (Phonology) under the thumbnail.
4. Leave a note for colleagues with **Notities** (Notes). **Logboek**
   (Logbook) shows who changed what.

To record the reference video (*snelle opname*), open the row menu **⋮** and
choose **Zelfopname maken** (Record selfie video). After that the gloss shows
up in Camera Control under its theme and label, ready for the studio.

## 4. Push the gloss to Signbank

1. Switch the header to **Signbank**. If you do not see the switch, your
   account has only one view. Ask an administrator for access to both.
2. Find the gloss and open its row menu **⋮**.
3. Choose **Push naar Signbank** (Push to Signbank). It is only there for
   glosses that are not linked yet.
4. Confirm *Glos "…" naar Signbank pushen?* with **Ja, doorgaan** (Yes,
   continue).
5. The window shows the result, a timeline of the steps, and the request and
   answer:
    - *Signbank: succes*: the gloss was created on Signbank. The footer says
      *Klaar — HTTP …*.
    - *Signbank gaf een fout*: Signbank refused it. The footer says
      *Mislukt — HTTP …*. Click **Opnieuw verzenden** (Resend) to try again,
      or see [Push fails](../troubleshooting/glosses.md#gl-push-failed).

After a successful push, *Verbonden met Signbank* (Connected to Signbank)
appears. The row shows a link **SB #1234** with the Signbank number, and the
row menu now shows **Vergelijken met Signbank (#1234)**.

<!-- screenshot: Push to Signbank result window with timeline, page /menu_beta/ -->

## 5. Compare and sync a linked gloss

1. In the Signbank view, open **⋮** > **Vergelijken met Signbank (#…)**
   (Compare with Signbank).
2. The table shows each field in SignCollect and in Signbank, marked
   *gelijk* (match) or *verschillend* (mismatch). It also shows both videos.
3. Choose one:
    - **Push verschillen** (Push differences): send only the fields that
      differ to Signbank.
    - **Push alles → Signbank** (Push all): overwrite Signbank with all
      SignCollect fields.
    - **Pull alles ← Signbank** (Pull all): overwrite SignCollect with the
      Signbank fields.
    - **Open in Signbank**: look at the gloss on the Signbank website.
4. Confirm with **Ja, doorgaan**.
5. The result shows *Push: voltooid* (completed), *Push: deels gelukt*
   (partially succeeded, the failed fields are listed) or *Push: mislukt*
   (failed). The table refreshes.

!!! warning "Push alles and Pull alles overwrite"
    Both replace every field on the other side. Use **Push verschillen**
    unless you are sure.

## Unlink a gloss from Signbank

Open **⋮** > **Loskoppelen van Signbank (#…)** (Disconnect from Signbank) and
confirm. The gloss stays in SignCollect, but the linked gloss on Signbank is
archived.

!!! warning
    Only disconnect when the Signbank gloss should no longer be used.

## New Signbank glosses in the gloss search

The gloss search in the annotation editors and the Glos Wizard use a copy of
the Signbank gloss list. An administrator refreshes it in the
[Signbank connector](../interfaces/signbank-connector.md), by hand
(**Nu verversen**) or on a schedule. A gloss you just pushed shows up there
after the next refresh.

## Related

- [Main menu and gloss management](../interfaces/main-menu.md)
- [Signbank connector](../interfaces/signbank-connector.md)
- [Troubleshooting](../troubleshooting/glosses.md)
