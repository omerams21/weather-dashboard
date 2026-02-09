# Weather Dashboard (Frontend)

A Flask-based frontend application that allows users to select a city from a dropdown
and fetch current weather information from the backend service.

## Dropdown Options (Cities)
- New York   (newyork)
- Sydney     (sydney)
- Cape Town  (capetown)
- Bangkok    (bangkok)

The frontend provides:
- A dropdown for city selection
- A Submit button
- A results area displaying the JSON response

## Backend URL Configuration
The frontend proxies all API requests through the `/api/weather/<location_key>` endpoint.
The frontend communicates with the backend using the environment variable `BACKEND_URL`.

Examples:
- Local backend: http://localhost:5000
- Docker Compose backend service: http://weather-service:5000

## Run Locally (Linux / WSL, No Docker)

### 1. Start the Backend
Make sure the backend is already running on port 5000.

### 2. Run the Frontend
1. Navigate to the frontend repository:
   cd weather-dashboard

2. Create and activate a virtual environment:
   python3 -m venv .venv
   source .venv/bin/activate

3. Install dependencies:
   pip install -r requirements.txt

4. Set the backend URL and run the frontend:
   export BACKEND_URL="http://localhost:5000"
   python app.py

The frontend will be available at:
http://localhost:5000

## Run with Docker (Frontend Only)

This mode assumes the backend is already running on the host machine.
In WSL with Docker Desktop, use `host.docker.internal` to reach the host.

1. Build the Docker image:
   docker build -t weather-dashboard:flask .

2. Run the container:
   docker run --rm -p 8080:5000 \
     -e BACKEND_URL="http://host.docker.internal:5000" \
     weather-dashboard:flask

Open in browser:
http://localhost:8080

## Run with Docker Compose (Recommended)

When using the Docker Compose setup (weather-stack repository):
- Backend and frontend are started together
- The frontend automatically connects to the backend via service name

Start the stack:
docker compose up --build

Open:
http://localhost:8080

## Expected UI

The expected user interface includes:
- A dropdown list with four cities
- A Submit button
- A results section showing the weather data in JSON format

A screenshot of the expected UI is available at:
docs/ui-screenshot.png
![Weather Dashboard UI](docs/ui-screenshot.png)
