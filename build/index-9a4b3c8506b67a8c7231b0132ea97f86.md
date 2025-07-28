# ESA Project Results Repository

The [ESA Project Results Repository (PRR)](https://eoresults.esa.int/) provides long term storage for research outcomes. It provides access to data, workflows, experiments and documentation from ESA Projects organised across Collections, accessible via the [STAC API](https://github.com/radiantearth/stac-api-spec). Each Collection contains [STAC Items](https://github.com/radiantearth/stac-spec/blob/master/item-spec/item-spec.md), with their related Assets stored within the PRR storage. Scientists/commercial companies can access the PRR via the [EarthCODE](https://earthcode.esa.int/) and [APEx](https://esa-apex.github.io/apex_documentation/) projects.


# Uploading data to the PRR
In order to upload data to the ESA Project Results Repository (PRR) you have to generate a STAC Collection that is associated to your files. The STAC Collection provides metadata about your files and makes them searchable and machine readable. The metadata generation process is organised in four steps process:

1. Generate a root STAC Collection
2. Group your dataset files into STAC Items and STAC Assets
3. Add the Items to the Collection
4. Save the normalised Collection
5. Send the data, metadata and some extra information to the EarthCODE team.

Below you will find guides to the whole process, we recomend starting with the introductory notebook.

- [Generating a STAC Collection for the PRR(Introduction)](./PRR_STAC_introduction.ipynb) - A notebook explaining how to create the required PRR metadata. It describes the steps in detail and uses a relatively simple example, with a single .nc raster data file.
- [Generating a STAC Collection for the PRR (Multiple file types)](./example_tccas.ipynb) - Example how to generate metadata for a more complicated dataset which has multiple types of data and different file formats.
- [Generating a STAC Collection for the PRR(Large dataset for multiple regions)](./Creating%20STAC%20Catalog_from_PRR_example.ipynb) - Example how to generate metadata for a large dataset that has multiple disjoint regions.

If you are interested in exploring/downloading PRR data you can use this notebook as a guide:
- [ESA Project Results Repository (PRR) Data Access and Collections Preview](./PRR_STAC_download_example.ipynb) - A notebook explaining how Item Catalogs should be created, uses raster data.
