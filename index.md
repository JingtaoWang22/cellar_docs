---
title: Home
layout: default
nav_order: 1
description: "Cellar is an interactive tool for analyzing single-cell omics data."
permalink: /
---

# Cellar Documentation
{: .fs-9}

**Cellar** is an interactive tool for analyzing single-cell omics data. Cellar
is written in Python using [Dash](https://plotly.com/dash/).
{: .fs-6 .fw-300}


[Visit Cellar](https://data.test.hubmapconsortium.org/app/cellar){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View it on GitHub](https://github.com/ferrocactus/CellarV){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## Getting started

### Web Server
Our [web server](https://data.test.hubmapconsortium.org/app/cellar) running
a copy of Cellar is free for everyone to use and contains several test
datasets. Most of these datasets were generated by the
**Human BioMolecular Atlas Program** ([HuBMAP](https://hubmapconsortium.org/))
and can be downloaded via Cellar's interface.

Video tutorials are also available on [YouTube](https://www.youtube.com/playlist?list=PL5sLSLkTYpWgfBQ0M8ObfBIqDMAzx0-D2).

### Local Installation: Docker
Cellar can also be installed locally. This has the advantage of being able
to use on premises resources and avoid network latency. The easiest way
to install Cellar locally is via [docker](https://www.docker.com/).
1. Pull the image
```bash
$ docker pull euxhen/cellarv
```
2. Start a Cellar server on port 8050
```bash
$ docker run --rm -p 8050:8050 euxhen/cellarv
```
```bash
# You can also bind mount a local directory of `.h5ad` files to be read by Cellar
$ docker run --rm -p 8050:8050 -v /path/to/directory:/home/nonroot/cellar/data euxhen/cellarv
```
3. Wait for a few seconds and point your web browser to [localhost:8050](localhost:8050)

### Local Installation: Conda
An alternative to a Docker installation is to create a local
[conda](https://docs.conda.io/en/latest/) virtual environment
with all the required dependencies. If you do not have conda installed, please
follow these [instructions](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) first. Assuming conda is now available, follow the steps below.
1. Download Cellar's [conda environment](https://github.com/ferrocactus/CellarV/blob/master/env.yml) yml file
```bash
$ wget https://raw.githubusercontent.com/ferrocactus/CellarV/master/env.yml
```
2. Install the conda environment
```bash
$ conda env create -f env.yml
```
This will create an environment named `cellar`.
3. Activate the environment
```bash
$ conda activate cellar
```
4. Download the [install_Rdeps.py](https://github.com/ferrocactus/CellarV/blob/master/install_Rdeps.py) script
```bash
$ wget https://raw.githubusercontent.com/ferrocactus/CellarV/master/install_Rdeps.py
```
5. Install R dependencies
```bash
$ python install_Rdeps.py
```
6. Download Cellar's source code
```bash
$ git clone https://github.com/ferrocactus/CellarV
```
7. Run Cellar
```bash
$ cd CellarV
$ python main.py
```
8. Visit [localhost:8050](localhost:8050) on your web browser.

---

### About the project

Cellar is developed and maintained by the
[Systems Biology Group](http://www.sb.cs.cmu.edu/) at
[Carnegie Mellon University](https://www.cmu.edu/). It was developed
to enable research groups to compare and integrate data from different
modalities by using a simple and intuitive interface. Cellar is meant to
be a one-stop solution to the single cell analysis pipeline by offering a
wide selection of tools that follow best practices agreed upon in the community.

A preprint is available on [bioRxiv](https://www.biorxiv.org/content/10.1101/2021.03.19.436162v1?rss=1).

### License

Cellar is distributed by an [MIT license](https://github.com/ferrocactus/CellarV/blob/master/LICENSE.txt).