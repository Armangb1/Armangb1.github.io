---
title: "SweetSignal SmartHome IoT"
description: "End-to-end smart-home IoT platform: Arduino/ESP8266 publishes sensor data via MQTT → Node-RED → InfluxDB, Django REST API with JWT auth serves history & relays commands, Flutter mobile app for control."
date: 2022-12-01
tech: ["Arduino", "C++", "Python", "Django", "Django REST Framework", "Flutter", "Docker", "MQTT", "InfluxDB", "Node-RED", "IoT", "Smart Home"]
link: "https://github.com/Armangb1/SmartHome_IoT"
---

SweetSignal SmartHome IoT is an end-to-end smart-home platform built for the Introduction to Robotics & Lab course (Fall 2022, KNTU). An Arduino-based controller (ESP8266/ESP-01 + L298N) publishes sensor data over MQTT to a Mosquitto broker, Node-RED bridges the data into InfluxDB for time-series storage, and a Django REST API serves the history and relays actuator commands back to the hardware. A Flutter mobile app provides JWT-authenticated login and device control.

The architecture flows sensor data (gas, lamp, water, lock) from the Arduino → MQTT (Mosquitto:1883) → Node-RED → InfluxDB (org `sweetsignal`, bucket `IOT-buck`). The Django API (`:8000`) exposes `GET/POST /api/read/<topic>/` for querying time-series data and `POST /api/write/<topic>/` for sending actuator commands, secured with JWT authentication (simplejwt) and staff-only access. Commands published to MQTT topics (`controller1/lamp`, `controller1/water`, `controller1/lock`, `controller1/gas`) are received by the hardware.

Hardware subsystems on the Arduino include a gas valve (L298N + stepper, 1385° rotation), lamp (relay/digital out), lock (digital out), and water tap (motor + open/closed limit switches). The firmware uses PubSubClient and WiFiEsp libraries on ESP8266 with SoftwareSerial.

The stack is containerized with Docker Compose orchestrating Mosquitto, Node-RED, InfluxDB, and the Django backend (gunicorn). CI runs style checks (pycodestyle) and unit tests (with InfluxDB/MQTT mocked) on every push. The Flutter frontend provides a clean mobile interface for monitoring sensors and controlling actuators remotely.