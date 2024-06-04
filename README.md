# Data Contract GPT

<p>
  <a href="https://datacontract.com/slack" rel="nofollow"><img src="https://camo.githubusercontent.com/5ade1fd1e76a6ab860802cdd2941fe2501e2ca2cb534e5d8968dbf864c13d33d/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f736c61636b2d6a6f696e5f636861742d77686974652e7376673f6c6f676f3d736c61636b267374796c653d736f6369616c" alt="Slack Status" data-canonical-src="https://img.shields.io/badge/slack-join_chat-white.svg?logo=slack&amp;style=social" style="max-width: 100%;"></a>
</p>

[Data Contract GPT](https://chatgpt.com/g/g-QGMQrqm3p-data-contract-gpt) for the [Data Contract Specification](https://datacontract.com) to create data contracts from your example data, chat with your data contracts, or export in other formats. And yes, we know that GPTs can be wrong. That's why we also offer a [deterministic open source tool around data contracts written in Python](https://cli.datacontract.com).

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

Help others and contribute your great prompt ideas to [datacontract-gpt repository](https://github.com/datacontract/datacontract-gpt).

## Credits

Created by [Simon Harrer](https://www.linkedin.com/in/simonharrer/) and [Jochen Christ](https://www.linkedin.com/in/jochenchrist/), with the help of many folks from INNOQ.


<a href="https://github.com/datacontract/datacontract-gpt" class="github-corner" aria-label="View source on GitHub"><svg width="80" height="80" viewBox="0 0 250 250" style="fill:#151513; color:#fff; position: absolute; top: 0; border: 0; right: 0;" aria-hidden="true"><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor" style="transform-origin: 130px 106px;" class="octo-arm"></path><path d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor" class="octo-body"></path></svg></a><style>.github-corner:hover .octo-arm{animation:octocat-wave 560ms ease-in-out}@keyframes octocat-wave{0%,100%{transform:rotate(0)}20%,60%{transform:rotate(-25deg)}40%,80%{transform:rotate(10deg)}}@media (max-width:500px){.github-corner:hover .octo-arm{animation:none}.github-corner .octo-arm{animation:octocat-wave 560ms ease-in-out}}</style>
