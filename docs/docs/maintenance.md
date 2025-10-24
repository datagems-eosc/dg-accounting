# Maintenance

The service is part of the DataGEMS platform offered through an existing deployment, following the DataGEMS release and deployment procedures over a managed infrasrtucture along with the maintenance activities that are scheduled within the platform. The purpose of this section is not to detail the maintenance activities put in place by the DataGEMS team.

## Healthchecks

The service does not offer an explicit healthcheck endpoint but there are endpoints that serve the purpose. The version check endpoint offered by the Accounting service can be used to track the status of the service. 

An example response that returns 200 OK for healthy state is:
```json
[
    {
        "key": "DB.Core",
        "version": "00.04.000",
        "deployedAt": "2025-09-10T06:38:52.466482Z"
    }
]
```

## Verions & Updates

The service follows the versioning and update scheme (Semantic Versions) that the [Accounting service](https://github.com/datagems-eosc/dg-accounting) supports.

## Backups

All operational state persisted by the service is maintained in the relational database while accounting events are stored in an Elastic Search index as described in the respective [datastores](datastore.md) section.

To keep backups of the state, the respective utilities must be scheduled to run in a consistent manner. 

## Troubleshooting

Troubleshooting is primarily done through the logging mechanisms that are available and are described in the respective [logging](logging.md) section.