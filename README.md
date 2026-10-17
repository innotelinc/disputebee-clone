# CrediSure

A full-stack credit repair and credit management application built to help users review credit reports, detect errors, generate dispute letters, and track their progress toward improving their credit profile.

Repository: https://github.com/innotelinc/disputebee-clone

## Overview

CrediSure is a SaaS-style platform for managing credit repair workflows. It includes:

- Credit report upload and analysis
- AI-assisted dispute letter generation
- Dispute tracking and status monitoring
- Credit score simulator
- Educational resources and learning content
- Subscription and billing flows
- Admin dashboards for analytics, disputes, billing, and users

This repo is split into:
- `backend/` — Express API, MongoDB models, routes, authentication, and business logic
- `frontend/` — Next.js application for the public site, dashboard, and admin experience
- `docker-compose.yml` — local development environment for MongoDB and the API

## Tech Stack

Frontend
- Next.js
- React
- TypeScript
- Tailwind-style utility classes in the app

Backend
- Node.js
- Express
- MongoDB + Mongoose
- JWT authentication
- Swagger UI / OpenAPI docs
- OpenAI integration
- Stripe integration
- Nodemailer support
- Jest for tests

Infrastructure
- Docker Compose
- Vercel-ready deployment configuration

## Repository Structure

```text
.
├── .github/
│   └── workflows/
├── backend/
│   ├── __tests__/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── utils/
│   ├── validators/
│   ├── .env.example
│   ├── Dockerfile
│   ├── jest.config.js
│   ├── package.json
│   ├── server.js
│   └── vercel.json
├── frontend/
│   ├── src/
│   ├── next.config.js
│   ├── vercel.json
│   └── ...
├── docker-compose.yml
├── .gitignore
└── README.md
```

## Features

### User Features
- Upload and analyze credit reports
- Detect potential credit issues and discrepancies
- Generate dispute letters tailored to account issues
- Track dispute progress over time
- Access educational content and learning materials
- Explore plan options and subscription workflows

### Admin Features
- User management
- Billing and subscription oversight
- Dispute reviews
- Content management
- Analytics dashboard

### Platform Features
- REST API with Swagger documentation
- Secure request middleware
- File upload support
- Email notifications
- AWS and Stripe integrations
- Health check endpoint
- Dockerized local development environment

## Getting Started

### Prerequisites

Make sure you have installed:

- Node.js 18+
- npm
- Docker and Docker Compose
- MongoDB access (or use Docker)
- API credentials for:
  - OpenAI
  - Stripe
  - AWS
  - SendGrid / email provider

### 1) Clone the repo

```bash
git clone https://github.com/innotelinc/disputebee-clone.git
cd disputebee-clone
```

### 2) Configure environment variables

Copy the backend example file:

```bash
cp backend/.env.example backend/.env
```

Update the values in `backend/.env` to match your setup.

Example environment variables:

```env
NODE_ENV=development
PORT=5000
MONGO_URI=mongodb://credisure:credisure123@mongodb:27017/credisure?authSource=admin
JWT_SECRET=your_jwt_secret
JWT_EXPIRE=7d
OPENAI_API_KEY=your_openai_key
STRIPE_SECRET_KEY=your_stripe_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret
AWS_BUCKET_NAME=your_bucket_name
AWS_REGION=your_region
SENDGRID_API_KEY=your_sendgrid_key
FROM_EMAIL=no-reply@example.com
FROM_NAME=CrediSure
```

### 3) Start the app with Docker

```bash
docker compose up --build
```

This starts:
- MongoDB on port `27017`
- Backend API on port `5000`

### 4) Run the backend locally

```bash
cd backend
npm install
npm run dev
```

The API will run using the configured environment and usually listens on port `5000`.

## Health Check

The backend includes a health endpoint:

```bash
curl http://localhost:5000/health
```

## API Documentation

Swagger UI is enabled in the backend and is typically available at:

```text
http://localhost:5000/api-docs
```

## Scripts

From the `backend` directory:

```bash
npm start
npm run dev
npm test
```

## Testing

The project includes Jest-based tests for backend route and integration behavior:

```bash
cd backend
npm test
```

## Deployment Notes

- The frontend is set up for Vercel deployment.
- The backend can be run as a Node.js service or adapted for serverless hosting.
- MongoDB should be managed in a production-ready environment.
- Sensitive keys should be stored as environment variables or injected through a secure secret manager.

## License

This project appears to use the ISC license as defined in the repository’s backend package metadata.

## Notes

This repository is a full-stack credit repair platform inspired by the DisputeBee-style product workflow. It includes public-facing marketing pages, authenticated user flows, dispute generation tools, and admin dashboards for credit-related operations.

## Contributing

Contributions are welcome. A typical workflow:

```bash
git checkout -b feature/my-change
git commit -am "Add my feature"
git push origin feature/my-change
```

Then open a Pull Request on GitHub.

## Contact

For questions or project updates, use the repository’s GitHub page:
https://github.com/innotelinc/disputebee-clone
