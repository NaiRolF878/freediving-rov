# Projektübersicht

## Vision

Ziel des Projekts ist die Entwicklung einer autonomen Unterwasserplattform, die Freediver und Gerätetaucher begleitet und eigenständig hochwertige Videoaufnahmen erstellt.

Die Plattform soll als zusätzliche Kameraplattform neue Perspektiven ermöglichen und den Taucher während eines Tauchgangs begleiten. Sie ersetzt dabei weder einen Buddy noch einen erforderlichen Sicherheits- oder Sicherungstaucher.

Das Projekt verbindet die Bereiche Robotik, Computer Vision, Unterwassertechnik und autonome Systeme.

---

## Projektziel

Langfristig soll die Plattform in der Lage sein, einen Taucher unter Wasser zu erkennen, seine relative Position zu bestimmen und ihre eigene Bewegung an einem gewünschten Aufnahmeziel auszurichten.

Je nach Aufnahmemodus soll die Plattform unterschiedliche Perspektiven ermöglichen. Dazu gehören beispielsweise:

- Freediving – Deep Dive,
- Freediving – Streckentauchen,
- freie Aufnahmen für Freediving und Scuba, bei denen neben dem Taucher auch die Umgebung bewusst in die Aufnahme einbezogen wird.

Die konkrete Ausgestaltung der einzelnen Aufnahmeprofile wird im weiteren Entwicklungsverlauf durch technische und praktische Tests weiterentwickelt.

---

## Entwicklungsansatz

Die Entwicklung erfolgt schrittweise und beginnt mit einem realen Unterwasserdemonstrator in einer kontrollierten Umgebung.

Dabei werden Software und Hardware möglichst früh einzeln validiert und anschließend schrittweise zu einem Gesamtsystem integriert.

Der Demonstrator wird in drei aufeinander aufbauenden Stufen entwickelt:

1. **Wahrnehmung bei manueller Steuerung** – den Taucher erkennen und seine relative Position bestimmen.
2. **Autonomes Folgen** – den erkannten Taucher selbstständig begleiten.
3. **Autonomes Folgen mit Kollisionsvermeidung** – die Umgebung aktiv berücksichtigen und Kollisionen vermeiden.

---

## Grundprinzipien

Bei der Entwicklung stehen folgende Grundsätze im Mittelpunkt:

- **Sicherheit vor Aufnahmequalität:** Eine sichere Bewegung und Kollisionsvermeidung haben immer Vorrang vor der gewünschten Kameraposition.
- **Schrittweise Validierung:** Funktionen und Komponenten werden möglichst früh einzeln getestet, bevor sie in das Gesamtsystem integriert werden.
- **Modularität:** Die Architektur soll den Austausch und die Erweiterung einzelner Komponenten ermöglichen.
- **Erweiterbarkeit:** Das System soll langfristig um zusätzliche Funktionen und Aufnahmemodi ergänzt werden können.
- **Nachvollziehbare Entwicklung:** Entscheidungen und technische Erkenntnisse werden öffentlich dokumentiert.

---

## Langfristige Perspektive

Nach dem erfolgreichen Nachweis der grundlegenden Fähigkeiten des ersten Demonstrators kann das Projekt schrittweise weiterentwickelt werden.

Mögliche nächste Schritte sind Tests im Freiwasser, die Weiterentwicklung der autonomen Navigation und Wahrnehmung sowie zusätzliche Aufnahme- und Sicherheitsfunktionen.

Die detaillierte Entwicklungsplanung und der aktuelle technische Projektstatus werden in der zentralen `ROADMAP.md` und in `docs/PROJECT_STATUS.md` dokumentiert.
