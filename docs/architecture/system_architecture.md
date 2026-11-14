# System Architecture

## 3. High-Level-System

Das High-Level-System bildet die übergeordnete Steuerungs- und Verarbeitungsebene der autonomen Unterwasserplattform. Es verarbeitet die verfügbaren Sensor- und Kameradaten, erkennt und verfolgt den Taucher und leitet daraus die erforderlichen Bewegungsziele ab.

Darüber hinaus übernimmt es die Missionslogik, die Umgebungswahrnehmung sowie übergeordnete Sicherheitsfunktionen. Die direkte Umsetzung der Bewegungsvorgaben und die Ansteuerung des Antriebssystems liegen dagegen im Verantwortungsbereich des Low-Level-Systems.

### 3.1 Aufgabe und Abgrenzung

Das High-Level-System übernimmt die übergeordnete Entscheidungsfindung und bestimmt, welches Verhalten die Unterwasserplattform in der jeweiligen Betriebssituation ausführen soll.

Zu den zentralen Aufgaben gehören:

- Erfassung und Verarbeitung von Kamera- und Sensordaten
- Erkennung und Verfolgung des Tauchers
- Bestimmung der relativen Position und Bewegungsrichtung des Tauchers
- Abschätzung der Entfernung zum Taucher
- Ausführung der Missions- und Aufnahmelogik
- Planung geeigneter Bewegungsziele
- Auswertung von Umgebungsinformationen zur Hinderniserkennung
- Überwachung des Systemzustands und übergeordneter Sicherheitsfunktionen
- Kommunikation mit der Benutzeroberfläche und Verwaltung relevanter Systemdaten

Die Aufgabenverteilung zwischen High-Level und Low-Level ist dabei klar abgegrenzt:

Das High-Level-System bestimmt das gewünschte Verhalten und gibt entsprechende Positions- und Bewegungsvorgaben vor. Das Low-Level-System setzt diese Vorgaben durch die erforderliche Regelung und Ansteuerung der Aktoren um.

Die autonome Funktionalität soll dabei nicht von einer dauerhaft bestehenden Verbindung zur Benutzeroberfläche oder einer externen Kommunikationsverbindung abhängig sein.

### 3.2 Hardwarekonzept

Für die Verarbeitung der rechenintensiven Aufgaben wird eine leistungsfähige zentrale Recheneinheit vorgesehen. Diese übernimmt insbesondere Computer Vision, Tracking, Positionsbestimmung, Missionslogik und Bewegungsplanung.

Als mögliche Plattform kommt beispielsweise ein NVIDIA Jetson Orin Nano infrage. Die konkrete Hardwareauswahl ist jedoch noch offen und soll im weiteren Entwicklungsverlauf anhand folgender Kriterien bewertet werden:

- Rechenleistung für Bildverarbeitung und KI-Anwendungen
- Energieverbrauch und Wärmeentwicklung
- Verfügbare Schnittstellen
- Baugröße und Integrationsaufwand
- Kosten und Erweiterbarkeit

Als vorläufiges Architekturkonzept wird eine Aufteilung auf zwei Recheneinheiten betrachtet:

**Hauptrechner**

Mögliche Plattform: NVIDIA Jetson oder vergleichbare Recheneinheit.

Aufgaben:
- Computer Vision und Bildverarbeitung
- Tauchererkennung und Tracking
- Positionsbestimmung und Sensorverarbeitung
- Missions- und Bewegungslogik
- Bewegungsplanung und Vorgabe der Sollwerte

**Zusätzliche Recheneinheit**

Mögliche Plattform: Raspberry Pi.

Aufgaben:
- Kommunikation mit der Benutzeroberfläche
- Verwaltung externer Kommunikationsverbindungen
- Systemmanagement und Diagnose
- Koordination von Software- und Firmware-Updates

Diese Aufteilung ist zunächst eine Architekturüberlegung und keine abschließende Hardwareentscheidung. Im weiteren Entwicklungsverlauf ist zu prüfen, ob eine zusätzliche Recheneinheit tatsächlich erforderlich ist oder die Kommunikations- und Verwaltungsaufgaben ebenfalls vom Hauptrechner übernommen werden können.

Eine wesentliche Anforderung ist dabei die funktionale Unabhängigkeit der autonomen Steuerung: Ein Ausfall der zusätzlichen Recheneinheit darf die autonomen Kernfunktionen des Hauptrechners nicht unterbrechen.

Die konkrete Auswahl und Aufgabenverteilung der Recheneinheiten wird im Zuge der Systementwicklung weiter spezifiziert.

