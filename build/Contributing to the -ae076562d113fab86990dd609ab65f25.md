---
order: 1
---
# Publishing Science Results

The catalog functionalities described in the previous sections are granted to any user (registered/and non-registered users). Catalog exploration and content discovery and access to the products is fully open and transparent. In this section we will describe how to make new data accessible through the catalog and make them available for the broad scientific community.

:::tip :peanuts: STAC IN A NUTSHELL
A STAC catalog is a structured, machine-readable collection of geospatial assets, described using JSON-based metadata records. It provides a standardized way to organize and link datasets, making it easy to search, access, and analyze geospatial data across different sources. A STAC catalog consists of collections (groupings of related datasets) and items (individual assets like satellite images or model outputs), with links connecting them for easy navigation and interoperability.
:::

### Who can contribute?

If you are an **ESA Project PI, Data Owner or OSC Admin** you can contribute to the content of the Open Science Catalog (OSC) in the following ways:

- Result publishing by adding content to the OSC
- Updating content (description of Products, Projects, etc.)
- Request removal of existing entries

**Other user requirements include:**

- Only users with an active GitHub account are allowed to contribute to the catalog. In case of absence of GitHub account, please [create an account first.](https://github.com/join)

### How to Publish Results

In order to publish your results to the OSC, you need to create valid STAC and/or OGC API Record objects (a structure of JSON files) and upload these through a Pull Request to the [open-science-catalog-metadata](https://github.com/ESA-EarthCODE/open-science-catalog-metadata/tree/main) repository.

In fact, in most cases you would need to create two separate STAC or Record objects:
1. __Item catalog__ — A self-contained STAC catalog, typically hosted in your own public GitHub repository (__Accessible__).
2. __Product, Workflow, or Experiment entry__  — The metadata record you upload to the OSC, linking to related Projects, Themes, Variables, and your external Item Catalog (__Findable__).

::: details Why keep them separate?
Earth observation research can generate large amounts of datasets with extensive metadata. Keeping data assets separate ensures faster __loading, less clutter, and a consistent access method__, while the OSC remains focused on structured metadata.
:::

If you are new to using STAC, git, or both, this can be an intimidating process, but luckily there are many tools available to more or less automate this process depending on your setup. Check out the [OSC examples](../../../examples/index-1) for an overview.

__Typical workflow for uploading a product to OSC:__
1. Upload your data to a persistent remote storage (e.g. ESA's Project Results Repository (PRR), an object storage (S3) bucket, Zenodo, etc.).
2. Create the Item Catalog, with links to your assets in the remote storage.
3. Create an OSC product entry, with a link to your Item Catalog.


## Step 1: Uploading your data to a remote storage

To share your data, it must be __openly accessible via the cloud__. How you achieve this depends on your use case. If your data is already hosted by a cloud storage provider, there's no need to duplicate it, simply use those links. The key requirement is that the data is __publicly available and persistent__ (i.e., it won't be deleted).

If your data isn't in the cloud or its persistence is uncertain, the recommended process is to request access to the official
[ESA PRR](https://eoresults.esa.int/data_provider_guide.html#) and upload it there following the described procedure.
After requesting a data provider account you need to request a PRR collection which is used in the next steps as the STAC Item Catalog.

Alternatively there is also an object storage bucket maintained by the EarthCODE team that can be used to persistently store data.
Feel free to [contact the EarthCODE team](https://earthcode.esa.int/contact) to discuss available options.


## Step 2: Creating and uploading a STAC Item Catalog

### Description

The purpose of the STAC Item Catalog is to collect metadata and references to your assets in a format that can be easily reused by other scientists and automated workflows, and displayed correctly in the Open Science Catalog.

The hierarchy is structured as follows:

1. Catalog – A top-level container with a title and description, grouping related data files.
2. Items – Each Item represents a single data file and contains metadata such as geospatial extent, temporal range, and projection.
3. Assets – Each Item has one or more Assets, which have a direct link to the actual data files and contain metadata such as file type and spectral bands.

__Example folder structure__
```
my-item-catalog
├── catalog.json
└── item_1
    └── item_1.json
```

::: details Example `catalog.json`
```json
{
  "type": "Catalog",
  "id": "item-catalog-for-my-data",
  "stac_version": "1.1.0",
  "description": "A useful description about the datasets in my project.",
  "links": [
    {
      "rel": "root",
      "href": "./catalog.json",
      "type": "application/json",
      "title": "Item Catalog Example"
    },
    {
      "rel": "item",
      "href": "./item_1/item_1.json",
      "type": "application/geo+json"
    },
  ],
  "title": "Item Catalog Example"
}
```
:::

::: details Example `item.json`
```json{60}
{
  "type": "Feature",
  "stac_version": "1.1.0",
  "stac_extensions": [
    "https://stac-extensions.github.io/eo/v1.1.0/schema.json"
  ],
  "id": "item_1",
  "geometry": {
    "type": "Polygon",
    "coordinates": [
      [
        [
          -50.17968937855544,
          66.77834561360399
        ],
        [
          -47.9894188361956,
          66.83503196763441
        ],
        [
          -48.056356656894216,
          67.37093506267574
        ],
        [
          -50.295235368856346,
          67.31275872920898
        ],
        [
          -50.17968937855544,
          66.77834561360399
        ]
      ]
    ]
  },
  "bbox": [
    -50.295235368856346,
    66.77834561360399,
    -47.9894188361956,
    67.37093506267574
  ],
  "properties": {
    "datetime": "2025-03-18T09:47:57.377671Z"
  },
  "links": [
    {
      "rel": "root",
      "href": "../catalog.json",
      "type": "application/json",
      "title": "Item Catalog Example"
    },
    {
      "rel": "parent",
      "href": "../catalog.json",
      "type": "application/json",
      "title": "Item Catalog Example"
    }
  ],
  "assets": {
    "data": {
      "href": "https://zenodo.org/records/<project-id>/files/extent_ABC.tif",
      "type": "image/tiff; application=geotiff",
      "eo:bands": [
        {
          "name": "b1",
          "description": "gray"
        }
      ],
      "roles": []
    }
  }
}
```
:::

### Creating the Item Catalog

One way to create an Item Catalog is to copy an existing catalog and edit it manually in a text editor to fit your data. If you're new to STAC and only have a few data assets, this approach can work, but it is prone to errors.

Manually editing STAC Items can be tedious, and extracting all the required metadata correctly can be challenging. For most Item Catalogs, we recommend using automated tools, for example:

- The [`stactools`](https://stactools.readthedocs.io/en/stable/cli.html#stac-create-item) CLI provides a simple command-line interface for generating STAC Items. With the [`stactools-datacube`](https://github.com/stactools-packages/datacube) extension even following the STAC datacube extension.
- A combination of [`PySTAC`](https://pystac.readthedocs.io/en/stable/) to create the Catalog and [`rio-stac`](https://github.com/developmentseed/rio-stac) for automatically generating valid STAC Items with all required metadata.

Typically, this workflow starts by defining individual STAC objects (a Catalog and its Items). Once created, these objects are linked together using STAC relationships.

In the final step, the Catalog is __saved and normalized__ to a specified root directory. At this stage, you can choose to set the Catalog type to __"self-contained"__. When enabled, this ensures that all internal links are automatically resolved and adjusted to be relative, making the Catalog portable and independent of absolute file paths. 

The process is straightforward, and we highly recommend checking out [this notebook](../../../examples/creating-an-item-catalog).

::: warning IMPORTANT  
Regardless of how you create the catalog, it must be **self-contained**. This means:
- Internal links should use **relative paths** (e.g., `"../catalog.json"` instead of `"/Users/name/catalog/catalog.json"`).
- Data asset paths should point to **remote storage**, not local files on your system.
:::  

### Uploading the Item Catalog

The **Item Catalog must be hosted separately** from the Open Science Catalog, and like the data files, it should be **persistent and publicly accessible**.

Since the Item Catalog only contains metadata (JSON) files rather than actual datasets, a simple and effective solution is to store it in a public repository, such as **GitHub**. This approach is demonstrated in the [Creating an Item Catalog notebook](../../../examples/creating-an-item-catalog).

Alternatively, if you have access to a **reliable cloud storage service**—such as the EarthCODE object storage bucket—you can host your Item Catalog there.

If you choose to use the ESA PRR the generated STAC Items have to be sent via `POST` requests to the [PRR Registration Gateway](https://eoresults.esa.int/reg-api/docs#/) for registration using the previously requested collection.

The only requirement is that __other users and the STAC browser must be able to find and read your repository!__

:::info  
In the next step where you will be uploading metadata to the Open Science Catalog, EarthCODE administrators will review your Item Catalog and assist you with any necessary adjustments.  
:::  


## Step 3: Creating a Product entry in the OSC

### How to publish new data to the catalog?

Data ingestion to the catalog can be performed in different ways, depending on **where the products are originally stored** , but also depending on **the number of products to be ingested** and therefore size.

All Themes, Variables, EO Missions, Projects, Products, Workflows, and Experiments are hosted as a metadata repository placed on the GitHub platform: Git and [GitHub API](https://docs.github.com/en/rest). Each update to metadata is handled via a [Pull Request (PR)](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests). This Pull Request allows for reviewers to see the changes to be applied in advance, to check for validity of the requested changes (via an automated validation script) and to provide reviews as comments. If appropriate, the changes can be merged with the main branch of the repository. When a Pull Request is merged, the updated STAC catalog is deployed as Static Catalog.

![ingest-data-scheme](https://github.com/EOEPCA/open-science-catalog-metadata/assets/120453810/5d6297e7-5d66-4564-9538-bb6eaeb92598)

At the moment Open Science Catalog supports ingestion of new products via **GitHub only**. This allows data providers like projects PI to apply **multiple changes or adding several new products at once**.

Work is underway to provide a CMS-like GUI based editing functionality using [git-clerk](https://github.com/EOX-A/git-clerk) via the EarthCODE Portal. Although this GUI approach is still relying on GitHub the complexity is abstracted and hidden to the user.

In this section the contribution procedure is described in an example for a Product. Please note that in the same way new Variables, Projects, Themes, EO Missions, Workflows, and Experiments can be added. We will be using three Use Case scenarios to better describe the procedure of product ingestion to the catalog:

1. Adding metadata of a single product (item) to the catalog manually.
2. Ingesting metadata of assets with STAC Catalog:
   1. Adding multiple or single product(s) stored in external server (open-access storage)
   2. Adding multiple or single product(s) stored locally

### Which information is needed before I start importing new data?

Before making any changes to the catalog's content please make sure you have already prepared the following information about your product:

- The Product should be related to a result of an ESA-funded project. Check if the Project's page is already existing within the ESA Open Science Catalog: [https://opensciencedata.esa.int/](https://opensciencedata.esa.int/). If not **create a Project page first.**
- **Complete metadata available** (to correctly describe the Product)
- The Product should be stored in an external database that is approved and a **stable data repository** (e.g. ESA PRR, CEDA Data Archive: [https://catalogue.ceda.ac.uk/](https://catalogue.ceda.ac.uk/); Zenodo repository: [https://zenodo.org/](https://zenodo.org/), etc.)
- If the product you would like to ingest is stored elsewhere, see other data ingestion scenarios described in the section TBD.
- Data provided in formats acceptable by GDAL and rasterio library.

Please refer to the graphic below to check which metadata are required for your product **before starting the Product upload.**

![metadata-stac](https://github.com/EOEPCA/open-science-catalog-metadata/assets/120453810/71b8e8a7-9a86-491b-ae54-1fb4de9ccf32)
