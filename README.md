Project Management Dashboard

A full-stack project management dashboard built with Next.js, Node.js, PostgreSQL, and AWS services.

Technology Stack

Frontend: Next.js, Tailwind CSS, Redux Toolkit, Redux Toolkit Query, Material UI Data Grid

Backend: Node.js, Express, Prisma ORM

Database: PostgreSQL

Cloud: AWS EC2, RDS, API Gateway, S3, Lambda, Amplify, Cognito

Prerequisites

Make sure the following are installed on your system:

Git

Node.js and npm

PostgreSQL

PgAdmin (optional, for database management)

Installation Steps

Clone the repository

git clone [REPO_URL]
cd project-management


Install dependencies

cd client
npm install

cd ../server
npm install


Set up the database

npx prisma generate
npx prisma migrate dev --name init
npm run seed


Configure environment variables

server/.env

PORT=5000
DATABASE_URL=your_postgres_connection_url


client/.env.local

NEXT_PUBLIC_API_BASE_URL=http://localhost:5000


Start the development servers

# Run backend
cd server
npm run dev

# In a new terminal, run frontend
cd client
npm run dev

Database Management

To reset the auto-incrementing ID in a table (e.g. after deleting rows):

SELECT setval(
  pg_get_serial_sequence('"[TABLE_NAME]"', 'id'),
  COALESCE(MAX(id)+1, 1),
  FALSE
) FROM "[TABLE_NAME]";