# Entscheidung 006 – Multi-Sensor-Tracking des Tauchers

## Status

Aktuell

## Kontext

Eine zentrale Funktion der autonomen Unterwasserplattform ist das sichere und möglichst zuverlässige Folgen eines definierten Tauchers.

Das Projekt verfolgt dabei nicht das Ziel, ein allgemeines Unterwasser-Positionierungssystem zu entwickeln. Die Entwicklung soll sich primär auf die autonome Unterwasserplattform, ihre Navigation, Wahrnehmung, Steuerung und das sichere Folgen eines Tauchers konzentrieren.

Daher gilt für das Tracking grundsätzlich:

> So wenig zusätzliche Eigenentwicklung wie möglich, jedoch ausreichend technische Kontrolle und Erweiterbarkeit für die Anforderungen des Projekts.

Im Rahmen der Konzeptphase wurden verschiedene Möglichkeiten untersucht, um die relative Position eines Tauchers gegenüber der autonomen Unterwasserplattform zu bestimmen.

Dabei wurden sowohl professionelle kommerzielle Unterwasser-Positionierungssysteme als auch kompakte akustische Beacon- und Transponderlösungen, universitäre Forschungsansätze und ein möglicher Eigenbau eines akustischen Ortungssystems betrachtet.

Die ursprüngliche Überlegung bestand darin, die Position des Tauchers primär über ein akustisches Beacon- beziehungsweise Transpondersystem zu bestimmen.

Im weiteren Verlauf der Untersuchung zeigte sich jedoch, dass ein einzelnes Sensorsystem für die geplante Anwendung entweder:

- technisch komplex,
- zu teuer,
- zu groß oder schwer,
- nur eingeschränkt in die geplante Fahrzeugarchitektur integrierbar,
- oder mit einem erheblichen zusätzlichen Entwicklungsaufwand verbunden wäre.

Parallel wurde deutlich, dass für die Unterwasserplattform ohnehin mehrere Sensoren vorgesehen sind.

Insbesondere:

- eine Raspberry-Pi-Kamera für die Fahrzeugsteuerung und visuelle Wahrnehmung,
- ein Sonarsystem für Umgebungswahrnehmung und Kollisionsvermeidung,
- eine IMU zur Bestimmung der Fahrzeugorientierung,
- ein Drucksensor zur Bestimmung der Tiefe,
- sowie perspektivisch ein kleines akustisches Beacon am zu verfolgenden Taucher.

Daraus entstand die Überlegung, die Taucherposition nicht durch ein einzelnes hochpräzises Positionierungssystem bestimmen zu lassen.

Stattdessen sollen die vorhandenen und zukünftigen Sensoren entsprechend ihrer jeweiligen Stärken kombiniert werden.

---

# Untersuchte Ansätze und Systeme

## Professionelle USBL- und Unterwasser-Positionierungssysteme

### Blueprint Subsea SeaTrac X110 / X150

Die SeaTrac-Systeme von Blueprint Subsea wurden als mögliche Lösung für die Unterwasserpositionierung betrachtet.

Das System basiert auf akustischer Unterwasserkommunikation und Positionierung.

Grundsätzlich erschien der Ansatz interessant, da sich damit die relative Position von Unterwasserobjekten bestimmen lässt.

Insbesondere wurde die Kombination verschiedener SeaTrac-Geräte betrachtet.

Dabei zeigte sich jedoch, dass für die geplante Anwendung eine komplexere Systemarchitektur erforderlich wäre.

Zusätzlich stellte sich die Frage, wie die verfügbare Softwarearchitektur und die vorgesehenen Bedien- beziehungsweise Integrationskonzepte in die geplante autonome ROS2-basierte Fahrzeugarchitektur integriert werden könnten.

Das System wurde daher nicht als unmittelbar geeignete Lösung für die erste Entwicklungsphase ausgewählt.

Die grundsätzliche Technologie bleibt jedoch als Referenz für professionelle akustische Unterwasserpositionierung relevant.

---

### Water Linked Underwater GPS

Auch Systeme von Water Linked wurden betrachtet.

Die Produkte sind insbesondere für die Positionierung und Kommunikation zwischen Unterwasserfahrzeugen und einer Einheit an der Wasseroberfläche ausgelegt.

