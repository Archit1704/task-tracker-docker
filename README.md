# 📌 Task Tracker

A simple full-stack task tracker built with **Node.js**, **Express**, **MySQL/MariaDB**, and **Vanilla JavaScript**. It includes login/signup, task CRUD, and a small chart-based status overview 📊

## ✨ Features

- 🔐 User signup and login
- 📝 Create, view, update, and delete tasks
- 📊 Task status chart on the dashboard
- 🚦 Protected task routes using JWT
- 🐳 Docker support with `Dockerfile` and `docker-compose.yml`

## 🛠️ Tech Stack

- Node.js
- Express
- MySQL / MariaDB
- JWT + bcrypt
- HTML, CSS, JavaScript
- Chart.js

## 📁 Project Structure

```text
.
├── frontend/
│   ├── index.html      # Dashboard UI
│   ├── login.html      # Login / signup page
│   └── script.js       # Frontend logic
├── db.js               # MySQL connection
├── server.js           # Express server and API routes
├── Dockerfile
├── docker-compose.yml
├── .env.example
├── package.json
└── README.md
```

## 🚀 Run Locally

1. Install dependencies:

```bash
npm install
```

2. Create a `.env` file from `.env.example`:

```bash
cp .env.example .env
```

3. Start the server:

```bash
npm start
```

4. Open the app:

```text
http://localhost:3000
```

## 🔑 Environment Variables

The project includes an `.env.example` file with the current variables used by the app and Docker:

```env
DB_HOST=db
DB_USER=root
DB_PASSWORD=rootpassword
DB_NAME=taskdb

MYSQL_ROOT_PASSWORD=rootpassword
MYSQL_DATABASE=taskdb
```

For local non-Docker setup, `DB_HOST` is usually `localhost`.

## 🐳 Run With Docker

```bash
docker compose up --build
```

This starts:

- `app` on port `3000`
- `db` using `mariadb:11`

## 🔗 API Routes

- `POST /signup`
- `POST /login`
- `GET /tasks`
- `POST /tasks`
- `PUT /tasks/:id`
- `DELETE /tasks/:id`
- `GET /stats`

## ⚠️ Notes

- The frontend is served from the `frontend/` folder.
- The root route `/` opens `frontend/login.html`.
- The current server code uses a hardcoded JWT secret and port `3000`.
- A database schema SQL file is not included in this repository, so the required tables need to exist before the app can work fully.

## 👨‍💻 Author

Archit Sharma
