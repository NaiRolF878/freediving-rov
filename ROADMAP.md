# Projekt-Roadmap

Diese Roadmap beschreibt die übergeordneten Entwicklungsschritte des Projekts.

Jede Phase definiert:

- das Ziel der jeweiligen Entwicklungsstufe,
- die wesentlichen Entwicklungsaufgaben,
- das erwartete Ergebnis.

Detaillierte technische Entscheidungen und konkrete Implementierungsaufgaben werden in den jeweiligen Architektur-, Konzept- und Entscheidungsdokumenten festgehalten.

---

## Phase 0 – Projektgrundlagen und technische Konzeption

### Ziel

Die bisher entwickelten Projektideen, Anforderungen und technischen Konzepte zu einer konsistenten Grundlage für die weitere Entwicklung zusammenführen.

### Schwerpunkte

- Projektziel und Einsatzbereich konsolidieren.
- Den ersten Unterwasserdemonstrator und seine drei Entwicklungsstufen definieren.
- Die Teststrategie festlegen: Einzeltests → Integration → Demonstrator.
- Das bestehende Hardware- und Systemkonzept mit den aktuellen Anforderungen abgleichen.
- Die grundlegenden Aufnahmemodi dokumentieren.
- Anforderungen an Tauchertracking und Umgebungswahrnehmung ableiten.
- Offene technische Entscheidungen klar identifizieren.
- Widersprüche in der bestehenden GitHub-Dokumentation bereinigen.

### Ergebnis

Es liegt eine konsistente und nachvollziehbare Projektgrundlage vor, aus der hervorgeht:

- was der erste Demonstrator leisten soll,
- welche Entwicklungsstufen vorgesehen sind,
- welche technischen Konzepte bereits bestehen,
- welche Entscheidungen noch offen sind.

**Status:** In Bearbeitung

---

## Phase 1 – Einzelvalidierung von Software und Hardware

### Ziel

Kritische Funktionen und Komponenten möglichst früh und unabhängig vom vollständigen Fahrzeug testen.

### Software

- Einzelne Funktionen mit simulierten oder aufgezeichneten Daten testen.
- Grundlagen der ROS-2-Softwarearchitektur entwickeln und validieren.
- Tracking- und Positionsinformationen zunächst unabhängig von der Fahrzeugbewegung verarbeiten.
- Verhalten bei Zielverlust als einzelne Funktion untersuchen.

### Hardware

- Thruster und deren Ansteuerung einzeln testen.
- Trackingkamera und Filmkamera unabhängig testen.
- Sensoren hinsichtlich Funktion und Datenqualität prüfen.
- Geeignete Beacon-Technologien untersuchen und testen.
- Sonar und dessen Eignung für die spätere Umgebungswahrnehmung bewerten.

### Ergebnis

Die für den ersten Demonstrator vorgesehenen kritischen Funktionen und Komponenten sind einzeln getestet. Risiken und ungeeignete Komponenten werden frühzeitig erkannt.

---

## Phase 2 – Systemintegration

### Ziel

Die zuvor einzeln getesteten Software- und Hardwarekomponenten schrittweise zu einem funktionierenden Gesamtsystem verbinden.

### Schwerpunkte

- Sensoren in die Softwarearchitektur integrieren.
- Datenflüsse zwischen den Systemkomponenten aufbauen.
- Wahrnehmung und Tracking mit der geschätzten Zielposition verbinden.
- Fahrzeugsteuerung und Thrusteransteuerung integrieren.
- Schnittstellen zwischen High-Level-Software und Low-Level-Fahrzeugsteuerung testen.
- Logging und Diagnosefunktionen für spätere Tests vorbereiten.

### Ergebnis

Die wesentlichen Komponenten können gemeinsam Daten austauschen und als integrierte Funktionsketten getestet werden.

Ein vollständig autonomer Unterwassereinsatz ist in dieser Phase noch nicht erforderlich.

---

## Phase 3 – Demonstrator Stufe 1: Wahrnehmung bei manueller Steuerung

### Ziel

Die Wahrnehmung und Positionsbestimmung eines realen Tauchers unter kontrollierten Unterwasserbedingungen validieren.

### Schwerpunkte

- Taucher zuverlässig als Ziel erkennen.
- Relative Position des Tauchers bestimmen.
- Richtung und Abstand zum Taucher bestimmen.
- Die geschätzte Zielposition während des Tests darstellen.
- Eine Meldung bei Zielverlust ausgeben.
- Die Plattform weiterhin manuell steuern.
- Die vollständige Videoaufnahme parallel betreiben.

### Ergebnis

Es ist nachgewiesen, dass das System die für das spätere autonome Folgen erforderlichen Informationen unter realen Unterwasserbedingungen erfassen kann, ohne dass die autonome Fahrzeugbewegung bereits Bestandteil des Tests ist.

**Testumgebung:** kontrollierte Unterwasserumgebung / Becken

---

## Phase 4 – Demonstrator Stufe 2: Autonomes Folgen

### Ziel

Die Plattform soll den erkannten Taucher in einer kontrollierten Umgebung autonom begleiten.

### Schwerpunkte

- Wahrnehmungs- und Positionsdaten für die autonome Bewegung verwenden.
- Dem Taucher selbstständig folgen.
- Die angestrebte Position und den Abstand abhängig vom gewählten Aufnahmemodus anpassen.
- Die Videoaufnahme während des autonomen Betriebs aufrechterhalten.
- Bei kurzfristigem Zielverlust für eine definierte Zeit warten.
- Bei dauerhaftem Zielverlust eine kontrollierte Sicherheitsroutine einleiten.

### Ergebnis

Die Plattform kann einen Taucher autonom begleiten und dabei ein definiertes Aufnahmeverhalten umsetzen.

Die Hindernisvermeidung ist in dieser Stufe noch nicht Bestandteil der autonomen Bewegungsentscheidung.

---

## Phase 5 – Demonstrator Stufe 3: Autonomes Folgen mit Kollisionsvermeidung

### Ziel

Das autonome Folgen um eine aktive Umgebungswahrnehmung und Kollisionsvermeidung erweitern.

### Schwerpunkte

- Die Umgebung mit dem vorgesehenen Sensorsystem erfassen.
- Relevante Hindernisse erkennen.
- Hindernisse aktiv in die Bewegungsplanung einbeziehen.
- Kollisionen vermeiden.
- Die gewünschte Kameraposition nur anfahren, wenn dies sicher möglich ist.

### Ergebnis

Die Plattform kann den Taucher autonom begleiten und gleichzeitig auf ihre Umgebung reagieren.

Dabei gilt als übergeordnete Systemregel:

> Kollisionsvermeidung und Sicherheit haben immer Vorrang vor der gewünschten Kameraposition und dem gewünschten Videomaterial.

---

## Phase 6 – Langfristige Weiterentwicklung

Diese Phase beginnt nach dem erfolgreichen Nachweis der grundlegenden Fähigkeiten des Demonstrators.

Mögliche Entwicklungsrichtungen sind:

- Erweiterung und Verfeinerung der Aufnahmemodi,
- Tests und Erweiterungen im Freiwasser,
- Verbesserung der Trackingverfahren,
- markerfreie oder weiterentwickelte visuelle Tauchererkennung,
- Erweiterung der autonomen Navigationsfähigkeiten,
- Variable Buoyancy System,
- weitere Sicherheitsfunktionen,
- spätere Trainings- und Analysefunktionen.

Die konkreten Erweiterungen werden auf Grundlage der Ergebnisse der vorherigen Demonstratorstufen priorisiert.
