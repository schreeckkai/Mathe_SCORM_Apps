# Mathe_SCORM_Apps

Geplante Sammlung von HTML-Mathe-Apps für Moodle – jeweils als **SCORM-1.2-Lernpaket** mit einheitlichem Design.

> **Projektstart · 14.10.2026:** Dieses Repository enthält bislang ausschließlich diese README. Es gibt noch keine fertigen Apps oder ZIP-Pakete; Live-Tests in Moodle wurden noch nicht durchgeführt.

## Konzept

- Jede App enthält **exakt 5 Fragen** und folgt einem einheitlichen, übersichtlichen Design.
- Nach der Bearbeitung werden die Antworten über einen **Abgabe-Button** eingereicht und ausgewertet.
- Die Punktzahl liegt zwischen **0 und 100**. Als Konvention gelten bei fünf gleich gewichteten Fragen **20 Punkte je richtiger Antwort**.
- Die Apps sollen ihre Ergebnisse über die SCORM-1.2-API an das LMS übermitteln.

## Geplante SCORM-Anbindung

Die Kommunikation verwendet `LMSInitialize`, `LMSGetValue`, `LMSSetValue`, `LMSCommit` und `LMSFinish`. Vorgesehen sind `cmi.core.score.raw` für die erreichte Punktzahl sowie `cmi.core.score.min = 0` und `cmi.core.score.max = 100`.

Nach der Abgabe wird `cmi.core.lesson_status` auf `completed` gesetzt. `passed` oder `failed` kommen nur infrage, wenn für die jeweilige App eine ausdrückliche Bestehensgrenze definiert ist; derzeit ist keine festgelegt.

## Geplante Struktur und Paketierung

```text
apps/<app-name>/   # Quelldateien der jeweiligen HTML-App
packages/         # SCORM-1.2-ZIP-Pakete für Moodle
```

Diese Verzeichnisse sind lediglich geplant und noch nicht angelegt. Jedes spätere ZIP-Paket muss eine **`imsmanifest.xml` direkt im ZIP-Wurzelverzeichnis** enthalten. Die im Manifest bezeichneten Ressourcen, die HTML-Startdatei und die Zuordnung als SCO müssen mit dem tatsächlichen Paketinhalt übereinstimmen.

## Nutzung in Moodle – vorgesehen

1. Das fertige ZIP-Paket in Moodle als Aktivität **Lernpaket / SCORM** hochladen.
2. Die Notenbewertung passend konfigurieren: Bewertungsmethode **Höchstnote**, Punktebereich beziehungsweise Maximalbewertung passend zur Skala **0–100**.
3. Mit einem Testkonto prüfen, ob Start, Abgabe, Punktzahl, Abschlussstatus und Übernahme ins Notenbuch wie vorgesehen funktionieren.

Die SCORM-Anbindung allein garantiert keine automatische Notenübernahme: Diese hängt auch von der Moodle-Konfiguration ab. Eine externe Moodle-Authentifizierung oder Einrichtung ist nicht Bestandteil des Projekts. Beim lokalen Offline-Start besteht kein Zugriff auf das Moodle-Notenbuch.