Für die geplante Anwendung besteht jedoch ein anderer Schwerpunkt.

Das Ziel ist primär die direkte relative Lokalisierung eines Tauchers durch die autonome Unterwasserplattform.

Eine permanente Surface Station soll hierfür möglichst nicht erforderlich sein.

Da die betrachteten Water-Linked-Systeme überwiegend auf die Kommunikation und Positionierung zwischen Unterwasserfahrzeug und Oberfläche ausgerichtet sind, entsprachen sie nicht unmittelbar dem gewünschten Konzept einer direkten Kommunikation beziehungsweise Lokalisierung zwischen Taucher und autonomer Unterwasserplattform.

Die Systeme wurden daher nicht weiter als primäre Trackinglösung verfolgt.

---

### Sonardyne

Auch professionelle Unterwasser-Positionierungssysteme von Sonardyne wurden betrachtet.

Sonardyne bietet verschiedene akustische Positionierungs- und Transponderlösungen für professionelle maritime Anwendungen an.

Die Systeme sind technisch leistungsfähig und werden unter anderem im Offshore-Bereich und für professionelle Unterwasserfahrzeuge eingesetzt.

Für das vorliegende Projekt ergaben sich jedoch mehrere Einschränkungen.

Insbesondere:

- hohe Kosten,
- professionelle Systemarchitekturen,
- teilweise umfangreiche Infrastruktur,
- für das Projekt überdimensionierte Leistungsfähigkeit,
- sowie keine einfache Low-Cost-Lösung für einen kleinen Beacon am Taucher.

Die Systeme wurden daher als technische Referenz betrachtet, jedoch nicht als realistische Lösung für die aktuelle Projektphase ausgewählt.

---

### Kongsberg µPAP

Der Kongsberg µPAP wurde als kompaktes professionelles Unterwasser-Positionierungssystem betrachtet.

Der Ansatz ist insbesondere deshalb interessant, weil Positionierungssysteme dieser Klasse auch für ROV- und AUV-Anwendungen ausgelegt sein können.

Damit bestätigt der µPAP grundsätzlich, dass eine kompakte Unterwasserplattform mit akustischer Positionierung technisch realisierbar ist.

Für das Projekt erscheint das System jedoch aufgrund seiner professionellen Produktklasse und der damit verbundenen Kosten voraussichtlich nicht geeignet.

Das System wurde daher nicht als konkrete Lösung weiterverfolgt.

---

### RJE International VADR

Der Vehicle Acoustic Directional Receiver von RJE International wurde als akustischer Empfänger für ROV- und AUV-Anwendungen betrachtet.

Der VADR ist interessant, da er direkt auf einem Unterwasserfahrzeug eingesetzt werden kann.

Damit entspricht die grundsätzliche Systemarchitektur stärker der gewünschten Anwendung.

Das Konzept besteht grundsätzlich aus:

- einem akustischen Sender oder Transponder am zu verfolgenden Objekt,
- einem Empfänger auf dem Unterwasserfahrzeug,
- einer nachgelagerten Verarbeitung der empfangenen Informationen,
- sowie der Integration der Ergebnisse in die Fahrzeugsteuerung.

In Verbindung mit einem geeigneten Transponder kann das System Informationen über Richtung und Entfernung liefern.

Der betrachtete RJE ATT-400 Acoustic Target Transponder wurde jedoch für die Anwendung am Taucher als ungeeignet bewertet.

Gründe hierfür waren insbesondere:

- große Bauform,
- hohes Gewicht,
- sowie hohe Kosten.

Der ATT-400 liegt deutlich außerhalb der für das Projekt angestrebten Größen- und Gewichtsanforderungen eines kleinen persönlichen Beacons.

Auch die Kosten der professionellen Empfängerhardware liegen außerhalb des für das studentische Nebenprojekt vorgesehenen Budgets.

Der Ansatz wurde daher nicht als primäre Lösung übernommen.

---

### Teledyne Benthos

Auch akustische Locator-, Pinger- und Transponderlösungen von Teledyne Benthos wurden betrachtet.

Die Produkte sind für unterschiedliche maritime Anwendungen und teilweise auch für ROV- und AUV-Anwendungen vorgesehen.

Der grundsätzliche Ansatz kleiner akustischer Sender ist für das Projekt interessant.

