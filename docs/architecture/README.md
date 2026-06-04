# Systemarchitektur

Dieses Verzeichnis dokumentiert den geplanten Aufbau des Gesamtsystems.

## Schwerpunkte

- ROS2 Architektur
- Pixhawk / ArduSub Integration
- MAVLink Kommunikation
- Sensorfusion
- Datenaufzeichnung
- State Machines

---

## Grundprinzip

### High-Level

Jetson Orin Nano + ROS2

Aufgaben:

- Tracking
- Computer Vision
- Follow-Logik
- Logging

### Low-Level

Pixhawk + ArduSub

Aufgaben:

- Stabilisierung
- Tiefenregelung
- Thrustersteuerung

---

Die Architektur ist modular aufgebaut und auf zukünftige Erweiterungen vorbereitet.
