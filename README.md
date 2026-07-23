# WanderLust

> A full-stack Airbnb-style platform for listing, browsing, and reviewing rental properties.

## Overview

This is a full-stack Node.js/Express application that enables users to list rental properties, browse listings by location and price, and leave reviews and ratings — replicating the core booking-platform experience of apps like Airbnb. It was built to practice full-stack architecture, session-based authentication, authorization patterns, and cloud service integration (image storage) in a real-world style project.

---

## Features

- Secure Session-Based Authentication (Passport.js)
- Owner/Author-Based Access Control
- CRUD Operations for Listings & Reviews
- Cloud Image Uploads (Cloudinary)
- Star Rating & Review System
- Flash Messages for User Feedback
- RESTful Route Structure
- Centralized Error Handling
- Input Validation (Joi)

---

## Tech Stack

### Frontend
- EJS (with `ejs-mate` for layouts)
- Bootstrap / CSS
- JavaScript (client-side validation)

### Backend
- Node.js
- Express.js
- MongoDB (Mongoose)
- Passport.js (`passport-local`, `passport-local-mongoose`)
- Cloudinary + Multer

### Tools
- Git
- GitHub
- Postman
- VS Code
- Render (Deployment)

---

## Architecture

```text
Client (EJS Views)
       │
       ▼
Express Server (Routes → Controllers)
       │
       ▼
MongoDB Database (Mongoose Models)
       │
       ▼
Cloudinary (Image Storage)
```

---

## Project Structure

```text
WanderLust/
│
├── controllers/
│   ├── listings.js
│   ├── reviews.js
│   └── users.js
│
├── models/
│   ├── listing.js
│   ├── review.js
│   └── user.js
│
├── routes/
│   ├── listing.js
│   ├── review.js
│   └── user.js
│
├── views/
│   ├── layouts/
│   ├── includes/
│   ├── listings/
│   └── users/
│
├── public/
│   ├── css/
│   └── js/
│
├── utils/
│   ├── ExpressError.js
│   └── wrapAsync.js
│
├── init/
├── middleware.js
├── cloudConfig.js
├── schema.js
├── app.js
└── package.json
```

---

## Getting Started

### Prerequisites
- Node.js
- npm
- MongoDB (local or Atlas)
- Cloudinary account

### Installation
```bash
git clone https://github.com/username/WanderLust.git
cd WanderLust
npm install
```

### Environment Variables
Create a `.env` file in the root directory.
```env
ATLASDB_URL=
SECRET=
CLOUD_NAME=
CLOUD_API_KEY=
CLOUD_API_SECRET=
```

### Run the Project
```bash
node app.js
```
The app runs on the port defined in `app.js` (default: `8080`).

---

## API / Route Documentation

| Method | Endpoint | Description |
|---------|----------|-------------|
| GET | /listings | View all listings |
| POST | /listings | Create a new listing |
| GET | /listings/:id | View a single listing |
| PUT | /listings/:id | Update a listing (owner only) |
| DELETE | /listings/:id | Delete a listing (owner only) |
| POST | /listings/:id/reviews | Add a review to a listing |
| DELETE | /listings/:id/reviews/:reviewId | Delete a review (author only) |
| GET | /signup | Render signup form |
| POST | /signup | Register a new user |
| GET | /login | Render login form |
| POST | /login | Authenticate user |
| GET | /logout | Log out user |

---

## Security

- Session-Based Authentication (Passport.js)
- Password Hashing via `passport-local-mongoose`
- Owner/Author-Only Route Protection Middleware
- Server-Side Input Validation (Joi)
- Environment Variables for Sensitive Config
- Flash-Based Error Feedback (no sensitive data leaked to client)

---

## Performance Optimizations

- Mongoose Post-Hook for Cascading Review Deletes (prevents orphaned data)
- Cloudinary-Optimized Image Delivery
- Centralized Async Error Handling (`wrapAsync`) to prevent unhandled promise crashes

---

## Screenshots

### Home Page
(Add Screenshot)

### Listing Detail Page
(Add Screenshot)

### Mobile View
(Add Screenshot)

---

## Challenges Faced

- Implementing owner/author-based authorization across nested routes (listings → reviews).
- Structuring a scalable MVC folder architecture for maintainability.
- Handling image uploads reliably with Cloudinary + Multer.
- Designing a clean cascading-delete relationship between listings and reviews.

---

## Future Improvements

- JWT-based API layer for mobile/external clients
- Search & Filter by location, price, category
- Pagination for listings
- Unit & Integration Testing
- Docker Support
- CI/CD Pipeline

---

## Contributing

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Open a Pull Request.

