# Data Contract GPT

[Data Contract GPT](https://chatgpt.com/g/g-QGMQrqm3p-data-contract-gpt) for the [Data Contract Specification](https://datacontract.com)

## Create an initial data contract for your domain

[Example](https://chatgpt.com/share/e/515633e9-2bbd-472a-8244-29430f107cda)

> Create a data contract for data in the logistics domain for my table shipments in Snowflake.

```yaml
dataContractSpecification: "0.9.3"
id: "logistics-shipments"
info:
  title: "Shipments Data Contract"
  version: "1.0.0"
  status: "active"
  description: "Data contract for shipments table in the logistics domain."
  owner: "Logistics Team"
  contact:
    name: "Logistics Support"
    email: "support@logistics.com"
servers:
  snowflake:
    type: "snowflake"
    account: "your_snowflake_account"
    database: "logistics_db"
    schema: "public"
models:
  shipments:
    description: "Details of shipments handled by the logistics department."
    type: "table"
    fields:
      shipment_id:
        description: "Unique identifier for each shipment."
        type: "string"
        primary: true
        required: true
        maxLength: 36
      origin:
        description: "Origin location of the shipment."
        type: "string"
        required: true
        maxLength: 255
      destination:
        description: "Destination location of the shipment."
        type: "string"
        required: true
        maxLength: 255
      shipment_date:
        description: "Date when the shipment was sent."
        type: "timestamp_ntz"
        required: true
      delivery_date:
        description: "Date when the shipment was delivered."
        type: "timestamp_ntz"
      status:
        description: "Current status of the shipment."
        type: "string"
        enum: ["pending", "in_transit", "delivered", "canceled"]
        required: true
        example: "pending"
quality:
  type: "SodaCL"
  specification: |
    checks for shipments:
      - schema:
          fail:
            when schema changes
      - valid_values:
          column: status
          values: ["pending", "in_transit", "delivered", "canceled"]
      - missing_count:
          column: shipment_id
          fail: "> 0"
      - valid_length:
          column: shipment_id
          min: 36
          max: 36
      - missing_count:
          column: origin
          fail: "> 0"
      - missing_count:
          column: destination
          fail: "> 0"
      - missing_count:
          column: shipment_date
          fail: "> 0"
examples:
  - type: "yaml"
    description: "Example shipment data"
    model: "shipments"
    data:
      - shipment_id: "123e4567-e89b-12d3-a456-426614174000"
        origin: "New York, NY"
        destination: "Los Angeles, CA"
        shipment_date: "2024-01-01T10:00:00Z"
        delivery_date: "2024-01-05T15:00:00Z"
        status: "delivered"
```

## Create a data contract from example data

[Example](https://chatgpt.com/share/e/1b27cab6-6ea8-49ff-8c8e-d1765fb34dd9)

Upload example data.

> Create a data contract for the uploaded example data.

```yaml
dataContractSpecification: "0.9.3"
id: "shipment-data-contract"
info:
  title: "Shipment Data Contract"
  version: "1.0.0"
  status: "active"
  description: "Data contract for shipment information."
  owner: "Logistics Team"
  contact:
    name: "Logistics Support"
    email: "logistics-support@example.com"
servers:
  S3:
    type: "s3"
    location: "s3://logistics-data/shipments"
    format: "json"
models:
  shipments:
    description: "Details of each shipment."
    type: "table"
    fields:
      shipment_id:
        type: "string"
        description: "Unique identifier for the shipment."
        primary: true
        required: true
      sender:
        type: "string"
        description: "Name of the sender."
        required: true
      recipient:
        type: "string"
        description: "Name of the recipient."
        required: true
      origin:
        type: "string"
        description: "Origin location of the shipment."
        required: true
      destination:
        type: "string"
        description: "Destination location of the shipment."
        required: true
      weight:
        type: "decimal"
        description: "Weight of the shipment in kilograms."
        precision: 10
        scale: 2
        required: true
      shipped_date:
        type: "timestamp"
        description: "Date and time when the shipment was sent."
        required: true
      delivery_date:
        type: "timestamp"
        description: "Date and time when the shipment was delivered."
      status:
        type: "string"
        description: "Current status of the shipment."
        enum: ["pending", "shipped", "in_transit", "delivered", "canceled"]
        required: true
examples:
  - type: "json"
    model: "shipments"
    data:
      - shipment_id: "SHIP12345"
        sender: "Company A"
        recipient: "Customer B"
        origin: "New York, NY"
        destination: "San Francisco, CA"
        weight: 15.75
        shipped_date: "2023-06-01T10:00:00Z"
        delivery_date: "2023-06-03T15:30:00Z"
        status: "delivered"
  - type: "json"
    model: "shipments"
    data:
      - shipment_id: "SHIP12346"
        sender: "Company C"
        recipient: "Customer D"
        origin: "Los Angeles, CA"
        destination: "Seattle, WA"
        weight: 5.20
        shipped_date: "2023-06-01T11:00:00Z"
        status: "in_transit"
quality:
  type: "SodaCL"
  specification: |
    checks for shipments:
      - schema:
          fail:
            when required column missing:
              - shipment_id
              - sender
              - recipient
              - origin
              - destination
              - weight
              - shipped_date
              - status
      - values in shipment_id:
          must not be null:
            fail:
              count: 1
      - values in weight:
          must not be null:
            fail:
              count: 1
          must be between 0 and 1000:
            fail:
              count: 1
      - values in status:
          must be in:
            - pending
            - shipped
            - in_transit
            - delivered
            - canceled
```

## Extend an existing data contract interactively

[Example](https://chatgpt.com/share/e/6079bdf8-3b9b-477a-ba4f-93a0dee4e6dc)

> Add new field location to this data contract.
> 
> PASTE DATA CONTRACT YAML HERE

```yaml
dataContractSpecification: "0.9.3"
id: "shipment-data-contract"
info:
  title: "Shipment Data Contract"
  version: "1.0.0"
  status: "active"
  description: "Data contract for shipment information."
  owner: "Logistics Team"
  contact:
    name: "Logistics Support"
    email: "logistics-support@example.com"
servers:
  S3:
    type: "s3"
    location: "s3://logistics-data/shipments"
    format: "json"
models:
  shipments:
    description: "Details of each shipment."
    type: "table"
    fields:
      shipment_id:
        type: "string"
        description: "Unique identifier for the shipment."
        primary: true
        required: true
      sender:
        type: "string"
        description: "Name of the sender."
        required: true
      recipient:
        type: "string"
        description: "Name of the recipient."
        required: true
      origin:
        type: "string"
        description: "Origin location of the shipment."
        required: true
      destination:
        type: "string"
        description: "Destination location of the shipment."
        required: true
      weight:
        type: "decimal"
        description: "Weight of the shipment in kilograms."
        precision: 10
        scale: 2
        required: true
      shipped_date:
        type: "timestamp"
        description: "Date and time when the shipment was sent."
        required: true
      delivery_date:
        type: "timestamp"
        description: "Date and time when the shipment was delivered."
      status:
        type: "string"
        description: "Current status of the shipment."
        enum: ["pending", "shipped", "in_transit", "delivered", "canceled"]
        required: true
      location:
        type: "string"
        description: "Current location of the shipment."
examples:
  - type: "json"
    model: "shipments"
    data:
      - shipment_id: "SHIP12345"
        sender: "Company A"
        recipient: "Customer B"
        origin: "New York, NY"
        destination: "San Francisco, CA"
        weight: 15.75
        shipped_date: "2023-06-01T10:00:00Z"
        delivery_date: "2023-06-03T15:30:00Z"
        status: "delivered"
        location: "Warehouse 5"
  - type: "json"
    model: "shipments"
    data:
      - shipment_id: "SHIP12346"
        sender: "Company C"
        recipient: "Customer D"
        origin: "Los Angeles, CA"
        destination: "Seattle, WA"
        weight: 5.20
        shipped_date: "2023-06-01T11:00:00Z"
        status: "in_transit"
        location: "En route to Seattle"
quality:
  type: "SodaCL"
  specification: |
    checks for shipments:
      - schema:
          fail:
            when required column missing:
              - shipment_id
              - sender
              - recipient
              - origin
              - destination
              - weight
              - shipped_date
              - status
      - values in shipment_id:
          must not be null:
            fail:
              count: 1
      - values in weight:
          must not be null:
            fail:
              count: 1
          must be between 0 and 1000:
            fail:
              count: 1
      - values in status:
          must be in:
            - pending
            - shipped
            - in_transit
            - delivered
            - canceled
```

> Can you give recommendations for the service levels?

```yaml
servicelevels:
  availability:
    description: "The server is available 24/7 with a guaranteed uptime."
    percentage: "99.9%"
  retention:
    description: "Data is retained for one year from the shipment date."
    period: "P1Y"
  latency:
    description: "Data is available within 24 hours after the shipment is processed."
    threshold: "PT24H"
    sourceTimestampField: "shipped_date"
    processedTimestampField: "delivery_date"
  freshness:
    description: "The data for shipments is updated daily to ensure accuracy."
    threshold: "P1D"
    timestampField: "shipped_date"
  frequency:
    description: "Data is updated in batches once a day."
    type: "batch"
    interval: "daily"
    cron: "0 0 * * *"
  support:
    description: "Support is available during business hours."
    time: "9am to 5pm in EST on business days"
    responseTime: "24 hours"
  backup:
    description: "Data is backed up weekly, every Sunday at 0:00 UTC."
    interval: "weekly"
    cron: "0 0 * * 0"
    recoveryTime: "24 hours"
    recoveryPoint: "1 week"
```
