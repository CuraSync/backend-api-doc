## **Register**

#### **Endpoint:**

```
POST /doctor/register
```

#### **Request Body:**

```json
{
  "name": {
    "firstname": "John",
    "middlename": "Michael",
    "lastname": "Doe"
  },
  "address": {
    "street": "123 Main St",
    "city": "New York",
    "state": "NY",
    "zipCode": "10001",
    "country": "USA"
  },
  "nicNo": "987654321V",
  "mobileNo": "+1-123-456-7890",
  "email": "johndoe@example.com",
  "password": "SecurePass123!",
  "specialization": "Cardiologist",
  "govDocRegId": "DOC12345678",
  "birthOfDate": "1985-07-20",
  "qualifications": [
    "MBBS - Harvard Medical School",
    "MD - Cardiology"
  ],
  "experience": [
    {
      "hospital": "NYC General Hospital",
      "years": 5
    },
    {
      "hospital": "Boston Medical Center",
      "years": 3
    }
  ],
  "currentWorkingHospitals": [
    "New York-Presbyterian Hospital",
    "Mount Sinai Hospital"
  ],
  "socialMediaLinks": {
    "linkedin": "https://www.linkedin.com/in/johndoe",
    "twitter": "https://twitter.com/johndoe"
  },
  "description": "Experienced cardiologist with a passion for patient care and medical research.",
  "profilePic": "https://example.com/images/johndoe.jpg"
}
```

#### **Response:**

- **Success (200):**
    - When register is successful and return the Doctor Id:

```json
{
    "message": "Successfully Registered",
    "id": "D12345"
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

## **Get data that required in the doctor’s home page**

#### **Endpoint:**

```
GET /doctor/home
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
  "name": {
    "firstname": "John",
    "middlename": "Michael",
    "lastname": "Doe"
  },
  "address": {
    "street": "123 Main St",
    "city": "New York",
    "state": "NY",
    "zipCode": "10001",
    "country": "USA"
  },
  "nicNo": "987654321V",
  "mobileNo": "+1-123-456-7890",
  "email": "johndoe@example.com",
  "specialization": "Cardiologist",
  "govDocRegId": "DOC12345678",
  "birthOfDate": "1985-07-20",
  "qualifications": [
    "MBBS - Harvard Medical School",
    "MD - Cardiology"
  ],
  "experience": [
    {
      "hospital": "NYC General Hospital",
      "years": 5
    },
    {
      "hospital": "Boston Medical Center",
      "years": 3
    }
  ],
  "currentWorkingHospitals": [
    "New York-Presbyterian Hospital",
    "Mount Sinai Hospital"
  ],
  "socialMediaLinks": {
    "linkedin": "https://www.linkedin.com/in/johndoe",
    "twitter": "https://twitter.com/johndoe"
  },
  "description": "Experienced cardiologist with a passion for patient care and medical research.",
  "profilePic": "https://example.com/images/johndoe.jpg",
  "patientsCount": 20,
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
GET /doctor/patient
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Response:**

- **Success (200):**
    - Successfully returned paients list:

```json
[
  {
    "patientId": "Pa2045",
    "messageStatus": "enable",
    "priority": 3,
    "lastVisit": "2025/02/10"
  },
  {
    "patientId": "Pa2046",
    "messageStatus": "disable",
    "priority": 1,
    "lastVisit": "2025/01/15"
  },
  {
    "patientId": "Pa2047",
    "messageStatus": "enable",
    "priority": 2,
    "lastVisit": "2025/02/05"
  },
  {
    "patientId": "Pa2048",
    "messageStatus": "enable",
    "priority": 1,
    "lastVisit": "2025/01/20"
  },
  {
    "patientId": "Pa2049",
    "messageStatus": "disable",
    "priority": 3,
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
## **Add new patient to the patient’s list**

#### **Endpoint:**

```
POST /patient
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
    "patientId": "Pa2047",
    "messageStatus": "enable",
    "priority": 2,
    "lastVisit": null
}
```

#### **Response:**

- **Success (200):**
    - Successfully added patient to the patients list:

```json
{
    "message": "Successfully added to the patient's list"
}
```

- **Duplicate Field (409):**
    - If that patient is already in the patient's list database:
    - Status Code: `409 Conflict`

```json
  {
    "message": "The patient is already in the list."
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
GET /doctor/doctors
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Response:**

- **Success (200):**
    - Successfully returned doctors list:

```json
[
  {
    "doctortId": "D2045",
    "messageStatus": "enable"
  },
  {
    "doctortId": "D2046",
    "messageStatus": "disable"
  },
  {
    "doctortId": "D2047",
    "messageStatus": "enable"
  },
  {
    "doctortId": "D2048",
    "messageStatus": "enable"
  },
  {
    "doctortId": "D2049",
    "messageStatus": "disable"
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
## **Add new doctor to the doctor's list**

#### **Endpoint:**

```
POST /doctor
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
    "doctortId": "D2047",
    "messageStatus": "enable",
}
```

#### **Response:**

- **Success (200):**
    - Successfully added doctor to the doctor list:

```json
{
    "message": "Successfully added to the doctor's list"
}
```

- **Duplicate Field (409):**
    - If that doctor is already in the doctor's list database:
    - Status Code: `409 Conflict`

```json
  {
    "message": "The doctor is already in the list."
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