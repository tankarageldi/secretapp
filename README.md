# Secrets App - README

## Overview

The **Secrets App** is a web application that allows users to securely register, log in, and share secrets anonymously. This app was created to practice on local authentication, and OAuth authentication using Google and Passport.js.

---

## Features

- **User Authentication**:
  - Local authentication using email and password.
  - Google OAuth for seamless login.
- **Secrets Management**:
  - Submit and view personal secrets securely.
- **Session Handling**:
  - Maintains user sessions with `express-session`.
- **Security**:
  - Passwords are hashed with bcrypt.
  - Sensitive data managed using environment variables.

---

## Technologies Used

- **Backend**: Node.js, Express.js
- **Database**: PostgreSQL
- **Authentication**: Passport.js (Local & Google strategies)
- **Templating**: EJS
- **Other Libraries**:
  - `dotenv` for environment variables.
  - `body-parser` for parsing request bodies.
  - `bcrypt` for hashing passwords

---

## Prerequisites

- Node.js and npm installed
- PostgreSQL installed and configured
- Google Cloud account (for OAuth credentials)

---

## Installation

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/your-repo/secrets-app.git
   cd secrets-app
   ```

2. **Install Dependencies**:

   ```bash
   npm install
   ```

3. **Set Up Environment Variables**:
   Create a `.env` file in the root directory with the following:

   ```env
   SESSION_SECRET=your-session-secret
   PG_USER=your-database-username
   PG_HOST=your-database-host
   PG_DATABASE=your-database-name
   PG_PASSWORD=your-database-password
   PG_PORT=your-database-port
   GOOGLE_CLIENT_ID=your-google-client-id
   GOOGLE_CLIENT_SECRET=your-google-client-secret
   CALLBACK_URL=http://localhost:3000/auth/google/secrets
   USER_PROFILE_URL=https://www.googleapis.com/oauth2/v3/userinfo
   ```

4. **Set Up Database**:
   Run the following SQL commands to create the necessary table:

   ```sql
   CREATE TABLE users (
       id SERIAL PRIMARY KEY,
       email VARCHAR(255) UNIQUE NOT NULL,
       password VARCHAR(255),
       secret TEXT
   );
   ```

5. **Run the Server**:

   ```bash
   npm start
   ```

   The app will run on `http://localhost:3000`.

---

## Authentication Workflows

1. **Local Authentication**:

   - Register with email and password.
   - Passwords are hashed using bcrypt before storage.
   - Authenticate using Passport's Local strategy.

2. **Google OAuth**:
   - Redirect to Google for authentication.
   - Retrieve user profile and save it to the database if it’s their first login.
   - Authenticate using Passport's Google Strategy

---
