---
title: 'TUTORIAL: Joint Analysis & Label Transfer'

category: Tutorials
layout: null
type: tutorial
---
This is another step-by-step Cellar tutorial for joint analysis, a [video demo](https://www.youtube.com/watch?v=QBUXhFZrHec) is also available on YouTube. Joint analysis allows the user to do side-by-side comparison between two datasets and generate labels for one dataset based on the other. We will use two server datasets `ucsd-snare-rna-20201005-D-preprocessed` and `ucsd-snare-atac-cbg-20201005-D-preprocessed` as example.

We first run the basic analysis pipeline on the RNA dataset. The steps are: 1. Load the dataset using the **LOAD DATA** panel in the navigation bar; 2. Use the **DIMENSIONALITY REDUCTION** panel to get low dimensional embedding and 2D visualization of the dataset; 3. Use the **UNSUPERVISED** tab in the **CLUSTERING** panel to get labels for the cells.

<br>
<img src="images/joint-step1-rna-analysis.png" alt="drawing" width="300"/>
<br>

More details about the basic analysis steps can be found in **Tutorial: Basic Gene Expression Analysis Pipeline** and the documentation for the corresponding UIs.

Then, to load another dataset, click the <span class='mbutton'>DUAL MODE</span> button in the navigation bar. This will split the main plot into two parts: the main plot, and the side plot. Clicking the <span class='mbutton'>ACTIVATE</span> button at the top-right corner of the side plot will activate the side plot (and deactivate the main plot). This means all the functionalities (except label transfer, which will be mentioned later) in the navigation bar, side bar, and the analysis panels, will only be associated with the side plot. More details about the dual mode function can be found in the **DUAL/SINGLE MODE** section of this documentation. After activating the side plot, we can load the other dataset using **LOAD DATA**.

<br>
<img src="images/joint-step2-dual.png" alt="drawing" width="300"/>
<br>

Then, do dimensionality reduction just as we did for the dataset in the main plot.


<br>
<img src="images/joint-step3-2d-atac.png" alt="drawing" width="300"/>
<br>

Now, we have two options of getting the labels for this dataset. We can either use the **UNSUPERVISED** tab in the **CLUSTERING** panel just as we did before and compare the visualizations of two datasets side-by-side, or we can use the **LABEL TRANSFER** tab.

<br>
<img src="images/label-transfer.png" alt="drawing" width="300"/>
<br>

The label transfer function can generate labels for the cells in the activated dataset, based on their nearest neighbors (in the dimensionality reduced space) in the deactivated dataset. Please refer to the **CLUSTERING** section for more details.

<br>
<img src="images/joint-step4-label-transfer.png" alt="drawing" width="300"/>
<br>

Clicking the <span class='mbutton'>SINGLE VIEW</span> button in the navigation bar will expand the activated plot and hide the other one. But the information of the other plot is not lost. You can return to the dual mode and activate the other one whenever you would like to.

<br>
<img src="images/joint-step5-single.png" alt="drawing" width="300"/>
<br>





