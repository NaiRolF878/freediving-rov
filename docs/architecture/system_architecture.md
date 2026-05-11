# System Architecture

## High-Level Computer

NVIDIA Jetson Orin Nano

Aufgaben:

- Computer Vision
- Marker Detection
- Tracking
- Follow Logic
- Datenaufzeichnung

---

# Low-Level Controller

Pixhawk / STM32

Aufgaben:

- Stabilisierung
- Sensorfusion
- Thrustersteuerung
- Echtzeitregelung

---

# Sensorsysteme

- IMU
- Tiefensensor
- Kamerasystem

---

# Kamerasystem

Dual-Kamera-Architektur:

## Video-Kamera

- optimiert für Bildqualität
- feste Belichtung
- cineastischer Fokus

## Tracking-Kamera

- optimiert für Tracking
- spätere adaptive Belichtung möglich

---

# Beleuchtung

Gemeinsames LED-System:

- versetzte Positionierung
- Reduktion von Backscatter

---

# Antriebssystem

6-Thruster-Konfiguration:

## Horizontal

4 Thruster im X-Layout

Funktionen:

- Vortrieb
- Seitwärtsbewegung
- Rotation

## Vertikal

2 Thruster

Funktionen:

- Tiefenkontrolle
- Stabilisierung

---

# Stabilitätskonzept

- passiv stabil
- Schwerpunkt unter Auftriebspunkt
- keine aggressive Regelung

---

# Variable Buoyancy System (VBS)

## Konzept

Geplantes zentrales Auftriebssystem zur präzisen Tiefenkontrolle.

Ziele:

- leises Auf- und Absteigen
- reduzierte Thrusterlast
- geringerer Energieverbrauch
- weichere Kamerabewegungen
- stabilere Filmaufnahmen

---

# Geplante Umsetzung

- zentrales Bladder-System
- Position im Heckbereich
- Arbeitsmedium: Wasser
- Volumenänderung ca. 300 ml

---

# Betriebsstrategie

## MVP

Das MVP verwendet ausschließlich:

- vertikale Thruster
- passive Stabilität

Das VBS ist zunächst nicht integriert.

---

## Spätere Versionen

Kombinierter Betrieb:

- VBS = grobe Tiefenregelung
- vertikale Thruster = Feinregelung

---

# Vorteile

- leisere Bewegung
- bessere Energieeffizienz
- reduzierte Turbulenzen
- natürlicheres Bewegungsverhalten
- verbesserte Videoqualität

---

# Langfristige Vision

Das VBS soll das System langfristig näher an ein echtes AUV bringen und die Unterwasserbewegung deutlich effizienter und ruhiger machen.
# Zukunft

Spätere Erweiterungen:

- VBS
- KI-Tracking
- Sicherheitsfunktionen