Die betrachteten Systeme erfüllten jedoch bisher nicht gleichzeitig alle Anforderungen hinsichtlich:

- Größe,
- Gewicht,
- Kosten,
- direkter Integration in die Fahrzeugarchitektur,
- sowie der gewünschten Funktion als kleines Beacon am Taucher.

Daher wurde kein konkretes Teledyne-Benthos-System als Trackinglösung ausgewählt.

---

# Kompakte akustische Beacon- und Transponderlösungen

## RJE ATT-400 Acoustic Target Transponder

Der RJE ATT-400 wurde als möglicher akustischer Transponder am zu verfolgenden Objekt betrachtet.

Der Transponder ist grundsätzlich für die akustische Unterwasserortung vorgesehen.

Für die geplante Anwendung am Taucher wurde das System jedoch als ungeeignet bewertet.

Insbesondere sind Größe und Gewicht deutlich zu hoch.

Die angestrebte Lösung für den Taucher soll:

- möglichst klein,
- unauffällig,
- leicht,
- und mit einem Gewicht von maximal etwa 50 g

sein.

Der ATT-400 liegt deutlich oberhalb dieser Zielgröße.

Zusätzlich sind die Kosten des Gesamtsystems aus Transponder und Empfänger für das Projekt zu hoch.

Der ATT-400 wurde daher nicht weiter als konkrete Hardwarelösung verfolgt.

---

## Desert Star DiveTracker Scout

Der Desert Star DiveTracker Scout wurde untersucht, da das System speziell für Anwendungen mit Tauchern entwickelt wurde.

Der grundsätzliche Anwendungsfall ist damit deutlich näher am Projektziel als viele professionelle Offshore-Positionierungssysteme.

Der Sender fungiert als akustisches Signal am Taucher.

Die zugehörige Empfängereinheit ist jedoch primär für die Nutzung durch einen menschlichen Taucher vorgesehen.

Damit ist die vorhandene Empfängerarchitektur nicht unmittelbar für die Integration in ein autonomes ROV beziehungsweise AUV mit ROS2 ausgelegt.

Zusätzlich liegt das System hinsichtlich der Gesamtkosten weiterhin oberhalb des für die Trackingfunktion angestrebten Budgets.

Der Ansatz wurde daher nicht als fertige Lösung übernommen.

Die grundsätzliche Idee eines kleinen persönlichen akustischen Senders bleibt jedoch für die weitere Entwicklung interessant.

---

# Universitärer Forschungsansatz

## AquaTracer – Technische Universität Hamburg

Ein besonders interessanter Forschungsansatz wurde an der Technischen Universität Hamburg untersucht.

Im Projekt AquaTracer wird an kleinen, energieeffizienten und kostengünstigen akustischen Unterwasser-Tracern gearbeitet.

Der Forschungsansatz ist für das Projekt besonders interessant, da er sich deutlich von professionellen USBL- und Offshore-Positionierungssystemen unterscheidet.

Im Mittelpunkt stehen kleine und kostengünstige akustische Tracer.

Der Ansatz verfolgt unter anderem folgende Ziele:

- kleine Bauform,
- geringer Energieverbrauch,
- lange Betriebsdauer,
- geringe Kosten,
- akustische Identifikation,
- akustische Detektion,
- sowie Lokalisierung von Unterwasserobjekten.

Besonders interessant ist die grundsätzliche Übertragbarkeit auf die Lokalisierung eines Tauchers.

Das AquaTracer-Konzept kommt damit der ursprünglichen Vorstellung eines kleinen, einfachen und kostengünstigen akustischen Tags am Taucher deutlich näher als die bisher betrachteten professionellen Systeme.

Der Forschungsansatz stellte jedoch keine unmittelbar verfügbare, fertige Lösung dar, welche alle Anforderungen des Projekts erfüllt.

Insbesondere wurde keine bereits verfügbare Lösung übernommen, mit der die angestrebte relative Positionsbestimmung direkt innerhalb der geplanten autonomen Unterwasserplattform umgesetzt werden kann.

Der AquaTracer wurde daher nicht als konkrete Hardwarelösung festgelegt.

Der Forschungsansatz hatte jedoch einen wesentlichen Einfluss auf die weitere Entwicklung des Trackingkonzepts.

