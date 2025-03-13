### **1. Pharmacy Registration**

- **Endpoint**: `POST /pharmacy/register`
- **Description**: Registers a new pharmacy.
- **Request Body**:
    
    ```json
    {
      "pharmacyName": "HealthPlus Pharmacy",
      "email": "contactus@healthpluspharmacy.com",
      "licenceNumber": "74247",
      "password": "12345",
      "phoneNumber": "+1234567890",
      "location": "456 Elm St, Anytown, USA"
    }
    
    ```
    
- **Success Response (201 Created)**:
    
    ```json
    {
      "message": "Pharmacy created successfully",
      "pharmacyId": "PH1234"
    }
    
    ```
    
- **Errors**:
    - `400 Bad Request`: Missing required fields.
    - `409 Conflict`: Licence Number or Email already exists.
    - `500 Internal Server Error`: Unexpected error.

---

### **2. Update Pharmacy Profile**

- **Endpoint**: `POST /pharmacy/profile`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Updates the pharmacy’s profile (excludes `pharmacyId`, `email`, `licenceNumber`, and `password`).
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
    { "message": "Pharmacy updated successfully" }
    
    ```
    
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `500 Internal Server Error`: Server error.

---

### **3. Get Pharmacy Profile**

- **Endpoint**: `GET /pharmacy/profile`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves the pharmacy’s profile (excludes sensitive fields like `password`).
- **Success Response (200 OK)**:
    
    ```json
    {
        "pharmacyId": "PH64247",
        "pharmacyName": "HealthPlus Pharmacy",
        "email": "contactus@healthpluspharmacy.com",
        "licenceNumber": "74247",
        "phoneNumber": "+1234567890",
        "location": "456 Elm St, Anytown, USA",
        "description": "A reliable pharmacy provvviddinng a wide range of medications and health products.",
        "operatingHours": "10 AM - 10 PM",
        "rating": 4.5,
        "profilePic": "pharmacyprofilepic.jpg",
        "contactInformation": [
            "+1234567890",
            "contact@healthpluspharmacy.com"
        ],
        "createdAt": "2025-02-19T09:12:00.470Z",
        "updatedAt": "2025-02-19T09:13:01.674Z",
        "__v": 0
    }
    
    ```
    
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: Pharmacy not found.

---

### **4. Get Pharmacy Homepage Data**

- **Endpoint**: `GET /pharmacy/home`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves the pharmacy’s homepage data (same as profile in current implementation).
- **Success Response (200 OK)**:
    
    ```json
    {
        "pharmacyId": "PH64247",
        "pharmacyName": "HealthPlus Pharmacy",
        "email": "contactus@healthpluspharmacy.com",
        "licenceNumber": "74247",
        "phoneNumber": "+1234567890",
        "location": "456 Elm St, Anytown, USA",
        "description": "A reliable pharmacy provvviddinng a wide range of medications and health products.",
        "operatingHours": "10 AM - 10 PM",
        "rating": 4.5,
        "profilePic": "pharmacyprofilepic.jpg",
        "contactInformation": [
            "+1234567890",
            "contact@healthpluspharmacy.com"
        ],
        "createdAt": "2025-02-19T09:12:00.470Z",
        "updatedAt": "2025-02-19T09:13:01.674Z",
        "__v": 0
    }
    ```
    
- **Errors**:
    - `401 Unauthorized`: Invalid/missing token.
    - `404 Not Found`: Pharmacy not found.

---

### **5. Get Patient List**

- **Endpoint**: `GET /pharmacy/patients`
- **Headers**: `Authorization: Bearer <JWT>`
- **Description**: Retrieves patients associated with the pharmacy.
- **Success Response (200 OK)**:
    
    ```json
    [
        {
            "patientId": "PA40157",
            "firstName": "John",
            "lastName": "Doe",
            "profilePic": "profilepic.jpg"
        },
        {
            "patientId": "PA40157",
            "firstName": "John",
            "lastName": "Doe",
            "profilePic": "profilepic.jpg"
        }
    ]
    ```
    
- `401 Unauthorized`: Invalid/missing token.
- `404 Not Found`: No patients found.