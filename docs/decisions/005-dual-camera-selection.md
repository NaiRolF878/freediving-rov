# ADR 005 — Auswahl des Dual-Kamera-Systems

## Status

Accepted

---

# Kontext

Das System soll gleichzeitig hochwertige Videoaufnahmen erstellen und den Taucher autonom verfolgen.

Filmaufnahme und Computer Vision stellen unterschiedliche Anforderungen an die Kamerahardware.

---

# Entscheidung

Es wird ein Dual-Kamera-System verwendet:

## Filmkamera

DJI Osmo Action 6

## Trackingkamera

Raspberry Pi Camera Module

---

# Begründung

Das Projekt konzentriert sich primär auf die Entwicklung einer autonomen Unterwasserplattform mit den Schwerpunkten:

* Robotik
* Computer Vision
* Tracking
* Systemintegration

Die Entwicklung eines eigenen Kamerasystems inklusive Bildpipeline, Unterwasseroptimierung und Videomanagement würde einen erheblichen zusätzlichen Entwicklungsaufwand bedeuten und liegt außerhalb des aktuellen Projektfokus.

Daher wird für die Filmaufnahme bewusst auf ein bereits etabliertes und ausgereiftes Kamerasystem gesetzt.

Die DJI Osmo Action 6 übernimmt die hochwertige Videoaufzeichnung, während die Raspberry Pi Camera vollständig für die Computer-Vision-Aufgaben genutzt wird.

Diese klare Trennung reduziert das Projektrisiko, vereinfacht die Softwarearchitektur und ermöglicht es, die Entwicklungsressourcen auf die Kernfunktionen des Systems zu konzentrieren.

Das Projekt verfolgt grundsätzlich den Ansatz, auf bewährte Standardkomponenten zurückzugreifen, sofern diese keinen unmittelbaren Innovationsgewinn durch eine Eigenentwicklung bieten.

---

# Konsequenzen

## Vorteile

- klare Aufgabentrennung
- robuste Softwarearchitektur
- einfache Integration in ROS2
- geringere Kompromisse zwischen Film und Tracking

## Nachteile

- zusätzlicher Platzbedarf
- höherer Stromverbrauch
- erhöhte Systemkomplexität