Insbesondere wurde dadurch die Überlegung verstärkt, dass ein Beacon nicht zwingend alleine die vollständige Position des Tauchers bestimmen muss.

Ein kleines akustisches System kann stattdessen eine zusätzliche Information innerhalb eines größeren Sensorverbunds liefern.

Diese Erkenntnis wurde später zu einem wesentlichen Bestandteil des Multi-Sensor-Tracking-Konzepts.

---

# Eigenentwickeltes Hydrofonarray

Als Alternative zu kommerziellen Positionierungssystemen wurde ein eigenes akustisches Ortungssystem betrachtet.

Das Konzept hätte aus einem kleinen akustischen Beacon am Taucher und mehreren am Fahrzeug angeordneten Hydrofonen bestehen können.

Abhängig von der Anzahl und Anordnung der Hydrofone könnten Informationen aus:

- Laufzeitunterschieden,
- Phasenunterschieden,
- Signalstärke,
- oder anderen Signalmerkmalen

zur Bestimmung der relativen Position verwendet werden.

Der Ansatz ist technisch grundsätzlich interessant.

Er wurde jedoch nicht als primäre Trackinglösung weiterverfolgt.

Der Grund hierfür ist der erhebliche zusätzliche Entwicklungsaufwand.

Ein eigenes Hydrofonarray würde ein zusätzliches eigenständiges Entwicklungsgebiet innerhalb des Projekts eröffnen.

Es müssten unter anderem folgende Punkte untersucht und entwickelt werden:

- Anzahl der Hydrofone,
- Positionierung am Fahrzeug,
- optimale Array-Geometrie,
- mechanische Integration,
- Einfluss des Fahrzeugkörpers auf die Messung,
- akustische Abschattung,
- Reflexionen,
- Mehrwegeausbreitung,
- Synchronisation mehrerer Messkanäle,
- geeignete Analog-Digital-Wandlung,
- Samplingrate,
- Signalverarbeitung,
- Kalibrierung,
- sowie die spätere Integration in ROS2.

Damit würde das Projekt zusätzlich zur Entwicklung einer autonomen Unterwasserplattform auch die Entwicklung eines eigenen akustischen Positionierungssystems umfassen.

Dies entspricht nicht der grundsätzlichen Entwicklungsstrategie:

> So viel Eigenentwicklung wie sinnvoll, aber so wenig zusätzliche Eigenentwicklung wie möglich.

Der Ansatz bleibt daher als zukünftige Forschungs- oder Erweiterungsoption bestehen.

Er ist jedoch nicht als primäres Trackingkonzept vorgesehen.

---

# Erkenntnis aus der Untersuchung

Die Untersuchung der verschiedenen Systeme führte zu einer wesentlichen Erkenntnis.

Es ist nicht sinnvoll, von einem einzelnen Sensor zu verlangen, gleichzeitig:

- den richtigen Taucher zu identifizieren,
- seine Richtung zu bestimmen,
- seine Entfernung zu bestimmen,
- seine vollständige relative Position zu bestimmen,
- und bei schlechter Sicht oder Hindernissen zuverlässig zu funktionieren.

Jede dieser Aufgaben kann durch unterschiedliche Sensoren besser erfüllt werden.

Die autonome Unterwasserplattform verfügt beziehungsweise soll zukünftig über mehrere Sensoren verfügen.

Daher wurde entschieden, die jeweiligen Stärken der Sensoren zu kombinieren.

---

# Entscheidung

Die relative Position und der Zustand des zu verfolgenden Tauchers sollen zukünftig über eine Multi-Sensor-Architektur bestimmt werden.

Das Trackingkonzept basiert auf:

- Computer Vision über die Raspberry-Pi-Kamera,
- Sonar zur Erfassung der Umgebung und zur Bestimmung räumlicher Informationen,
- einem kleinen akustischen Beacon als zusätzliche Informationsquelle,
- IMU-Daten zur Berücksichtigung der Fahrzeugorientierung,
- sowie Tiefendaten über einen Drucksensor.

Keiner der Sensoren soll alleine für die vollständige Bestimmung der Taucherposition verantwortlich sein.

---

# Aufgaben der einzelnen Sensoren

## Raspberry-Pi-Kamera

Die Raspberry-Pi-Kamera dient als primärer Sensor für die visuelle Wahrnehmung des zu verfolgenden Objekts.

