# GYMFLOW v4 – stärkere Planbilder und Cardio

**Dein Backup vom 21.10.2026 ist bereits eingebaut.** Bei einer NEUEN Installation erscheinen automatisch deine Pläne **Push**, **Pull** und **Legs**, insgesamt 19 Übungen. Im bereitgestellten Backup sind keine abgeschlossenen Trainings enthalten (`history: []`). Zusätzlich ergänzt die App jetzt automatisch einen vierten Plan **Cardio**, falls er noch nicht existiert.

**Wichtig bei einem Update deiner bestehenden iPhone-App:** Deine bisherigen Daten bleiben erhalten, denn GYMFLOW benutzt denselben lokalen Speicherschlüssel (`gymflow-data-v1`). Vorhandene Pläne, neue Änderungen und Workouts haben Vorrang vor den eingebauten Backup-Daten. Die Backup-Vorgaben werden ausschließlich benutzt, wenn noch keine lokalen Daten existieren. Der Cache wird erneuert, aber keine Daten absichtlich gelöscht. Bewahre dein exportiertes Backup sicher auf.

## Ganzes ZIP auf GitHub Pages aktualisieren

1. ZIP auf deinem Windows-PC entpacken.
2. Dein bestehendes GitHub-Repository `gymflow-app` öffnen (dasselbe Repository und dieselbe GitHub-Pages-Adresse wie bisher beibehalten).
3. `Add file` → `Upload files` wählen und **alle Inhalte aus dem entpackten Ordner** hochladen, auch `icons/`, `app.js`, `sw.js`, `index.html`, `manifest.webmanifest` und `styles.css`. Dateien gleichen Namens ersetzen; die neuen Icon-Dateien `icon-192-v2.png` und `icon-512-v2.png` mit hochladen.
4. `Commit changes` anklicken. GitHub Pages braucht gegebenenfalls kurz für die Veröffentlichung.
5. Deine bisherige GYMFLOW-App auf dem iPhone schließen und wieder öffnen. Wenn noch das alte Symbol auf dem Home-Bildschirm angezeigt wird, kann iOS es zwischenspeichern. Dein Backup ist deine Absicherung, bevor du eine Web-App-Installation entfernst. **Die Web-App nicht voreilig löschen** – beim Entfernen können lokal gespeicherte Trainingsdaten verloren gehen.

Die Daten liegen weiterhin ausschließlich lokal. Das Backup ist in der öffentlich gehosteten App auch als Ausgangsbestand im Quellcode vorhanden: Da du GitHub Pages nutzt, ist der App-Code öffentlich. In dieser Sicherung sind nur die Trainingspläne, keine Workout-Historie.

---

# GYMFLOW – kostenlose Gym-App für iPhone und Windows

Eine vollständige Progressive Web App (PWA) ohne Abo, Werbung, Anmeldung oder externe Dienste. Alles läuft lokal im Browser. Die Web-App nutzt HTML, CSS und JavaScript, benötigt keine Build-Tools und keine kostenpflichtige Entwicklerlizenz.

## Funktionen

- Deine angepassten Pläne Push, Pull und Legs aus deinem Backup plus automatisch ergänzter Cardio-Plan
- Sätze, Gewicht (kg), Wiederholungen – inklusive Vorschlagswerten aus dem vorherigen Training
- Zwischenspeicherung des aktiven Workouts, Abschluss und Trainingshistorie
- Bestgewichte pro Übung und Diagramme für Bestgewichte und 8 Wochen Trainingsvolumen
- Export und Import aller Daten als JSON-Datei
- Offline-Unterstützung nach dem ersten erfolgreichen Online-Laden
- Home-Bildschirm-Icon, mobile Darstellung, keine externe Verbindung aus dem Programm

## 1. Lokal auf Windows testen

1. ZIP entpacken.
2. Im Ordner `gymflow-app` `index.html` doppelt anklicken. Das funktioniert zur Voransicht, aber der Offline-Service-Worker funktioniert unter `file://` nicht.
3. Für eine vollständige lokale Voransicht: Falls Python installiert ist, im entpackten Ordner ein Terminal öffnen und `python -m http.server 8000` ausführen. Anschließend `http://localhost:8000` im Browser öffnen.

