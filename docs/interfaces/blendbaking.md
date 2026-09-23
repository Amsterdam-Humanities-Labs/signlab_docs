# blendBaking

blendBaking (blendbaking) is a tool for the baked motion-capture takes of the
sentence corpus. A *baked* take is a mocap take that has been converted to a
3D animation file (GLB). blendBaking lets you download the gloss subtitle files
(SRT) of those takes, see every base gloss with its variants, and query gloss
timings through a public API.

- **Who uses it:** researchers, and projects that use the gloss timings.
- **Address:** <https://signcollect.nl/blendBaking/>
- **Login:** no. The page and its API are open.

!!! note "Not the avatar site"
    <https://avatar.signcollect.nl> is a different app, the avatar player. It
    is linked from the [mocap portal](mocap-portal.md).

## Open it

Go to <https://signcollect.nl/blendBaking/>.

<!-- screenshot: blendBaking SRT bestanden tab with search and status filter, page /blendBaking/ -->

## The screen

The page has three tabs.

### SRT bestanden (SRT files)

The baked videos that have a gloss SRT.

- Search by base gloss or sentence.
- Filter on status: **Alle**, **Klaar**, **Check nodig**, **Niet Klaar**.
- **Download geselecteerde als ZIP:** the SRTs you ticked.
- **Download alles (huidige filter):** every SRT that matches the filter.

### Glossen (glosses)

Each base gloss with its count, its variants and its category. Expand a gloss
to see every sentence it occurs in, with timecode, SRT and FBX link.

- Search by base gloss or variant, and filter by category.
- **Exporteer CSV** and **Exporteer JSON** save the list.
- **Herbouw index** rebuilds the list now. It is rebuilt by itself every ten
  minutes.

### API

Documentation for the **Gloss timings API** (`action=timings`), with a **Try
it** form. The API returns, per sentence, when each gloss starts and ends.

Parameters, all optional:

| Parameter | Meaning |
|---|---|
| `base` or `bases` | One base gloss, or several separated by commas |
| `sentenceId` | One sentence |
| `gloss` | A base gloss |
| `search` | Free text |
| `mcpStatusTijdAnnotatie` | The time-annotation status |
| `page`, `limit` | Paging. `limit` is 25 by default, at most 200 |

!!! tip "Check `success`"
    The API always answers with HTTP 200. Look at the `success` field of the
    answer to know whether the request worked.

## Common tasks

### Download the gloss SRTs of all finished sentences

1. Open the **SRT bestanden** tab.
2. Set the status filter to **Klaar**.
3. Click **Download alles (huidige filter)**.

### Find every sentence with a gloss

1. Open the **Glossen** tab.
2. Search for the base gloss, for example `HUILEN`.
3. Expand it to see the sentences, timecodes and links.

## Related

- [Get mocap from Vicon to a baked animation](../guides/mocap-to-animation.md)
- [Export and download annotations](../guides/export-annotations.md)
- [Troubleshooting](../troubleshooting/index.md)
