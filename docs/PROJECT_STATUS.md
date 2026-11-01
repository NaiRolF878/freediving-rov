# Projektstatus – Autonomous Freediving ROV

## 1. Zweck dieses Dokuments

Dieses Dokument fasst den aktuellen Entwicklungsstand des Projekts zusammen.

Es unterscheidet zwischen:

- bestätigten Projektentscheidungen,
- vorläufigen Entwurfsannahmen,
- offenen technischen Fragen.

Es dient als zentrale fachliche Entscheidungsbasis für die weitere Entwicklung. Bestehende Architektur-, Tracking- und Roadmap-Dokumente sollen mit den hier festgehaltenen Projektentscheidungen abgeglichen werden.

Technische Ansätze, die in anderen Dokumenten beschrieben werden, sind nicht automatisch verbindliche Entscheidungen.

---

## 2. Projektziel

Ziel des Projekts ist die Entwicklung einer modularen, autonomen Unterwasserplattform, die Freediver und Gerätetaucher begleitet und eigenständig Videoaufnahmen erstellt.

Die Plattform soll den Taucher während eines Tauchgangs erfassen und langfristig in der Lage sein, ihre Position und Bewegung an unterschiedliche Aufnahmeziele anzupassen.

Das Projekt verbindet insbesondere die Bereiche:

- Robotik,
- Computer Vision,
- Unterwassertechnik,
- autonome Systeme,
- System Engineering.

Die Plattform ist als zusätzliche Kameraplattform vorgesehen. Sie ersetzt weder einen Buddy noch einen erforderlichen Sicherheits- oder Sicherungstaucher.

Langfristige Erweiterungen, beispielsweise weiterentwickelte KI-gestützte Tauchererkennung oder Trainingsanalyse, sind möglich, aber keine Voraussetzung für den ersten funktionsfähigen Unterwasserdemonstrator.

---

## 3. Erster zentraler Entwicklungsmeilenstein

Der erste zentrale Meilenstein des Projekts ist ein **funktionierender Unterwasserdemonstrator mit einem realen Taucher**.

Die Entwicklung soll schrittweise erfolgen. Simulationen, Einzeltests von Softwarefunktionen und Hardwarekomponenten sowie Integrationsversuche dienen als vorbereitende Meilensteine auf dem Weg zum realen Demonstrator.

Die erste Testumgebung soll eine **kontrollierte Unterwasserumgebung, beispielsweise ein Becken**, sein.

Ein späterer Einsatz im Freiwasser ist ein weiterer Entwicklungsschritt und keine Voraussetzung für den ersten Demonstrator.

---

## 4. Demonstratorstufen

Der Unterwasserdemonstrator wird schrittweise entwickelt und validiert.

### Stufe 1 – Tauchererkennung und manuelle Steuerung

In der ersten Demonstratorstufe wird die Wahrnehmung des Tauchers unter realen Unterwasserbedingungen getestet, während die Bewegung der Plattform weiterhin manuell gesteuert wird.

Das System soll dabei:

- den Taucher als Ziel erkennen,
- die relative Position des Tauchers zur Plattform bestimmen,
- die Richtung zum Taucher bestimmen,
- den Abstand zum Taucher bestimmen,
- die geschätzte Position während des Tests darstellen,
- bei Verlust des Ziels eine einfache Meldung ausgeben,
- parallel eine vollständige Videoaufnahme ermöglichen.

Die Plattform wird in dieser Stufe noch nicht autonom dem Taucher folgen.

Ziel dieser Stufe ist es, die für das spätere autonome Folgen erforderliche Wahrnehmung und Positionsbestimmung unabhängig von der autonomen Fahrzeugbewegung unter realen Unterwasserbedingungen zu validieren.

### Stufe 2 – Autonomes Folgen

In der zweiten Demonstratorstufe soll die Plattform den Taucher auf Basis der verfügbaren Positionsinformationen autonom begleiten.

Die gewünschte relative Position und der Abstand zum Taucher sollen dabei grundsätzlich vom gewählten Aufnahmemodus abhängen.

Bei einem Verlust des Ziels soll die Plattform zunächst für eine definierte Zeit auf eine erneute Erkennung warten.

Bleibt das Ziel dauerhaft verloren, soll eine kontrollierte Sicherheitsroutine eingeleitet werden. Das genaue Verhalten und die erforderlichen Bedingungen müssen im weiteren Entwicklungsverlauf spezifiziert werden.

Die autonome Hindernisvermeidung ist noch nicht Bestandteil dieser Demonstratorstufe.

