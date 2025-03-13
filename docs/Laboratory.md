### **1. Laboratory Registration**

- **Endpoint**: `POST /laboratory/register`
- **Description**: Registers a new laboratory.
- **Request Body**:
    
    ```json
    {
      "labName": "Central Lab",
      "email": "central.lab@example.com",
      "licenceNumber": "LAB12345",
      "password": "SecurePass123",
      "phoneNumber": "0712345678",
      "location": "Colombo"
    }
    
    ```
    
- **Success Response (201 Created)**:
    
    ```json
    {
      "message": "Laboratory created successfully",
      "labId": "L12345"
    }
    
    ```
    
- **Errors**:
    - `400 Bad Request`: Missing required fields.
    - `409 Conflict`: Licence Number or Email already exists.
    - `500 Internal Server Error`: Unexpected error.

---

### **2. Update Laboratory Profile**

- **Endpoint**: `POST /laboratory/profile`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Updates the laboratory’s profile (excludes `labId`, `email`, `licenceNumber`, and `password`).
- **Request Body (Example)**:
    
    ```json
    {
      "location": "456 Elm St, Anytown, USA",
      "description": "A reliable pharmacy providing a wide range of medications and health products.",
      "operatingHours": "9 AM - 9 PM",
      "rating": 4.5,
      "profilePic": "pharmacyprofilepic.jpg",
      "contactInformation": ["+1234567890", "contact@healthpluspharmacy.com"]
    }
    
    ```
    
- **Success Response (200 OK)**:
    
    ```json
    { "message": "Profile updated successfully" }
    
    ```
    
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `500 Internal Server Error`: Server error.

---

### **3. Get Laboratory Profile**

- **Endpoint**: `GET /laboratory/profile`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves the laboratory’s profile (excludes sensitive fields like `password`).
- **Success Response (200 OK)**:
    
    ```json
    {
        "labId": "L74247",
        "labName": "Advanced Diagnostics Lab",
        "email": "info@advanceddiagnosticslab.com",
        "licenceNumber": "74247",
        "phoneNumber": "+1234567890",
        "location": "456 Elm St, Anytown, USA",
        "description": "A reliable pharmacy providing a wide range of medications and health products.",
        "operatingHours": "9 AM - 9 PM",
        "rating": 4.5,
        "profilePic": "pharmacyprofilepic.jpg",
        "contactInformation": [
            "+1234567890",
            "contact@healthpluspharmacy.com"
        ],
        "createdAt": "2025-02-19T10:25:56.947Z",
        "updatedAt": "2025-02-19T10:31:23.773Z",
        "__v": 0
    }
    ```
    
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: Lab not found.

---

### **4. Get Laboratory Homepage Data**

- **Endpoint**: `GET /laboratory/home`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves the laboratory’s homepage data (same as profile in current implementation).
- **Success Response (200 OK)**:
    
    ```json
    {
        "labId": "L74247",
        "labName": "Advanced Diagnostics Lab",
        "email": "info@advanceddiagnosticslab.com",
        "licenceNumber": "74247",
        "phoneNumber": "+1234567890",
        "location": "456 Elm St, Anytown, USA",
        "description": "A reliable pharmacy providing a wide range of medications and health products.",
        "operatingHours": "9 AM - 9 PM",
        "rating": 4.5,
        "profilePic": "pharmacyprofilepic.jpg",
        "contactInformation": [
            "+1234567890",
            "contact@healthpluspharmacy.com"
        ],
        "createdAt": "2025-02-19T10:25:56.947Z",
        "updatedAt": "2025-02-19T10:31:23.773Z",
        "__v": 0
    }
    
    ```
    
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: Lab not found.

---

### **5. Get Patient List**

- **Endpoint**: `GET /laboratory/patients`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves patients associated with the laboratory.
- **Success Response (200 OK)**:
    
    ```json
    [
      {
        "patientId": "PA40157",
        "_id": "67b5625ff811ceecfdd5f916",
        "firstName": "John",
        "lastName": "Doe",
        "profilePic": "profilepic.jpg"
        }
    ]
    
    ```
    
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: No patients found.