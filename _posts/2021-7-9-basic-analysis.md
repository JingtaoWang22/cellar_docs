---
title: 'TUTORIAL: Basic Gene Expression Analysis Pipeline'

category: Tutorials
layout: null
type: tutorial
---
This is a step-by-step tutorial for performing basic single cell gene expression data analysis using Cellar. A related [video demo](https://www.youtube.com/watch?v=J61itSMezFI) is also available on YouTube. The functions included in this tutorial work for all types of datasets. We use the default settings for every method throughout this tutorial. However, feel free to check out detailed information about other available options of each step in the corresponding sections, so that you can experiment with different settings and see which one works best for you.

**1. Load Dataset**
<br>
    We begin the analysis by loading a dataset. To load a dataset, click the <span class='mbutton'>LOAD DATA</span> button in the navigation bar, which is at the top of the page. This will expand a panel for loading datasets. We can either select a server dataset from the dropdown menu, or upload a dataset and select it from the menu. See the **LOAD DATA** section for specific instructions regarding uploading a dataset. Here we select take server dataset `HBMP1_lymph_node_1` as an example. After select a dataset, we click the <span class='mbutton'>LOAD</span> to load the dataset.

<br>
![Basic Load Dataset](images/basic-load-dataset.png)
<br>
    After loading the dataset, information stored in the dataset (e.g. 2D plot, celltype annotations, etc.) will be visualized. However, this dataset contains only the expression matrix and none of the analysis. So only the number of cells and number of genes is shown.

<br>
![Basic Cells Genes](images/basic-cells-genes.png)
<br>

**2. Preprocessing (optional)**
<br>
    If your dataset is not preprocessed, which is not the case for server datasets, you can use click the  <span class='mbutton'>PREPROCESSING</span> button in the navigation bar and use our preprocessing tools. See the **PREPROCESSING** section for more details.

<br>
![Preprocessing](images/preprocessing1.png)
<br>

**3. Dimensionality Reduction**
<br>
    First go to the **DIMENSIONALITY REDUCTION** panel in the sidebar and run dimensionality reduction by: selecting the embedding method (e.g. PCA) followed by the 2D embedding method (e.g. UMAP, TSNE). Finally, click the <span class='mbutton'>RUN</span> button. You can also configure the parameters by clicking the setting buttons on the right of the dropdown menus. Here, "embedding" is a low dimensional (default 40) embedding used for subsequent analysis (e.g. clustering and DE analysis), and 2D embedding is used for visalization. After this step, a scatter plot (2D embedding) will be shown in the main plot.

<br>
![Dim Settings](images/dim-settings.png)
<br>
You can also download the plot at any time by clicking the button at the top-right corner of the main plot.
<br>
![2D Embedding](images/basic-2d.png)
<br>

**4. Clustering**
<br>
    Go to the **CLUSTERING** panel in the sidebar and stay in the **UNSUPERVISED** tab. Choose a clustering algorithm from the dropdown menu. The default option is Leiden. Click the button on the right to expand a setting panel and if you want to change the parameters of the algorithm. Finally, click <span class='mbutton'>RUN</span> to begin clustering. Once it is finished, the colors of the marker points will change to indicate clusters. These colors can be modified for each individual cluster, by clicking on the palette icon at that plot's header bar.

<br>
![Settings](images/cluster-settings.png)
<br>

<br>
![Leiden](images/basic-leiden.png)
<br>

**5. Annotations**
<br>
    In the **ANNOTATIONS** panel, you can: 1. annotate a cluster with a cell type; 2. store a group of cells as a subset for subsequent analysis (DE analysis); 3. merge a subset into a new cluster.
<br>
<br>
    To annotate a cluster, select a cluster using the dropdown menu in the first row, enter the cell type name (e.g. "cell type 1"), and click <span class='mbutton'>STORE</span>.
<br>
![Cell type annotation](images/basic-cell-type.png)
<br>
<br>
    To store a subset, you first need to use the lasso tool to select a group of cells in the main plot, enter the new subset name, and click <span class='mbutton'>STORE</span>.
<br>
![Store Subset](images/basic-subset.png)
<br>
<br>
    Finally, you can merge the cells in this new subset into a new cluster. To do so, simply select this new subset, and click <span class='mbutton'>MERGE</span>.
<br>
![Merge](images/basic-merge.png)
<br>

**6. Differentially Expressed Genes Analysis**
<br>
To do DE analysis, scroll down and into the **DE Analysis** panel in the **ANALYSIS** tab. Select two subsets that you wish to compare. These subsets include the subsets the you defined in previous steps, and all the clusters. After clicking <span class='mbutton'>FIND DE GENES</span>, a table will show the DE genes with p-values below <span class='mbutton'>alpha</span>,which is also adjustable. For example, here we find the DE genes of the new subset that we just defined against all the remaining cells.

<br>
![DE](images/basic-de.png)
<br>

**7. Feature Visualizations**
<br>
You can also visualize one or more genes in the **Feature Visualization** panel, which is on the right of the **DE Analysis** panel. For example, if we are interested in the first DE gene "CD74", we select this gene by either typing or finding it in the first dropdown. Then we select the range to visualize (optional). Finally, we select the type of visualization in the second dropdown, which has 3 options `PLOT EXPRESSION`, `HEATMAP`, and `VIOLIN PLOT`. For example let's first take a look at a violin plot.
<br>

![violin](images/basic-violin.png)
<br>

We can see this DE gene is indeed expressed higher in the new cluster that we just defined (Cluster 9).
<br>

If we select `PLOT EXPRESSION`, then the color of the main plot will change to indicate the expression value of that gene in each cell. Brighter color means higher expression. If multiple genes are selected, then the co-expression value will be visualized (see the **ANALYSIS** section for more details). In this case, we plot the first DE gene and we can see it is indeed expressed in the new subset.

<br>

![expression](images/basic-plot-expression.png)
<br>
Finally, we plot a heatmap for top 3 DE genes. Again it is clear that their expression values are higher in cluster 9.

<br>
![exprheatmapession](images/basic-heatmap.png)
<br>

**8. Enrichment Analysis**
<br>
In the **Enrichment Analysis** panel, we provide several marker lists for enrichment analysis. You can use them to, for example, identify cell types. You only need to choose a marker list, enter the number of top DE genes to use, and click <span class='mbutton'>RUN</span>. Then the results will be presented in a table. Here we find top cell type candidates for cluster 9.
<br>
![enrichment](images/basic-enrichment.png)
<br>

**9. Export Session**
<br>
When you are done with the analysis, you can export your results in the **SESSION** panel. **EXPORT SESSION** will download the dataset with all the results as an <span class='extension'>h5ad</span> file. **EXPORT ANNOTATIONS ONLY** will only download cell barcodes and their annotations as a <span class='extension'>csv</span> file.
<br>
![session](images/session.png)
<br>

