# Review clusters

A pipeline has split a set of videos into signs automatically and grouped
similar signs into *clusters*. Each cluster should be one sign. This guide
shows how to review that result: label the clusters, decide which clusters
belong together, and correct the segments of each video.

The review pages are part of the [annotation tool](../interfaces/annotation-tool.md).
The current set holds the *horeco* and *health_holland* videos.

| Page | Address | What you do there | Saved where |
|---|---|---|---|
| Sign clusters | `/annotation-tool/clusters/index.html` | Look at each cluster and give it a gloss | Only in the open page, until you download |
| Merge review | `/annotation-tool/clusters/merge.html` | Decide whether two clusters are the same sign | On the server (login needed) |
| Segmented videos | `/annotation-tool/clusters/videos.html` | Open each video to correct its segments | On the server (login needed) |

## 1. Label the clusters

1. Open <https://signcollect.nl/annotation-tool/clusters/index.html>.
2. Sort **by size** (largest clusters first) or **novel first**. Clusters
   marked **new?** may be signs that are not in the gloss list yet.
3. Narrow the list with the category filter (**horeco**,
   **health_holland**), **novel only**, **low-conf only** (clusters with
   uncertain segments) or **search gloss**.
4. Click a cluster's video (or **alle … ▸**) to see all its members. Each
   member plays a short clip. Click a clip to open that video in the editor
   at that moment, in a new tab. **✕ close** or **Esc** closes the overview.
5. Under each cluster, click one of the suggested glosses, or type the gloss
   in **confirm / new gloss**. The counter at the top shows how many clusters
   you labelled.
6. When you are done, click **Download cluster_labels.json** and send the file
   to the researcher who runs the pipeline.

!!! warning "Labels are not saved on the server"
    The labels on this page live only in the open page. Reloading or closing
    the page loses them. Download often.

<!-- screenshot: Sign clusters page with cluster cards, page /annotation-tool/clusters/index.html -->

## 2. Merge clusters that are the same sign

1. Click **⇄ merge review**, or open
   <https://signcollect.nl/annotation-tool/clusters/merge.html>. Log in if
   asked.
2. The page shows two clusters side by side, with example clips and their
   similarity.
3. Decide:
    - **✓ Merge (M):** they are the same sign.
    - **✗ Keep separate (K):** they are different signs.
    - **skip →** (→ or space): decide later. **◀ back** (←): the previous pair.
4. The counter shows how many pairs you merged, kept and have left. **show**
   set to **undecided** shows only the open pairs; **all** shows every pair.
5. When every pair is done, the page says *All pairs reviewed*. Tell the
   researcher who runs the pipeline.

Each decision is sent to the server at once. When you open the page again,
it loads your earlier decisions and starts at the first undecided pair, so
you can stop and continue later.

!!! note "When a decision is not saved"
    If a save fails, you get an alert and the pair goes back to undecided:
    decide it again. If your login has expired, the page sends you to the
    login page first.

## 3. Correct the segments of each video

1. Open <https://signcollect.nl/annotation-tool/clusters/videos.html>.
2. Filter by category and by status (**klaar** or **niet klaar**). Click a
   column header to sort. The confidence columns show how sure the pipeline
   was; red means unsure.
3. Click **open ▶**. The video opens in the annotation tool in clusters mode.
   Log in if asked.
4. Correct the segments and their glosses on the timeline. The tool saves on
   the server as you work; the save button says **Opgeslagen op server**.
5. Set **Status:** to **Klaar** and click **Volgende ▶**. The tool saves and
   opens the next video that is not *Klaar*. When all are done it says
   *Alle video's staan op Klaar!*.

If saving fails, the button says **Opslaan mislukt!**. See
[Annotation tool](../troubleshooting/annotation-tool.md#at-clusters-save).

## Related

- [Annotation tool](../interfaces/annotation-tool.md)
- [Troubleshooting](../troubleshooting/index.md)
