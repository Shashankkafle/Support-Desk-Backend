# Support Desk — Backend

A REST API for a customer support ticketing system. Users can register, log in, submit support tickets, and track their status. Built with Node.js, Express, and MongoDB.

## Tech Stack

- **Node.js** + **Express** — server and routing
- **MongoDB** + **Mongoose** — database and ODM
- **JSON Web Tokens (JWT)** — stateless authentication
- **bcryptjs** — password hashing
- **express-async-handler** — clean async error handling
- **dotenv** — environment variable management
- **CORS** — cross-origin support

## Project Structure

```
Support-Desk-Backend/
├── config/          # Database connection
├── controllers/     # Business logic (users, tickets, notes)
├── middlewear/      # Auth middleware (JWT verification)
├── models/          # Mongoose schemas (User, Ticket, Note)
├── routes/          # Express route definitions
├── server.js        # App entry point
└── .env             # Environment variables (not committed)
```

## Getting Started

### Prerequisites

- Node.js v16+
- MongoDB running locally or a MongoDB Atlas connection string

### Installation

```bash
git clone https://github.com/Shashankkafle/Support-Desk-Backend.git
cd Support-Desk-Backend
yarn install
```

### Environment Variables

Create a `.env` file in the root:

```env
NODE_ENV=development
PORT=5000
MONGO_URI=mongodb://localhost:27017/supportdesk
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=30d
```

### Running the Server

```bash
# Development (with nodemon)
yarn server

# Production
yarn start
```

The API will be available at `http://localhost:5000`.

## API Endpoints

> All protected routes require `Authorization: Bearer <token>` header.

**Auth**

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/api/users` | Register a new user | — |
| POST | `/api/users/login` | Log in, receive JWT | — |
| GET | `/api/users/me` | Get current user profile | ✓ |

**Tickets**

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/api/tickets` | Get all tickets for current user | ✓ |
| POST | `/api/tickets` | Create a new ticket | ✓ |
| GET | `/api/tickets/:id` | Get a single ticket | ✓ |
| PUT | `/api/tickets/:id` | Update ticket status | ✓ |
| DELETE | `/api/tickets/:id` | Delete a ticket | ✓ |

**Notes**

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/api/tickets/:id/notes` | Get notes for a ticket | ✓ |
| POST | `/api/tickets/:id/notes` | Add a note to a ticket | ✓ |

## Status

Work in progress. Auth, ticket CRUD, and notes are implemented. A matching frontend ([Support-Desk-Frontend](https://github.com/Shashankkafle/Support-Desk-Frontend)) is in a separate repo but was not fully completed.
