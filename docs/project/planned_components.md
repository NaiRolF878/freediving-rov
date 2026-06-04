# Geplante Hauptkomponenten

## Recheneinheit

- NVIDIA Jetson Orin Nano

---

## Flug-/ROV-Controller

- Pixhawk
- ArduPilot / ArduSub

---

## Kamerasystem

### Filmkamera

Aktuell vorgesehen:

- DJI Osmo Action 6

Gründe:

- sehr gute Bildqualität
- integrierte Bildstabilisierung (optional)
- eigenständige Videoaufzeichnung
- kein eigener Unterwassermodus im ROV erforderlich
- hohe Zuverlässigkeit

---

### Trackingkamera

Aktuell vorgesehen:

- Raspberry Pi Camera Module

Aufgabe:

- Marker Detection
- Visual Tracking
- spätere Sonar-Sensorfusion
- keine Videoaufzeichnung für den Benutzer

Die Trackingkamera wird unabhängig von der Filmkamera betrieben.

---

## Antrieb

- 6 × Unterwasserthruster

Aktuell wird eine Lösung auf Basis von Blue Robotics Komponenten favorisiert.

---

## Sensorik

### Basis

- IMU
- Drucksensor / Tiefensensor

### Geplante Erweiterungen

- Sonarsystem
- Leckagesensor
- Drucküberwachung

---

## Auftriebssystem

Für spätere Entwicklungsphasen vorgesehen:

- Variable Buoyancy System (VBS)
- wasserbasiertes Bladder-System

---

## Beleuchtung

Gemeinsames LED-System für:

- Filmkamera
- Trackingkamera

Die Belichtung soll zukünftig aktiv geregelt werden.
