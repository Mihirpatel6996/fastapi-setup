# FastAPI with SQLAlchemy Project

A robust REST API built with FastAPI and SQLAlchemy, featuring user management and PostgreSQL integration.

## 🚀 Features

- FastAPI REST API implementation
- PostgreSQL database integration with SQLAlchemy ORM
- Pydantic models for request/response validation
- Environment variable configuration
- User management (CRUD operations)
- Automatic API documentation (Swagger UI)

## 📋 Prerequisites

- Python 3.8+
- PostgreSQL
- pip (Python package installer)

## 🛠️ Project Structure

```
fastapi-project/
│
├── app/
│   ├── __init__.py
│   ├── main.py          # FastAPI application instance and endpoints
│   ├── database.py      # Database configuration and session management
│   ├── models.py        # SQLAlchemy models
│   └── schemas.py       # Pydantic models/schemas
│
├── .env                 # Environment variables
├── requirements.txt     # Project dependencies
└── README.md           # Project documentation
```

## ⚙️ Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd fastapi-project
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Configure the database:
   - Create a PostgreSQL database
   - Copy `.env.example` to `.env`
   - Update `.env` with your database credentials:
```env
DATABASE_URL=postgresql://user:password@localhost/dbname
```

5. Run the application:
```bash
uvicorn app.main:app --reload
```

## 🔄 API Endpoints

### Users

- `POST /users/`
  - Create a new user
  - Request body: `{"email": "user@example.com", "username": "username"}`

- `GET /users/`
  - List all users
  - Query parameters:
    - `skip`: Number of records to skip (default: 0)
    - `limit`: Maximum number of records to return (default: 100)

- `GET /users/{user_id}`
  - Get user by ID
  - Path parameter: `user_id` (integer)

## 📚 API Documentation

Once the application is running, you can access:
- Swagger UI documentation: `http://localhost:8000/docs`
- ReDoc documentation: `http://localhost:8000/redoc`

## 🔍 Database Models

### User Model
```python
class User(Base):
    __tablename__ = "users"
    id = Column(Integer, primary_key=True, index=True)
    email = Column(String, unique=True, index=True)
    username = Column(String, unique=True, index=True)
    created_at = Column(DateTime(timezone=True), server_default=func.now())
```

## 🧪 Testing

To run tests (when implemented):
```bash
pytest
```

## 🛡️ Environment Variables

| Variable      | Description           | Default Value |
|---------------|-----------------------|---------------|
| DATABASE_URL  | PostgreSQL connection URL | postgresql://user:password@localhost/dbname |

## 🔐 Security Considerations

- Update the default database credentials
- Implement authentication and authorization
- Use HTTPS in production
- Validate and sanitize all inputs
- Implement rate limiting for API endpoints

## 🚀 Deployment

1. Set up a production PostgreSQL database
2. Update environment variables for production
3. Use a production ASGI server (like Uvicorn or Gunicorn)
4. Set up reverse proxy (like Nginx)
5. Enable HTTPS

Example production startup command:
```bash
gunicorn app.main:app -w 4 -k uvicorn.workers.UvicornWorker
```

## ✨ Future Enhancements

- [ ] Add authentication and authorization
- [ ] Implement more complex database relationships
- [ ] Add request validation middleware
- [ ] Create comprehensive test suite
- [ ] Add logging configuration
- [ ] Implement caching
- [ ] Add database migrations

## 📝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Authors

- Your Name - Initial work

## 🙏 Acknowledgments

- FastAPI documentation
- SQLAlchemy documentation
- PostgreSQL documentation