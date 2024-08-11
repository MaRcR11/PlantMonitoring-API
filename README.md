# API Documentation: Retrieve Sensor Data

## Endpoint

- **URL:** `/api/getPlantData`
- **Method:** `GET`

## Query Parameters

| Parameter          | Type    | Description                                                      | Example           |
|--------------------|---------|------------------------------------------------------------------|-------------------|
| `plant`            | string  | The name of the plant field in the database. | `test_plant`      |
| `startTs`          | number  | Start timestamp for filtering data. Must be a UNIX timestamp.   | `1653675600000`   |
| `endTs`            | number  | End timestamp for filtering data. Must be a UNIX timestamp.     | `1653762000000`   |
| `sensorType`       | string  | Type of sensor to filter data.                                    | `temperature`     |
| `minSensorValue`   | number  | Minimum value of the sensor to filter data.                     | `10`              |
| `maxSensorValue`   | number  | Maximum value of the sensor to filter data.                     | `50`              |
| `sensorUnit`       | string  | Unit of the sensor to filter data.                               | `°C`              |
| `page`             | number  | Page number for pagination (default: 1).                         | `2`               |
| `limit`            | number  | Number of documents per page for pagination (default: 100).      | `20`              |

## Responses

### Success

- **Status Code:** `200 OK`
- **Content:**

```json
{
    "data": [
        {
            "plantName": "test_plant_1",
            "measurements": [
                {
                    "ts": 1723220739.149128,
                    "sensors": [
                        {
                            "type": "temperature",
                            "value": 15.1,
                            "unit": "°C"
                        },
                        {
                            "type": "humidity",
                            "value": 52.2,
                            "unit": "%"
                        },
                        {
                            "type": "pressure",
                            "value": 99801.3,
                            "unit": "Pa"
                        }
                    ]
                },
                {
                    "ts": 1723220799.149128,
                    "sensors": [
                        {
                            "type": "temperature",
                            "value": 15.1,
                            "unit": "°C"
                        },
                        {
                            "type": "humidity",
                            "value": 52.3,
                            "unit": "%"
                        },
                        {
                            "type": "pressure",
                            "value": 99801.4,
                            "unit": "Pa"
                        }
                         // More sensor objects
                    ]
                }
                // More measurement objects
            ]
        }
        // More plant data objects
    ],
    "meta": {
        "totalDocuments": 4,
        "totalMeasurements": 200,
        "currentPage": 1,
        "totalPages": 2,
        "limit": 100
    }
}
