# Tracking Strategy

## Ziel

Robustes Verfolgen eines Tauchers unter Wasser.

---

# Grundprinzip

Das Tracking basiert auf einem hybriden Ansatz:

1. Marker Tracking
2. Visual Tracking
3. Motion Prediction

---

# Marker Tracking

Primäres System zur Initialisierung und Referenz.

Technologie:

- ArUco Marker
- OpenCV

Funktionen:

- Position
- Distanz
- Orientierung
- Tracking-Initialisierung

---

# Visual Tracking

Wenn der Marker kurzzeitig verdeckt wird:

- Optical Flow
- Bounding Box Tracking
- Feature Tracking

Das System verfolgt NICHT einzelne Objekte wie Flossen oder Masken.

Stattdessen:

Das System verfolgt ein bereits identifiziertes Zielobjekt weiter.

---

# Motion Prediction

Fallback-System bei kurzzeitigem Trackingverlust.

Funktionen:

- Bewegungsabschätzung
- weiche Übergänge
- Suchverhalten

---

# Tracking State Machine

## MARKER_LOCK

Marker sichtbar:

- höchste Präzision
- Tracking-Referenz
- Zielmodell aktualisieren

---

## VISUAL_TRACK

Marker nicht sichtbar:

- visuelles Tracking aktiv
- Ziel wird anhand vorheriger Informationen verfolgt

---

## LOST

Ziel verloren:

- stoppen oder langsam suchen
- Re-Acquisition versuchen

---

# Zukunft

Spätere Erweiterungen:

- KI-gestützte Tauchererkennung
- markerfreies Tracking
- automatische Re-Acquisition
