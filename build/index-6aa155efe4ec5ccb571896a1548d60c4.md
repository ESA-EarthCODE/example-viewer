# Open Science Catalog

The [Open Science Catalog (OSC)](https://opensciencedata.esa.int/) is a key component of the ESA EO Open Science framework. It is a publicly available web-based application designed to provide easy access to scientific resources including geoscience products, workflows, experiments and documentation from activities and projects funded by ESA under the EO Programme.

There are three different ways and several tools to contribute to Open Science Catalog:

### 1: Use a Visual GUI Interface (No coding required) 

- [Git Clerk](./git_clerk_example.md) - A guide for using the Git Clerk tool which is a user interface for automatically creating product entries and creating a Pull Request in the OSC GitHub Repo.

### 2: Manually contribution (For users familiar with Git)
- [Direct editing metadata in JSON](./osc_pr_manual.ipynb) - A guide for manually creating Open Science Catalog entries by creating JSON files with metadata. 

- [Generating OSC files with pystac](./osc_pr_pystac.ipynb) - A guide for creating Open Science Catalog entries in more automated way by implementing `pystac`. Require familiarity with Python. 

### 3: Using one of the platform tools (For EarthCODE integrated platforms users)
- [DeepCode](https://github.com/deepesdl/deep-code) - An example using DeepCode: a library for automatically generating product entries for DeepESDL datasets.
- [openEO Publishing Tool](https://publish.earthcode.vito.be/) - A platform agnostic tool to publish workflows, experiments and products created on openEO-based platforms. Learn more in our dedicated [publication](../openeo/3_publication.md) guide.
