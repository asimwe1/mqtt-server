### 🌡️ Environmental Monitoring Dashboard

A modern web application that collects temperature and humidity data from an MQTT broker, stores it in an SQLite database, and visualizes it with real-time updates and historical trends.





## ✨ Features

- **Real-time Monitoring**: Live temperature and humidity data with instant updates
- **Interactive Visualizations**: Beautiful charts showing historical trends and patterns
- **Data Storage**: Persistent SQLite database for reliable historical data access
- **Responsive Design**: Optimized interface for all devices from desktop to mobile
- **Modern UI**: Clean blue and white interface with glass-morphism effects


## 🚀 Getting Started

### Prerequisites

- Node.js (v16 or later)
- npm (v7 or later)


### Installation

1. Clone the repository:

```shellscript
git clone https://github.com/asimwe1/mqtt-server
cd mqtt-server
```


2. Install dependencies:

```shellscript
npm install
```


3. Configure your environment:
Create a `.env` file in the root directory with your MQTT broker details:

```plaintext
MQTT_BROKER=mqtt://your-broker-address
MQTT_USERNAME=your_username
MQTT_PASSWORD=your_password
MQTT_TOPIC=sensors/environmental
```


4. Start the application:

```shellscript
npm run dev
```


5. Access the dashboard:
Open your browser and navigate to `http://localhost:3000`


## 📂 Project Structure

```plaintext
environmental-dashboard/
├── public/
│   └── assets/           # Static assets and icons
├── src/
│   ├── components/       # React components
│   ├── lib/              # Utility functions and database logic
│   ├── pages/            # Application pages
│   └── styles/           # CSS and styling
├── server/
│   ├── mqtt-client.js    # MQTT connection and message handling
│   └── database.js       # SQLite database operations
├── package.json          # Project dependencies
└── README.md             # Documentation
```

## 🔄 How It Works

1. The application connects to your MQTT broker and subscribes to sensor topics
2. Incoming data is displayed in real-time on the dashboard
3. All readings are stored in the SQLite database for historical analysis
4. The dashboard automatically updates charts and displays with the latest data
5. Historical data can be filtered and analyzed through the interface


## 📊 Data Visualization

The dashboard provides multiple visualization options:

- **Real-time Gauges**: Current temperature and humidity values
- **Time-series Charts**: Historical trends with customizable time ranges
- **Statistical Analysis**: Min/max/average values for selected periods


## 🗄️ Database Schema

### Sensor Readings

```sql
CREATE TABLE sensor_readings (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  sensor_id TEXT NOT NULL,
  reading_type TEXT NOT NULL,  -- 'temperature' or 'humidity'
  value REAL NOT NULL,
  timestamp TEXT NOT NULL
);
```

### Aggregated Data

```sql
CREATE TABLE aggregated_data (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  time_period TEXT NOT NULL,   -- '5min', 'hourly', 'daily'
  avg_temperature REAL,
  avg_humidity REAL,
  min_temperature REAL,
  max_temperature REAL,
  min_humidity REAL,
  max_humidity REAL,
  timestamp TEXT NOT NULL
);
```

## 🧰 API Endpoints

- `GET /api/readings/current` - Get the most recent sensor readings
- `GET /api/readings/history` - Get historical data with optional time filters
- `GET /api/statistics` - Get statistical analysis of sensor data


## 🚀 Deployment

### Quick Start

1. Navigate to the project directory
2. Run the application:

```shellscript
npm start
```


3. Access the dashboard at `http://localhost:3000`


### Production Deployment

For production environments, we recommend using PM2 or Docker:

```shellscript
# Using PM2
npm install -g pm2
pm2 start npm --name "environmental-dashboard" -- start

# Using Docker
docker build -t environmental-dashboard .
docker run -p 3000:3000 environmental-dashboard
```

## 📱 Mobile Access

The dashboard is fully responsive and can be accessed from any device with a web browser. For the best experience on mobile devices, we recommend adding the site to your home screen.

---

Made with ❄️ and 💧 by Asimwe Landry
