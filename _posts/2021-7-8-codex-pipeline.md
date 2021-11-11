---
title: 'TUTORIAL: CODEX and 10X Spatial Transcriptomics'

category: Tutorials
layout: null
type: tutorial
---
This is a step-by-step tutorial for analyzing CODEX and Visium 10x Spatial Transcriptomics data. A [video tutorial](https://www.youtube.com/watch?v=zG3j3DdqLUQ) is also available on YouTube. We will consider the `CODEX_Florida_19-003-lymph-node-R2` dataset (analysis of 10X Spatial Transcriptomics follows a similar procedure). We will focus on how to generate spatial tiles for the dataset.

To begin the analysis, we need to load the dataset. At the top of the page, click <span class='mbutton'>LOAD DATA</span>.
This will expand a panel with any server datasets. Alternatively, you can upload your own CODEX or 10X dataset and select it in the dropdown menu. See details in the **LOAD DATA** section. After selecting the dataset, click <span class='mbutton'>LOAD</span>.

<br>
<img src="images/codex-load-dataset.png" alt="drawing" width="300"/>
<br>

This will load the dataset and show a scatter plot of the data. In our case, the server dataset that we loaded has 2D embeddings, cluster labels, and cell type annotations stored in the h5ad file.
<br>
![CODEX Main Plot](images/codex-mainplot.png)
<br>
Number of samples (cells) and number of features (proteins) is also shown.
<br>
<img src="images/codex-cells-genes.png" class="w400"/>
<br>
Cell type annotations are also shown in the **ANNOTATIONS** panel in the side bar.
<br>
<img src="images/codex-cell-types.png" class="w400"/>
<br>
Please refer to the section **Tutorial: Basic Analysis Pipeline** for details on how to perform this analysis and how to visualize protein expression.

Next, we show how to project cell type annotations into the spatial tile. To do so, click the **SPATIAL DATA** tab uncer the main plot and select `CODEX` (or `Visium 10x`, depending on your data type) in the dropdown menu. Then, if you are working with your own dataset, you also need to upload a file including the spatial image and spatial information about the cells by clicking the <span class='mbutton'>UPLOAD</span> button (See the **SPATIAL DATA** section for more details). But we can skip this step since these files are already stored on the server for server datasets. Finally, click the <span class='mbutton'>GENERATE TILE</span> button. After a few seconds, the spatial tile will be generated. You can download a high resolution version of this figure by clicking <span class='mbutton'>DOWNLOAD TILE</span>.
<br>
<br>
![CODEX Results](images/codex-spatial-image.png)
<br>
Note that the colors are consistent with the ones in the main plot. This means if you change the labels in the main plot (e.g. by re-clustering, merging clusters), and click <span class='mbutton'>GENERATE TILE</span> again, the color in the spatial image will change accordingly.

If is also possible to view expression levels of proteins in the spatial tile by selecting the desired proteins from the dropdown menu next to the <span class="mbutton">GENERATE TILE</span> button. For example, below we show the expression levels of CD20 in our lymph node dataset. The expression range of multiple proteins will be handled in the same way as with multiple genes (see Analysis).
<br>
<br>
![CODEX Expression](images/codex-spatial-expression.png)
<br>
Currently, Cellar also supports cluster and protein co-localization scores which are computed via the [adjacency score](https://github.com/CamaraLab/AdjacencyScore). These scores are shown as heatmaps and describe how well two clusters or proteins are localized in the spatial tile. Co-localization scores can be found at the bottom of the Spatial panel. We show an example of a cluster co-localization heatmap for the lymph node dataset below. We can see that cluster 2 (blue, B lymphocytes) is highly co-localized with itself and cluster 9.
<br>
<br>
<img src="images/codex-coloc-cluster.png" class="w400"/>
<br>

You can also perform the same actions to visualize a Visium 10x Genomics Spatial Transcriptomics dataset, [Human Breast Cancer Dataset](https://support.10xgenomics.com/spatial-gene-expression/datasets/1.3.0/Visium_FFPE_Human_Breast_Cancer).
<br>
![10x clustering](images/10x-clustering.png)
<br>
<br>
<img src="images/10x-spatial-image.png" class="w400"/>
<br>


