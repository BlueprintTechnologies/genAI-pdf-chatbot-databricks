# Before You Get Started
## Medallion Architecture
Although not required, it would be helpful to be familiar with the medallion architecture used in a lakehouse. The layers in the architecture are referred to as bronze, silver, and gold. However, your organization may utilize different terminology. You can learn more about the medallion architecture [here](https://www.databricks.com/glossary/medallion-architecture).
![Image of medallion architecture](https://cms.databricks.com/sites/default/files/inline-images/building-data-pipelines-with-delta-lake-120823.png)

## About This Accelerator
This accelerator is self-contained. 
1. No third party services are used. Everything, including your data, stays within your Databricks workspace.
2. Although your workspace must attached to a Unity Catalog metastore, this accelerator generates the catalog, schema, tables and volumes for you.
2. This accelerator leverages a managed volume in Unity Catalog. External storage does not have to be defined.
3. No cluster init scripts are used.
4. All code is displayed in the notebooks.

## Databricks Prerequisites
- The workspace must be attached to a Unity Catalog metastore. For help on this, see https://docs.databricks.com/en/data-governance/unity-catalog/get-started.html.
- Serverless compute enabled.
- Personal access tokens must be enabled. For more information on this, see https://docs.databricks.com/en/administration-guide/access-control/tokens.html
- Access to Databricks Foundation Model APIs. For more information on this, see https://docs.databricks.com/en/machine-learning/foundation-models/index.html.

## Recommended Compute
The Databricks workspace used to test this accelerator is in the West US 2 region. 
- Compute policy: `unrestricted`
- Databricks Runtime: `14.3 LTS ML`
- Worker type: `Standard_DS3_v2`
- Min workers: `1`
- Max workers: `2`
- Autoscaling: `yes`
- Photon acceleration: `no`
- Termination period: `10 minutes`

# Optimization
During the course of building out this accelerator, we made heavy use of the [Lakehouse Optimizer (LHO)](https://azuremarketplace.microsoft.com/en/marketplace/apps/blueprint-consulting-services-llc.lakehouse-monitor?tab=overview) to analyze our compute performance and orchestration. 

Early on, based on back-of-napkin estimates, we had configured our compute worker for a minimum of 4 and maximum of 8. However, after evaluating the `CPU Process Load` and `Process Memory Load` KPIs in LHO, we adjusted our compute without a noticeable impact to performance.
