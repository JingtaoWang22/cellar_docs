---
title: 'ANNOTATIONS & TOOLS'

category: User Interface
layout: null
type: ui
---
These panel consists of general tools related to cell type annotation
and subset creation.
<br>
<img src="images/annotations.png" class="w400"/>
<br>

* **Annotation**
    * This panel displays cell type assignments for each cluster. Only
    non-empty annotations are shown.
    <span class="warn">!!</span> If a selected subset contains cells from multiple
    clusters, the labels of those cells will be lost and replaced by
    the new type.

* **Store Subset**
    * Any subset of cells can be selected from the plot by using the lasso tool.
    This subset can then be stored here by giving it a
    unique identifier. To select a subset of cells, first make sure the
    <span class='mbox'>Lasso Select</span> tool is selected.
    Then, by clicking anywhere on the plot and dragging your mouse around,
    one should be able to select a group of cells
    (double-click on the plot to reset the selection).<br>
    ![Lasso Select](images/lasso-select.png)<br>
    Click <span class="mbutton">STORE</span> will save that subset
    under the typed identifier. These identifiers
    can be used to find DE genes for the corresponding subset under
    the <span class='mbox'>Analysis</span> menu, or can be used to assign cell
    types to entire subsets.
    Subsets that start with `Cluster` are reserved for clusters and no new
    subsets can start with this prefix.
    * The subsets are stored in a dictionary under `adata.uns['subsets']`.


* **Merge**
    * This allows the users to select a subset and store it as a new cluster.
    The color in the main plot will change accordingly.
    * Updates the `adata.obs['labels']` key.

* **Integrate**
    * Cellar allows the integration of CITE-seq and CODEX protein data
    using [STvEA](https://www.science.org/doi/10.1126/sciadv.abc5464).
    To upload a CITE-seq dataset to Cellar, the data
    must be in AnnData format, with `adata.X` corresponding to the
    mRNA expression matrix
    and `adata.obsm['proteins']` corresponding to the protein expression matrix.
    A tutorial showing how to perform the integration can be found below.