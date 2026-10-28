Demonstration Video Link uploaded in the linkedin https://lnkd.in/p/dUN2HVmD

A hands-on Azure Data Factory project for integrating airline booking
data from a local file system into Azure Data Lake Storage Gen2 (ADLS
Gen2). The solution uses a Self-hosted Integration Runtime (SHIR) for
connectivity, Mapping Data Flows for data transformation, and full and
incremental loading workflows.
Project status: Implemented and successfully tested by the project
author.

Table of Contents
- Overview
- Objectives
- Architecture and Data Flow
- Technologies
- Repository Structure
- Data Assets
- Implementation
- Testing and Validation
- Prerequisites
- Setup Guide
- Security Notes
- Skills Demonstrated
- Future Enhancements
  
Overview
This project demonstrates a cloud data integration workflow using Azure
Data Factory. Source files are held on a local file system and accessed
through SHIR. Azure Data Factory orchestrates the workflow, Mapping Data
Flows transform data, and ADLS Gen2 is used as the cloud destination.

The repository contains Azure Data Factory project artefacts, sample
airline-related data files, and a SQL script containing booking data.
Objectives
- Practise ingesting local files into Azure cloud storage.
- Configure connections and data references using linked services and
  datasets.
- Use Mapping Data Flows to transform data.
- Implement and test both full and incremental loading workflows.
- Organise Azure Data Factory artefacts in GitHub for review and
  version control.
- Explore SQL data and fact-table concepts using the supplied booking
  data script.
Architecture and Data Flow
Local File System
       |
       | CSV / JSON files
       v
Self-hosted Integration Runtime (SHIR)
       |
       v
Azure Data Factory
       |
       | Pipeline orchestration
       v
Mapping Data Flows
       |
       | Transform data
       v
Azure Data Lake Storage Gen2
Flow summary
1. Source data is stored in files on a local machine or accessible
   local file system.
2. SHIR provides the connectivity required for Azure Data Factory to
   access the local source.
3. ADF pipelines orchestrate the integration workflow.
4. Mapping Data Flows apply the configured data transformations.
5. The transformed output is written to ADLS Gen2.
6. Full and incremental loading workflows are run and tested.
Update this section with your exact pipeline names, storage
container/folder paths, and incremental-load mechanism if you want the
README to document those implementation details.

Technologies
  Technology                          Purpose
  Azure Data Factory                  Pipeline orchestration and data
                                      integration

  Self-hosted Integration Runtime     Connectivity between ADF and the
                                      local file system

  Mapping Data Flows                  Visual data transformation

  Azure Data Lake Storage Gen2        Cloud destination for data files

  SQL                                 Working with booking data and SQL
                                      scripts

  CSV and JSON                        Source data formats present in the
                                      repository

  GitHub                              Source control and project
                                  documentation
Repository Structure
AzureDataFactory_Project/
├── dataflow/                 # Mapping Data Flow artefacts
├── dataset/                  # Dataset definitions
├── factory/                  # Factory-level configuration
├── integrationRuntime/       # Integration Runtime artefacts
├── linkedService/            # Connection definitions
├── pipeline/                 # Pipeline definitions
├── DimAirline.csv            # Airline dimension sample data
├── DimAirport.json           # Airport dimension sample data
├── DimFlight.csv             # Flight dimension sample data
├── DimPassenger.csv          # Passenger dimension sample data
├── fact_bookings_full.sql    # SQL script for booking fact data
└── publish_config.json       # Publish configuration
Folder contents and file names may change as the project evolves. Review
the exported JSON definitions in Azure Data Factory Studio before
deploying them to another environment.

Data Assets
The repository includes airline-related sample data:
- DimAirline.csv
- DimAirport.json
- DimFlight.csv
- DimPassenger.csv
- fact_bookings_full.sql
The filenames suggest a fact-and-dimension style dataset for airline
bookings. The SQL script contains booking table definitions and data
statements. Treat this as a learning dataset; confirm the actual
relationships and schema in the SQL script before documenting a complete
dimensional model.
Implementation
1. Source connectivity
- Used a local file system as the source.
- Configured a Self-hosted Integration Runtime to provide connectivity
  from Azure Data Factory to the local environment.
