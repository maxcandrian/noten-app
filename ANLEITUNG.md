# Noten-App – Anleitung

Eine kleine Web-App (PWA), um deine Studiennoten nach Semester zu erfassen.
Läuft offline, Daten bleiben **nur auf deinem Gerät** (localStorage).

## Was die App kann
- Semester anlegen, umbenennen, löschen
- Fächer/Module mit Name, ECTS-Credits und Note erfassen
- **ECTS-gewichteter Schnitt** pro Semester und gesamt
- Summe der **bestandenen ECTS** (Note ≥ 4.0)
- Umschalter **1–6 ⇄ A–F** in den Einstellungen (⚙︎)
- Backup **exportieren / importieren** (JSON) – wichtig bei Handywechsel

## Umrechnung 1–6 → A–F (feste Konvention, keine offizielle Formel)
| Schweizer Note | Buchstabe |
|---|---|
| ≥ 5.75 | A |
| 5.25 – 5.74 | B |
| 4.75 – 5.24 | C |
| 4.25 – 4.74 | D |
| 4.00 – 4.24 | E (bestanden) |
| < 4.00 | F (nicht bestanden) |

Hinweis: Die ECTS-Buchstaben sind offiziell rang-/prozentbasiert und keine echte
1:1-Umrechnung aus Zahlennoten. Diese Tabelle ist eine praktische Vereinfachung
und wird in der App unter ⚙︎ angezeigt.

---

## Aufs Smartphone bringen – so wird es eine echte Offline-App

Damit die App offline läuft und ein Homescreen-Icon bekommt, muss sie einmal über
**HTTPS** erreichbar sein. Das Öffnen der Datei direkt aus OneDrive reicht dafür
**nicht** (Offline-Funktion/Service Worker starten nur über eine Web-Adresse).
Empfohlener, kostenloser Weg: **GitHub Pages** (das hast du früher schon genutzt).

### Variante A – GitHub Pages (empfohlen)
1. Neues, öffentliches Repository auf GitHub anlegen (z.B. `noten-app`).
2. Die 6 Dateien aus diesem Ordner hochladen:
   `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`, `icon-512-maskable.png`.
3. Im Repo: **Settings → Pages → Branch: `main` / root → Save**.
4. Nach ~1 Minute bekommst du eine Adresse wie
   `https://<deinname>.github.io/noten-app/`.
5. Diese Adresse auf dem Handy im Browser öffnen → siehe „Installieren" unten.

### Installieren auf dem Homescreen
- **iPhone (Safari):** Teilen-Symbol → „Zum Home-Bildschirm".
- **Android (Chrome):** Menü (⋮) → „App installieren" / „Zum Startbildschirm".

Danach hast du ein eigenes Icon, die App startet im Vollbild und funktioniert
**offline** – auch im Flugmodus.

### Variante B – nur schnell testen (ohne Installation)
Am Computer die Datei `index.html` doppelklicken. Alles funktioniert, nur die
Offline-Installation aufs Handy geht über diesen Weg nicht.

---

## Wichtig: Backup
Die Daten liegen nur auf dem Gerät. Wenn du die App löschst, den Browser-Speicher
leerst oder das Handy wechselst, sind die Noten weg. Darum in den Einstellungen
regelmässig **„Backup exportieren"** – die JSON-Datei kannst du später wieder
importieren.
