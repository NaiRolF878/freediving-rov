
# Projektstatus – Autonomous Freediving ROV

## 1. Zweck dieses Dokuments

Dieses Dokument fasst den aktuellen Entwicklungsstand zusammen.
Es unterscheidet zwischen bestätigten Entscheidungen, vorläufigen
Entwurfsannahmen und offenen technischen Fragen.

Es dient als Ausgangspunkt für die weitere System- und
Softwarearchitektur.

## 2. Projektziel

Entwicklung einer autonomen Unterwasserplattform, die Freediver
und Gerätetaucher begleitet und eigenständig Videoaufnahmen erstellt.

Die Plattform soll modular aufgebaut sein. Erweiterungen wie
KI-gestützte Tauchererkennung und Trainingsanalyse sind langfristige
Ziele und keine Voraussetzung für das erste funktionsfähige MVP.

Das System soll den Taucher filmen, aber weder einen Buddy noch
einen erforderlichen Sicherheits- oder Sicherungstaucher ersetzen.

## 3. Bestätigte Projektentscheidungen

### Kamerakonzept

- Filmkamera: DJI Osmo Action 6
- Trackingkamera: Raspberry Pi Camera Module
- Begründung: Trennung von hochwertiger Filmaufnahme und
  kamerabasierter Wahrnehmung

Referenz: `docs/decisions/005-dual-camera-selection.md`

### Softwareansatz

- ROS 2 als Grundlage für die übergeordnete Softwarearchitektur
- Modulare Aufteilung in Wahrnehmung, Zustandsschätzung,
  Missionslogik und Bewegungssteuerung
- Simulation und Softwareentwicklung sollen möglichst vor der
  Anschaffung und Integration der Hardware beginnen.

### Tracking-Grundsatz

- Kamerabasierte Wahrnehmung ist ein zentraler Bestandteil.
- Sonar dient vorrangig der Umgebungswahrnehmung und
  Kollisionsvermeidung.
- Sonar ist nicht als alleinige Methode zur Taucherverfolgung
  vorgesehen.
- Ein zusätzlicher akustischer Sender am Taucher wird als mögliche
  Unterstützung untersucht; eine geeignete Lösung ist noch offen.

## 4. Vorläufige Entwurfsannahmen

Die folgenden Punkte sind noch nicht als technisch validierte
Systemeigenschaften zu verstehen:

- angestrebte Einsatztiefe: etwa 100 m
- geplante kompakte Bauform
- vorgesehene Sechs-Thruster-Konfiguration
- Einsatz einer übergeordneten Recheneinheit mit ROS 2
- mögliche Nutzung von Pixhawk und ArduSub für die
  untergeordnete Fahrzeugsteuerung
- passive Stabilisierung und spätere Erweiterbarkeit um ein
  Variable Buoyancy System (VBS)

Komponentenwahl, Leistungsfähigkeit und technische Machbarkeit
müssen im weiteren Entwicklungsverlauf überprüft werden.

## 5. Offene technische Fragen

### Tauchertracking

- Welches Trackingverfahren bildet das erste MVP?
- Ist ein visueller Marker der erste zuverlässige Referenzpunkt?
- Welche Rolle kann ein akustischer Sender übernehmen?
- Wie werden Position, Bewegungsrichtung und Unsicherheit des
  geschätzten Taucherzustands beschrieben?
- Wie erfolgt die Wiedererkennung nach einem Trackingverlust?

### Sicherheit und Missionslogik

- Welche Zustände und Übergänge benötigt die State Machine?
- Wie verhält sich das System bei Verlust des Trackings?
- Welche Grenzen gelten für Abstand, Geschwindigkeit und Bewegung?
- Wie wird ein sicherer Abbruch definiert?

### Softwarearchitektur

- Welche ROS-2-Nodes werden benötigt?
- Welche Nachrichten und Koordinatensysteme verwenden sie?
- Welche Aufgaben liegen bei ROS 2 und welche bei der
  Fahrzeugsteuerung?
- Wie können Tracking und Missionslogik ohne echte Hardware
  getestet werden?

### Hardware

- Welche Recheneinheit wird endgültig gewählt?
- Welche Sensoren sind für das erste MVP erforderlich?
- Wie werden Druckfestigkeit, Auftrieb, Stabilität und
  Energiebedarf nachgewiesen?

## 6. Nächste Entwicklungsschritte

1. Bestehende Dokumentation prüfen und Widersprüche bereinigen.
2. Systemarchitektur und Verantwortlichkeiten der Softwaremodule
   festlegen.
3. ROS-2-Nodes, Schnittstellen und Koordinatensysteme definieren.
4. Missionszustände und Sicherheitsreaktionen spezifizieren.
5. Softwareprototyp mit simulierten Sensordaten erstellen.
6. Hardwareintegration auf Basis der validierten Anforderungen planen.

## 7. Entwicklungsstatus

Aktuelle Phase: Konzeptkonsolidierung und Vorbereitung der
Softwarearchitektur.

Die Umsetzung und Validierung der Hardware stehen noch aus.
