---
title: 'TUTORIAL: Joint Analysis & Label Transfer'

category: Tutorials
layout: null
type: tutorial
---
This is another step-by-step Cellar tutorial for joint analysis. A related [video tutorial](https://www.youtube.com/watch?v=QBUXhFZrHec) is also available on YouTube. Joint analysis allows the user to perform side-by-side comparison between two datasets and transfer labels from one dataset to the other. We will use two server datasets `kidney_SNARE_ATAC_20201005` and `kidney_SNARE_RNA_20201005` as an example.

We first run the basic analysis pipeline on the chromatin data. The steps are: 1. Load the dataset using the **LOAD DATA** panel in the navigation bar; 2. Use the **DIMENSIONALITY REDUCTION** panel to get low dimensional embedding (cisTopic) and a 2D visualization (UMAP) of the dataset; 3. Use the **UNSUPERVISED** tab in the **CLUSTERING** panel to get labels for the cells (Leiden).

<br>
<img src="images/kidney-snare-atac.png" alt="drawing" width="300"/>
<br>

More details about the basic analysis steps can be found in **Tutorial: Basic Gene Expression Analysis Pipeline** and the documentation for the corresponding UIs.

To load another dataset, click the <span class='mbutton'>DUAL MODE</span> button in the navigation bar. This will split the main plot into two parts: the main plot, and the side plot. Clicking the <span class='mbutton'>ACTIVATE</span> button at the top-right corner of the side plot will activate the side plot (and deactivate the main plot). This means all the functionalities (except label transfer) in the navigation bar, side bar, and the analysis panels, will only be apply to the side plot. More details about the dual mode function can be found in the **DUAL/SINGLE MODE** section of this documentation. After activating the side plot, we can load the other dataset from **LOAD DATA**.

<br>
<img src="images/kidney-snare-dual.png" alt="drawing" width="300"/>
<br>

Then, we perform dimensionality reduction (PCA) just as we did for the dataset in the main plot.


<br>
<img src="images/kidney-snare-both.png" alt="drawing" width="300"/>
<br>

Now, we have two options of obtaining labels for this dataset. We can either use the **UNSUPERVISED** tab in the **CLUSTERING** like before, or we can use the **LABEL TRANSFER** functionality.

<br>
<img src="images/label-transfer.png" alt="drawing" width="300"/>
<br>

Label transfer can be used to transfer labels from the deactivated dataset to the activate one, based on a nearest neighbors approach (Scanpy Ingest) or correlation-based approach (SingleR). Since we are using a SNARE-seq dataset and the cell IDs are the same, we can also use the "Cell ID Based" method that simply copies labels from one data to the other by matching cell IDs.

<br>
<img src="images/kidney-snare-transfer.png" alt="drawing" width="300"/>
<br>

Clicking the <span class='mbutton'>SINGLE VIEW</span> button in the navigation bar will expand the activated plot and hide the other one. But the information of the other plot is not lost. You can return to the dual mode and activate the other one whenever you want.

<br>
<img src="images/kidney-snare-single.png" alt="drawing" width="300"/>
<br>





