# API Documentation: Retrieve Sensor Data

## Endpoint

- **URL:** `/api/getPlantData`
- **Method:** `GET`

## Query Parameters

| Parameter          | Type    | Description                                                      | Example           |
|--------------------|---------|------------------------------------------------------------------|-------------------|
| `plant`            | string  | The name of the plant field in the database (default: `test_plant`). | `test_plant`      |
| `startTs`          | number  | Start timestamp for filtering data. Must be a UNIX timestamp.   | `1653675600000`   |
| `endTs`            | number  | End timestamp for filtering data. Must be a UNIX timestamp.     | `1653762000000`   |
| `sensorType`       | string  | Type of sensor to filter data.                                    | `temperature`     |
| `minSensorValue`   | number  | Minimum value of the sensor to filter data.                     | `10`              |
| `maxSensorValue`   | number  | Maximum value of the sensor to filter data.                     | `50`              |
| `sensorUnit`       | string  | Unit of the sensor to filter data.                               | `Celsius`         |
| `page`             | number  | Page number for pagination (default: 1).                         | `2`               |
| `limit`            | number  | Number of documents per page for pagination (default: 50).        | `20`              |

## Responses

### Success

- **Status Code:** `200 OK`
- **Content:**

```json
{
    "data": [
        {
            "_id": "64a9b6d2f7d4f0001c0a8c0a",
            "test_plant": {
                "ts": 1653675600000,
                "sensors": [
                    {
                        "type": "temperature",
                        "value": 22.5,
                        "unit": "Celsius"
                    },
                    {
                        "type": "humidity",
                        "value": 60,
                        "unit": "%"
                    }
                ]
            }
        },
        // More data objects
    ],
    "meta": {
        "totalDocuments": 100,
        "currentPage": 1,
        "totalPages": 2,
        "limit": 50
    }
}