## 2. Kostenlos mit GitHub Pages veröffentlichen

1. Einen kostenlosen Account bei https://github.com erstellen oder anmelden.
2. Oben auf `+` → `New repository`, als Repository-Namen z.B. `gymflow-app` wählen, **Public** auswählen, `Create repository`.
3. `uploading an existing file` oder `Add file` → `Upload files` auswählen. Den entpackten **Inhalt** des Ordners `gymflow-app` hochladen: `index.html`, `styles.css`, `app.js`, `sw.js`, `manifest.webmanifest` und den Unterordner `icons/` mit den PNG-Dateien. Nicht den äußeren ZIP-Ordner hochladen. **Wichtig:** Unter `icons/` müssen besonders `icon-192-v2.png` und `icon-512-v2.png` ankommen. (Die Datei `.nojekyll` ist optional.) Auf `Commit changes` klicken.
4. Im Repository: `Settings` → `Pages` → `Build and deployment` → `Source: Deploy from a branch` → `Branch: main`, Ordner `/(root)` → `Save`.
5. Nach der Veröffentlichung findest du deine App unter `https://DEIN-NAME.github.io/gymflow-app/`. GitHub zeigt die echte URL auch unter `Settings` → `Pages`.

GitHub Pages hostet den **öffentlichen Quellcode**, aber nicht die Trainingsdaten: Die bleiben lokal auf deinem Gerät, solange du kein Backup selbst teilst.

## 3. Auf das iPhone installieren

1. Die veröffentlichte HTTPS-Adresse **in Safari** auf dem iPhone öffnen.
2. Das Teilen-Menü öffnen und `Zum Home-Bildschirm hinzufügen` wählen.
3. Gegebenenfalls `Als Web-App öffnen` einschalten → `Hinzufügen`.
4. Die App über das neue GYMFLOW-Symbol starten. Einmal mit Internet öffnen, damit die Offline-Dateien im Cache liegen.

## Daten & wichtige Hinweise

- **Keine Synchronisierung:** Die Daten von iPhone und Windows sind zunächst getrennt; Übertragung nur durch Export/Import unter `Mehr`.
- **Backups:** Browserdaten können gelöscht werden (z. B. beim Bereinigen von Website-Daten oder Gerätewechsel). Regelmäßig unter `Mehr` → `Backup herunterladen` sichern. Nach einem Wechsel der URL/Domain muss das Backup importiert werden.
- **Gewicht:** Das Feld ist in kg; für Übungen mit dem eigenen Körpergewicht kannst du `0` eintragen. Es gibt keine medizinische Trainingssteuerung.
- **PWA vs. App Store:** Dies ist eine Home-Bildschirm-Web-App, keine App-Store-App. Du brauchst kein Mac-Gerät und kein Apple-Developer-Abo dafür.
- **Installation:** PWA-Installation und Offline-Cache benötigen die HTTPS-Seite oder `localhost`; ein lokal per Doppelklick geöffnetes `index.html` kann nicht als vollständige PWA installiert werden.
- **Updates:** Ändere bei einer späteren Code-Version den Cache-Namen in `sw.js` (z.B. `gymflow-static-v3`), um das Offline-Paket zu erneuern. Die lokalen Daten in `localStorage` bleiben davon unberührt, sofern du den Speicher nicht löschst.

## Dateien

- `index.html` — Einstieg
- `styles.css` — Design
- `app.js` — sämtliche Funktionen und lokale Datenspeicherung
- `manifest.webmanifest` — installierbare App-Einstellungen
- `sw.js` — Offline-Caching
- `icons/` — neue App-Symbole (mit `-v2` für den iPhone-Icon-Cache)
- `DEIN-TRAININGSPLAN-BACKUP.json` — Original-Backup zum manuellen Wiederherstellen

© Eigene Nutzung, frei veränderbar.
