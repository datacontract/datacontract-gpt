# Data Contract GPT

[Data Contract GPT](https://chatgpt.com/g/g-QGMQrqm3p-data-contract-gpt) for the [Data Contract Specification](https://datacontract.com)

[![](/images/browser.png){: width="60%"}](https://chatgpt.com/g/g-QGMQrqm3p-data-contract-gpt)

## Create an initial data contract for your domain

[Open Example in Data Contract GPT](https://chatgpt.com/share/e/515633e9-2bbd-472a-8244-29430f107cda)

> **User**
> 
> Create a data contract for data in the logistics domain for my table shipments in Snowflake.

> **Data Contract GPT**
> 
> YAML of a data contract

## Create a data contract from example data

[Open Example in Data Contract GPT](https://chatgpt.com/share/e/1b27cab6-6ea8-49ff-8c8e-d1765fb34dd9)

> **User**
> 
> *Upload [example data](example_shipment.yaml) to ChatGPT*
> 
> Create a data contract for the uploaded example data.

> **Data Contract GPT**
>
> YAML of a data contract

## Extend an existing data contract interactively

[Open Example in Data Contract GPT](https://chatgpt.com/share/e/6079bdf8-3b9b-477a-ba4f-93a0dee4e6dc)

> **User**
> 
> Add new field location to this data contract.
> 
> *Paste contents of example_datacontract.yaml into prompt*

> **Data Contract GPT**
> 
> YAML of the data contract with the location field

> **User**
>
> Can you give recommendations for the service levels?

> **Data Contract GPT**
>
> ```yaml
>  servicelevels:
>    availability:
>      description: "The server is available 24/7 with a guaranteed uptime."
>      percentage: "99.9%"
>    retention:
>      description: "Data is retained for one year from the shipment date."
>      period: "P1Y"
>    latency:
>      description: "Data is available within 24 hours after the shipment is processed."
>      threshold: "PT24H"
>      sourceTimestampField: "shipped_date"
>      processedTimestampField: "delivery_date"
>    freshness:
>      description: "The data for shipments is updated daily to ensure accuracy."
>      threshold: "P1D"
>      timestampField: "shipped_date"
>    frequency:
>      description: "Data is updated in batches once a day."
>      type: "batch"
>      interval: "daily"
>      cron: "0 0 * * *"
>    support:
>      description: "Support is available during business hours."
>      time: "9am to 5pm in EST on business days"
>      responseTime: "24 hours"
>    backup:
>      description: "Data is backed up weekly, every Sunday at 0:00 UTC."
>      interval: "weekly"
>      cron: "0 0 * * 0"
>      recoveryTime: "24 hours"
>      recoveryPoint: "1 week"
>  ```