Die Kamera kann insbesondere Informationen liefern über:

- Erkennung eines Tauchers,
- Position des Tauchers im Bild,
- relative Richtung des Ziels,
- Bewegung des Ziels,
- kontinuierliches visuelles Tracking.

Die zentrale Frage der Kamera lautet:

> Wo befindet sich das zu verfolgende Objekt im aktuellen Sichtfeld?

Die Kamera liefert dabei nicht zwangsläufig direkt eine hochpräzise räumliche Entfernung.

Ihre Hauptaufgabe besteht in der visuellen Identifikation und kontinuierlichen Beobachtung des Ziels.

---

## Sonar

Das Sonar ist primär für die Wahrnehmung der Unterwasserumgebung und die Kollisionsvermeidung vorgesehen.

Es liefert Informationen über:

- Objekte,
- Hindernisse,
- räumliche Strukturen,
- sowie Entfernungen.

Im Rahmen des Trackingkonzepts kann das Sonar zusätzlich genutzt werden.

Wenn die Kamera bereits ein Ziel erkannt und dessen ungefähre Richtung bestimmt hat, muss das Sonar nicht eigenständig den gesamten Raum nach dem Taucher durchsuchen.

Die visuelle Information kann stattdessen genutzt werden, um einen erwarteten Bereich im Sonar zu definieren.

Das Sonar kann anschließend prüfen, ob sich in diesem erwarteten Bereich ein Objekt befindet und welche Entfernung dieses Objekt besitzt.

Dadurch entsteht eine gezielte Kombination aus visueller und akustischer Wahrnehmung.

---

## Akustisches Beacon

Ein kleines akustisches Beacon soll zukünftig als zusätzliche Informationsquelle untersucht werden.

Das Beacon ist ausdrücklich nicht als vollständiges hochpräzises Positionierungssystem definiert.

Es soll primär folgende Aufgaben unterstützen:

- Bestätigung, dass sich das Ziel weiterhin in Reichweite befindet,
- Unterstützung bei mehreren Personen im Wasser,
- Unterstützung bei der Zuordnung zum vorgesehenen Taucher,
- Unterstützung bei kurzzeitigem Verlust des visuellen Kontakts,
- Unterstützung während eines Lost-Zustands,
- Unterstützung bei der Wiedererfassung des Ziels.

Das Beacon kann damit als zusätzliche Zielinformation betrachtet werden.

Die genaue Hardware ist derzeit noch nicht festgelegt.

Zielanforderungen für ein zukünftiges Beacon sind:

- möglichst kleine Bauform,
- möglichst geringes Gewicht,
- Zielgewicht maximal etwa 50 g,
- keine Bedienung durch den Taucher während des normalen Betriebs,
- zuverlässige Reichweite von mindestens 30 m,
- Druckfestigkeit für die geplante maximale Einsatztiefe,
- möglichst geringe Kosten,
- möglichst einfache Integration in die Fahrzeugarchitektur.

Für die Trackingfunktion wird langfristig ein Kostenrahmen von maximal etwa 100 € angestrebt.

---

## IMU

Die IMU liefert Informationen über die Orientierung und Bewegung der Unterwasserplattform.

Diese Informationen sind notwendig, um Sensordaten korrekt in das Fahrzeugkoordinatensystem zu übertragen.

Insbesondere müssen Richtungsinformationen aus:

- Kamera,
- Sonar,
- und zukünftigen Sensoren

mit der aktuellen Fahrzeugorientierung kombiniert werden.

---

## Drucksensor

Der Drucksensor liefert die aktuelle Tiefe der Unterwasserplattform.

Die Tiefeninformation ist relevant für:

- Fahrzeugregelung,
- Bewegungsplanung,
- sowie die räumliche Interpretation von Sensordaten.

---

# Sensorfusion

Die Informationen der Sensoren sollen in einem Target Estimator zusammengeführt werden.

Der Target Estimator erhält Informationen aus:

- dem Visual Tracking,
- dem Sonarsystem,
- dem zukünftigen Beacon-System,
- der IMU,
- sowie dem Drucksensor.

Der Target Estimator erzeugt daraus eine geschätzte relative Zielposition.

Zusätzlich soll eine Bewertung der Zuverlässigkeit der aktuellen Schätzung erzeugt werden.

