🌍 Sprachen: [🇺🇸 English](https://github.com/Dreamdancer100/Nextcloud-GLX-Mail-Reload/blob/main/README.md#) | [🇩🇪 Deutsch](https://github.com/Dreamdancer100/Nextcloud-GLX-Mail-Reload/blob/main/README.de.md)

<div align="center">

# 📬 GLX-Mail-Reload for Nextcloud

### New mail shows up on its own — no more reloading the page 🔄

*A small helper for the Nextcloud Mail app. It checks for new messages on a schedule you choose and refreshes the view by itself — while politely staying out of your way whenever you are writing.* ⚡

![Nextcloud](https://img.shields.io/badge/Nextcloud-App-0082C9?logo=nextcloud&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.0%2B-777BB4?logo=php&logoColor=white)
![License](https://img.shields.io/badge/License-AGPL--3.0--or--later-blue)
![Made by](https://img.shields.io/badge/made%20by-Dreamdancer100-8b0000)

</div>

---

> 🌐 **Language note:** The app interface is currently **German only**. An English translation is planned.

---

## 🤔 Why this exists

Nextcloud reliably fetches new mail in the background. What it does not do is refresh the view afterwards — so new messages stay invisible until you reload the entire page. The refresh button alone does not help either: it shows what is already in the database, and the freshly arrived mail is not on screen yet. 😤

That is the gap this app closes. It asks the server on a schedule whether anything newer has arrived and refreshes the view by itself. No button, no habit to build, no waiting.

---

## 📸 Overview & Screenshots

### 1️⃣ Settings Page

One switch to turn it on, one number for the interval. That is the whole configuration — deliberately. ⚙️

<p align="center">
  <img src="https://github.com/Dreamdancer100/GLX-Mail-Relaod-Nextcloud-App-/blob/main/settings.png" alt="Settings page" width="850">
</p>

---

### 2️⃣ The Gear in the Header Bar

While the helper is active, a small gear sits next to search and notifications. It spins briefly with every check and dims while paused — so you can always tell what is going on. Clicking it takes you straight to the settings. 🔘

<p align="center">
  <img src="https://github.com/Dreamdancer100/GLX-Mail-Relaod-Nextcloud-App-/blob/main/header-icon.png" alt="The gear icon in the header bar" width="850">
</p>

---

## ✨ Features

- 🔄 **Automatic refresh** — new mail appears without you touching anything.
- ⏱️ **Interval of your choice** — anywhere from 10 seconds to an hour.
- ✍️ **Pauses while you write** — an open compose window suspends the whole thing. Nothing is ever reloaded out from under a half-written mail.
- 📤 **Watches the outbox too** — as long as a message is waiting to be sent, the helper holds still.
- 🔘 **Status at a glance** — the gear spins while checking, dims while paused.
- 🎯 **Only where it belongs** — the script loads on Mail pages and nowhere else in your Nextcloud.
- 🛡️ **Update-proof** — reads the mail tables directly instead of relying on the Mail app's internals, so its updates cannot break this one.
- 🪶 **No baggage** — plain PHP and lean JavaScript. No build step, no third-party packages.

---

## 🛠️ How to Use It

Open **Settings → Administration → GLX-Mail-Reload**.

1. ☑️ Tick **Unterstützung aktiv** — the master switch.
2. ⏱️ Set **Prüfen alle … Sekunden**. 60 seconds is a good starting point.
3. 💾 Click **Speichern**.
4. 📬 Open the Mail app — the gear appears in the header and does its job from there on.

💡 **On the interval:** shorter means faster, but every check is one request to your server. Between 30 and 120 seconds is the sweet spot for most setups.

---

## 🔬 How It Works

Every round the app asks its own endpoint for three numbers: the timestamp of the newest message, the unread count, and how many messages are sitting in the outbox. If the newest timestamp is ahead of the one from when the page loaded, the view is refreshed. 🕵️

Two safeguards run before that happens. The browser checks whether a compose window is open, and the server reports whether the outbox still holds anything. If either is true, the round is skipped entirely — and checked again right before the refresh, in case a compose window opened in the meantime.

The queries go straight to the mail tables rather than through the Mail app's own classes. That is deliberate: it means an update to the Mail app cannot pull the rug out from under this one. 🛡️

---

## 🧩 Requirements

- ☁️ Nextcloud (compatible with recent major versions)
- 📮 The **Mail** app, installed and set up
- 🐘 PHP 8.0 or higher
- 📦 No further dependencies

---

## 📦 Installation

1. ⬇️ Download or clone this repository into your Nextcloud `apps/` directory.
2. 📁 Make sure the folder is named exactly **`glxmailreload`**.
3. 🖱️ Enable the app through your Nextcloud Administrator panel.

> ⚠️ **Watch the folder name.** With any other name Nextcloud looks for the app in the App Store and fails with *"Could not download app"*.

> 💡 The app does not appear in the app menu on purpose — it works in the background. You will find it under *Settings → Administration*.

---

## 📄 License

This project is licensed under the **AGPL-3.0-or-later** license. See the [LICENSE](LICENSE) file for details.

---

## 🔗 More about this app

👉 **[GLX-Mail-Reload on gordonx.de](https://gordonx.de/glx-mail-relaod-nextcloud/)** — description, screenshots and download.

---
