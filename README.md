# Task Tracker

Task Tracker is a small full-stack task management app built with Node.js, Express, MariaDB/MySQL, and plain HTML/CSS/JavaScript. It supports user signup and login, task creation, status updates, deletion, and a simple chart-based overview of task status.

## Features

- User signup and login with hashed passwords
- JWT-protected task endpoints
- Create, list, update, and delete personal tasks
- Pie chart dashboard using Chart.js
- Docker support for the app and database

## Tech Stack

- Node.js
- Express
- MariaDB / MySQL
- `mysql2`
- `bcrypt`
- `jsonwebtoken`
- Vanilla HTML, CSS, and JavaScript
- Chart.js

## Project Structure

```text
.
├── database/
│   └── init.sql
├── frontend/
│   ├── index.html
│   ├── login.html
│   └── script.js
├── db.js
├── Dockerfile
├── docker-compose.yml
├── package-lock.json
├── package.json
├── README.md
└── server.js
```

## Prerequisites

- Node.js 18 or newer
- npm
- MySQL or MariaDB

## Local Setup

1. Install dependencies:

```bash
npm install
```

2. Create a `.env` file in the project root:

```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=taskdb
MYSQL_ROOT_PASSWORD=your_password
MYSQL_DATABASE=taskdb
```

3. Create the database schema by running the SQL in `database/init.sql`.

4. Start the server:

```bash
npm start
```

5. Open the app at `http://localhost:3000`.

## Docker Setup

1. Create a `.env` file in the project root:

```env
DB_HOST=db
DB_USER=root
DB_PASSWORD=rootpassword
DB_NAME=taskdb
MYSQL_ROOT_PASSWORD=rootpassword
MYSQL_DATABASE=taskdb
```

2. Start the containers:

```bash
docker compose up --build
```

The compose setup starts:

- `app` on port `3000`
- `db` using `mariadb:11`

The database container loads `database/init.sql` automatically on first startup.

## API Endpoints

### Authentication

- `POST /signup`
- `POST /login`

### Tasks

- `GET /tasks`
- `POST /tasks`
- `PUT /tasks/:id`
- `DELETE /tasks/:id`
- `GET /stats`

Task endpoints require the JWT token in the `Authorization` header.

## Database Schema

The app uses two tables:

- `users`
- `tasks`

The schema is defined in `database/init.sql`.

## Frontend Flow

- `/` serves `frontend/login.html`
- After login, the token is stored in `localStorage`
- Authenticated users are redirected to `frontend/index.html`
- The dashboard loads tasks and chart data from the backend API

## Current Limitations

- The JWT secret is hardcoded in `server.js`
- The app port is hardcoded to `3000`
- Login and signup UI error handling is minimal
- There is no logout/session invalidation on the server side
- There are no automated tests configured in `package.json`

## Scripts

```bash
npm start
```
