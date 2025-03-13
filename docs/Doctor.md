### **1. Doctor Registration**

- **Endpoint**: `POST /doctor/register`
- **Description**: Registers a new doctor.
- **Request Body** (Example):
    
    ```json
    {
      "firstName": "Jane",
      "lastName": "Doe",
      "fullName": "Jane Doe",
      "email": "jane.doe@example.com",
      "slmcRegisterNumber": "SLMC12345",
      "nic": "987654321V",
      "password": "SecurePass123",
      "phoneNumber": "0771234567"
    }
    ```
    
- **Success Response**:
    
    ```json
    {
      "message": "Doctor registered successfully",
      "doctorId": "D12345"
    }
    ```
    
    - **Status Code**: `201 Created`
- **Errors**:
    - `400 Bad Request`: Missing required fields.
    - `409 Conflict`: NIC, SLMC Register Number, or Email already in use.
    - `500 Internal Server Error`: Unexpected error.

### **2. Update Doctor Profile**

- **Endpoint**: `POST /doctor/profile`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Updates the profile of an authenticated doctor.
- **Request Body**: Any fields to update (except `password`, `email`, `nic`, or `id`).
- **Success Response**:
    
    ```json
    {
      "message": "Doctor update profile successful"
    }
    ```
    
    - **Status Code**: `200 OK`
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `500 Internal Server Error`: Unexpected error.

### **3. Get Doctor Profile**

- **Endpoint**: `GET /doctor/profile`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves the profile of the authenticated doctor.
- **Success Response**:
    - Returns the doctor's profile excluding sensitive fields like `password` and `_id`.
    - **Status Code**: `200 OK`
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: User not found.
    - `500 Internal Server Error`: Unexpected error.

### **4. Get Doctor Homepage Data**

- **Endpoint**: `GET /doctor/home`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves homepage data for the authenticated doctor.
- **Success Response**:
    - Returns the doctor's profile excluding sensitive fields like `password` and `_id`.
    - **Status Code**: `200 OK`
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: User not found.
    - `500 Internal Server Error`: Unexpected error.

### **5. Get Patient List**

- **Endpoint**: `GET /doctor/patient`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves the list of patients associated with the authenticated doctor.
- **Success Response**:
    - Returns an array of patients with details like `firstName`, `lastName`, and `profilePic`.
    - **Status Code**: `200 OK`
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: No patients found.
    - `500 Internal Server Error`: Unexpected error.

### **6. Add a Patient**

- **Endpoint**: `POST /doctor`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Adds a patient to the authenticated doctor's list.
- **Request Body** (Example):
    
    ```json
    {
      "patientId": "PA12345"
    }
    ```
    
- **Success Response**:
    
    ```json
    {
      "message": "Patient successfully added to the list"
    }
    ```
    
    - **Status Code**: `200 OK`
- **Errors**:
    - `400 Bad Request`: Missing required fields.
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: Invalid patient.
    - `409 Conflict`: Patient is already in the list.
    - `500 Internal Server Error`: Unexpected error.

### **7. Add a Doctor**

- **Endpoint**: `POST /doctor`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Adds another doctor to the authenticated doctor's list.
- **Request Body** (Example):
    
    ```json
    {
      "reciveDoctorId": "D67890"
    }
    ```
    
- **Success Response**:
    
    ```json
    {
      "message": "Doctor successfully added to the list"
    }
    ```
    
    - **Status Code**: `200 OK`
- **Errors**:
    - `400 Bad Request`: Missing required fields.
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: Invalid doctor recipient.
    - `409 Conflict`: Doctor is already in the list.
    - `500 Internal Server Error`: Unexpected error.

### **8. Get Doctor List**

- **Endpoint**: `GET /doctor/doctors`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves the list of doctors associated with the authenticated doctor.
- **Success Response**:
    - Returns an array of doctors with details like `firstName`, `lastName`, and `profilePic`.
    - **Status Code**: `200 OK`
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: No doctors found.
    - `500 Internal Server Error`: Unexpected error.
