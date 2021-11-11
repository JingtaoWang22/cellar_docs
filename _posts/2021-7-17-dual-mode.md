---
title: 'DUAL/SINGLE MODE'

category: User Interface
layout: null
type: ui
---
Dual mode is useful for analyzing and visualizing two datasets simultaneously.
This can be particularly useful when analyzing SNARE-seq chromatin and
mRNA expression data, or when integrating two datasets (e.g., via
label transfer). Tutorials on joint analysis and data integration can be
found below.
<br>
![CODEX Main Plot](images/dual1.png)
<br>

* **<span class='mbutton'>DUAL MODE</span>**
    * When in dual mode, only one dataset (plot) is active. This means that
    all of Cellar's functionality applies to that dataset only. This includes
    clustering, annotation, and analysis panels. A plot can be activated
    by clicking the <span class='mbutton'>ACTIVATE</span> button at that plot's
    toolbar. Also, any label transfer functions assume the inactive dataset
    to be "reference" data, while the active dataset to be the one we wish
    to obtain labels for.

* **<span class='mbutton'>SINGLE VIEW</span>**
    * This switches back to single mode. The session for the other dataset
    will not be lost and can be recovered by entering dual mode again.

    Dual Mode:
    <br>
    <img src="images/dual2.png" class="w600"/>
    <br>

    Single View:
    <br>
    <img src="images/single.png" class="w600"/>
    <br>
