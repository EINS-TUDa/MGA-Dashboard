# MGA Compass

![License](https://img.shields.io/github/license/EINS-TUDa/MGA-Compass)

## Installation

### Prerequisites

- Python 3.14+
- Node.js 20.19+ or 22.12+

### Backend

```bash
cd backend
pip install -e ".[standard]"
uvicorn mgaserver.main:app --reload
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```

The app will be available at `http://localhost:5173`.

## Docker

### Docker prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

### Run locally

```bash
docker compose up --build
```

The app will be available at `http://localhost`.

### Deploy to production

#### 1. Build and push images

```bash
docker build -t <your-dockerhub-username>/mga-backend:latest ./backend
docker build -t <your-dockerhub-username>/mga-frontend:latest ./frontend

docker push <your-dockerhub-username>/mga-backend:latest
docker push <your-dockerhub-username>/mga-frontend:latest
```

#### 2. Deploy backend

Create a service using the image `<your-dockerhub-username>/mga-backend:latest` on port `8000`.

#### 3. Deploy frontend

Create a service using the image `<your-dockerhub-username>/mga-frontend:latest` on port `80`.

Set the following environment variable:

| Variable                  | Value                         |
|---------------------------|-------------------------------|
| `BACKEND_URL`             | `https://<your-backend-url>`  |