---

# Konsequenzen

Die Taucherverfolgung wird zukünftig nicht als einzelnes Sensorsystem betrachtet.

Stattdessen wird ein Multi-Sensor-Ansatz verfolgt.

Die grundlegende Rollenverteilung lautet:

| Sensor | Hauptaufgabe |
|---|---|
| Kamera | Ziel erkennen und verfolgen |
| Sonar | Umgebung und Entfernung |
| Beacon | Präsenz, Identifikation und Lost-Unterstützung |
| IMU | Fahrzeugorientierung |
| Drucksensor | Tiefe |

---

# Vorteile

Der Multi-Sensor-Ansatz bietet mehrere Vorteile:

- kein einzelner Sensor muss die vollständige Taucherposition alleine bestimmen,
- bereits vorhandene Sensoren können mehrfach genutzt werden,
- keine teure professionelle USBL-Infrastruktur ist zwingend erforderlich,
- kein Hydrofonarray ist als primäre Trackinglösung erforderlich,
- die Hardwarearchitektur bleibt kompakter,
- einzelne Sensoren können sich gegenseitig ergänzen,
- höhere Robustheit gegenüber kurzzeitigigem Sensorausfall,
- Unterstützung bei mehreren Personen im Wasser,
- Unterstützung bei Lost- und Reacquisition-Szenarien,
- spätere Erweiterbarkeit.

---

# Nachteile und offene Punkte

Die Entscheidung für einen Multi-Sensor-Ansatz führt zu neuen Anforderungen an die Softwarearchitektur.

Insbesondere müssen zukünftig untersucht werden:

- zeitliche Synchronisation der Sensordaten,
- Transformation zwischen Kamera-, Sonar- und Fahrzeugkoordinatensystem,
- Genauigkeit der Sonardaten,
- Fähigkeit des Sonars, ein visuell bekanntes Objekt als separates Objekt zu erfassen,
- Umgang mit widersprüchlichen Sensorinformationen,
- Definition der Sensorzuverlässigkeit,
- Auswahl eines geeigneten Beacon-Systems,
- Verhalten bei schlechter Sicht,
- Verhalten bei vollständigem Verlust des visuellen Kontakts,
- Anforderungen an Aktualisierungsrate und Latenz.

---

# Konsequenz für die ROS2-Architektur

Die Sensordaten sollen in separaten ROS2-Nodes verarbeitet werden.

Die grundsätzliche Architektur soll folgende Komponenten enthalten:

- Camera Node,
- Visual Tracking Node,
- Sonar Node,
- Beacon Node,
- IMU Node,
- Depth Node,
- Target Estimator,
- Follow Controller,
- Motion Control.

Die einzelnen Sensorinformationen werden zunächst separat verarbeitet.

Anschließend werden sie im Target Estimator zusammengeführt.

Der Target Estimator erzeugt einen Target State Estimate.

Dieser wird anschließend an den Follow Controller übergeben.

Der Follow Controller bestimmt daraus die gewünschte Bewegung der Plattform.

Die Motion-Control-Ebene setzt diese Vorgaben anschließend in konkrete Bewegungs- und Ansteuerbefehle für die Antriebseinheit um.

Die genaue Umsetzung wird in einer späteren Architekturphase definiert.

---

# Zusammenfassung

Die Untersuchung professioneller Unterwasser-Positionierungssysteme, kompakter akustischer Beacon-Systeme, universitärer Forschungsansätze und eines möglichen Hydrofonarrays hat gezeigt, dass keine bisher betrachtete einzelne Lösung alle Anforderungen des Projekts gleichzeitig erfüllt.

Die zukünftige Trackingarchitektur basiert daher auf der Kombination mehrerer Sensoren.

Die Kamera liefert primär Informationen über das visuell erkannte Ziel.

Das Sonar liefert räumliche Informationen und unterstützt die Bestimmung der Entfernung sowie die Kollisionsvermeidung.

Ein zukünftiges kleines akustisches Beacon soll zusätzliche Informationen über die Präsenz und Wiedererkennung des vorgesehenen Tauchers liefern.

Die Kombination der Sensoren soll langfristig eine robustere Lösung ermöglichen als die Abhängigkeit von einem einzelnen Positionierungssystem.
