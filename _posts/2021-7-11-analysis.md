---
title: 'ANALYSIS'

category: User Interface
layout: null
type: ui
---
The analysis panels consist of tools for differentially
expressed features, enrichment analysis and visualizations that
can be used to get a better understanding of the cell types and
their function.
<!--
<br>
![Analysis](images/ui-analysis-panels.png)
<br> -->

* **DE Analysis**
    * DE analysis can be performed for any cluster or user-defined subset.
    To store a group of cells as a subset, see
    <span class='mbox'>Store Subset</span> under
    <span class='mbox'>ANNOTATIONs</span>.
    It is possible to run "one vs all" or "one vs one" tests. If
    the second subset is set to <span class='keyword'>rest</span>,
    then Cellar will find DE genes for Subset 1 against all the remaining
    cells. Otherwise, Cellar finds DE genes of Subset 1 vs Subset 2.

    * To determine DE genes we use a t-test as implemented
    in the [diffxpy](https://diffxpy.readthedocs.io/en/latest/)
    package. All DE genes are sorted by log fold-change.
    The corrected p-value threshold or fold-change threshold can
    also be specified under the settings popover. If FC is set
    to 0, then no fold-change filtering is applied. If the data has been
    log-transformed during the preprocessing step, make sure "Is Data Logged"
    has been set to True, and False otherwise.

    * Clicking on any row of the DE table will paste the corresponding gene
    into the feature visualization select menu where it can be visualized
    using one of the different plotting tools.

    * The DE table also shows the mean of the selected gene for both chosen
    subsets. NOTE: this mean is computed on the normalized data (if
    normalization was applied during the preprocessing step), therefore,
    it may contain negative values. However, the data is scaled back
    during the computation of log fold-change.
<br>
![DE](images/ui-analysis-de.png)
<br>

* **Feature Visualization**
    * Three types of feature visualization tools are supported:
    **PLOT EXPRESSION**, **HEATMAP**, and **VIOLIN PLOT**. To perform
    the visualization, first select any features you wish to visualize
    in the dropdown menu. If "auto-scale" is checked, Cellar will
    attempt to remove (more precisely, clip) any outlier values it finds
    so that very high or low values do not extend the colorscale unnecessarily.
    Unchecking "auto-scale" will enable a range slider for the selected
    feature which allows a manual clipping of values.

    * When multiple genes are selected, a co-expression value is shown.
    To compute this co-expression value, we first scale each gene
    to the $$[0, 1]$$ range, and for every cell we take the minimum scaled
    expression value across all selected genes. Formally,
    if we let the expression matrix be
    $$M\in\mathbb{R}^{m\small\times n}$$, then given a cell
    $$i\in[m]$$, and a gene set $$G=\{g_1, \dots, g_r\}$$
    we compute the co-expression value of $$i$$ w.r.t. $$G$$ as
    $$c_i = \min_{j=1,\dots,r} \Big\{ \frac{M_{i, g_j} - v_{g_j}}{V_{g_j} - v_{g_j}} \Big\}$$
    where $$v_t = \min_j M_{j, t}$$ and $$V_t = \max_j M_{j, t}$$, i.e., the
    minimum and maximum expression values for gene $$t$$. Notice that
    $$0\leq c_i\leq 1$$. We apply this normalization so as not to bias the
    co-expression towards any one gene. We choose to display the minimum
    as the minimum satisfies the property that
    $$\min\{0, p\}=\min\{p, 0\}=\min\{0, 0\}=0$$
    for $$p\geq 0$$. In all these three cases we would want the co-expression
    to be $$0$$.

    Plot Gene Expression:
    <br>
    <img src="images/ui-analysis-plot-expression.png" class="w600"/>
    <br>

    Heatmap:
    <br>
    <img src="images/ui-analysis-heatmap.png" class="w500"/>
    <br>

    Violin Plot:
    <br>
    <img src="images/ui-analysis-violin.png" class="w500"/>
    <br>

* **Enrichment Anlysis**
    * After DE analysis, this can be used for performing different enrichment analysis using the GSEAPY Python package. To do this analysis, simply choose a marker
    list in the first dropdown menu, enter the number of DE genes to use for the analysis, and click <span class="mbox">RUN</span>. Then a table will be generated for showing the results.
    The entries are sorted by p-value.
    An <span class="mbox">EXPORT</span> button above the table
    will download the dataframe as a <span class="extension">csv</span> file.<br>

<br>
![Enrichment](images/ui-analysis-enrichment.png)
<br>
