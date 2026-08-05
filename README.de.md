🌍 Sprachen: [🇺🇸 English](https://github.com/Dreamdancer100/GLX-Mail-Relaod-Nextcloud-App-/blob/main/README.md) | [🇩🇪 Deutsch](https://github.com/Dreamdancer100/GLX-Mail-Relaod-Nextcloud-App-/blob/main/README.de.md)

<div align="center">

# 📬 GLX-Mail-Reload für Nextcloud

### Neue Mails erscheinen von allein — kein Neuladen mehr 🔄

*Eine kleine Hilfs-App für die Nextcloud-Mail-App. Sie prüft im selbst gewählten Takt auf neue Nachrichten und frischt die Ansicht selbstständig auf — hält sich aber höflich zurück, solange du schreibst.* ⚡

![Nextcloud](https://img.shields.io/badge/Nextcloud-App-0082C9?logo=nextcloud&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.0%2B-777BB4?logo=php&logoColor=white)
![Lizenz](https://img.shields.io/badge/License-AGPL--3.0--or--later-blue)
![Gebaut von](https://img.shields.io/badge/made%20by-Dreamdancer100-8b0000)

</div>

---

> 🌐 **Hinweis zur Sprache:** Die Oberfläche der App ist derzeit **nur auf Deutsch**. Eine englische Übersetzung ist geplant.

---

## 🤔 Wozu das Ganze?

Nextcloud holt neue Mails zuverlässig im Hintergrund ab. Was es nicht tut: die Ansicht danach auffrischen — neue Nachrichten bleiben also unsichtbar, bis man die ganze Seite neu lädt. Auch der Aktualisieren-Knopf hilft nicht: Er zeigt, was schon in der Datenbank liegt, und die frisch eingetroffene Mail steht eben noch nicht auf dem Schirm. 😤

Genau diese Lücke schließt die App. Sie fragt im eingestellten Takt nach, ob etwas Neueres angekommen ist, und frischt die Ansicht von selbst auf. Kein Knopf, keine Angewohnheit, kein Warten.

---

## 📸 Überblick & Bildschirmfotos

### 1️⃣ Die Einstellungsseite

Ein Schalter zum Einschalten, eine Zahl für den Takt. Mehr gibt es bewusst nicht einzustellen. ⚙️

<p align="center">
  <img src="https://raw.githubusercontent.com/Dreamdancer100/Nextcloud-GLX-Mail-Reload/main/settings.png" alt="Einstellungsseite" width="850">
</p>

---

### 2️⃣ Das Zahnrad in der Kopfleiste

Ist die Unterstützung aktiv, sitzt neben Suche und Glocke ein kleines Zahnrad. Es dreht sich kurz bei jeder Prüfung und wird blass, solange pausiert wird — du siehst also jederzeit, was gerade läuft. Ein Klick führt direkt zu den Einstellungen. 🔘

<p align="center">
  <img src="https://raw.githubusercontent.com/Dreamdancer100/Nextcloud-GLX-Mail-Reload/main/header-icon.png" alt="Das Zahnrad in der Kopfleiste" width="850">
</p>

---

## ✨ Funktionen

- 🔄 **Automatisches Auffrischen** — neue Mails erscheinen, ohne dass du etwas anfassen musst.
- ⏱️ **Takt frei wählbar** — von 10 Sekunden bis zu einer Stunde.
- ✍️ **Pause beim Schreiben** — ein offenes Schreibfenster setzt alles aus. Es wird nie unter einer halbfertigen Mail neu geladen.
- 📤 **Postausgang im Blick** — solange dort etwas auf den Versand wartet, hält die App still.
- 🔘 **Zustand auf einen Blick** — das Zahnrad dreht sich beim Prüfen und wird blass in der Pause.
- 🎯 **Nur dort, wo es hingehört** — das Skript lädt ausschließlich auf den Seiten der Mail-App.
- 🛡️ **Update-fest** — liest die Mail-Tabellen direkt aus, statt sich auf die Innereien der Mail-App zu verlassen. Deren Updates können dieser App also nichts anhaben.
- 🪶 **Kein Ballast** — reines PHP und schlankes JavaScript. Kein Bauschritt, keine Fremdpakete.

---

## 🛠️ So wird es benutzt

Zu finden unter **Einstellungen → Verwaltung → GLX-Mail-Reload**.

1. ☑️ **Unterstützung aktiv** anhaken — der Hauptschalter.
2. ⏱️ Bei **Prüfen alle … Sekunden** den Takt setzen. 60 Sekunden sind ein guter Anfang.
3. 💾 Auf **Speichern** klicken.
4. 📬 Die Mail-App öffnen — das Zahnrad erscheint in der Kopfleiste und macht ab da seine Arbeit.

💡 **Zum Takt:** Kürzer heißt schneller, aber jede Prüfung ist eine Anfrage an deinen Server. Zwischen 30 und 120 Sekunden liegt für die meisten der beste Mittelweg.

---

## 🔬 Wie es funktioniert

Bei jeder Runde fragt die App ihren eigenen Endpunkt nach drei Zahlen: dem Zeitstempel der neuesten Nachricht, der Anzahl ungelesener Mails und der Anzahl im Postausgang. Liegt der neueste Zeitstempel vor dem vom Seitenaufbau, wird die Ansicht aufgefrischt. 🕵️

Vorher greifen zwei Sicherungen. Der Browser prüft, ob ein Schreibfenster offen ist, und der Server meldet, ob im Postausgang noch etwas liegt. Trifft eines davon zu, wird die Runde komplett ausgelassen — und direkt vor dem Auffrischen noch einmal nachgesehen, falls in der Zwischenzeit ein Schreibfenster aufgegangen ist.

Die Abfragen gehen direkt an die Mail-Tabellen statt über die Klassen der Mail-App. Das ist Absicht: So kann ein Update der Mail-App dieser hier nicht den Boden unter den Füßen wegziehen. 🛡️

---

## 🧩 Voraussetzungen

- ☁️ Nextcloud (mit den aktuellen Hauptversionen verträglich)
- 📮 Die **Mail**-App, installiert und eingerichtet
- 🐘 PHP 8.0 oder neuer
- 📦 Keine weiteren Abhängigkeiten

---

## 📦 Installation

1. ⬇️ Dieses Verzeichnis herunterladen oder klonen, in den `apps/`-Ordner deiner Nextcloud legen.
2. 📁 Der Ordner muss exakt **`glxmailreload`** heißen.
3. 🖱️ Die App im Administrationsbereich von Nextcloud aktivieren.

> ⚠️ **Auf den Ordnernamen achten.** Heißt er anders, sucht Nextcloud die App im App Store und bricht mit *„Could not download app"* ab.

> 💡 Die App taucht bewusst nicht im App-Menü auf — sie arbeitet im Hintergrund. Du findest sie unter *Einstellungen → Verwaltung*.

---

## 📄 Lizenz

Dieses Projekt steht unter der **AGPL-3.0-or-later**-Lizenz. Einzelheiten in der Datei [LICENSE](LICENSE).

---

## 🔗 Mehr zur App

👉 **[GLX-Mail-Reload auf gordonx.de](https://gordonx.de/glx-mail-relaod-nextcloud/)** — Beschreibung, Bilder und Download.

---
