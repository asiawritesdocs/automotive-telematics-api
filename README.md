# Automotive Telematics & Service API 🚗

This API allows developers to manage vehicle health data, track mileage, and maintain digital service records. It is designed for integration with fleet management software and consumer vehicle-tracking applications.

---

## 🔐 Authentication & Security

All requests must include a valid API Key in the request header. 

> **Warning:** To ensure your account stays secure, do not make your secret API key known on public sites and/or resources.

| Header | Value | Description |
| :--- | :--- | :--- |
| `Authorization` | `Bearer <API_KEY>` | **Required.** Your unique secret key. |
| `Content-Type` | `application/json` | **Required.** Tells the server we are sending JSON data. |

---

## 🛠 Service Record Management

### Replace a Service Record
The `PUT` endpoint allows the user to replace a service record for a specific day.

**Endpoint:** `PUT /v1/vehicle/service_records/{record_id}`

#### Request Body
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `date` | String | **Required.** The date of the car service (e.g., "04-13-2026"). |
| `service_type` | String | **Required.** The type of car service (e.g., "Oil Change"). |
| `mileage` | Integer | **Required.** Miles at time of service (e.g., "185000"). |
| `technician_notes` | String | **Optional.** Comments or concerns from the technician. |

> **Warning:** If a field isn't included in the `PUT` request, the data may get deleted or set to blank!

---

## 🛑 Error Handling

This API uses standard HTTP status codes to indicate the success or failure of a request.

| Status Code | Meaning | Description |
| :--- | :--- | :--- |
| `401` | Unauthorized | No valid API key provided. |
| `403` | Forbidden | You do not have permission to access this specific vehicle. |
| `422` | Unprocessable Entity | Missing a required field (e.g., `date`) or invalid data format. |

#### Example Error Response (422)
```json
{
  "error": "Missing Required Field",
  "message": "The field 'date' is required for this request.",
  "status_code": 422
}
```

### 📂 About This Documentation

This project was drafted as part of a technical writing portfolio to demonstrate proficiency in documenting CRUD operations, JSON data structures, and RESTful API security standards.
