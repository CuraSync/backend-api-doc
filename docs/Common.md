## **Login**

#### **Endpoint:**

```
POST /login
```

#### **Request Body:**

```json
{
  "role": "doctor",             // Role of the user: doctor, patient, pharmacy, lab
  "credential_type": "email",   // Type of credential: id or email
  "credential_data": "admin@example.com", // The actual id or email
  "password": "adminPass123"     // Password for the user
}
```

#### **Response:**

- **Success (200):**
    - When login is successful and JWT is generated:

```json
{
    "message": "Login successful",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiYWRtaW4iLCJpZCI6IjEyMyJ9.bWIsfdxTYwHfkl5o3fTn"
}
```

- **Invalid Role (400):**
    - If the role provided in the request body is invalid:
    - Status Code: `400 Bad Request`

```json
  {
    "message": "Invalid role"
  }
```


- **Invalid Credentials (401):**
    - If the provided credentials do not match any user in the database:
    - Status Code: `401 Unauthorized`

```json
  {
    "message": "Invalid credentials"
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
<br/><br/>
## **Get Profile Details**

#### **Endpoint:**

```
GET /profile
```

#### **Headers:**

```json
{
  "Authorization": "Bearer <your_jwt_token>"
}
```

#### **Response:**

- **Success (200):**
    - Successfully retrieved profile:

```json
{
  "id": "123456",
  "name": "John Doe",
  "email": "john@example.com",
  "role": "doctor",
  "specialty": "Cardiology"
}
```

- **Invalid Role (400):**
    - If the role provided in the request body is invalid:
    - Status Code: `400 Bad Request`

```json
  {
    "message": "Invalid role"
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

- **Internal Server Error (500):**
    - If there’s an unexpected error on the server:
    - Status Code: `500 Internal Server Error`

```json
  {
    "message": "Internal server error"
  }
```