### Stufe 3 – Autonomes Folgen mit Kollisionsvermeidung

In der dritten Demonstratorstufe wird das autonome Folgen um eine aktive Umgebungswahrnehmung und Kollisionsvermeidung erweitert.

Das System soll dabei:

- relevante Hindernisse erkennen,
- Hindernisse bei der Bewegungsentscheidung berücksichtigen,
- Kollisionen aktiv vermeiden,
- die gewünschte Kameraposition nur dann anfahren, wenn dies sicher möglich ist.

Für alle Aufnahmemodi gilt dabei der übergeordnete Grundsatz:

> Kollisionsvermeidung und Sicherheit haben immer Vorrang vor der gewünschten Kameraposition und dem gewünschten Videomaterial.

---

## 5. Aufnahmekonzept

Die Plattform soll langfristig unterschiedliche Aufnahmemodi unterstützen.

Die Auswahl eines Aufnahmemodus soll beeinflussen, welche relative Position und welchen Abstand die Plattform gegenüber dem Taucher anstrebt.

Die derzeit vorgesehenen grundlegenden Einsatzbereiche sind:

### Freediving – Deep Dive

Dieser Modus ist auf überwiegend vertikale Tauchbewegungen ausgerichtet.

Mögliche Aufnahmeprofile sind beispielsweise:

- seitliche Begleitung,
- frontale Aufnahme,
- Verfolgung von hinten oder versetzt.

Die konkrete Ausgestaltung soll später auf Grundlage praktischer Tests und der gewünschten Videoergebnisse weiterentwickelt werden.

### Freediving – Streckentauchen

Dieser Modus ist auf überwiegend horizontale Bewegungen ausgerichtet.

Mögliche Aufnahmeprofile sind beispielsweise:

- seitliche Begleitung,
- frontale Aufnahme,
- Verfolgung von hinten.

Ein gleichmäßiges und stabiles Begleiten des Tauchers ist in diesem Einsatzbereich besonders relevant.

### Spaßmodus – Freediving und Scuba

Der Spaßmodus soll eine freiere Gestaltung der Aufnahmen ermöglichen.

Neben unterschiedlichen Perspektiven auf den Taucher sollen dabei auch bewusste Aufnahmen der Umgebung möglich sein.

Mögliche Aufnahmeziele umfassen:

- Aufnahmen des Tauchers von vorne,
- Aufnahmen des Tauchers von hinten,
- seitliche Aufnahmen,
- gemeinsame Aufnahmen von Taucher und Umgebung,
- eigenständige Aufnahmen einer interessanten Umgebung.

Die konkrete Anzahl und Ausgestaltung späterer Aufnahmeprofile ist noch offen.

Die Architektur soll grundsätzlich flexibel genug sein, um weitere Aufnahmemodi und Aufnahmeprofile ergänzen zu können.

---

## 6. Bestätigte Projektentscheidungen

### Kamerakonzept

Das Projekt verfolgt ein separates Kamerakonzept für Videoaufnahme und technische Wahrnehmung.

- Filmkamera: DJI Osmo Action 6
- Trackingkamera: Raspberry Pi Camera Module

Die Trennung ermöglicht es, die Anforderungen an hochwertige Videoaufnahmen und die technische Wahrnehmung unabhängig voneinander zu betrachten.

Referenz: `docs/decisions/005-dual-camera-selection.md`

### Softwareansatz

- ROS 2 ist als Grundlage für die übergeordnete Softwarearchitektur vorgesehen.
- Die Software soll modular aufgebaut werden.
- Einzelne Softwarefunktionen sollen, sofern sinnvoll, bereits vor der vollständigen Hardwareintegration mit Simulationen oder simulierten Daten getestet werden.
- Software und Hardware sollen schrittweise integriert und gemeinsam validiert werden.

Die konkrete ROS-2-Architektur und die benötigten Nodes sind noch nicht festgelegt.

### Tracking-Grundsatz

Die Plattform muss für das autonome Folgen Informationen über die relative Position des Tauchers erhalten.

Für die erste Demonstratorstufe sollen insbesondere folgende Informationen bestimmt werden:

- relative Position des Tauchers,
- Richtung zum Taucher,
- Abstand zum Taucher.

Kamerabasierte Wahrnehmung und ein zusätzlicher Beacon am Taucher bilden derzeit die bevorzugte Richtung für das Tracking, sofern eine geeignete technische Lösung gefunden und in das System integriert werden kann.

Die konkrete technische Umsetzung des Beacon-Systems ist noch offen.

