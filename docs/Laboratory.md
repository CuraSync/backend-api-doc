## **Register**

#### **Endpoint:**

```
POST /laboratory/register
```

#### **Request Body:**

```json
{
  "labId": "LAB-2025001",
  "labName": "Advanced Diagnostic Center",
  "location": {
    "street": "456 Maple Avenue",
    "city": "Los Angeles",
    "state": "CA",
    "zipCode": "90001",
    "country": "USA"
  },
  "email": "contact@advanceddiagnostics.com",
  "password": "SecureLabPass123!",
  "contactNo": "+1-555-6789-123",
  "GovRegId": "GOV-987654321",
  "description": "A state-of-the-art diagnostic laboratory offering comprehensive medical testing services.",
  "profilePic": "https://example.com/uploads/lab-profile.jpg",
  "socialMediaLinks": {
    "linkedin": "https://www.linkedin.com/in/####",
    "twitter": "https://twitter.com/####"
  },
}
```

#### **Response:**

- **Success (200):**
    - When register is successful and return the Laboratory Id:

```json
{
    "message": "Successfully Registered",
    "id": "L12345"
}
```

- **Missing Required Fields (400):**
    - If the required field is missing:
    - Status Code: `400 Bad Request`

```json
  {
    "message": "The <field> field is required."
  }
```

- **Fields Invalid Format (400):**
    - If the required field is invalid:
    - Status Code: `400 Bad Request`

```json
  {
    "message": "Invalid <field>. Please provide valid <field>."
  }
```

- **Duplicate Field (409):**
    - If the unique fields like nicNo, govRegNo, email is already in the database:
    - Status Code: `409 Conflict`

```json
  {
    "message": "The <field> is already in use."
  }
```

- **Data Type Mismatch (422):**
    - If the dataType send was incorrect:
    - Status Code: `422 Unprocessable Entity`

```json
  {
    "message": "The <field> field must be <dataType>."
  }
```

- **Internal Server Error (500):**
    - If there’s an unexpected error on the server:
    - Status Code: `500 Internal Server Error`

```json
  {
    "message": "Internal server error"
  }
```
<br/>

## **Get data that required in the laboratory's home page**

#### **Endpoint:**

```
GET /laboratory/home
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Response:**

- **Success (200):**
    - Successfully returned data:

```json
{
  "labId": "LAB-2025001",
  "labName": "Advanced Diagnostic Center",
  "location": {
    "street": "456 Maple Avenue",
    "city": "Los Angeles",
    "state": "CA",
    "zipCode": "90001",
    "country": "USA"
  },
  "email": "contact@advanceddiagnostics.com",
  "contactNo": "+1-555-6789-123",
  "GovRegId": "GOV-987654321",
  "description": "A state-of-the-art diagnostic laboratory offering comprehensive medical testing services.",
  "profilePic": "https://example.com/uploads/lab-profile.jpg",
  "socialMediaLinks": {
    "linkedin": "https://www.linkedin.com/in/####",
    "twitter": "https://twitter.com/####"
  },
  "patientsCount": 20
}
```

- **User not found (404):**
    - If user not found in the database:
    - Status Code: `404 Not Found`

```json
  {
    "message": "User not found"
  }
```

- **Invalid Credentials (401):**
    - If the provided JWT token invalid:
    - Status Code: `401 Unauthorized`

```json
  {
    "message": "Invalid token"
  }
```

- **Internal Server Error (500):**
    - If there’s an unexpected error on the server:
    - Status Code: `500 Internal Server Error`

```json
  {
    "message": "Internal server error"
  }
```

<br/>

## **Get patient's list to the frontend patient’s list page**

#### **Endpoint:**

```
GET /laboratory/patients
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Response:**

- **Success (200):**
    - Successfully returned patients list:

```json
[
  {
    "patientId": "Pa2045",
    "lastMessage": "2025/02/10"
  },
  {
    "patientId": "Pa2046",
    "lastMessage": "2025/01/15"
  },
  {
    "patientId": "Pa2047",
    "lastMessage": "2025/02/05"
  },
  {
    "patientId": "Pa2048",
    "lastMessage": "2025/01/20"
  },
  {
    "patientId": "Pa2049",
    "lastMessage": "2025/02/01"
  }
]

```

- **User not found (404):**
    - If user not found in the database:
    - Status Code: `404 Not Found`

```json
  {
    "message": "User not found"
  }
```

- **Invalid Credentials (401):**
    - If the provided JWT token invalid:
    - Status Code: `401 Unauthorized`

```json
  {
    "message": "Invalid token"
  }
```

- **Internal Server Error (500):**
    - If there’s an unexpected error on the server:
    - Status Code: `500 Internal Server Error`

```json
  {
    "message": "Internal server error"
  }
```