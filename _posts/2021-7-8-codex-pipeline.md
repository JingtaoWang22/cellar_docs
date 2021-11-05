---
title: 'TUTORIAL: CODEX and 10X Spatial Transcriptomics'

category: Tutorials
layout: null
type: tutorial
---
This is a step-by-step tutorial for analyzing CODEX data and 10x Genomics's Spatial Transcriptomics data. A [video demo](https://www.youtube.com/watch?v=zG3j3DdqLUQ) is also available on YouTube. We will consider the `CODEX_Florida_19-003-kymph-node-R2` dataset. The analysis of 10X Spatial Transcriptomics follows almost exactly the same steps as the previous tutorial. We will focus on how to generate spatial tiles for the dataset. Details about other basic analysis based on gene expressions are covered in the **Tutorial: Basic Analysis Pipeline** section.

To begin the analysis, we need to load the dataset. At the top of the page, click <span class='mbutton'>LOAD DATA</span>.
This will expand a panel with any server datasets. Alternatively, you can upload your own CODEX or 10X dataset and select it in the dropdown menu. See details in the **LOAD DATA** section. After selecting the dataset, click <span class='mbutton'>LOAD</span>.

<br>
<img src="images/codex-load-dataset.png" alt="drawing" width="300"/>
<br>

This will load the dataset and show a scatter plot of the data. In our case, the server dataset that we loaded has 2D embeddings, cluster labels, and cell type annotations stored in the h5ad file.
<br>
![CODEX Main Plot](images/codex-mainplot.png)
<br>
Number of samples (cells) and number of features (genes) is also shown.
<br>
![CODEX No. Cells and No. Genes](images/codex-cells-genes.png)
<br>
Cell type annotations are also shown in the **ANNOTATIONS** panel in the side bar.
<br>
![CODEX Cell Types](images/codex-cell-types.png)
<br>
This is how these results look like in Cellar:
<br>
<br>
![CODEX Results](images/codex-results.png)
<br>
Please refer to the section **Tutorial: Basic Analysis Pipeline** for details on how to perform this analysis and how to visualize gene expression.

Next, we show how to project cell type annotations into the spatial tile. To do so, click the **SPATIAL DATA** tab uncer the main plot and select `CODEX` (or `10X Genomics`, depending on your data type) in the dropdown menu. Then, if you are working with your own dataset, you also need to upload a file including the spatial image and spatial information about the cells by clicking the <span class='mbutton'>UPLOAD</span> button (See the **SPATIAL DATA** section for more details). But we can skip this step since these files are already stored on the server for server datasets. Finally, click the <span class='mbutton'>GENERATE TILE</span> button. After a few seconds, the spatial tile will be generated. You can download this figure by clicking <span class='mbutton'>DOWNLOAD TILE</span>.
<br>
![CODEX Results](images/codex-spatial-image.png)
<br>
Note that the colors are consistent with the ones in the main plot. This means if you change the labels in the main plot (e.g. by re-clustering, merging clusters), and click <span class='mbutton'>GENERATE TILE</span> again, the color in the spatial image will be changed accordingly.

You can also perform the same actions to visualize a 10X Genomics Spatial Transcriptomics dataset, [Human Breast Cancer Dataset](https://support.10xgenomics.com/spatial-gene-expression/datasets/1.3.0/Visium_FFPE_Human_Breast_Cancer).
<br>
![10x clustering](images/10x-clustering.png)
<br>
<br>
![10x spatial image](images/10x-spatial-image.png)
<br>


