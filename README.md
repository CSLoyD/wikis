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
            "delivery_details": {
                "shipping_name": "Sample Test",
                "shipping_address": {
                    "first_name": "Sample",
                    "last_name": "Test",
                    "company": "",
                    "address_1": "Mabolo Street",
                    "address_2": "",
                    "city": "Cebu City",
                    "state": "CEB",
                    "postcode": "6000",
                    "country": "PH",
                    "phone": "281271416187"
                },
                "notes": "",
                "phone": "281271416187",
                "email": "web2.loyd+test2@gmail.com"
            },
            "fulfillment_details": {
                "id": 24,
                "status": "processing",
                "total": {
                    "amount": "20",
                    "currency": "ZAR"
                },
                "created": {
                    "date": "2024-11-04 14:16:08.000000",
                    "timezone_type": 1,
                    "timezone": "+00:00"
                }
            }
        },
        {
            "delivery_details": {
                "shipping_name": "Sample Test",
                "shipping_address": {
                    "first_name": "Sample",
                    "last_name": "Test",
                    "company": "",
                    "address_1": "Mabolo Street",
                    "address_2": "",
                    "city": "Cebu City",
                    "state": "CEB",
                    "postcode": "6000",
                    "country": "PH",
                    "phone": "812145116162"
                },
                "notes": "",
                "phone": "812145116162",
                "email": "web2.loyd+test2@gmail.com"
            },
            "fulfillment_details": {
                "id": 23,
                "status": "processing",
                "total": {
                    "amount": "20",
                    "currency": "ZAR"
                },
                "created": {
                    "date": "2024-11-04 13:30:52.000000",
                    "timezone_type": 1,
                    "timezone": "+00:00"
                }
            }
        },
        {
            "delivery_details": {
                "shipping_name": "Sample Test",
                "shipping_address": {
                    "first_name": "Sample",
                    "last_name": "Test",
                    "company": "",
                    "address_1": "Miramonte St",
                    "address_2": "",
                    "city": "Cebu",
                    "state": "CEB",
                    "postcode": "6000",
                    "country": "PH",
                    "phone": "9091238123"
                },
                "notes": "",
                "phone": "9091238123",
                "email": "web2.loyd+test2@gmail.com"
            },
            "fulfillment_details": {
                "id": 16,
                "status": "processing",
                "total": {
                    "amount": "0",
                    "currency": "PHP"
                },
                "created": {
                    "date": "2024-10-27 12:29:51.000000",
                    "timezone_type": 1,
                    "timezone": "+00:00"
                }
            }
        },
        {
            "delivery_details": {
                "shipping_name": "Test Sample",
                "shipping_address": {
                    "first_name": "Test",
                    "last_name": "Sample",
                    "company": "Testing",
                    "address_1": "Sample Address",
                    "address_2": "",
                    "city": "Cebu",
                    "state": "",
                    "postcode": "6000",
                    "country": "PH",
                    "phone": ""
                },
                "notes": "",
                "phone": "123148148",
                "email": "web2.loyd+test2@gmail.com"
            },
            "fulfillment_details": {
                "id": 13,
                "status": "processing",
                "total": {
                    "amount": "100",
                    "currency": "PHP"
                },
                "created": {
                    "date": "2024-10-27 09:01:36.000000",
                    "timezone_type": 1,
                    "timezone": "+00:00"
                }
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
        "shipping": {
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

## Add Shipping Zone

| Method   | Description                              |
| -------- | ---------------------------------------- |
|  POST    |                                          |
| Headers  |        pikpoint-api-key (required)       |
|  POST    |          zone_name (required)            |
|  POST    |        regions (array) (required)        |

### Request

`/wp-json/pikpoint/v1/shipping/zone/add`

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
        "message": "shipping zone created successfully",
        "zone_id: 2
    }

## Add Shipping Method

| Method   | Description                              |
| -------- | ---------------------------------------- |
|  POST    |                                          |
| Headers  |        pikpoint-api-key (required)       |
|  POST    |          zone_id (required)              |
|  POST    |         method_id (required)             |
|  POST    |           cost (optional)                |

### Request

`/wp-json/pikpoint/v1/shipping/method/add`

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
        "message": "shipping method added successfully",
        "method_id: "free shipping"
    }
