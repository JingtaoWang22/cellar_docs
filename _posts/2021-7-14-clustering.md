---
title: 'CLUSTERING'

category: User Interface
layout: null
type: ui
---
Obtaning cluster assignments can be performed using three different approaches:
i.e., via **UNSUPERVISED**, **SEMI-SUPERVISED**, and **LABEL TRANSFER** methods.
**UNSUPERVISED** allows the user to cluster the
reduced data and generate labels for the cells using no reference.
**SEMI-SEPERVISED** assumes some knowledge of the cluster assignments.
This can be used to fix any cell labels with high
certainty and re-cluster any low certainty cells. **LABEL TRANSFER**
should be used under dual mode and with the active dataset being the one
we wish to obtain labels for, based on the reference inactive dataset.

* **UNSUPERVISED**
<br>
<img src="images/unsupervised.png" class="w400"/>
<br>

    * The dropdown menu includes
    [Leiden](https://www.nature.com/articles/s41598-019-41695-z) (default)
    and several other classical algorithms such as KMeans and Spectral
    Clustering.
      * Leiden does not require the user to manually set the number
        of clusters, however, this number can be controlled via the
        <span class='mbox'>Resolution</span>
        parameter (default: 1). Higher resolution means more clusters.
        You may want to experiment with this
        value until you get a desirable cluster configuration. Our experiments
        show that for CODEX data an optimal resolution is smaller than 0.3.
        Leiden is a
        community detection algorithm that takes as input a connectivity graph.
        We construct this graph by looking at the nearest neighbors
        of each cell. For small datasets, Cellar computes the exact nearest
        neighbors, while for large datasets (more than 5,000 cells), we
        switch to an approximate neighbors computation via the
        [faiss](https://github.com/facebookresearch/faiss) library
        which provides huge speedups at a small cost in accuracy.
        The default algorithm can be overriden in the settings panel for Leiden,
        along with the <span class='mbox'>number of neighbors</span>.
      * The other algorithms, unlike Leiden, require knowledge of
        the number of clusters to use.
        To make tuning this hyperparameter easier, we allow the users to specify
        a range (or list) of values. Doing this will run the selected
        algorithm once for each value and will automatically select the number
        of clusters that achieves the highest score (default:
        [Silhouette Score](https://en.wikipedia.org/wiki/Silhouette_(clustering))).
        To specify a range, use the notation $$(\text{start}, \text{end}+1,
        \text{step})$$.
        For example, $$(3, 7, 1)$$ will run four instances of the selected
        algorithm, one for each number of clusters in $$[3, 4, 5, 6]$$.
        Alternatively, you can use a list of values. (Note the distinction
        betweeen parentheses ( ) and square brackets [ ]) E.g., $$[4, 8, 16]$$ will
        spawn three instances of the algorithm. Finally, a single
        integer value can also be used instead.
      * Uncertainty clustering can only be run after cells have been labeled
        by any of the other algorithms. Uncertainty clustering generates a
        new cluster (cluster ID -1) for cells that have a high uncertainty
        score. The uncertainty score is computed according to the cells'
        distance from the cluster centers in the reduced space. After this,
        re-clustering the newly generated uncertain cluster using
        Constrained Leiden oftens improves clustering. Intuitively,
        the improvements come from incorporating information about the
        cluster centers into the algorithm, which is not considered in Leiden.


      [//]:# "* An [Ensemble](https://github.com/GGiecold/Cluster_Ensembles) algorithm"
      [//]:# "  based on Hypergraph Partitioning has been added which allows the"
      [//]:# "  selection and integration of several clustering algorithms into an"
      [//]:# "  ensemble."

    * This cluster IDs are stored in the `adata.obs['labels']` key.



* **SEMI-SEPERVISED**
<br>
<img src="images/semi-supervised.png" class="w400"/>
<br>

    * Cellar incorporates a semi-supervised clustering algorithm based
    on Leiden. This can be useful when the user intervenes in the data by
    manually splitting/merging clusters or after running label transfer.
    Constrained Leiden allows the user to "preserve"
    a set of clusters. These clusters will be left as is, while
    the remaining clusters will be subject to change. Clicking on the gear
    button will show a list of clusters and user-defined subsets which can
    be selected in order to be preserved by the algorithm.

    * This step updates the `adata.obs['labels']` key.

* **LABEL TRANSFER**
<br>
<img src="images/label-transfer.png" class="w400"/>
<br>

  * Label transfer should be used under dual mode. It can be used to transfer
    the labels from the inactive dataset (reference)
    to the active dataset (a dataset can be activated by clicking
    "Activate" at the corresponding Plot's toolbar).
    Currently Cellar supports label transfer with
    [Scanpy Ingest](https://scanpy-tutorials.readthedocs.io/en/latest/integrating-data-using-ingest.html)
    and [SingleR](https://bioconductor.org/packages/devel/bioc/vignettes/SingleR/inst/doc/SingleR.html).
    <span class="warn">!!<span class="tooltip">Attention</span></span>
    When running label transfer, we use only
    the features which are common in both the active and the reference dataset.
    Make sure the two datasets use the same feature naming convention.

    Scanpy Ingest typically takes a few minutes to finish while SingleR
    can take much longer. Scanpy Ingest is based on a projection of the data
    into a shared PCA space and uses a nearest neighbor classifier to
    assign labels, while SingleR is a correlation-based method that queries
    the reference dataset while iteratively removing low scoring cell
    types until one remains.

  * "Cell ID Based" label transfer is used to transfer labels from one dataset
    to the other by matching cell barcodes among the two. This can be useful
    for example in SNARE-seq datasets where both the expression levels and chromatin
    accessibility are profiled for the same cells.

  * This updates the `adata.obs['labels']` key.
