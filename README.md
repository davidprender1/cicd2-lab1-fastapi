# CICD-2 FastAPI Lab Template

This repository contains a FastAPI lab for the CICD-2 module.  
Use this `README.md` as the standard structure for future labs.

---

## Lab Title

**Replace this with the lab title**

Example:

> Lab 1 — Creating a Basic FastAPI Application

---
## Repository Structure

Use the following structure for the labs:

```text
project-name/
│
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── schemas.py
│   ├── services.py
│   └── models.py
│
├── tests/
│   ├── __init__.py
│   └── test_main.py
│
├── requirements.txt
├── README.md
└── .gitignore
```

## Lab 5 - Two FastAPI Microservices with HTTPX

This project contains two FastAPI microservices:

- User API - Port 8000
- Product Service - Port 8001

### Running the Services

Open two separate terminals in GitHub Codespaces.

Terminal 1 - Start Product Service:

python3 -m uvicorn product_service.main:app --host 0.0.0.0 --port 8001 --reload

Terminal 2 - Start User API:

python3 -m uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload

### Product Endpoint

GET /api/products/{product_id}

The User API uses HTTPX to request product information
from the Product Service.

Expected responses:
- 200: Product found
- 404: Product not found
- 502: Product Service returned an upstream error
- 503: Product Service unavailable

### Configuration

PRODUCT_SERVICE_URL defines the address of the
Product Service.

Default: http://127.0.0.1:8001

This can be changed when using Docker Compose.

### Running Tests

python3 -m pytest

Tests use dependency overrides so the Product Service
does not need to be running.

