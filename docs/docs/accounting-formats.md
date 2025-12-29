# Accounting Overview

## Accounting Log Formats

Two accounting log formats are supported at this point. They are very similar but have been extended to support generic log entry construction rather than rely on specific implementation details of some logging library. A note to be repeated here, additonal properties, if they do not map to the Accounting Model are omited.

The format that the accounting service ingestion pipeline will expect for each component follows the formats that are available for the [DataGEMS Logging Service](https://datagems-eosc.github.io/dg-logging/latest/logging-overview/). So, if a component generates log entries of format **json-cf-1**, it is expected that they will also generate accounting entries of the format **json-cf-1**.

For the logging and accounting service to distinguish between the supported formats, the deployment of each component must be decorated with the log format that it produces.

### json-cf-1 format

**json-cf-1** is an accounting log format that expects the following information to be available in the log message:

```json
{
	"SourceContext": "accounting",
	"@mt": "{\"m\":{\"timestamp\":\"2025-11-12T13:50:41.9342204Z\",\"serviceId\":\"d...i\",\"action\":\"U...d\",\"resource\":\"D...t\",\"userId\":\"1...1\",\"value\":\"1\",\"measure\":\"Unit\",\"type\":\"+\"}}"
}
```

The accounting entry is contained as a serialized json in the **@mt** field


### json-cf-2 format

**json-cf-2** is an accounting log format that expects the following information to be available in the log message:

```json
{ 
	"SourceContext": "accounting",
	"UserId": "1...1",
	"Action": "U...d",
	"Resource": "D...t",
	"Type": "+",
	"Value": "1",
	"Measure": "Unit",
	"Timestamp": "2025-11-12T13:50:41.9342204Z"
}
```

Both formats carry the same information. It is important that the **SourceContext** property is set to "accounting" in order for the ingestion pipeline to differentiate the target of the log entry betwen troubleshooting logs and accounting entries
