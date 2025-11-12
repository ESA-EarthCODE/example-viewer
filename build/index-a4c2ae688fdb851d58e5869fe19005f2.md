# ESA Project Results Repository

The [ESA Project Results Repository (PRR)](https://eoresults.esa.int/) provides long term storage for research outcomes. It provides access to data, workflows, experiments and documentation from ESA Projects organised across Collections, accessible via the [STAC API](https://github.com/radiantearth/stac-api-spec). Each Collection contains [STAC Items](https://github.com/radiantearth/stac-spec/blob/master/item-spec/item-spec.md), with their related Assets stored within the PRR storage. Scientists/commercial companies can upload data to the PRR via the [EarthCODE](https://earthcode.esa.int/) and [APEx](https://esa-apex.github.io/apex_documentation/) projects. Most data in the PRR is open access and anyone can download and use it, subject to the dataset's particular license.


# Uploading data to the PRR
In order to upload data to the ESA Project Results Repository (PRR) you have to generate a STAC Collection that is associated to your files. The STAC Collection provides metadata about your files and makes them searchable and machine readable. The metadata generation process is organised in four steps process:

1. Generate a root STAC Collection
2. Group your dataset files into STAC Items and STAC Assets
3. Add the Items to the Collection
4. Save the normalised Collection
5. Send the data, metadata and some extra information to the EarthCODE team.

# Getting Started with PRR Metadata Creation

These notebooks are designed for users who are new to the process of publishing data to the ESA Project Results Repository (PRR). They provide step-by-step guidance on how to generate STAC Collections that meet PRR ingestion requirements. 
Whether you're working with a single raster file or a large, multi-format dataset, notebooks below will assist you in this process. 

- [Generating a STAC Collection for the PRR (Introduction)](./PRR_STAC_introduction.ipynb) - Detailed explanation on how to create valid metadata to ingest simple raster data file (.nc) into PRR. 
- [Generating a STAC Collection for the PRR (Multiple file types)](./TCCAS_v2.ipynb) - Example how to generate metadata for a more complex dataset with varied data types and formats.
- [Generating a STAC Collection for the PRR (Large dataset for multiple regions)](./Creating%20STAC%20Catalog_from_PRR_example.ipynb) - Example focuses on handling large dataset across multiple disjoint regions.
- [Generating STAC Collection for the PRR (zarr files)](./prr_zarr.ipynb) - A guide for generating a collection from zarr files.

# Accessing and Exploring data products on ESA PRR
This notebook is generated for users willing to explore the ESA PRR repository, by browsing, previewing and/or downloading data published on the PRR. 

- [ESA Project Results Repository (PRR) Data Access and Collections Preview](./PRR_STAC_download_example.ipynb) - Use this notebook to access, explore, query, and download data from the ESA Project Results Repository (PRR).
