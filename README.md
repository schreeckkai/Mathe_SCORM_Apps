# Mathe-Schreck – Mathematik-Lernapps für Moodle / SCORM

**Interaktive Mathematikübungen mit vorbereiteter Anbindung an ein Lernmanagementsystem.**

Dieses Projekt entwickelt HTML-Mathe-Apps für den Einsatz als SCORM-1.2-Lernpakete in Moodle. Im Mittelpunkt stehen die Bearbeitung von Aufgaben, eine Auswertung auf der Skala 0–100 und die Übermittlung des Ergebnisses an das LMS.

## Aktueller Stand

Es sind inzwischen **zwei HTML-Anwendungen mit SCORM-Wrapper** vorhanden. Das Projekt ist damit über die reine Konzeptphase hinaus. Die Paketierung und eine erfolgreiche Ende-zu-Ende-Prüfung in Moodle sind durch den hier geprüften Repository-Stand jedoch noch nicht belegt.

| Datei | Inhalt |
|---|---|
| [stmfkten-plnme.html](stmfkten-plnme.html) | Stammfunktions-Akademie für Polynome |
| [stammfkt-vktete-Fkten.html](stammfkt-vktete-Fkten.html) | Stammfunktions-Akademie für linear verkettete Funktionen |
| [imsmanifest.xml](imsmanifest.xml) | Vorhandenes Manifest, dessen Startdatei-Zuordnung noch anzupassen ist |

Die Dateilinks oben öffnen den Quellcode auf GitHub, keine veröffentlichte Live-Demo. Fertige ZIP-Pakete sind im aktuellen Dateibaum nicht enthalten.

## Lernkonzept

Das zugrunde liegende Konzept sieht kurze Übungseinheiten mit fünf Aufgaben, mathematischer Eingabe, einer abschließenden Abgabe und einer Bewertung zwischen 0 und 100 vor. Bei fünf gleich gewichteten Aufgaben entspricht eine richtige Antwort 20 Punkten.

Die Anwendungen verbinden die Eingabe von Stammfunktionen mit mathematischer Darstellung und einer Auswertung. Das Projekt behandelt sowohl die fachliche Übung als auch die technische Einbindung in einen digitalen Kurs.

## Was im Code bereits vorhanden ist

Die beiden Apps enthalten einen SCORM-1.2-Wrapper einschließlich Initialisierung, Setzen von Werten, Commit und Abschluss der Sitzung. Der Auswertungscode schreibt unter anderem:

- `cmi.core.score.raw`, `cmi.core.score.min` und `cmi.core.score.max` für die Punktzahl auf der Skala 0–100.
- `cmi.core.lesson_status = completed` für den Bearbeitungsabschluss.
- `cmi.suspend_data` für Zustandsdaten.
- `cmi.core.session_time` für die Sitzungszeit.

`completed` bedeutet hier abgeschlossen, nicht automatisch bestanden. Ohne erreichbare LMS-Schnittstelle verwenden die Apps lokale Speichermechanismen als Fallback; daraus entsteht keine Übertragung ins Moodle-Notenbuch.

## Noch offen: korrektes Paket und Moodle-Test

**Das vorhandene Manifest verweist auf `index.html`. Diese Datei ist im aktuellen Repository nicht vorhanden.** Daher darf der Repository-Inhalt nicht unverändert als fertig geprüftes SCORM-Paket beschrieben werden.

Für ein auslieferbares Paket sind folgende Schritte vorgesehen:

1. Die gewünschte App als Startdatei festlegen und die Ressourcenangaben im Manifest mit den tatsächlichen Dateinamen abgleichen.
2. Alle benötigten Paketdateien zusammenstellen; `imsmanifest.xml` muss direkt im ZIP-Wurzelverzeichnis liegen.
3. Das ZIP in Moodle als Aktivität „Lernpaket / SCORM“ importieren und die Bewertung passend zur Skala 0–100 konfigurieren. Die ursprünglich vorgesehene Bewertungsmethode ist „Höchstnote“; die konkrete Kurskonfiguration ist zu prüfen.
4. Mit einem Testkonto Start, Bearbeitung, Abgabe, Punktzahl, Abschlussstatus, Wiederaufnahme und Übernahme ins Notenbuch prüfen.

Eine implementierte SCORM-Schnittstelle allein belegt noch keine erfolgreiche Notenübernahme. Diese hängt auch vom korrekten Paket und der Moodle-Konfiguration ab. Externe Bibliotheken der HTML-Apps benötigen zudem eine erreichbare Internetverbindung.

## Weiterentwicklung

Die ursprünglich geplanten Verzeichnisse `apps/<app-name>/` und `packages/` sind noch nicht angelegt. Sie können später Quellmodule und geprüfte ZIP-Pakete voneinander trennen. Weitere Themen und ein einheitliches Design bleiben Entwicklungsziele.

## Projektprofil

Das Projekt verbindet die Gestaltung mathematischer Übungen mit Fragen der LMS-Integration: Wie werden Bearbeitungsstand und Ergebnisse erfasst, übergeben und im Kurs nutzbar gemacht? Der aktuelle Stand wird bewusst als Entwicklungsprojekt dokumentiert.

**Ein Projekt von Kai · [GitHub-Profil](https://github.com/schreeckkai)**
