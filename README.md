# Data Contract GPT

[Data Contract GPT](https://chatgpt.com/g/g-QGMQrqm3p-data-contract-gpt) for the [Data Contract Specification](https://datacontract.com)

[![Data Contract GPT Browser Window](/images/datacontract-gpt-browser.png){: width="100%"}](https://chatgpt.com/g/g-QGMQrqm3p-data-contract-gpt)

## Create an initial data contract for your domain

[Open Example in Data Contract GPT (Requires free ChatGPT account)](https://chatgpt.com/share/9695cd45-0352-4d9a-bae2-6ee1b236a1a0)

> **User**
> 
> Create a data contract for data in the logistics domain for my table shipments in Snowflake.

> **Data Contract GPT**
>
> ```yaml
> dataContractSpecification: "0.9.3"
> id: "logistics_shipments_001"
> info:
>   title: "Logistics Shipments"
>   version: "1.0.0"
>   status: "active"
>   description: "Data contract for the shipments table in the logistics domain."
>   owner: "Logistics Team"
> ...
> ```

## Create a data contract from example data

[Open Example in Data Contract GPT (Requires free ChatGPT account)](https://chatgpt.com/share/82614125-2152-4603-b52d-03619e59699e)

> **User**
> 
> *Upload [example data](example_shipment.yaml) to ChatGPT*
> 
> Create a data contract for the uploaded example data.

> **Data Contract GPT**
>
> ```yaml
> dataContractSpecification: "0.9.3"
> id: "shipment-data-contract"
> info:
>   title: "Shipment Data Contract"
>   version: "1.0.0"
>   status: "active"
>   description: |
>     This data contract defines the structure and requirements for shipment data, including details 
>     about the shipment ID, order ID, shipping address, shipment date, and delivery date.
>   owner: "Logistics Team"
> ...
> ```

## Extend an existing data contract interactively

[Open Example in Data Contract GPT (Requires free ChatGPT account)](https://chatgpt.com/share/fc3486e4-c289-4314-8e29-e1ea26b744dd)

> **User**
> 
> *Paste [example contract](example_datacontract.yaml) into prompt*
> 
> Add new field location to this data contract.

> **Data Contract GPT**
> 
> ```yaml
> ...
> models:
>   shipments:
>     fields:
>       location:
>         type: "string"
>         description: "Current location of the shipment."
> ...
> examples:
>   - type: "json"
>     model: "shipments"
>     data:
>     - shipment_id: "SHIP12345"
>       ...
>       location: "San Francisco, CA"
> ...
> ```

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
>  ...
>  ```

## You have even better prompt ideas?

Help others and contribute your great prompt ideas to this repository.
