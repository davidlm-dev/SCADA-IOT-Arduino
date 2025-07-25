# SCADA system project

## About the project

This project consists of a **Supervisory Control and Data Acquisition** **(SCADA)** system based on **Arduino Uno R4 WiFi** and a **BMP280 sensor**. The system is designed to monitor and control environmental variables such as temperature and pressure, and to demonstrate knowledge in areas like:

1. **IoT**

2. **Backend**

3. **Frontend**

4. **Databases**

5. **Communication protocols**

6. **DevOps tools**

System Architecture Overview

The system is composed of several components working together:

- Arduino Uno R4 WiFi for sensor data acquisition.

- MQTT protocol for efficient, lightweight communication.

- A backend built with Node.js (TypeScript) for data processing and API management.

- Two databases:

    - PostgreSQL for storing sensor data.

    - MongoDB for managing users and system configurations.

- A frontend in React for data visualization and system control.

- JWT authentication for secure user access.

- Docker for deployment and containerization.

- Microservice architecture for scalability and modularity.

## Project Objective

The main goal of this project is to develop a **Supervisory Control and Data Acquisition (SCADA)** system for the **management and monitoring** of a **weather station**. The system will use an **Arduino Uno R4 WiFi** and a **BMP280 sensor** to measure various environmental variables, including:

- **Temperature**
- **Humidity**
- **Pressure**
- **Altitude** (measured by the BMP280 sensor)

Furthermore, the system will allow **remote management** of the weather station through a **React frontend**, where users will be able to:

- **Visualize real-time graphs** of temperature, humidity, pressure, and altitude data.
- **Access historical data** stored in a database for long-term analysis.
- **Receive alerts** both **virtually** (on the UI) and **physically** (through an LED matrix on the hardware) if any values exceed critical thresholds (e.g., high temperature, humidity out of range, etc.).

## **SCADA Breakdown:**

This section breaks down how each part of the SCADA system is addressed and implemented in the project.

### **S - Supervisory**

- **Remote Management**: Users can manage and control the weather station from the **React-based frontend**. This includes setting sensor parameters, adjusting sampling rates, and managing alert thresholds.
- **Real-Time Monitoring**: Data from the **BMP280 sensor** (temperature, humidity, pressure, and altitude) is continuously monitored and displayed in real-time.
- **Visualizations**: The frontend displays dynamic **graphs** of sensor data, offering a clear overview of the system's performance.

### **C - Control**

- **Alarm Systems**: The SCADA system will trigger **alerts** when sensor values exceed predefined thresholds. These alerts are both:
  - **Virtual**: Shown on the frontend UI (e.g., warning messages, visual indicators).
  - **Physical**: An **LED matrix** connected to the **Arduino Uno R4** will provide physical notifications of critical sensor readings.
- **Adjustable Parameters**: Users can modify sensor configurations (e.g., the **sampling rate**) or adjust **alarm thresholds** from the frontend to control how the system operates.

### **A - Acquisition & Data**

- **Data Acquisition**: The **Arduino Uno R4 WiFi** will collect data from the **BMP280 sensor**, which measures temperature, humidity, pressure, and altitude. The sensor data will be sent to the backend for processing.
- **Data Communication**: Data will be sent using the **MQTT protocol**, allowing for lightweight and efficient transmission between the sensor (Arduino) and the backend server.
- **Data Storage**: The project uses a **dual-database architecture** to store and manage data:
  - **PostgreSQL** will store time-series data from the sensor (temperature, humidity, pressure, altitude) to ensure data integrity and efficient querying.
  - **MongoDB** will manage user data, system configurations, and other dynamic data (e.g., user preferences, sensor settings).
- **Historical Data**: Users can access historical data through the **React frontend**, which will display the data in **graphical form**. This historical data can also be exported for further analysis if needed.
- **Real-Time Sensor Data**: The **Arduino Uno R4 WiFi** continuously reads the sensor data, ensuring the backend receives and processes the most up-to-date information.
- **Sensor Calibration**: The system allows calibration of the **BMP280 sensor** if needed, and adjustments can be made based on specific operational requirements (e.g., measuring altitude accurately or adjusting temperature readings).


## Project Structure

The project's folder structure is:

    ├── arduino/               # Arduino code and configurations
    ├── backend/               # Node.js backend (API, microservices, databases)
    ├── docker/                # Docker configurations and deployment files
    ├── documentation/         # Documentation files (architecture, API docs, etc.)
    ├── frontend/              # React frontend (UI, components, graphs)
    ├── README.md              # Project overview and setup guide
    ├── LICENSE                # Project license
    └── .gitignore             # Git ignore file

## Tech Stack

This point is divided by the different parts in which this project is going to be built.It is only mentioned the most relevant packages/information which may vary meanwhile the project is being develop. This parts and their respectful Tech Stacks are:



1. Arduino  
    - Arduino Uno R4 WiFi
    - BMP280
    - MQTT 

