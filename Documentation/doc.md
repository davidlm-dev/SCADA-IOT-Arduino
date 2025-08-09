# SCADA system project

## About the project

This project consists of a **Supervisory Control and Data Acquisition** **(SCADA)** system with **simulated sensor data** instead of physical sensors.  
The system is designed to monitor and control environmental variables such as temperature and pressure, and to demonstrate knowledge in areas like:

1. **IoT (simulation-focused)**
2. **Backend**
3. **Frontend**
4. **Databases**
5. **Communication protocols**
6. **DevOps tools**

**System Architecture Overview**

The system is composed of several components working together:

- **Sensor data simulation** instead of real Arduino/BME280 hardware, generating realistic temperature, humidity, and pressure readings.
- MQTT protocol for efficient, lightweight communication between simulated sensors and backend.
- A backend built with Node.js (TypeScript) for data processing and API management.
- Two databases:
  - **MongoDB** for storing **sensor data**.
  - **PostgreSQL** (or another SQL database) for storing **users, configurations, and general system data**.
- A frontend in React for data visualization and system control.
- JWT authentication for secure user access.
- Docker for deployment and containerization.
- Microservice architecture for scalability and modularity.

## Project Objective

The main goal of this project is to develop a **Supervisory Control and Data Acquisition (SCADA)** system for the **management and monitoring** of a **simulated weather station**.  
The system will simulate measurements for:

- **Temperature**
- **Humidity**
- **Pressure**
- **Altitude**

The system will allow **remote management** through a **React frontend**, where users will be able to:

- **Visualize real-time graphs** of the simulated environmental data.
- **Access historical data** stored in a database for long-term analysis.
- Optionally, **receive alerts** (virtually on the UI) if simulated values exceed critical thresholds.

## **SCADA Breakdown**

### **S - Supervisory**
- **Remote Management**: Users can manage the simulated weather station from the **React-based frontend**, adjusting simulation parameters such as sampling rate or data variation ranges.
- **Real-Time Monitoring**: Simulated temperature, humidity, and pressure values are continuously monitored and displayed in real-time.
- **Visualizations**: The frontend will display dynamic **graphs** for quick understanding of the simulated data.

### **C - Control**
- **Alarm Systems**: The SCADA system will trigger **alerts** when simulated sensor values exceed predefined thresholds:
  - **Virtual**: Shown on the frontend UI.
- **Adjustable Parameters**: Users can modify simulation settings from the frontend to test different system responses.

### **A - Acquisition & Data**
- **Data Acquisition**: Instead of physical readings, the backend generates simulated sensor data based on configurable parameters.
- **Data Communication**: The simulated readings are transmitted using **MQTT** to mimic real IoT communication flows.
- **Data Storage**:  
  - **MongoDB** stores sensor readings for efficient handling of large, dynamic datasets.  
  - **PostgreSQL** stores user accounts, system configurations, and other relational data.
- **Historical Data**: Users can view and analyze past simulated data via the frontend, possibly exporting it for further analysis.

## Project Structure

```
├── simulation/            # Code for simulating sensor data
├── backend/               # Node.js backend (API, microservices, databases)
├── docker/                # Docker configurations and deployment files
├── documentation/         # Documentation files (architecture, API docs, etc.)
├── frontend/              # React frontend (UI, components, graphs)
├── README.md              # Project overview and setup guide
├── LICENSE                # Project license
└── .gitignore             # Git ignore file
```

## Tech Stack

1. **Sensor Simulation**  
    - Node.js script for generating simulated BMP280-like data
    - MQTT

2. **Backend**  
    - NodeJS
    - TypeScript
    - Express
    - MongoDB/mongoose (sensor data)
    - PostgreSQL (users/configurations)
    - JWT

3. **Frontend**  
    - React
    - JWT

4. **DevOps**  
    - EsLint
    - Docker  
    - Production server (local or cloud)

5. **Project Management**  
    - GitHub Projects
    - Documentation folder

## Design Decisions

### Why Simulated Sensors?
Physical hardware was replaced with **simulated sensors** to allow more flexibility, faster prototyping, and easier deployment without requiring specialized components. This approach allows testing of backend, frontend, and database features without hardware dependency.

### Why MongoDB for Sensor Data and SQL for the Rest?
- **MongoDB** was chosen for sensor data because it handles large volumes of dynamic time-series data efficiently.
- **PostgreSQL** is used for user data, system configurations, and relational information to ensure consistency and integrity.

### Why MQTT?
MQTT will still be used to simulate IoT communication, preserving the same publish/subscribe model as in real SCADA implementations.

### Why Node.js + TypeScript, React, and Docker?
Same reasons as original design — scalability, type safety, efficient development, and containerized deployment.

---

## Possible Analysis & Visualization Ideas

To make the project more interesting and closer to a real SCADA, you could:

1. **Real-time Graphs**  
   - Temperature, humidity, and pressure changing over time.
   - Multiple time scales (last minute, last hour, last day).

2. **Statistical Analysis**  
   - Average, minimum, and maximum values per hour/day.
   - Moving averages to smooth fluctuations.

3. **Anomaly Detection**  
   - Highlight sudden spikes/drops in values.
   - Alert if readings deviate from the expected range.

4. **Comparison Views**  
   - Compare simulated days with different “weather patterns”.
   - Overlay multiple simulation runs.

5. **Export & Reports**  
   - Export data as CSV/JSON for external analysis.
   - Auto-generate daily reports with summaries and charts.

6. **Predictive Simulation**  
   - Simple linear regression to predict short-term future values.
   - Simulate “what-if” scenarios (e.g., extreme heat wave).