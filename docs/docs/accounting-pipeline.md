# Accounting Overview

## Ingestion Pipeline

The accounting service offers HTTP API endpoints through which event ingestion can take place. For the purpose of the DataGEMS integration we have choosen a less intrucive approach for the integrating components that is also offered by the Logging Service.

We make use of the logging capabilities and the infrastructure and processes put in place for the [Logging Service](https://datagems-eosc.github.io/dg-logging). Integrating components can produce log entries that are explicitly marked to be interpreted as Accounting Entries. These entires are not picked up by the logging service aggregation mechanism but from a pipeline that explicitly picks them up, transforms and ingests them to the Accounting Service Elastic Search index.

Through the deployment model utilized, an agent will read the logs produced by each pod and will scan for entries marked as Accounting Events. A transformation step will apply any needed mutations to the log entry retrieved to match the accounting model expected by the accounting service. The trasformation can be customized based on specific deployment labels. A set of supported schemas is provided and each deployed service can declare the accounting event schema it conforms to. Based on this schema the transformation is applies. After the accounting entry model is transformed, enriched with environment metadata and generated, it is pushed to the accounting service datastore where it becomes available for aggregations.
