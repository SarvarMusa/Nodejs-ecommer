# Node.js E-Commerce Platform

[![CI](https://github.com/SarvarMusa/Nodejs-ecommer/actions/workflows/ci.yml/badge.svg)](https://github.com/SarvarMusa/Nodejs-ecommer/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Description: A full-stack e-commerce web application that solves the problem of building a scalable online store. It features a Node.js/Express REST API backend with JWT authentication, role-based access control, Redis caching, and rate limiting — paired with a modern React + Chakra UI frontend for a complete shopping experience.

## Tech Stack

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB & Mongoose
- **Auth:** JWT (jsonwebtoken) + bcrypt
- **Caching:** Redis (ioredis, express-redis-cache)
- **Rate Limiting:** express-rate-limit + rate-limit-redis
- **Validation:** Joi
- **RBAC:** accesscontrol

### Frontend
- **Framework:** React 17
- **UI Library:** Chakra UI + Ant Design
- **State/Data:** React Query, Axios
- **Forms:** Formik + Yup
- **Routing:** React Router DOM
- **Animations:** Framer Motion

## Setup instructions

### Prerequisites
- Node.js 14+
- MongoDB instance (local or Atlas)
- Redis instance (local or cloud)

### Backend
```bash
cd backend
yarn install
cp .env.example .env   # fill in your values
yarn dev
```

### Frontend
```bash
cd client
yarn install
yarn start
```

## Environment variables

Create a `.env` file inside the `backend/` directory:

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/ecommerce
JWT_ACCESS_SECRET=your_access_token_secret
JWT_REFRESH_SECRET=your_refresh_token_secret
REDIS_URL=redis://localhost:6379
```

> ⚠️ Never commit your `.env` file. It is already excluded via `.gitignore`.

## Usage examples

1. Register a user via `POST /auth/register`
2. Login to receive a JWT access token via `POST /auth/login`
3. Include the token in the `Authorization: Bearer <token>` header for protected routes
4. Browse and manage products via `/product` routes
5. Place and manage orders via `/order` routes (authentication required)

## API endpoints

| Method | Endpoint              | Description                     | Auth Required |
|--------|-----------------------|---------------------------------|---------------|
| `POST` | `/auth/register`      | Register a new user             | No            |
| `POST` | `/auth/login`         | Login and receive JWT           | No            |
| `GET`  | `/product`            | Get all products                | No            |
| `POST` | `/product`            | Create a product                | Yes (Admin)   |
| `PUT`  | `/product/:id`        | Update a product                | Yes (Admin)   |
| `DELETE` | `/product/:id`      | Delete a product                | Yes (Admin)   |
| `GET`  | `/order`              | Get user orders                 | Yes           |
| `POST` | `/order`              | Place a new order               | Yes           |