Ein visueller Marker ist derzeit nicht als verbindlicher Bestandteil des Systems festgelegt. Seine mögliche Rolle im weiteren Projektverlauf bleibt offen.

### Sonar und Umgebungswahrnehmung

Sonar ist vorrangig für die Umgebungswahrnehmung und spätere Kollisionsvermeidung vorgesehen.

Sonar ist nicht als alleinige Methode zur Taucherverfolgung geplant.

Die aktive Einbindung der Hinderniserkennung in die Fahrzeugbewegung ist Bestandteil der dritten Demonstratorstufe.

### Sicherheit

Sicherheit hat bei autonomen Bewegungsentscheidungen Vorrang vor dem gewünschten Videomaterial.

Insbesondere gilt:

> Kollisionsvermeidung hat immer Vorrang vor der gewünschten Kameraposition.

Das Verhalten bei Zielverlust soll über eine definierte Sicherheitsroutine geregelt werden.

### Positionsreferenz und Rückkehrkonzept

Für spätere Sicherheits- und Rückkehrfunktionen soll eine pragmatische Positionsreferenz untersucht werden.

Der grundsätzliche Ansatz ist:

- Erfassung und Speicherung einer GPS-Position an der Oberfläche,
- Nutzung der letzten bekannten GPS-Position als Referenz beim Abtauchen,
- Schätzung der eigenen Bewegung unter Wasser auf Basis verfügbarer Bewegungs- und Sensordaten,
- kontrolliertes Auftauchen bei dauerhaftem Zielverlust,
- erneute Positionsbestimmung nach Wiedererlangen eines GPS-Signals an der Oberfläche,
- mögliche Rückkehr zu einem zuvor definierten Einstiegspunkt.

GPS ist dabei nicht als Unterwasser-Positionssystem vorgesehen.

Die Genauigkeit einer geschätzten Unterwasserposition muss für den vorgesehenen Einsatzzweck bewertet werden. Ein hochpräzises und kostenintensives Unterwasser-Ortungssystem ist derzeit nicht als Voraussetzung vorgesehen.

---

## 7. Vorläufige Entwurfsannahmen

Die folgenden Punkte sind noch nicht als technisch validierte oder endgültig festgelegte Systemeigenschaften zu verstehen:

- angestrebte Einsatztiefe von etwa 100 m,
- kompakte Bauform,
- vorgesehene Sechs-Thruster-Konfiguration,
- Einsatz einer übergeordneten Recheneinheit mit ROS 2,
- mögliche Nutzung von Pixhawk und ArduSub für die untergeordnete Fahrzeugsteuerung,
- passive Stabilisierung,
- spätere Erweiterbarkeit um ein Variable Buoyancy System (VBS).

Auch die endgültliche Auswahl der Recheneinheit, der Sensoren, des Antriebssystems und weiterer Hardwarekomponenten steht noch aus.

Komponentenwahl, Leistungsfähigkeit und technische Machbarkeit müssen im weiteren Entwicklungsverlauf überprüft werden.

---

## 8. Entwicklungs- und Testprinzip

Die Entwicklung soll schrittweise erfolgen.

### Softwaretests

Einzelne Softwarefunktionen sollen, sofern sinnvoll, zunächst unabhängig vom vollständigen Fahrzeug getestet werden.

Mögliche Beispiele sind:

- Tests mit simulierten Sensordaten,
- Simulation einzelner Tracking- oder Bewegungsfunktionen,
- Tests von Datenflüssen und Software-Schnittstellen,
- Validierung von Verhalten bei Zielverlust.

Eine vollständige Simulation des gesamten Fahrzeugs ist nicht in jeder Entwicklungsphase erforderlich.

### Hardwaretests

Hardwarekomponenten sollen vor der vollständigen Integration einzeln getestet werden.

Mögliche Beispiele sind:

- Ansteuerung und Verhalten von Thrusters,
- Kamerafunktion und Bildqualität,
- Funktion und Datenqualität von Sensoren,
- Reichweite und Informationsgehalt eines Beacon-Systems,
- Funktion der Sonar-basierten Umgebungswahrnehmung.

### Integrationstests

Software und Hardware sollen anschließend schrittweise zusammengeführt werden.

Dabei sollen einzelne Funktionsketten unabhängig getestet werden, bevor das vollständige Gesamtsystem integriert wird.

Beispiele:

- Sensor → Software → Auswertung,
- Kamera → Tauchererkennung → Positionsschätzung,
- Steuerbefehl → Fahrzeugsteuerung → Thruster,
- Wahrnehmung → Bewegungsentscheidung → Fahrzeugbewegung.

