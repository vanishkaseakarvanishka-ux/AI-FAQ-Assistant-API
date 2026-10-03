# AI FAQ Assistant API - Backend

MERN backend for an AI-powered FAQ and knowledge management platform.

## Main features

- JWT registration/login
- bcryptjs password hashing
- Role-based access control (user/admin)
- FAQ CRUD
- Category management
- MongoDB text-based semantic-like search
- Google Gemini AI answers using FAQ context
- AI response history
- Request validation
- Helmet security headers
- CORS
- Rate limiting
- Morgan request logging
- Centralized error handling
- Pagination

## Requirements

- Node.js 18+
- npm 8+
- MongoDB
- Google Gemini API key
- Postman (recommended for testing)
- VS Code or another editor

## Setup

1. Extract the ZIP.
2. Open the extracted `ai-faq-assistant-backend` folder in VS Code.
3. Run:

```bash
npm install
```

4. Copy `.env.example` to `.env`.
5. Add your MongoDB connection string, JWT secret, and Gemini API key.
6. Start MongoDB.
7. Run:

```bash
npm run dev
```

The API runs on:

`http://localhost:5000`

## API endpoints

### Authentication

- `POST /api/auth/register`
- `POST /api/auth/login`

### FAQs

- `GET /api/faqs`
- `GET /api/faqs/:id`
- `GET /api/faqs?search=login`
- `POST /api/faqs`
- `PUT /api/faqs/:id`
- `DELETE /api/faqs/:id`

### Categories

- `GET /api/categories`
- `POST /api/categories` (admin)
- `PUT /api/categories/:id` (admin)
- `DELETE /api/categories/:id` (admin)

### AI Assistant

- `POST /api/ai/ask`
- `GET /api/ai/history`

### Users

- `GET /api/users/profile`
- `GET /api/users` (admin)
- `PATCH /api/users/:id/role` (admin)

## Authentication

After login/register, send the JWT token in:

`Authorization: Bearer YOUR_TOKEN`

## Example register body

```json
{
  "name": "Test User",
  "email": "test@example.com",
  "password": "password123"
}
```

## Example FAQ body

```json
{
  "question": "How can I reset my password?",
  "answer": "Open the login page and select Forgot Password.",
  "category": "CATEGORY_ID",
  "keywords": ["password", "reset", "login"],
  "isPublished": true
}
```

## Example AI question

```json
{
  "question": "How do I reset my password?"
}
```

## Important note about admin

New registrations are created as `user`. For the first admin, update the user's `role` to `admin` directly in MongoDB, then use the admin-protected category/user endpoints.

## Project structure

```text
ai-faq-assistant-backend/
├── server.js
├── package.json
├── .env.example
├── README.md
└── src/
    ├── app.js
    ├── config/
    ├── controllers/
    ├── middleware/
    ├── models/
    ├── routes/
    ├── services/
    └── utils/
```
