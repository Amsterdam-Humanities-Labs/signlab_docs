# Mocap overview and file API

- **What:** an overview of the whole motion-capture dataset, and an API to find
  and download its animation files.
- **Who uses it:** the avatar team (Jari Andersen, Mabel), and anyone who needs
  mocap files in bulk.
- **Address:** `signcollect.nl/mocapOverview/` (overview) and
  `signcollect.nl/mocapOverview/api/` (API documentation and playground).
- **Login:** the overview asks for a page password. The API needs an API key, or
  that same page login. Ask an administrator for either.

## The overview page

| Section | What it shows |
|---|---|
| **Capture sessions** | Per session (Zin in NGT, BAK, 3DLEX, LSC/LSE, other): how many takes and files, and their size |
| **Full inventory** | Every kind of data per session, with counts, sizes and where it lives |
| **Where to work with the data** | Which tool to use for each kind of file |
| **Reading the file names** | How take and file names are built: `{name}_{YYMMDD}_{take}` |

The numbers come from an inventory that is rebuilt on the server. A full rebuild
takes about half an hour.

## The file API

Search files with `GET /mocapOverview/api/files`. Send your key in the
`X-API-Key` header (or as `?key=`). The playground on `/mocapOverview/api/` lets you try every
parameter in the browser once you are logged in.

```bash
curl -H "X-API-Key: <your key>" \
  "https://signcollect.nl/mocapOverview/api/files?session=zin&type=cc_pp&format=glb&latest=1"
```

### Search parameters

| Parameter | Example | Meaning |
|---|---|---|
| `gloss` | `TAART*` | The sign's gloss (wildcards allowed) |
| `signbank_id` | `1662` | Signbank gloss ID; combine with `session`, because 3DLEX and LSC IDs overlap |
| `id` | `6436` | SignCollect record ID (a sentence for Zin, a form for BAK) |
| `sentence_gloss` | `GLIJBAAN` | Zin sentences whose gloss list contains this gloss |
| `name` / `take` / `file` | `M20260119_1147` | Match on name, take or file name |
| `q` | `glijbaan` | Free text over gloss, name, take and sentence |
| `type` | `cc_raw,cc_pp` | File type (see below); several allowed |
| `session` | `zin` | `zin`, `bak`, `3dlex`, `lsc`, `other` |
| `avatar` | `cc` | `cc` (Palmer), `rpm` (ReadyPlayerMe), `vicon` |
| `stage` | `pp` | `raw` or `pp` (post-processed) |
| `format` | `glb` | `fbx`, `glb` or `shapekeys` (face curves) |
| `date`, `date_from`, `date_to` | `2026-03` | Capture date: a day, a month or a year |
| `latest` | `1` | Only the newest take per name, type and format |
| `group` | `take` | One entry per take with its files (JSON only) |
| `sort` | `-date` | `name`, `date`, `size`, `modified`; a `-` sorts descending |
| `limit`, `offset` | `100` | Paging. JSON: 100 by default, at most 1000. The JSON `next` field holds the next page |
| `output` | `csv` | `json` (default), `csv` (download) or `urls` (one URL per line) |

`GET /mocapOverview/api/meta` returns the types, sessions, date range and counts.

### File types

| Type | Avatar | Stage | What it is |
|---|---|---|---|
| `cc_raw` | CC (Palmer) | raw | As exported from Unreal. FBX and GLB |
| `cc_pp` | CC (Palmer) | post-processed | Cleaned in Unreal and uploaded through the Motion Capture File Manager |
| `ccp_raw` | CC (Palmer) | raw | Web-viewer version: body GLB plus face shape keys |
| `ccp_pp` | CC (Palmer) | post-processed | The same, after post-processing |
| `rpm_raw` / `rpm_pp` | ReadyPlayerMe | raw / post-processed | The older glassesGuy avatar |
| `vicon_raw` | Vicon skeleton | raw | The skeleton straight from Vicon |

!!! tip "Download a whole set"
    Use `output=urls` to get a plain list of download links, one per line, and
    feed it to a download tool.

## Related

- [Motion capture portal](mocap-portal.md)
- [From Vicon to a baked animation](../guides/mocap-to-animation.md)
- [Troubleshooting: motion capture](../troubleshooting/mocap.md)