- Configured the relevant linked services and datasets.
2. Pipeline orchestration
- Organised the integration workflow in Azure Data Factory pipelines.
- Used datasets to reference the source and destination data.
- Used the relevant pipeline and data flow artefacts stored in the
  repository.
3. Data transformation
- Used Mapping Data Flows for the transformations configured in the
  project.
- Wrote transformed output to ADLS Gen2.
Add the exact transformations here (for example, filtering, derived
columns, joins, or aggregations) only if they are present in your
implementation.
4. Full and incremental loading
- Implemented and tested a full-load workflow.
- Implemented and tested an incremental-load workflow.
For a more reproducible technical description, document how incremental
records are identified (for example, a watermark, timestamp, or another
change-detection rule), how duplicates are handled, and what happens
when a run is repeated.
Testing and Validation
The project has been successfully executed and tested by the author.

Recommended evidence to include in this repository:
- Screenshot of a successful pipeline run in ADF Monitor.
- Screenshot of Mapping Data Flow configuration.
- Example source file and corresponding output in ADLS Gen2.
- Evidence of a successful full load and a subsequent incremental run.
- Row counts or validation results, if collected.
Do not add screenshots containing access keys, tokens, passwords,
connection strings, or other sensitive information.
Prerequisites
To reproduce the project, you will generally need:
- An Azure subscription with permission to create or use Azure Data
  Factory and ADLS Gen2 resources.
- Azure Data Factory.
- An ADLS Gen2-enabled storage account and a destination file
  system/container.
- A machine that can access the source files and run the Self-hosted
  Integration Runtime.
- Appropriate permissions for the configured source and destination
  connections.
- The project files from this repository.
Azure resources and usage may incur charges. Review pricing and remove
resources that are no longer needed.
Setup Guide
The exact resource names and paths depend on your Azure environment. Use
placeholders until you configure your own resources.
1. Clone or download the repository.
   git clone https://github.com/SiddharthV26/AzureDataFactory_Project.git
   cd AzureDataFactory_Project
2. Review the exported artefacts. Inspect the folders for
   pipelines, datasets, linked services, data flows, and factory
   configuration.
3. Prepare the local source. Place the required source files in
   your chosen local directory.
4. Configure SHIR. Install and register a Self-hosted Integration
   Runtime on a machine that can access the source directory. Confirm
   that the runtime is online.
5. Configure linked services. In your own ADF environment, update
   connection settings for the local source and ADLS Gen2 destination.
   Do not reuse environment-specific identifiers or secrets blindly.
6. Configure datasets and paths. Update file names, folders,
   container/file-system names, and any parameters to match your
   environment.
7. Review Mapping Data Flows and pipelines. Confirm that all
   referenced datasets and linked services exist and that the
   transformations match your intended workflow.
8. Run and validate. Execute the full-load workflow first, inspect
   the destination output, then run the incremental workflow and verify
   the expected changes.
This repository is an exported project, not a one-click deployment
package. Environment-specific linked services, credentials, resource
identifiers, and settings may need to be configured before execution.

Security Notes
- Never commit storage account keys, passwords, client secrets, access
  tokens, or connection strings containing credentials.
- Use secure authentication supported by your environment and grant
  only the permissions required.
- Keep environment-specific configuration separate from public sample
  artefacts.
- If a secret was committed, rotate or revoke it; deleting it from the
  latest commit alone may not remove it from Git history.
Skills Demonstrated
- Azure Data Factory pipelines and orchestration
- Self-hosted Integration Runtime connectivity
- Linked services and datasets
- Mapping Data Flows
- Azure Data Lake Storage Gen2
- Full and incremental data loading
- CSV and JSON file integration
- SQL and booking-data exploration
- GitHub-based project versioning and documentation
Future Enhancements
Potential extensions, if implemented and tested, include:
- Parameterise file paths and environment-specific settings.
- Add data-quality checks for nulls, duplicates, schema changes, and
  row counts.
- Add explicit failure handling, retry policies, and operational
  logging.
- Document incremental-load logic and make reruns safe.
- Add a clear architecture diagram and screenshots of successful runs.
- Extend the project with Azure Databricks, PySpark, and Delta Lake to
  build a broader data engineering workflow.
