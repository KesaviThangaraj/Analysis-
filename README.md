AI-POWERED SMART CHARGING INTELLIGENCE ENERGY MANAGEMENT SYSTEM

AI-Powered Smart Charging Intelligence Energy Management System is a modern, responsive, and intelligent full-stack energy management platform designed to monitor, optimize, and automate EV charging and power consumption. The system uses AI-based analytics, IoT sensor integration, and real-time monitoring to improve charging efficiency, reduce energy waste, and provide transparent energy usage reports.

🚀 Key System Features

 Role-Based Workspaces: Separate dashboards for Users, Charging Station Operators, and Administrators.

 🔋 Smart Charging Management: Monitor charging sessions, battery status, charging history, and energy consumption in real time.

🤖 AI-Powered Energy Optimization: Uses intelligent algorithms to recommend optimal charging schedules and reduce electricity costs.

🎙️ Voice Command Support: Users can control charging operations using voice commands through the Web Speech API.

📍 Charging Station Locator: Interactive map displaying nearby charging stations with GPS coordinates.

📊 Smart Analytics Dashboard: Displays energy consumption, charging trends, battery performance, and cost analysis using Chart.js.

🌍 Energy Usage Heatmap: Visualizes energy demand and charging station utilization across different locations.

📸 Charging Session Logs:  Stores charging reports, equipment images, and maintenance records securely.

🔔 Real-Time Notifications: Sends alerts for charging completion, low battery, maintenance schedules, and abnormal power usage.

🔐 Secure Authentication:
    JWT Authentication, bcrypt password hashing, Helmet security headers, and Rate Limiting.

🗄️ Database Schema & Architecture

The system uses MySQL as the primary database with a local JSON fallback mechanism for offline development.

Database schema location:

/backend/database/schema.sql

Database Tables

users

*User information
*Login credentials
*Roles (User, Operator, Administrator)

charging_sessions

*Charging start/end time
*Energy consumed
*Battery percentage
*Charging status
*Station ID

stations

*Charging station details
*GPS location
*Availability
*Power capacity

notifications

*Alerts
*Charging reminders
*Maintenance notifications

 🛠️ Local Installation & Setup

Prerequisites

*Node.js (v18 or higher)
*MySQL Server (v8.0 or higher)
Configure Environment Variables

Rename:

.env.example → .env

Update:

Environment
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=smart_charging
DB_PORT=3306

JWT_SECRET=generate_a_secure_token_key

Import Database

Bash

mysql -u root -p < backend/database/schema.sql

Install & Run

Bash
npm install
npm run dev

Application runs at:

http://localhost:3000

API Documentation

Authentication APIs (/api/auth)

POST /register

Register a new user.

Payload:

JSON
{
  "name":"",
  "email":"",
  "phone":"",
  "password":"",
  "role":""
}

POST /login

Login using Email & Password.

GET /profile
Get user profile.
(JWT Protected)

PUT /profile
Update profile.
(JWT Protected)

PUT /password
Change password.
(JWT Protected)

Charging Management APIs (/api/charging) (/api/charging)

POST /start

Start a charging session.
Fields

*station_id
*battery_level
*charging_mode

POST /stop

Stop charging session.

GET /sessions

Retrieve charging history.

PUT /schedule

Schedule smart charging.

Payload

JSON
{
  "startTime":"",
  "endTime":""
}

GET /stations

Retrieve available charging stations.

GET /notifications

Retrieve notifications.

PUT /notifications/read

Mark notifications as read.

Analytics APIs (/api/dashboard)

GET /stats

Returns

*Energy Consumption
*Daily Charging
*Monthly Charging
*Battery Performance
*Charging Cost
*Station Utilization
*AI Energy Recommendations

☁️ Render Deployment Guide

Deploy Database

Create a cloud MySQL database using:
*Aiven
*PlanetScale
*Railway
*Render External Database

Save:

*DB_HOST
*DB_USER
*DB_PASSWORD
*DB_NAME
*DB_PORT

Deploy Backend

Create a Render Web Service.

Build Command

Bash
npm install && npm run build

Start Command

Bash
npm start

Environment Variables
Environment
NODE_ENV=production

DB_HOST=Cloud Database Host
DB_USER=Cloud Database Username
DB_PASSWORD=Cloud Database Password
DB_NAME=smart_charging
DB_PORT=3306

JWT_SECRET=SecureRandomSecret

Deploy Frontend

Build command:
Bash
vite build && esbuild server.ts --bundle --platform=node --format=cjs --packages=external --sourcemap --outfile=dist/server.cjs


The built React application and Express backend are deployed together as a single full-stack Web Service, simplifying deployment, reducing hosting costs, and eliminating CORS issues.