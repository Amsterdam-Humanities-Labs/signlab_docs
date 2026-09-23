# Review clusters

A pipeline has split a set of videos into signs automatically and grouped
similar signs into *clusters*. Each cluster should be one sign. This guide
shows how to review that result: label the clusters, decide which clusters
belong together, and correct the segments of each video.

The review pages are part of the [annotation tool](../interfaces/annotation-tool.md).
The current set holds the *horeco* and *health_holland* videos.

| Page | Address | What you do there |
|---|---|---|
| Sign clusters | `/annotation-tool/clusters/index.html` | Look at each cluster and give it a gloss |
| Merge review | `/annotation-tool/clusters/merge.html` | Decide whether two clusters are the same sign |
| Segmented videos | `/annotation-tool/clusters/videos.html` | Open each video to correct its segments |

## 1. Label the clusters

1. Open <https://signcollect.nl/annotation-tool/clusters/index.html>.
2. Sort **by size** (largest clusters first) or **novel first**. Clusters
   marked **new?** may be signs that are not in the gloss list yet.
3. Narrow the list with the category filter, **novel only**, **low-conf
   only** (clusters with uncertain segments) or **search gloss**.
4. Click a cluster to see its members. Each member plays a short clip. Click
   a clip to open that video in the editor at that moment.
5. In the field **confirm / new gloss**, type the gloss for the cluster.
6. When you are done, click **Download cluster_labels.json** and send the file
   to the researcher who runs the pipeline.

!!! warning "Labels are not saved on the server"
    The labels on this page live in your browser until you download them.
    Download before you close the page.

<!-- screenshot: Sign clusters page with cluster cards, page /annotation-tool/clusters/index.html -->

## 2. Merge clusters that are the same sign

1. Click **⇄ merge review**, or open
   <https://signcollect.nl/annotation-tool/clusters/merge.html>. You need to be
   logged in.
2. The page shows two clusters side by side.
3. Decide:
    - **✓ Merge (M):** they are the same sign.
    - **✗ Keep separate (K):** they are different signs.
    - **skip →** (→ or space): decide later. **◀ back** (←): the previous pair.
4. The counter shows how many pairs you merged, kept and have left. Set
   **show** to **undecided** to see only the open pairs.

Your decisions are saved on the server as you go.

## 3. Correct the segments of each video

1. Open <https://signcollect.nl/annotation-tool/clusters/videos.html>.
2. Filter by category and by status (**klaar** or **niet klaar**). The
   confidence columns show how sure the pipeline was; start with the lowest.
3. Click **open ▶**. The video opens in the annotation tool in clusters mode.
   This mode needs a login.
4. Correct the segments and their glosses on the timeline. The tool saves on
   the server as you work.
5. Set the status to **Klaar** and click **Volgende ▶**. The tool saves and
   opens the next video that is not *Klaar*.


## Related

- [Annotation tool](../interfaces/annotation-tool.md)
- [Troubleshooting](../troubleshooting/index.md)
