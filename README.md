# 🚑 RD Tastatur

> ESP32-S3 basiertes USB-HID Gerät für den Rettungsdienst – Text per iPhone auf den Einsatzrechner übertragen, ohne Installation, ohne Treiber.

---

## 💡 Idee

Im Rettungsdienst muss Dokumentation oft schnell und präzise in Einsatzsoftware eingegeben werden. Die RD Tastatur löst das Problem: Ein kleines ESP32-Board steckt am USB-Port des Notebooks und erscheint dort als normale Tastatur. Das iPhone verbindet sich per WLAN direkt mit dem Board – eine Web-App öffnet sich automatisch. Vorlage antippen, anpassen, SENDEN – der Text erscheint sofort am Cursor.

---

## ✨ Features

- **Plug & Play** – Windows erkennt das Gerät als USB-Tastatur, kein Treiber nötig
- **Automatisches Captive Portal** – Web-App öffnet sich automatisch nach WLAN-Verbindung
- **DE-QWERTZ** – Alle Umlaute (ä ö ü ß) werden korrekt übertragen
- **8 Vorlagen** vorinstalliert (Einsatzmeldung, ABCDE, NACA, Reanimation, Trauma, …)
- **Vorlagen verwalten** – Neu erstellen, Bearbeiten, Löschen direkt auf dem iPhone
- **Dauerhafter Speicher** – Vorlagen bleiben nach Stromausfall erhalten (NVS-Flash)
- **Export / Import** – Vorlagen per Text-Copy-Paste sichern und übertragen
- **Hell/Dunkel-Modus** – Umschaltbar per Button
- **LED-Status** – Rot blinkend = kein Gerät, Grün = verbunden
- **Kein Internet nötig** – Funktioniert komplett offline

---

## 🛠 Hardware

| Komponente | Details |
|---|---|
| **Board** | [Waveshare ESP32-S3-Zero](https://www.waveshare.com/esp32-s3-zero.htm) |
| **Chip** | ESP32-S3, Dual-Core 240 MHz |
| **Flash** | 4 MB |
| **PSRAM** | 2 MB Quad |
| **Anschluss** | USB-C |
| **RGB LED** | WS2812B auf GPIO 21 |
| **Preis** | ca. 5–8 € |

---

## 🔧 Funktionsweise

```
iPhone
  │
  │  WLAN (Hotspot "RD-Tastatur")
  │  Captive Portal → 192.168.4.1
  ▼
ESP32-S3-Zero
  │
  │  USB-C → USB HID Keyboard
  ▼
Notebook (Windows)
  → Text erscheint am Cursor
```

1. ESP32 erstellt WLAN-Hotspot **„RD-Tastatur"** (kein Router nötig)
2. iPhone verbindet sich → Captive Portal öffnet sich automatisch
3. Vorlage antippen → Text anpassen → SENDEN
4. ESP32 simuliert Tastatureingaben per USB HID
5. Text erscheint direkt im aktiven Programm am Notebook

---

## 📋 Vorlagen

| Vorlage | Felder |
|---|---|
| Einsatzmeldung | Art, Uhrzeit, Patient, Befund, Maßnahmen |
| ABCDE-Schema | Atemweg, Atmung, Kreislauf, Neurologie, Exposure |
| NACA-Score | Score 0–V mit Erklärung |
| Übergabe Notaufnahme | Patient, Ereignis, Vitalzeichen, Therapie |
| Reanimation | Rhythmus, Defis, Adrenalin, ROSC |
| Trauma | Mechanismus, Verletzungen, Zugang, Analgesie |
| Vitalzeichen | RR, Puls, SpO2, AF, BZ, Temperatur |
| Übergabe Leitstelle | Fahrzeug, Ort, Diagnose, Zielklinik |

Eigene Vorlagen können direkt auf dem iPhone erstellt und dauerhaft gespeichert werden.

---

## 🚀 Installation

### Voraussetzungen

- [Arduino IDE](https://www.arduino.cc/en/software) (Version 2.x)
- ESP32 Board-Support von Espressif
- Adafruit NeoPixel Bibliothek

### ESP32 Board-Support installieren

1. Arduino IDE → Datei → Einstellungen
2. Bei „Zusätzliche Boardverwalter-URLs" einfügen:
```
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
```
3. Werkzeuge → Board → Boardverwalter → **„esp32 by Espressif Systems"** installieren

### Adafruit NeoPixel installieren

Werkzeuge → Bibliotheken verwalten → **„Adafruit NeoPixel"** suchen → Installieren

### Arduino IDE Einstellungen

| Einstellung | Wert |
|---|---|
| Board | `ESP32S3 Dev Module` |
| USB Mode | `USB-OTG (TinyUSB)` |
| USB CDC On Boot | `Disabled` |
| Upload Mode | `UART0 / Hardware CDC` |
| Flash Size | `4MB (32Mb)` |
| Partition Scheme | `Default 4MB with spiffs` |
| PSRAM | `Quad PSRAM` |

### Flashen

Der ESP32-S3-Zero hat nur eine BOOT-Taste (keine RESET-Taste):

```
1. BOOT-Taste gedrückt halten
2. USB-C Kabel einstecken  (BOOT weiter halten)
3. BOOT-Taste loslassen
4. In Arduino IDE: Port auswählen → Upload (→)
5. Nach "Done uploading": Kabel abziehen und neu einstecken
```

---

## 📱 Benutzung

```
1. USB-C in Notebook stecken  →  LED blinkt rot
2. iPhone: WLAN → "RD-Tastatur"  (Passwort: rettung123)
3. Captive Portal öffnet sich automatisch  →  LED leuchtet grün
4. Vorlage antippen → anpassen → SENDEN
5. Text erscheint am Notebook-Cursor ✓
```

> **Tipp:** Windows Tastaturlayout muss auf **Deutsch (DE)** eingestellt sein damit Umlaute korrekt übertragen werden.

---

## 💡 LED Status

| LED | Bedeutung |
|---|---|
| 🔴 Rot blinkend | Kein Gerät verbunden |
| 🟢 Grün dauerhaft | iPhone/Gerät verbunden |

---

## 📁 Projektstruktur

```
ESP32_RD_Tastatur/
└── ESP32_RD_Tastatur.ino   # Komplette Firmware (Arduino Sketch)
```

Die gesamte Firmware – USB HID, WLAN Hotspot, DNS Server, Webserver, Web-App (HTML/CSS/JS), NVS Speicher – ist in einer einzigen `.ino` Datei enthalten.

---

## 🔧 Konfiguration

WLAN-Name und Passwort können am Anfang der `.ino` Datei angepasst werden:

```cpp
const char* WIFI_SSID     = "RD-Tastatur";
const char* WIFI_PASSWORD = "rettung123";
```

---

## 📄 Lizenz

MIT License – frei verwendbar, anpassbar und weiterzugeben.

---

## ⚠️ Rechtlicher Hinweis

Dieses Projekt ist ein **unabhängiges Open-Source-Projekt** und steht in **keiner Verbindung** zu NIDA, dem NIDA Pad oder dessen Hersteller.

Die RD Tastatur simuliert ausschließlich eine **Standard-USB-HID-Tastatur** – identisch mit jeder handelsüblichen Tastatur. Es werden keine Änderungen am NIDA Pad, dessen Software oder Daten vorgenommen. Das Gerät sendet lediglich Tastatureingaben, genau so als würde jemand manuell auf einer Tastatur tippen.

Die Verantwortung für den korrekten Einsatz im klinischen und rettungsdienstlichen Umfeld liegt beim Anwender.
