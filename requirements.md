1. USER AUTHENTICATION SYSTEM
API Endpoints
Method              Endpoint                Description
POST                /api/register/          Register as guest/host
POST                /api/login              Login with email/pwd
GET                 /api/profile            Get user profile
PUT                 /api/profile            Update profile.


Example of the Input/Output
/api/register/ (POST)
Input:

{
  "first_name": "Joy",
  "last_name": "jane",
  "email": "joy@example.com",
  "password": "Secure123!",
  "role": "host"
}

Example of Output (201 Created):

{
  "message": "User registered successfully",
  "token": "<JWT Token>"
}


/api/login/ (POST)
Input example:
json

{
  "email": "joy@example.com",
  "password": "Secure123!"
}

Output example:
json

{
  "token": "<JWT Token>",
  "user": {
    "user_id": "uuid",
    "first_name": "joy",
    "role": "host"
  }
}


Validation Rules
Password: min 8 characters, must include a number and capital letter


Email: valid format and must be unique


Role: must be guest or host




2. PROPERTY LISTING MANAGEMENT
API Endpoints
Method              Endpoint                Description
POST                /api/properties         Host creates listing
PUT                 /api/properties/{id}/   Host updates listing
DELETE              /api/properties/{id}/   Host deletes listing
GET                 /api/properties/        Public listing of properties


Input Example (Create Property)
json

{
  "name": "Beachside Villa",
  "description": "Relaxing ocean view property",
  "location": "Lagos",
  "pricepernight": 250,
  "amenities": ["wifi", "pool", "parking"],
  "available_dates": ["2025-08-01", "2025-08-02"]
}

Output (201 Created):
json

{
  "property_id": "uuid",
  "message": "Property created successfully"
}


Validation Rules
Price: Must be positive number


Name: Required, max 100 chars


User role must be host


Performance Criteria


Paginated: 10 properties per page, sorted by price or rating



3. BOOKING MANAGEMENT
API Endpoints
Method              Endpoint                Description
POST                /api/bookings/          Guest creates a booking
DELETE              /api/bookings/{id}/     Cancel a booking
GET                 /api/bookings/          List user’s bookings


Example of Input (Create Booking)
json

{
  "property_id": "uuid",
  "start_date": "2025-07-01",
  "end_date": "2025-07-05"
}

Output:
json

{
  "booking_id": "uuid",
  "status": "pending",
  "total_price": 1000.00
}




