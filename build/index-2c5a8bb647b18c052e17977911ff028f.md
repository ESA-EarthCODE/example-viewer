# openEO

[openEO](https://openeo.org/) is an open standard designed to simplify access to and processing of EO data. It provides a unified API that abstracts away differences between cloud platforms, enabling scientists, developers, and analysts to build workflows and experiments in a consistent and portable way. Instead of learning the specifics of each platform or provider, users can work with a common interface to query datasets, chain processing steps, and run analyses at scale.

From a technical perspective, openEO defines a set of RESTful APIs and [client libraries](https://openeo.org/software.html#clients) in popular programming languages such as Python, R, and JavaScript. These libraries allow users to connect to different backends, discover available EO collections and processing capabilities, and construct workflows as [process graphs](https://openeo.org/documentation/1.0/glossary.html#processes). These process graphs describe the sequence of operations in a platform-independent format, making them reusable across environments. Whether the goal is atmospheric correction, time-series analysis, or machine learning integration, openEO provides the building blocks for scalable EO data science.

From a user perspective, openEO lowers the barrier to experimentation and collaboration. Users can start with small exploratory analyses in notebooks, gradually expand workflows into more complex experiments, and finally scale them up on powerful cloud infrastructures, all without changing the underlying logic. This portability fosters reproducibility and ensures that workflows developed once can be reused, adapted, or shared easily across projects.

The notebook tutorials provided in this section illustrate how to use openEO for common scientific tasks: from creating workflow using user defined processes and open source input data, incorporating it into scientific experiment, to publishing experiment with the workflow in EarthCODE. At the end reproducibility of published experiment is also demonstrated.

## openEO Tutorials

  1. [Creating an openEO workflow](1_workflow.ipynb): This guide demonstrates how to create a basic openEO workflow, executing a simple processing task and publishing it as workflow that can be shared and reused.
  2. [Creating an experiment](2_experiment.ipynb): This guide shows how to set up an experiment using the previously created workflow, defining parameters such as area of interest and time range, and executing the workflow to generate output products.
  3. [Publishing an experiment to EarthCODE](3_publication.md): This guide explains how to publish the created experiment to the EarthCODE Open Science Catalogue (OSC) using the openEO Publishing tool, making it discoverable and reusable by the scientific community.
  4. [Reproducing an experiment](4_reproduce.ipynb): This guide illustrates how to reproduce the published experiment using openEO, verifying the output products against the original experiment to ensure consistency and correctness.  
