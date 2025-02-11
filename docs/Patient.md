## **Register**

#### **Endpoint:**

```
POST /patient/register
```

#### **Request Body:**

```json
{
  "patientId": "P-2025001",
  "name": {
    "firstname": "John",
    "middlename": "Michael",
    "lastname": "Doe"
  },
  "address": {
    "street": "123 Elm Street",
    "city": "New York",
    "state": "NY",
    "zipCode": "10001",
    "country": "USA"
  },
  "nicNo": "987654321V",
  "mobileNo": "+1-555-1234-567",
  "email": "johndoe@example.com",
  "password": "SecurePass123!",
  "birthOfDate": "1990-05-15",
  "GuardianName": "Jane Doe",
  "GuardianContactNo": "+1-555-9876-543",
  "GuardianEmail": "janedoe@example.com",
  "Weight": 75.5,
  "Height": 1.75,
  "BMI": 24.7, 
  "profilePic": "https://example.com/uploads/johndoe-profile.jpg"
}
```

#### **Response:**

- **Success (200):**
    - When register is successful and return the Patient Id:

```json
{
    "message": "Successfully Registered",
    "id": "Pa12345"
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
    - If the unique fields like nicNo, email is already in the database:
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

## **Get data that required in the patient's home page**

#### **Endpoint:**

```
GET /patient/home
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
  "patientId": "P-2025001",
  "name": {
    "firstname": "John",
    "middlename": "Michael",
    "lastname": "Doe"
  },
  "address": {
    "street": "123 Elm Street",
    "city": "New York",
    "state": "NY",
    "zipCode": "10001",
    "country": "USA"
  },
  "nicNo": "987654321V",
  "mobileNo": "+1-555-1234-567",
  "email": "johndoe@example.com",
  "birthOfDate": "1990-05-15",
  "GuardianName": "Jane Doe",
  "GuardianContactNo": "+1-555-9876-543",
  "GuardianEmail": "janedoe@example.com",
  "Weight": 75.5,
  "Height": 1.75,
  "BMI": 24.7, 
  "profilePic": "https://example.com/uploads/johndoe-profile.jpg",
  "doctorsCount": 20
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

## **Get doctor's list to the frontend doctor's list page**

#### **Endpoint:**

```
GET /patient/doctors
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Response:**

- **Success (200):**
    - Successfully returned doctor list:

```json
[
  {
    "doctorId": "D2045",
    "messageStatus": "enable",
    "lastVisit": "2025/02/10"
  },
  {
    "doctorId": "D2046",
    "messageStatus": "disable",
    "lastVisit": "2025/01/15"
  },
  {
    "doctorId": "D2047",
    "messageStatus": "enable",
    "lastVisit": "2025/02/05"
  },
  {
    "doctorId": "D2048",
    "messageStatus": "enable",
    "lastVisit": "2025/01/20"
  },
  {
    "doctorId": "D2049",
    "messageStatus": "disable",
    "lastVisit": "2025/02/01"
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

<br/>

## **Get laboratory list to the frontend laboratory list page**

#### **Endpoint:**

```
GET /patient/laboratories
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Response:**

- **Success (200):**
    - Successfully returned laboratory list:

```json
[
  {
    "labId": "L2045",
    "lastMessage": "2025/02/10"
  },
  {
    "labId": "L2046",
    "lastMessage": "2025/01/15"
  },
  {
    "labId": "L2047",
    "lastMessage": "2025/02/05"
  },
  {
    "labId": "L2048",
    "lastMessage": "2025/01/20"
  },
  {
    "labId": "LD2049",
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

<br/>
## **Add new laboratory to the laboratories list**

#### **Endpoint:**

```
POST /laboratory
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Request Body:**

```json
{
    "labId": "L2047",
    "lastMessage": null
}
```

#### **Response:**

- **Success (200):**
    - Successfully added laboratory to the laboratory list:

```json
{
    "message": "Successfully added to the laboratory's list"
}
```

- **Duplicate Field (409):**
    - If that laboratory is already in the laboratory's list database:
    - Status Code: `409 Conflict`

```json
  {
    "message": "The laboratory is already in the list."
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

## **Get pharmacy list to the frontend pharmacy list page**

#### **Endpoint:**

```
GET /patient/pharmacies
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Response:**

- **Success (200):**
    - Successfully returned pharmacy list:

```json
[
  {
    "pharmacyId": "Ph2045",
    "lastMessage": "2025/02/10"
  },
  {
    "pharmacyId": "Ph2046",
    "lastMessage": "2025/01/15"
  },
  {
    "pharmacyId": "Ph2047",
    "lastMessage": "2025/02/05"
  },
  {
    "pharmacyId": "Ph2048",
    "lastMessage": "2025/01/20"
  },
  {
    "pharmacyId": "PhD2049",
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

<br/>
## **Add new pharmacy to the pharmacies list**

#### **Endpoint:**

```
POST /pharmacy
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Request Body:**

```json
{
    "pharmacyId": "Ph2047",
    "lastMessage": null
}
```

#### **Response:**

- **Success (200):**
    - Successfully added pharmacy to the pharmacy list:

```json
{
    "message": "Successfully added to the pharmacy's list"
}
```

- **Duplicate Field (409):**
    - If that pharmacy is already in the pharmacy's list database:
    - Status Code: `409 Conflict`

```json
  {
    "message": "The pharmacy is already in the list."
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