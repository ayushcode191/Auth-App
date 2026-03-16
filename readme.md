# Secure Authentication Management System

A secure backend authentication system built using **Node.js, Express.js, MongoDB, and JWT**.  
The system implements **OTP-based email verification, Access Token & Refresh Token authentication, and multi-device session management** to ensure secure user authentication.

---

## Features

- User **registration with OTP-based email verification**
- **Account verification required before login**
- **Password hashing** for secure credential storage
- **JWT-based authentication**
- **Access Token & Refresh Token** implementation
- **Secure session management**
- **Logout from current device**
- **Logout from all devices**
- RESTful authentication APIs

---

## Tech Stack

- **Backend:** Node.js, Express.js  
- **Database:** MongoDB  
- **Authentication:** JSON Web Token (JWT)  
- **Email Service:** Nodemailer  

---

## Authentication Flow

### 1. User Registration
- User registers using **email and password**
- Password is **hashed before storing**
- User account is created with **verification status set to false**
- An **OTP is sent to the user's email**

### 2. OTP Verification
- User submits the OTP
- If OTP is valid:
  - Account verification status becomes **true**
  - User account is activated

### 3. Login
Login is only allowed if the account is **verified**.

After successful login:
- **Access Token** is generated (short-lived)
- **Refresh Token** is generated (long-lived)

### 4. Token Refresh
When the **Access Token expires**, the client can request a new access token using the **Refresh Token**.

### 5. Logout
Two logout mechanisms are supported:

- **Logout current device** → removes current refresh token  
- **Logout from all devices** → invalidates all refresh tokens  

---

## API Endpoints

| Method | Endpoint | Description |
|------|------|------|
| POST | `/api/auth/register` | Register user and send OTP |
| POST | `/api/auth/verify-otp` | Verify OTP and activate account |
| POST | `/api/auth/login` | Login verified user |
| POST | `/api/auth/refresh-token` | Generate new access token |
| POST | `/api/auth/logout` | Logout from current device |
| POST | `/api/auth/logout-all` | Logout from all devices |

---

## Installation

Clone the repository:

```bash
git clone https://github.com/ayushcode191/Auth-App.git
cd Auth-App
npm install
```

---

## Environment Variables

Create a `.env` file in the root directory and add:

```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
ACCESS_TOKEN_SECRET=your_access_secret
REFRESH_TOKEN_SECRET=your_refresh_secret
EMAIL_USER=your_email
EMAIL_PASS=your_email_password
```

---

## Run the Server

```bash
npm start
```

Server will run on:

```
http://localhost:5000
```

---

## Security Practices Implemented

- Password hashing  
- JWT token authentication  
- OTP email verification  
- Refresh token based session management  
- Account verification before login  
- Multi-device logout capability  

---

## Author

**Ayush Bansal**  
B.Tech IT | Backend Developer  

GitHub:  
https://github.com/ayushcode191