### 3.3 Wahrnehmung und Tracking

Die Wahrnehmung des Tauchers bildet eine zentrale Grundlage für den autonomen Betrieb der Plattform.

Das System soll den Taucher anhand verfügbarer Kamera- und Sensordaten erkennen und dessen relative Position zur Unterwasserplattform bestimmen.

Hierzu gehören insbesondere:

- Erkennung des Tauchers
- Bestimmung der relativen Position und Bewegungsrichtung
- Abschätzung der Entfernung
- Verfolgung des Tauchers über mehrere aufeinanderfolgende Messungen
- Verarbeitung zusätzlicher Informationen zur Unterstützung der Positionsbestimmung

Für die Tauchererkennung wird eine dedizierte Tracking-Kamera verwendet. Diese ist auf die Anforderungen der Bildverarbeitung und nicht auf die Erstellung hochwertiger Videoaufnahmen ausgelegt.

Als ergänzende Informationsquelle wird ein Beacon-System betrachtet. Die Kombination aus Kamera und Beacon stellt derzeit eine bevorzugte Entwicklungsrichtung dar, sofern sich eine technisch geeignete Umsetzung realisieren lässt.

Ein visueller Marker kann insbesondere für erste Funktionstests unter kontrollierten Bedingungen, beispielsweise im Schwimmbecken, eingesetzt werden. Im weiteren Entwicklungsverlauf soll untersucht werden, ob ein Beacon den Marker ersetzen oder die kamerabasierte Erkennung sinnvoll ergänzen kann.

Die konkrete Tracking-Technologie und deren Zusammenspiel bleiben zunächst offen.

**Kamerasystem**

Die Bildverarbeitung und die eigentliche Videoaufzeichnung werden durch zwei getrennte Kamerasysteme realisiert:

**Tracking-Kamera**
- Raspberry Pi Camera Module
- Nutzung für Computer Vision und Tauchertracking
- Bereitstellung der Bilddaten für die Wahrnehmung und Positionsbestimmung

**Videokamera**
- DJI Osmo Action 6
- Hochwertige Videoaufzeichnung
- Eigenständige Aufzeichnung unabhängig von der Tracking-Verarbeitung

Die Trennung ermöglicht eine gezielte Optimierung beider Kamerasysteme für ihre jeweilige Aufgabe. Die Videoaufzeichnung soll nicht von der Funktionsfähigkeit der Tracking-Software abhängig sein.

### 3.4 Missions- und Bewegungslogik

Die Missionslogik bestimmt das übergeordnete Verhalten der Plattform abhängig von der gewählten Betriebsart und der aktuellen Situation.

Dazu gehören insbesondere die unterschiedlichen Aufnahmemodi:

- Freediving – Deep Dive
- Freediving – Streckentauchen
- Spaßmodus – Freediving und Scuba

Die gewählte Betriebsart beeinflusst unter anderem die gewünschte relative Position und Entfernung zum Taucher sowie das angestrebte Bewegungsverhalten der Plattform.

Aus den Tracking-Daten und der Missionslogik leitet das High-Level-System geeignete Positions- und Bewegungsvorgaben ab.

Dabei wird zwischen dem gewünschten Zielzustand und dessen Umsetzung unterschieden:

- **Zielvorgabe:** Welche relative Position soll die Plattform zum Taucher einnehmen?
- **Bewegungsvorgabe:** Welche Bewegung ist erforderlich, um diese Position zu erreichen oder beizubehalten?
- **Regelung und Ansteuerung:** Umsetzung der Bewegung durch das Low-Level-System.

Die konkrete Bewegungsplanung und die Übergabe der Sollwerte an das Low-Level-System werden im weiteren Entwicklungsverlauf spezifiziert.

### 3.5 Umgebungswahrnehmung und Sicherheit

Neben der Taucherverfolgung muss die Plattform ihre unmittelbare Umgebung erfassen können, um Hindernisse zu erkennen und Kollisionen zu vermeiden.

Hierzu sollen zusätzliche Sensorinformationen ausgewertet werden. Insbesondere Sonar wird als mögliche Grundlage für die Umgebungswahrnehmung betrachtet.

Das High-Level-System übernimmt dabei die Auswertung der verfügbaren Umgebungsinformationen und berücksichtigt erkannte Hindernisse bei der Bewegungsplanung.

Die Sicherheitslogik muss insbesondere folgende Situationen berücksichtigen:

- Verlust des erkannten Tauchers
- Hindernisse im Bewegungsbereich
- Abweichungen vom erwarteten Systemzustand
- Ausfall einzelner Komponenten oder Kommunikationsverbindungen

