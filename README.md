# PikPoint API

API WooCommerce Plugin for Orders and Shipping Functionality


## Get Orders

| Method   | Description                              |
| -------- | ---------------------------------------- |
|   GET    |                                          |
| Headers  |          pikpoint-api-key                |

### Request

`/wp-json/pikpoint/v1/orders/`

### Response

    HTTP/1.1 200 OK
    Date: Thu, 24 Oct 2024 12:12:12 GMT
    Status: 200 OK
    Connection: close
    Content-Type: application/json
    Content-Length: 2

    [
        {
            "id": 14,
            "status": "pending",
            "total": "1.00",
            "billing": {
                "first_name": "Test",
                "last_name": "Test",
                "company": "",
                "address_1": "Miramonte St",
                "address_2": "",
                "city": "Cebu",
                "state": "",
                "postcode": "6000",
                "country": "",
                "email": "web2.loyd+test2@gmail.com",
                "phone": ""
            },
            "pikpointng": {
                "first_name": "Test",
                "last_name": "test",
                "company": "",
                "address_1": "",
                "address_2": "",
                "city": "",
                "state": "",
                "postcode": "",
                "country": "",
                "phone": ""
            }
        }
    ]

## Update Order

| Method   | Description                              |
| -------- | ---------------------------------------- |
|  POST    |                                          |
| Headers  |        pikpoint-api-key (required)       |
|  POST    |           order_id (required)            |
|  POST    |           status (required)              |
|  POST    |        billing (array) (optional)        |
|  POST    |        shipping (array) (optional)       |
|  POST    |      custom_fields (array) (optional)    |

### Request

`/wp-json/pikpoint/v1/orders/update`

#### Example

    {
        "order_id": 14,
        "status": "on-hold",
        "billing": {
            "first_name": "Test",
            "last_name": "Testing",
            "address_1": "1234 Example St",
            "city": "Los Angeles",
            "postcode": "90001"
        },
        "pikpointng": {
            "first_name": "Test",
            "last_name": "Testing",
            "address_1": "1234 Example St",
            "city": "Los Angeles",
            "postcode": "90001"
        },
        "custom_fields": {
            "custom_note": "Please leave the package at the door."
        },
        "send_details": false
    }

### Response

    HTTP/1.1 200 OK
    Date: Thu, 24 Oct 2024 12:12:12 GMT
    Status: 200 OK
    Connection: close
    Content-Type: application/json
    Content-Length: 2

    {
        "message": "Order updated successfully."
    }

## Add pikpointng Zone

| Method   | Description                              |
| -------- | ---------------------------------------- |
|  POST    |                                          |
| Headers  |        pikpoint-api-key (required)       |
|  POST    |          zone_name (required)            |
|  POST    |        regions (array) (required)        |

### Request

`/wp-json/pikpoint/v1/pikpointng/zone/add`

#### Example

    {
        "zone_name": "Sample Zone",
        "regions": [
            "US",
            "CA"
        ]
    }

### Response

    HTTP/1.1 200 OK
    Date: Thu, 24 Oct 2024 12:12:12 GMT
    Status: 200 OK
    Connection: close
    Content-Type: application/json
    Content-Length: 2

    {
        "message": "pikpointng zone created successfully",
        "zone_id: 2
    }

## Add pikpointng Method

| Method   | Description                              |
| -------- | ---------------------------------------- |
|  POST    |                                          |
| Headers  |        pikpoint-api-key (required)       |
|  POST    |          zone_id (required)              |
|  POST    |         method_id (required)             |
|  POST    |           cost (optional)                |

### Request

`/wp-json/pikpoint/v1/pikpointng/method/add`

#### Example

    {
        "zone_id": 14,
        "method_id": 1,
        "cost": 10.00
    }

### Response

    HTTP/1.1 200 OK
    Date: Thu, 24 Oct 2024 12:12:12 GMT
    Status: 200 OK
    Connection: close
    Content-Type: application/json
    Content-Length: 2

    {
        "message": "pikpointng method added successfully",
        "method_id: "free pikpointng"
    }
