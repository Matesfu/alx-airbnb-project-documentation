# Airbnb Clone Backend - Requirements Specification

## Objective
Document the technical and functional requirements for each key backend feature of the Airbnb Clone backend.

---

## 1. User Authentication

**Objective:** Enable secure user registration, login, and profile management.

### API Endpoints
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth/register` | POST | Register a new user (guest or host) |
| `/api/auth/login` | POST | Login with email/password or OAuth |
| `/api/auth/logout` | POST | Logout user and invalidate JWT |
| `/api/users/profile` | GET | Fetch logged-in user profile |
| `/api/users/profile` | PUT/PATCH | Update profile details |

### Input/Output Specifications
**Register**
- Input:
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "Password@123",
  "role": "guest"
}

- Output (Success):

{
  "message": "User registered successfully",
  "userId": "12345",
  "token": "jwt_token_here"
}


Output (Error):

{
  "error": "Email already exists"
}


Login

Input:

{
  "email": "john@example.com",
  "password": "Password@123"
}


Output (Success):

{
  "message": "Login successful",
  "token": "jwt_token_here",
  "user": { "id": "12345", "name": "John Doe", "role": "guest" }
}

Validation Rules

Email must be valid and unique.

Password: Minimum 8 characters, at least 1 uppercase, 1 lowercase, 1 digit, 1 special character.

Role: Must be either "guest" or "host".

Performance Criteria

Registration/login response time ≤ 300ms.

JWT token expiration: configurable (e.g., 1 hour).

Support concurrent logins for 10,000+ users.
