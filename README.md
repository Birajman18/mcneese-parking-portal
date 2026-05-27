# McNeese Parking Services

A web-based parking permit management system built for McNeese State University. Students, faculty, and visitors can register, purchase parking hang tags, manage their vehicles, and view payment history through a clean dashboard interface.

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Database Setup](#database-setup)
- [API Reference](#api-reference)
- [Security](#security)

---

## Features

- User registration restricted to `@mcneese.edu` email addresses
- Secure login with session management and automatic timeout after 10 minutes of inactivity
- Purchase semester ($85) or annual ($150) parking hang tags
- Register and manage multiple vehicles per account
- Dashboard showing active permits, registered vehicles, and payment history
- Profile management including password change
- Forgot password flow
- Order confirmation page with permit details

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript (ES6+) |
| Backend | PHP 7.4+ |
| Database | MySQL 5.7+ |
| Server | Apache / Nginx |

---

## Project Structure

```
mcneese-parking-portal/
├── index.php                  # Landing page
├── login.html                 # Login page
├── register.html              # Registration page
├── forgot_password.html       # Password recovery
├── dashboard.html             # User dashboard
├── purchase.html              # Permit purchase page
├── confirmation.html          # Order confirmation
├── profile.html               # Profile management
├── about.html                 # About page
├── styles.css                 # Global stylesheet
├── auth.js                    # Authentication logic
├── dashboard.js               # Dashboard logic
├── purchase.js                # Purchase flow logic
├── confirmation.js            # Confirmation page logic
├── profile.js                 # Profile page logic
├── session-timeout.js         # Session timeout handler
├── database.sql               # MySQL database schema
├── McNeesePhoto.jpg           # University photo asset
├── api/
│   ├── config.php             # Database connection and configuration
│   ├── auth_api.php           # Authentication endpoints
│   ├── permits_api.php        # Permit endpoints
│   └── vehicles_api.php      # Vehicle endpoints
└── .gitignore
```

---

## Getting Started

### Prerequisites

- PHP 7.4 or higher
- MySQL 5.7 or higher
- A web server (Apache or Nginx)

### Installation

1. Clone the repository

```bash
git clone https://github.com/Birajman18/mcneese-parking-portal.git
```

2. Move the files to your web server's root directory (e.g. `htdocs` for XAMPP or `www` for WAMP)

3. Set up the database (see [Database Setup](#database-setup))

4. Update `api/config.php` with your own database host, username, password, and database name before running locally

5. Update the `API_BASE` URL in all JavaScript files to match your domain or localhost path

6. Open the app in your browser at your configured domain or `http://localhost/mcneese-parking-portal`

---

## Database Setup

Import the included SQL file to create all required tables:

```bash
mysql -u your_username -p your_database_name < database.sql
```

### Tables

| Table | Description |
|---|---|
| `users` | User accounts, credentials, and user type |
| `vehicles` | Vehicles registered by each user |
| `permits` | Purchased parking permits with expiry dates |
| `payments` | Transaction history and receipt records |

---

## API Reference

### Authentication — `api/auth_api.php`

| Method | Action | Description |
|---|---|---|
| POST | `register` | Create a new user account |
| POST | `login` | Log in and start a session |
| POST | `logout` | End the current session |
| GET | `checkSession` | Verify if session is still active |
| POST | `updateProfile` | Update user profile information |
| POST | `changePassword` | Change account password |

### Permits — `api/permits_api.php`

| Method | Action | Description |
|---|---|---|
| POST | `createPermit` | Purchase a new parking permit |
| GET | `getPermits` | Get all permits for the logged-in user |
| GET | `getPaymentHistory` | Get payment history |

### Vehicles — `api/vehicles_api.php`

| Method | Action | Description |
|---|---|---|
| POST | `addVehicle` | Register a new vehicle |
| GET | `getVehicles` | Get all vehicles for the logged-in user |
| POST | `removeVehicle` | Remove a registered vehicle |

---

## Security

- Passwords hashed with BCrypt
- All database queries use prepared statements to prevent SQL injection
- Input sanitized against XSS attacks
- Session cookies set to HttpOnly
- Login rate limiting to prevent brute force
- Session automatically expires after 10 minutes of inactivity
- Registration restricted to `@mcneese.edu` email addresses only

---

## Author

Birajman Tamang — [GitHub](https://github.com/Birajman18)