2. Backend
    
    - NodeJS
    - TypeScript
    - Express
    - MongoDB/mongoose
    - PostgreSQL
    - JWT
3. Frontend

    - React
    - JWT
4. DevOps

    - EsLint
    - Docker   
    - Production server (maybe hosted on my own PC or third party such as AWS)
5. Project Managment

    - GitHub Projects
    - Documentation folder

## Design Decisions 

As mentioned in the previous sections, several technologies have been chosen for this project, some of which were selected intentionally to learn new skills, while others were chosen based on their specific advantages in the context of this SCADA system.

### Why Arduino Uno R4 WiFi?

The Arduino Uno R4 WiFi was selected for its simplicity, accessibility, and the addition of built-in Wi-Fi capabilities, which make it ideal for IoT applications. Arduino’s open-source nature and large community support make it an excellent choice for rapid prototyping. The Wi-Fi feature in the R4 model enables wireless communication, which is essential for real-time data transfer from the sensor to the backend without the need for complex setups. Additionally, Arduino Uno R4 is well-documented, ensuring that I can quickly resolve any issues during the development phase.

This choice allows me to focus more on the IoT communication aspect (MQTT) and data processing rather than spending time on configuring hardware or custom network stacks.

Also its matrix led could be useful to implement real time notifications for the SCADA system physical operation.

### Why BMP280?

The BMP280 sensor was chosen for its compact size, low power consumption, and ability to measure both temperature and pressure accurately. These characteristics make it ideal for environmental monitoring in a SCADA system. While there are more advanced sensors available, the BMP280 offers a cost-effective solution with sufficient accuracy for the project’s needs. Furthermore, it has excellent community support and is widely used in hobbyist projects, which allows for easier troubleshooting and integration into the system.

The choice of the BMP280 sensor is driven by its simplicity, availability, and its suitability for demonstrating basic sensor readings in a SCADA system without overcomplicating the hardware side of the project.

### Why MQTT?

The MQTT protocol was selected due to its lightweight nature and low-bandwidth requirements, which make it highly efficient for IoT communication. MQTT is designed specifically for environments with low bandwidth or high latency, which is often the case in remote or distributed sensor systems. Additionally, MQTT supports publish/subscribe messaging, making it easy to handle multiple devices or sensors without complex connection management.

Since the project involves real-time data communication between an Arduino-based sensor and the backend, MQTT was chosen for its real-time message delivery and reliable transmission of sensor data. Furthermore, MQTT brokers like Mosquitto are simple to configure, lightweight, and easily integrate with Node.js, which is the core technology for the backend.

There is also anotther IoT protocol that may be interestin. This protocol is CoAP but it is based on UDP and in this case it does not suit our realibility specifications. Also MQTT supports QoS and CoAP does not and i will take the trade off between sacrificing bandwidth for realibility.


### Why Node.js + Typescript?

The choice of Node.js was driven by its ability to handle real-time data streams effectively, which is crucial for this SCADA system where sensor data needs to be processed continuously. Node.js offers non-blocking, event-driven architecture, making it a great fit for I/O-heavy applications like this one, where sensor readings must be constantly processed and transmitted.

The decision to use TypeScript was made to enhance code reliability, scalability, and maintainability. By using TypeScript, I gain the advantages of strong typing and early error detection, which is beneficial for a backend that might evolve into a more complex system in the future.

Personally I also have a some background with this techs so it will make the development easier for me.

### Why PostgreSQL and MongoDB?

- PostgreSQL was chosen for storing sensor data due to its robustness, ACID compliance, and the ability to handle complex queries efficiently. PostgreSQL is a powerful relational database that ensures data consistency, which is important for time-series data coming from the BMP280 sensor.

- MongoDB was chosen for managing user data and system configurations due to its flexibility in handling semi-structured or unstructured data. MongoDB’s document-based structure is ideal for storing dynamic data such as user preferences and system settings, which might change frequently during operation.

This dual-database architecture allows the system to leverage the best features of both databases: the reliability and query power of PostgreSQL for time-series data, and the flexibility and scalability of MongoDB for more dynamic data.

### Why React?

I chose React for this project because I wanted to try it out. I have some prior experience with Angular, which I used for a back-office application, as well as Flutter, which I applied in a custom Drone Shop project for my degree. These experiences allowed me to compare the strengths and weaknesses of different frontend technologies, and React seemed like a good fit for this project due to its flexibility and strong community support.

### Why Docker?

Docker was chosen for its ability to containerize each component of the system, ensuring a consistent environment across development, testing, and production. Using Docker makes it easy to deploy and run the project on different machines without worrying about system dependencies. This is especially useful for a project that might need to be deployed on both a local server and potentially a cloud platform later on. Docker also simplifies setting up microservices and managing their intercommunication in a scalable way.

Using Docker Compose will allow the entire system, including the backend services, databases, and MQTT broker, to run seamlessly in a single containerized environment.


## References