---

## 9. Offene technische Fragen

### Tauchertracking

- Welches konkrete Trackingverfahren wird für den ersten Demonstrator verwendet?
- Welche technische Lösung kann als Beacon am Taucher eingesetzt werden?
- Welche Messgrößen liefert das Beacon-System tatsächlich?
- Wie werden Kameradaten und Beacon-Informationen kombiniert?
- Welche Genauigkeit und Aktualisierungsrate werden für die einzelnen Demonstratorstufen benötigt?
- Welche Rolle kann ein visueller Marker gegebenenfalls übernehmen?
- Wie erfolgt die Wiedererkennung nach einem Trackingverlust?

### Autonomes Folgen und Aufnahmekonzept

- Welche konkreten Aufnahmeprofile sollen für die einzelnen Aufnahmemodi umgesetzt werden?
- Welche relativen Positionen und Abstände sollen die jeweiligen Aufnahmeprofile verwenden?
- Wie und wann darf die Plattform zwischen verschiedenen Aufnahmeprofilen wechseln?
- Welche Bewegungsgrenzen gelten für ein sicheres Folgen?

### Sicherheit und Missionslogik

- Welche Zustände und Übergänge benötigt die Missionslogik?
- Wie lange soll die Plattform bei Zielverlust auf eine erneute Erkennung warten?
- Wie genau ist die Sicherheitsroutine bei dauerhaftem Zielverlust aufgebaut?
- Unter welchen Bedingungen soll die Plattform kontrolliert auftauchen?
- Wie wird die Rückkehr zum Einstiegspunkt nach Wiedererlangen eines GPS-Signals umgesetzt?

### Umgebungswahrnehmung und Kollisionsvermeidung

- Welche Sonar- oder weiteren Sensoren werden benötigt?
- Welche Hindernisse müssen für den ersten Einsatzbereich erkannt werden?
- Welche Bewegungsentscheidungen sind bei einem erkannten Hindernis zulässig?
- Wie werden Kollisionsvermeidung und gewünschte Kameraposition gegeneinander priorisiert?

### Softwarearchitektur

- Welche ROS-2-Nodes werden benötigt?
- Welche Aufgaben gehören zur Wahrnehmung, Zustandsschätzung, Missionslogik und Bewegungssteuerung?
- Welche Nachrichten und Koordinatensysteme verwenden die einzelnen Komponenten?
- Welche Aufgaben liegen bei ROS 2 und welche bei der untergeordneten Fahrzeugsteuerung?
- Wie können einzelne Funktionen ohne vollständige Hardware getestet werden?

### Hardware

- Welche Recheneinheit wird endgültig gewählt?
- Welche Sensoren sind für die einzelnen Demonstratorstufen erforderlich?
- Wie werden Druckfestigkeit, Auftrieb, Stabilität und Energiebedarf nachgewiesen?
- Welche Hardware ist für den ersten realen Unterwasserdemonstrator tatsächlich erforderlich?

---

## 10. Nächste Entwicklungsschritte

Die weitere Entwicklung soll grundsätzlich in folgender Reihenfolge erfolgen:

1. Bestehende Dokumentation mit den in diesem Dokument festgehaltenen Entscheidungen abgleichen.
2. Widersprüche zwischen bestehenden Projekt-, Tracking-, Architektur- und Roadmap-Dokumenten bereinigen.
3. Die Anforderungen an das Tracking-System aus den Demonstratorstufen ableiten.
4. Die technische Machbarkeit und geeignete Komponenten für Kamera-, Beacon- und Sonarsysteme bewerten.
5. Die Softwarearchitektur und Verantwortlichkeiten der einzelnen Systemkomponenten festlegen.
6. Einzelne Softwarefunktionen und Hardwarekomponenten schrittweise validieren.
7. Software und Hardware schrittweise integrieren.
8. Den realen Unterwasserdemonstrator in einer kontrollierten Umgebung entwickeln und testen.

---

## 11. Entwicklungsstatus

**Aktuelle Phase: Konsolidierung der Projektentscheidungen und Vorbereitung der technischen Systemarchitektur.**

Das Projekt befindet sich weiterhin in einer frühen Konzept- und Architekturphase.

Die grundlegenden Ziele und Demonstratorstufen sind definiert. Die konkrete technische Umsetzung, die endgültige Hardwareauswahl sowie die detaillierte Softwarearchitektur müssen im weiteren Entwicklungsverlauf erarbeitet und validiert werden.
