### **1. Patient Registration**

- **Endpoint**: `POST /patient/register`
- **Description**: Register a new patient.
- **Request Body** (Example):
    
    ```json
    {
      "firstName": "John",
      "lastName": "Doe",
      "fullName": "John Doe",
      "email": "john.doe@example.com",
      "nic": "123456789V",
      "password": "password123",
      "phoneNumber": "+1234567890",
      "address": "123 Main St, City",
      "dateOfBirth": "1990-01-01"
    }
    ```
    
- **Success Response**:
    
    ```json
    {
      "message": "Patient created successfully",
      "patientId": "PA11234"
    }
    ```
    
    - **Status Code**: `201 Created`
- **Errors**:
    - `400 Bad Request`: Missing required fields.
    - `409 Conflict`: NIC/Email already exists.
    - `500 Internal Server Error`: Server error.

### **2. Update Patient Profile**

- **Endpoint**: `POST /patient/profile`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Update patient profile (excludes email, NIC, password, etc.).
- **Request Body** (Example):
    
    ```json
    {
      "height": 180,
      "weight": 75,
      "bmi": 23.1,
      "bloodType": "O+",
      "medicationAllergies": ["Penicillin", "Aspirin"],
      "guardianName": "Jane Doe",
      "guardianContactNumber": "+0987654321",
      "guardianEmail": "jane.doe@example.com",
      "profilePic": "profilepic.jpg"
    }
    ```
    
- **Success Response**:
    
    ```json
    { "message": "Patient profile updated successfully" }
    ```
    
    - **Status Code**: `200 OK`
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `500 Internal Server Error`: Server error

### **3. Get Patient Profile**

- **Endpoint**: `GET /patient/profile`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieve patient profile (excludes password).
- **Success Response** (Example):
    
    ```json
    {
      "patientId": "PA11234",
      "firstName": "John",
      "lastName": "Doe",
      "email": "john.doe@example.com",
      "phoneNumber": "+1234567890",
      "address": "123 Main St, City",
      "bloodType": "O+"
    }
    ```
    
    - **Status Code**: `200 OK`
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: Patient not found.

### **3. Get Patient Homepage Data**

- **Endpoint**: `GET /patient/home`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieve patient profile (excludes password).

**Status Code**: `200 OK`
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: Patient not found.

### **4. Add a Laboratory**

- **Endpoint**: `POST /laboratory`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Link a laboratory to the patient.
- **Request Body** (Example):
    
    ```json
    { "labId": "LAB123" }
    ```
    
- **Success Response**:
    
    ```json
    { "message": "Lab added successfully" }
    ```
    
    - **Status Code**: `201 Created`
- **Errors**:
    - `400 Bad Request`: Missing `labId`.
    - `404 Not Found`: Lab does not exist.
    - `409 Conflict`: Lab already added.
    - `500 Internal Server Error`: Server error.
    

### **4. Add a Pharmacy**

- **Endpoint**: `POST /pharmacy`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Link a pharmacy to the patient.
- **Request Body** (Example):
    
    ```json
    { "pharmacyId": "PH123" }
    ```
    
- **Success Response**:
    
    ```json
    { "message": "Pharmacy added successfully" }
    ```
    
    - **Status Code**: `201 Created`
- **Errors**:
    - `400 Bad Request`: Missing `labId`.
    - `404 Not Found`: Lab does not exist.
    - `409 Conflict`: Lab already added.
    - `500 Internal Server Error`: Server error.