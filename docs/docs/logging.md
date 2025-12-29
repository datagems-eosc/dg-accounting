# Logging

All DataGEMS services are producing logs in a structured way, usilizing common log formats. The logs are aggregated to the [Logging Service](https://datagems-eosc.github.io/dg-logging-service) where they can be queried and analyzed.

## Log format

The service utilized serilog for structured logging. The respective [Configuration](configuration.md) section describes where this is configured. 

The log format utilized by is compact json providing structured presentation of the information presented. This is easily parsed and made available for further processing.

## Troubleshooting Logs

Troubleshooting logs are produced by the service throughout the execution of caller requests. The messages are separated by the log level:

* Trace
* Debug
* Information
* Warning
* Error
* Critical

Log entries may contain the following information (where available):

* Timestamp in UTC (ISO8601)
* Subject Id
* Client Id
* Message text
* Log Level
* ... additional properties

## Accounting Logs

The service generates accounting entries that utilize the same logging mechanism but are differentiated by troubleshooting logs through the "SourceContext" property which is set to "accounting".

These accounting log entries are harvested and processed by the [Accounting Service](https://datagems-eosc.github.io/dg-accounting-service). So, any accounting events generated within the accounting service are again visible through the same service.