Bei einem Verlust des Tauchers soll das System zunächst eine definierte Wiedererkennungsstrategie verfolgen. Bleibt der Taucher über einen festzulegenden Zeitraum unauffindbar, muss eine geeignete Sicherheitsroutine eingeleitet werden.

Die Kollisionsvermeidung hat dabei grundsätzlich Vorrang vor der gewünschten Kameraposition und der Aufnahmefunktion.

Die konkrete Ausgestaltung der Sicherheitszustände und die Zusammenarbeit mit dem Low-Level-System werden im weiteren Verlauf der Architekturentwicklung festgelegt.

### 3.6 Kommunikation und Datenverwaltung

Das High-Level-System stellt die Kommunikation zwischen den internen Systemkomponenten, der Benutzeroberfläche und externen Schnittstellen sicher.

Für die Kommunikation mit der Oberfläche ist eine mobile Anwendung vorgesehen. Über diese sollen unter anderem Betriebszustände angezeigt und ausgewählte Funktionen gesteuert werden können.

Für die Verbindung zur Oberfläche werden unterschiedliche Kommunikationswege betrachtet:

**Kabelgebundene Verbindung (Tether)**

Eine kabelgebundene Verbindung soll auch während des Unterwasserbetriebs genutzt werden können. Sie kann insbesondere folgende Funktionen unterstützen:

- Übertragung von Live-Bilddaten
- Steuerungs- und Statusinformationen
- Diagnose und Wartung
- Datenübertragung und Software-Updates

Die konkrete Übertragungstechnik ist noch offen. Ethernet stellt hierfür eine mögliche Lösung dar.

**Drahtlose Verbindung**

Für die Kommunikation an der Wasseroberfläche werden WLAN und Mobilfunk betrachtet. Als Mobilfunkstandard kommen LTE/4G und gegebenenfalls 5G infrage.

Da WLAN und Mobilfunk unter Wasser nicht regulär zur Verfügung stehen, muss die entsprechende Antennentechnik für den Betrieb an der Wasseroberfläche ausgelegt werden. Eine möglichst integrierte Positionierung der Antenne ist bereits bei der mechanischen Gestaltung der Plattform zu berücksichtigen.

Eine bestehende Verbindung zur Benutzeroberfläche ist keine Voraussetzung für den autonomen Betrieb. Die Plattform muss ihre autonomen Funktionen auch bei unterbrochener Funk- oder Kabelverbindung selbstständig fortführen können.

**Datenverwaltung und Updates**

Das High-Level-System soll relevante Betriebs- und Missionsdaten erfassen und für Diagnose- und Auswertungszwecke bereitstellen. Dazu gehören insbesondere:

- Tracking- und Positionsdaten
- Sensorinformationen
- Systemzustände und Fehlermeldungen
- Missions- und Betriebsdaten

Die eigentliche Videoaufzeichnung erfolgt unabhängig davon durch die DJI Osmo Action 6.

Software- und Firmware-Updates sollen perspektivisch über die verfügbaren Kommunikationsschnittstellen ermöglicht werden. Eine zusätzliche Recheneinheit kann dabei die Koordination und Verwaltung der Updates übernehmen.

Die Installation von Updates muss in einem geeigneten Systemzustand erfolgen. Die konkrete Update- und Kommunikationsarchitektur ist noch festzulegen.

### 3.7 Softwarearchitektur

Als Grundlage für die übergeordnete Softwarearchitektur ist ROS 2 vorgesehen.

Die Software soll modular aufgebaut werden, sodass einzelne Funktionen unabhängig entwickelt, getestet und erweitert werden können.

Zu den vorgesehenen Funktionsbereichen gehören:

- Kamera- und Sensorverarbeitung
- Tauchererkennung und Tracking
- Positionsbestimmung
- Missions- und Bewegungslogik
- Umgebungswahrnehmung
- Sicherheitsfunktionen
- Kommunikation und Systemmanagement

Die konkrete Aufteilung in ROS-2-Nodes, deren Schnittstellen und die Kommunikation mit dem Low-Level-System werden im weiteren Entwicklungsverlauf festgelegt.

Die Architektur soll eine schrittweise Entwicklung und Validierung ermöglichen. Einzelne Funktionen sollen zunächst unabhängig getestet und anschließend schrittweise in das Gesamtsystem integriert werden.

Simulationen und aufgezeichnete Sensordaten können ergänzend genutzt werden, um Funktionen bereits vor der vollständigen Integration an der realen Plattform zu überprüfen.

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
