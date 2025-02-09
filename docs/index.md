# Home Page


This documentation outlines the backend endpoints for the CuraSync application, detailing their purpose, request structures, and expected response formats.

Unlike traditional API documentation, which is typically written after development, this documentation has been created before backend implementation. The reason for this approach is to provide the frontend team with a clear understanding of:

✅ The required request structure – What data needs to be sent in each API request.<br>
✅ Expected response formats – The structure and type of data each endpoint will return.<br>
✅ Error handling and status codes – How to handle various responses from the backend.

By defining the API in advance, we ensure a seamless integration between frontend and backend development, allowing both teams to work in parallel efficiently.


API Categories by User Roles
The CuraSync API is organized into different categories based on user roles. Each category contains endpoints specific to that role’s functionality:

  - [Common](Common.md) – Includes endpoints shared across all user roles, such as authentication (`/login`, `/logout`) and general system interactions.

  - [Doctor](Doctor.md)  – Contains endpoints for doctors to manage patient records, write prescriptions, view reports, and track medical histories.

  - [Patient](Patient.md)  – Provides endpoints for patients to access their medical history, view prescriptions, receive lab reports, and manage their profile.

  - [Laboratory](Lab.md)  – Includes endpoints for laboratories to upload test reports, associate them with patient records, and send notifications upon completion.

  - [Pharmacy](Pharmacy.md)  – Features endpoints that allow pharmacies to verify prescriptions, process medication requests, and check availability of medicines.