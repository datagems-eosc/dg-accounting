# Data Stores

The service functions as an aggregator of logging events from the platform services. The aggregated information needs to be stored in a manner that allows ad-hoc aggregating for reposting needs. It also requires operation metadata to be available and managed within the service.

## Relational Database

The primary data store for the service operational metadata is a PostgreSQL hosted relational database. 

## Event Datastore

The accountable event data is stored in a NoSQL Elastic Search datastore. 

## Filesystem

For the generation of file based reports, a filesystem mount point can be used to keep the generated files temporarily. No critical or long preservation data is kept in this datastore.

## Updates

When updating the Accounting service to newer versions, any needed database updates are handled by the migration process of the Accounting service.
