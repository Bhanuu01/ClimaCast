<h1 align="center">🌤️ ClimaCast</h1>
<h3 align="center">Real-Time Weather Monitoring & Alert System</h3>

<p align="center">
  <b>Track, Analyze, and Alert - All in Real-Time</b><br>
  <i>Built with Django · Celery · Redis · PostgreSQL</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9+-blue?logo=python" />
  <img src="https://img.shields.io/badge/Django-4.x-green?logo=django" />
  <img src="https://img.shields.io/badge/Celery-TaskQueue-brightgreen" />
  <img src="https://img.shields.io/badge/Redis-Broker-red?logo=redis" />
</p>

---

## 📌 Overview

ClimaCast is a full-stack application that collects real-time weather data, summarizes daily conditions, and sends temperature alerts using scheduled background tasks.

It includes:
- Real-time dashboard to visualize temperature data
- Scheduled tasks using Celery for periodic data updates
- Temperature scale switching (Celsius / Fahrenheit)

## Installation (WSL - Ubuntu)

1. **Clone the repository:**

    ```bash
    git clone https://github.com/Bhanuu01/Real-Time-Data-Processing-System-for-Weather-Monitoring.git
    cd Real-Time-Data-Processing-System-for-Weather-Monitoring/weather_monitoring
    ```

2. **Install the required packages:**

    ```bash
    pip install -r requirements.txt
    ```

## Running the Application (WSL - Ubuntu):

1. **Apply database migrations:**

    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```

2. **Start Django Development Server:**

    ```bash
    python manage.py runserver
    ```

3. **Install Redis:**

    ```bash
    sudo apt update
    sudo apt install redis-server
    ```

    **Start the Redis service:**

    ```bash
    sudo systemctl start redis-server
    ```

4. **Start Celery Worker:** Open a new terminal window, navigate to your project directory, and run:

    ```bash
    celery -A weather_monitoring worker --loglevel=info
    ```

5. **Start Celery Beat:** In another terminal window, run:

    ```bash
    celery -A weather_monitoring beat --loglevel=info
    ```

6. Add default cities to database
   
   ```bash
    python manage.py populate_cities
    ```


## Usage

**Running Tasks:**

- **Fetch Weather Data:** Runs every 5 minutes to fetch weather data for all cities.
- **Calculate Daily Summary:** Runs daily at midnight to calculate and store the daily weather summary.
- **Check Alerts:** Runs every 10 minutes to check if any city's temperature exceeds 35°C.

## Accessing the Dashboard

Open a web browser and navigate to [http://127.0.0.1:8000/dashboard/](http://127.0.0.1:8000/dashboard/) to view the weather dashboard.
Temaparature scale feature allows users to select their preferred temperature scale, as illustrated in the figure below. It then provides temperatures based on the user's selection.

![image](https://github.com/user-attachments/assets/2a9abad8-fee3-43d0-a946-a5f4b0a59347)

![image](https://github.com/user-attachments/assets/343965bd-1790-475e-b911-a0c4d70d5c97)

