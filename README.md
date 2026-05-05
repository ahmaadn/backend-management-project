# Backend Management Project

A robust backend API for a project management system built with [FastAPI](https://fastapi.tiangolo.com/). This application utilizes a clean, domain-driven architecture and features real-time notifications, role-based access control (RBAC), and comprehensive task tracking capabilities.

## Features

* **User & Role Management**: Secure authentication, authorization, and role assignments (e.g., Project Manager, Member).
* **Project Tracking**: Create, update, and organize projects, milestones, and specific categories.
* **Task Management**: Assign tasks to users, track statuses, leave comments, and upload file attachments.
* **Real-time Notifications**: Integrated support for Server-Sent Events (SSE), WebSockets, and Pusher for instant updates.
* **Audit Logging**: Automatically track state changes and user actions across projects and tasks.
* **Cloud Storage**: Seamless Cloudinary integration for handling task and project attachments.
* **Database Migrations**: Version-controlled database schema managed via Alembic.

## Tech Stack

* **Framework**: FastAPI (Python)
* **ORM & Database**: SQLAlchemy (Async support recommended), Alembic
* **Package Management**: [uv](https://github.com/astral-sh/uv) (and `requirements.txt` fallback)
* **Real-time**: WebSockets, SSE, Pusher
* **File Storage**: Cloudinary
* **Testing**: Pytest

## Prerequisites

* Python 3.10+ (Refer to `.python-version`)
* A supported Relational Database (e.g., PostgreSQL or MySQL)
* [uv](https://github.com/astral-sh/uv) package manager (recommended for speed) or pip.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/ahmaadn/backend-management-project.git
cd backend-management-project
```

### 2. Environment Configuration

Copy the example environment file and update it with your specific credentials:

```bash
cp .env.example .env
```
*Make sure to configure your database connection string, JWT secrets, Cloudinary API keys, and Pusher credentials.*

### 3. Install Dependencies

Using `uv` (Recommended):
```bash
uv sync
```

Or using `pip`:
```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\\Scripts\\activate`
pip install -r requirements.txt
```

### 4. Database Migrations

Apply the latest database migrations to set up your tables:

```bash
alembic upgrade head
```

*(Optional) If the project includes a seeder script, you can populate initial data:*
```bash
python -m app.seeder
```

### 5. Run the Application

Start the FastAPI development server:

```bash
uvicorn app.main:app --reload
```

* **Swagger UI (Interactive API Docs)**: [http://localhost:8000/docs](http://localhost:8000/docs)
* **ReDoc**: [http://localhost:8000/redoc](http://localhost:8000/redoc)

## Project Structure

```text
app/
├── api/          # FastAPI routers and dependency injections
├── client/       # External service clients (e.g., Pegawai client)
├── core/         # Core configurations, domain events, realtime drivers, and policies
├── db/           # SQLAlchemy models, repositories, uow, and Alembic migrations
├── middleware/   # Custom request and context middlewares
├── schemas/      # Pydantic models for request/response validation
├── services/     # Core business logic layer
├── utils/        # Helper functions, cloud uploads, and mail utilities
└── main.py       # FastAPI application entry point
```

## Testing

Run the automated test suite using `pytest`:

```bash
pytest
```
