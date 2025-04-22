---
order: 0
---
#  10 minutes to EarthCODE

Welcome to 10 Minutes to EarthCODE! This quick-start guide is designed to help you begin working with EarthCODE in just a few minutes. Whether you're new to Earth Science, a researcher, or a developer, EarthCODE provides a collaborative, open development environment for efficient access to Earth observation data, workflows, and computational platforms.

## What is EarthCODE?
EarthCODE stands for "Earth Science Collaborative Open Development Environment". EarthCODE is developed by The European Space Agency (ESA) to advance FAIR Open Science principles across ESA-funded activities, including but not limiting to the [ESA Science Clusters](https://eo4society.esa.int/communities/scientists/) and the [Science Hub](https://sciencehub.esa.int/). The EarthCODE Portal provides a centralised point of access to integrated tools, data, and services for seamless research development, execution, and publication, while fostering collaboration and enabling long-term preservation and reuse of scientific outputs.

## Accessing EarthCODE
To get started, sign in using your [GitHub](https://github.com/) account. EarthCODE provides secure authentication for accessing resources across platforms, including the [EarthCODE Forum](https://discourse-earthcode.eox.at). Once authenticated, you'll have access to all the tools, discussions, and data you need across EarthCODE’s integrated platforms.

## Suggested Paths

Different users of EarthCODE have different needs and goals. To help you find the most relevant information quickly, we've outlined suggested paths based on your role and intentions.  

### Researchers Ready to Upload Their Data  

If you've completed your research and are looking to **publish your data to the Open Science Catalog (OSC)**, your main priority is to ensure your data is **persistent, properly formatted and publicly available**.  

Head directly to the [**Uploading Data**](../Technical%20Documentation/Data/Contributing%20to%20the%20EarthCODE%20Catalog.md) section to learn how to:  
- Prepare your data for publication.
- Create valid STAC objects and metadata.
- Publish data products to the Open Science Catalog.

This section will guide you through the entire upload process, including validating your metadata and ensuring your data assets are accessible.  


### New Researchers Starting a Project  

If you're just starting a new research project, it’s important to choose the **right platform and tools** from the beginning. Your path depends on several factors, including:  
- The **type of data** you intend to use.  
- Your **workflow preferences** (e.g., no-code platforms vs. Jupyter Notebooks).  
- Whether you need **machine learning capabilities**.
- Whether you need **storage capabilities**.
- The level of **collaboration and sharing** required.  

Visit the [**Platform Selection**](../Technical%20Documentation/Platforms/Choosing%20Tools%20and%20Platforms.md) section to get tailored recommendations on:  
- Selecting the best platform for your needs.  
- Understanding which tools will streamline your workflow.  
- Setting up your environment for collaborative or individual work.  

If you plan to publish your results later, it’s a good idea to also familiarize yourself with the [**Uploading Data**](../Technical%20Documentation/Data/Contributing%20to%20the%20EarthCODE%20Catalog.md) section to understand the requirements early on.  

### Users Exploring Published Research  

If you’re here to **explore existing research outputs**, the Open Science Catalog is your primary destination. The catalog allows you to:  
- **Search for projects** by area, variable, theme, and more.  
- Access **datasets, workflows, and documentation** directly from published research.  
- View detailed **metadata and provenance information** for each project.  

Go to the [**Open Science Catalog**](https://opensciencedata.esa.int/) to start browsing and discovering data relevant to your interests. Whether you're looking for specific datasets, workflows, or scientific results, the catalog provides a centralized and well-organized resource.  


## Choosing a Platform
EarthCODE provides streamlined access to a range of platforms offering Earth Science datasets, tools, and services. With single sign-on via OpenID Connect, users can easily authenticate and explore resources tailored to their research needs. Below is a selection of supported platforms:

- [Copernicus Data Space Ecosystem (CDSE)](https://dataspace.copernicus.eu): Access and process earth observation datasets in the Copernicus Data Space Ecosystem with the openEO API.
- [Deep Earth System Data Laboratory (DeepESDL)](https://www.earthsystemdatalab.net/): Access and process data, and apply machine learning (ML) methods on Xarray Earth System Data Cubes (ESDC).
- [Euro Data Cube](https://eurodatacube.com/): A suite of services to access and process satellite data and develop applications.
- EOxHub/CoCalc: Process Earth observation data in the cloud with live collaboration on code.
- EOxHub/Pangeo: Perform high-performance computations on Earth Science data leveraging geoscience libraries.

Visit the [Working with Platforms](../Technical%20Documentation/Platforms/) page for help on how to choose the platform that best suits your research objectives.

## Exploring the EarthCODE Open Science Catalog

After finalising research on one of the platforms, your final data products and code can be published in the EarthCODE Catalog - The [Open Science Catalog](https://opensciencedata.esa.int/). The catalog includes datasets, workflows, and software that have been published and validated within EarthCODE (i.e., on one of the integrated platforms or following the EarthCODE best practices). It's your gateway to a wide range of resources, whether you're looking for environmental data, code for processing, or reusable workflows.

## Validating and Publishing Data to the Catalog {#publishing-anchor}

EarthCODE allows you to validate products and experiments, ensuring they meet reproducibility and scientific standards. If you have an ESA-funded project, you can contribute to the platform by publishing your datasets, software, or experiments, making your work available for the broader community to use.

### How data is published
The [Open Science Catalog](https://opensciencedata.esa.int/) is built on the [SpatioTemporal Asset Catalog (STAC)](https://stacspec.org/en), a standardised format for describing geospatial data. To contribute your research, you need to create valid STAC objects and commit them to the [`open-science-catalog-metadata-staging`](https://github.com/EOEPCA/open-science-catalog-metadata-staging) repository on GitHub. These STAC objects, stored as JSON files, will be automatically processed and rendered in the catalog.

Each STAC object should include all necessary references to ensure the reproducibility of your research, such as: 
- **Result data** - hosted on open-access data storage provided by ESA
- **Input data** - with full specification about spatial and temporal extent, bands, format, etc. This can also be part of the workflow.
- **Workflows** - executable processes that, when combined with input data, reproduce the results.

To improve discoverability, STAC objects also include metadata fields such as:
- Associated project
- Geospatial extent
- Variables
- Themes
- Earth Observation (EO) Mission (e.g. Sentinel, Landsat)

Because these objects must follow a strict predefined schema, ensuring compliance can be complex. However, EarthCODE provides example guides to help you structure your data correctly. Additionally, there are automated tools that simplify the creation of STAC objects, reducing manual effort.

You can read more on how to publish data in the [Uploading Your Data](../Technical%20Documentation/Data/Contributing%20to%20the%20EarthCODE%20Catalog.md) section, and check out our [examples](../../examples/).


## Who Can Publish?

Anyone with an ESA-funded project is encouraged to publish in EarthCODE. We especially welcome contributions from those part of the ESA Science Clusters, as collaboration among these projects helps promote sharing and innovation in Earth Science research.


