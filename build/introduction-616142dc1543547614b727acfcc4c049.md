# Introduction



# Welcome to the ESA EarthCODE 101 Workshop!

<b>Doing Open Science shouldn't be hard, and EarthCODE makes it easy!</b>

This hands-on tutorial is designed to introduce participants to EarthCODE's and the EDC Pangeo Platform's capabilities, guiding them from searching, finding, and accessing EO datasets and workflows to publishing reproducible experiments that can be shared with the wider scientific community.

This workshop will equip you with the tools and knowledge to leverage EarthCODE for your own projects and contribute to the future of open science. During this workshop, participants will, in a hands-on fashion will learn about the following:
- Introduction to EarthCODE and the future of FAIR and Open Science in Earth Observation
- Gain understanding in Finding, Accessing, Interoperability, and Reusability of data and workflows on EarthCODE
- Creating reproducible experiments using EarthCODE’s platforms - with a hands-on example with Euro Data Cube and Pangeo
- Publishing data and experiments to EarthCODE At the end of the workshop, we will take time for discussion and feedback on how to make EarthCODE better for the community.


### Running on EDC EOxHub Workspace

If you are using the EDC environment and have accessed this example through the Open Science Catalog, this example should have the correct kernel selected, and packages installed. You can directly use this example as is, with Dask Gateway. You can access this example on EDC Pangeo Platform.

### Running on your own computer

Most parts of this tutorial were designed to run with limited computer resources, so it is possible to run on your laptop.
It is a bit more complicated as you will have to install the software environment yourself. Also you will not be able to test real cloud distributed processing with Dask gateway.

Steps to run this tutorial on your own computer are listed below and demonstrated _through Linux commands only_:

1. git clone the repository.
```bash
git clone http://github.com/ESA-EarthCODE/tutorials/
```
1. Install the required software environment with Conda. If you do not have Conda, install it by following these instructions (see [here](https://docs.conda.io/en/latest/miniconda.html)). Then create the environment, this can take a few minutes.
```bash
conda env create -n pangeo -f ESA-EarthCODE/tutorials/pangeo/environment.yml
```
1. Launch a Jupyterlab notebook server from this environment.
```bash
conda activate pangeo
jupyter lab
```
1. Open a web browser and connect to the Jupyterlab provided URL (you should see it in the jupyter lab command outputs), something like: http://localhost:8888/lab?token=42fac6733c6854578b981bca3abf5152.
2. Navigate to pangeo_on_EarthCODE using the file browser on the left side of the Jupyterlab screen.

