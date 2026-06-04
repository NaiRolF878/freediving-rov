# Autonomous Freediving ROV

> Entwicklung einer autonomen Unterwasserdrohne für Freediver und Gerätetaucher.

---

## Projektvision

Ziel dieses Projekts ist die Entwicklung einer autonomen Unterwasserplattform, die Taucher selbstständig begleitet und hochwertige Videoaufnahmen erstellt.

Langfristig soll daraus eine modulare Plattform entstehen, die folgende Bereiche vereint:

- Autonome Filmaufnahmen
- Intelligentes Tauchertracking
- Trainingsanalyse
- KI-gestützte Auswertung
- optionale Sicherheitsassistenz

---

## Projektziele

### MVP (Version 1)

- Markerbasiertes Tracking
- Stabiler Follow-Modus
- Videoaufnahme
- Datenaufzeichnung
- Modulare Softwarearchitektur

### Zukünftige Erweiterungen

- Visual Tracking
- Sonar-assisted Tracking
- Markerfreies Tracking
- KI-gestützte Tauchererkennung
- Variable Buoyancy System (VBS)
- Trainingsanalyse
- Gesture Control
- Safety Features

---

## Tracking-Konzept

Das System verfolgt einen hybriden Ansatz:

1. Marker Tracking
2. Visual Tracking
3. Sonar-assisted Tracking
4. Motion Prediction

Dadurch soll auch bei kurzzeitigem Markerverlust ein stabiles Tracking gewährleistet werden.

---

## Hardware-Konzept

- Druckkörper für ca. 100 m Einsatztiefe
- 6-Thruster-Konfiguration
- Dual-Kamera-System
- Passive Stabilisierung
- spätere VBS-Integration
- Sonarsystem als zukünftige Erweiterung

---

## Software-Architektur

### High-Level

- ROS2
- OpenCV
- Tracking
- State Machine
- Logging

### Low-Level

- Pixhawk
- ArduPilot / ArduSub
- MAVLink
- Sensorfusion
- Thrustersteuerung

---

## Aktueller Entwicklungsstand

Das Projekt befindet sich aktuell in der Architektur- und Konzeptphase.

Aufgrund der anstehenden Klausurphase wird die aktive Entwicklung vorübergehend reduziert.

Der nächste Entwicklungsschritt ist die Implementierung der Softwarearchitektur auf Basis von ROS2.

---

## Repository-Struktur
/docs Dokumentation
/software High-Level Software
/firmware Low-Level Firmware
/hardware Mechanik & Elektronik
/simulations Simulationen
/datasets Trainings- und Testdaten
