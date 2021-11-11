---
title: 'DIMENSIONALITY REDUCTION'

category: User Interface
layout: null
type: ui
---
Cellar first reduces the dimensionality of the data by using
the method chosen under **Obtain Embeddings** (default: PCA). These embeddings are then
further reduced to 2D for visualization purposes (default: UMAP). The clustering
step uses the data reduced by the first method only.

<br>
<img src="images/dim-reduction.png" class="w400"/>
<br>

* **Obtain Embeddings**
    * The default method is PCA with 40 PCs. Truncated SVD and UMAP
    can also work with sparse matrices. PCA and Truncated SVD are typically
    the fastest performing methods, with UMAP and Diffusion Maps being slower.
    [cisTopic](https://www.nature.com/articles/s41592-019-0367-1)
    can be used to obtain a cell-by-topic matrix when working
    with scATAC-seq datasets (warning, cisTopic may take up to an hour
    to finish processing). The gear shaped button can be clicked to
    show any related settings that can be manually tuned, such as the number
    of components. Note: when analyzing CODEX datasets, the number of
    channels (proteins) is typically a few tens, therefore, it may be
    necessary to reduce the number of components first.

    [//]:# "* [cisTopic](https://www.nature.com/articles/s41592-019-0367-1) is a"
    [//]:# "probabilistic framework that uses Latent Dirichlet Allocation to model"
    [//]:# "cis-regulatory topics. We use cisTopic to mainly analyze scATAC-seq data."
    [//]:# "Instead of running the scATAC-seq preprocessing step, you may run "
    [//]:# "cisTopic"
    [//]:# "on the raw cell $$\small\times$$ peak matrix to obtain a cell"
    [//]:# "$$\small\times$$ cisTopic matrix."

    * The reduced data is stored in the `adata.obsm['x_emb']` key.

* **Obtain 2D Embeddings**
    * These algorithms are used to further reduce the embeddings
    obtained in the previous step to 2 dimensions for visualization
    purposes. [UMAP](https://umap-learn.readthedocs.io/en/latest/) generally
    gives good results, but methods like
    [t-SNE](https://www.jmlr.org/papers/volume9/vandermaaten08a/vandermaaten08a.pdf)
    or PCA can also be considered.
    If the number of points is too large, we recommend using either UMAP
    or PCA. t-SNE has a quadratic time complexity and might take considerable
    time to finish.

    * The 2D embeddings are stored in `adata.obsm['x_emb_2d']`.

* **<span class='mbutton'>RUN</span>**
    * Dimensionality reduction may take a while depending on the size of
    the data and the complexity of the chosen algorithm. For some rough
    time estimates, you can consult the estimates bulb next to the dataset
    shape. Once data reduction is done, you
    should see a scatter plot of your data. Initially all cells belong to
    a single cluster (cluster 0).
