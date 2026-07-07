Hardware

Microcontroller: Waveshare ESP32-S3-Zero

EigenschaftWertChipESP32-S3 (Dual-Core, 240 MHz)Flash4 MBPSRAM2 MB (Quad)WLAN802.11 b/g/n (2,4 GHz)BluetoothBT 5 LEUSBUSB-C (USB-OTG, HID-fähig)RGB LEDWS2812B auf GPIO 21Maße22,9 × 18 mmPreisca. 5–8 €


Funktion
USB HID Tastatur

Der ESP32-S3-Zero wird per USB-C an den Notebook angeschlossen. Windows, macOS und Linux erkennen ihn automatisch als USB-HID-Tastatur – genau wie eine normale kabelgebundene Tastatur. Es wird kein Treiber und keine Software installiert.
Wenn der Benutzer auf dem iPhone einen Text abschickt, simuliert der ESP32 die entsprechenden Tastatureingaben inklusive:

Alle Buchstaben A–Z
Zahlen und Sonderzeichen
Deutsche Umlaute: ä ö ü Ä Ö Ü ß
Sonderzeichen: € § ° und mehr
Zeilenumbrüche (Enter)


Das Tastaturlayout ist DE-QWERTZ – Windows muss auf Deutsch eingestellt sein.
WLAN Hotspot (Access Point)
Der ESP32 erstellt einen eigenen WLAN-Hotspot:

SSIDRD-TastaturPasswortrettung123IP-Adresse192.168.4.1Reichweiteca. 10–20 m

Der Hotspot funktioniert ohne Router und ohne Internet – das iPhone verbindet sich direkt mit dem ESP32.
Sobald das iPhone mit dem Hotspot verbunden ist, öffnet sich die Web-App automatisch – genau wie bei Hotel-WLANs. Dafür läuft auf dem ESP32 ein DNS-Server der alle Domains auf 192.168.4.1 umleitet. iOS erkennt dadurch dass kein echtes Internet vorhanden ist und zeigt das Captive Portal.

Die Webseite wird direkt vom ESP32 ausgeliefert (kein Internet nötig). Sie enthält:

Texteingabe mit 6 Zeilen
SENDEN-Button – Text wird per USB als Tastatur eingegeben
8 Standard-Vorlagen für häufige Einsatzdokumentationen
Vorlagen verwalten: Neu erstellen, Bearbeiten, Löschen
Export / Import per Text-Copy-Paste
Hell/Dunkel-Modus
Spracheingabe über das Mikrofon-Symbol der iPhone-Tastatur


Vorlagen-Speicherung
Vorlagen werden im NVS-Flash des ESP32 dauerhaft gespeichert. Nach einem Neustart oder Stromausfall sind alle selbst erstellten Vorlagen noch vorhanden. Die Standard-Vorlagen werden beim ersten Start automatisch geladen.

RGB LED Status
LEDBedeutung🔴 Rot blinkendKein Gerät verbunden🟢 Grün dauerhaftiPhone verbunden


Standard-Vorlagen
EinsatzmeldungArt, Uhrzeit, Patient, Befund, MaßnahmenABCDE-SchemaAtemweg, Atmung, Kreislauf, Neurologie, ExposureNACA-ScoreScore 0–V mit BeschreibungÜbergabe NotaufnahmePatient, Ereignis, Vitalzeichen, TherapieReanimationUhrzeit, Rhythmus, Defis, Adrenalin, ROSCTraumaMechanismus, Verletzungen, Immobilisation, ZugangVitalzeichenRR, Puls, SpO2, AF, BZ, TemperaturÜbergabe LeitstelleFahrzeug, Ort, Diagnose, Zielklinik, Ankunft


Flashen (Firmware aufspielen)
Einmalige Vorbereitung

Schritt 1 – Arduino IDE installieren
Arduino IDE herunterladen und installieren:
https://www.arduino.cc/en/software

Schritt 2 – ESP32 Board-Support installieren
Arduino IDE öffnen
Datei → Einstellungen
Bei „Zusätzliche Boardverwalter-URLs" einfügen:
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
OK klicken
Werkzeuge → Board → Boardverwalter
„esp32" suchen → „esp32 by Espressif Systems" → Installieren (ca. 5 Minuten)


Schritt 3 – Adafruit NeoPixel Bibliothek installieren
Werkzeuge → Bibliotheken verwalten
„Adafruit NeoPixel" suchen → Installieren



Firmware flashen

Schritt 1 – Projekt öffnen
Datei → Öffnen → ESP32_RD_Tastatur.ino auswählen

Schritt 2 – In Download-Modus wechseln

Der ESP32-S3-Zero hat nur eine BOOT-Taste (keine RESET-Taste):

1. BOOT-Taste auf dem Board gedrückt halten
2. USB-C Kabel einstecken (während BOOT gehalten)
3. BOOT-Taste loslassen
→ Windows erkennt den ESP32 im Download-Modus

Schritt 3 – COM-Port auswählen
Werkzeuge → Port → den neu erschienenen COM-Port auswählen (z.B. COM3 oder COM4)

Schritt 4 – Hochladen
Den Pfeil-Button (→ Upload) in der Arduino IDE klicken.

Compiling...    ca. 1 Minute
Uploading...    ca. 30 Sekunden
Done uploading  ✓

Schritt 5 – Neustart
USB-Kabel abziehen und neu einstecken. Der ESP32 startet automatisch.


Testen nach dem Flashen


USB-C Kabel in den Notebook stecken
Windows zeigt in der Taskleiste: „USB-Eingabegerät erkannt" ✓
iPhone → Einstellungen → WLAN → RD-Tastatur → Passwort: rettung123
Captive Portal öffnet sich automatisch
Vorlage antippen → SENDEN → Text erscheint am Notebook-Cursor ✓
LED leuchtet grün wenn iPhone verbunden ✓


Hardware

Microcontroller: Waveshare ESP32-S3-Zero

EigenschaftWertChipESP32-S3 (Dual-Core, 240 MHz)Flash4 MBPSRAM2 MB (Quad)WLAN802.11 b/g/n (2,4 GHz)BluetoothBT 5 LEUSBUSB-C (USB-OTG, HID-fähig)RGB LEDWS2812B auf GPIO 21Maße22,9 × 18 mmPreisca. 5–8 €


Funktion

USB HID Tastatur

Der ESP32-S3-Zero wird per USB-C an den Notebook angeschlossen. Windows, macOS und Linux erkennen ihn automatisch als USB-HID-Tastatur – genau wie eine normale kabelgebundene Tastatur. Es wird kein Treiber und keine Software installiert.

Wenn der Benutzer auf dem iPhone einen Text abschickt, simuliert der ESP32 die entsprechenden Tastatureingaben inklusive:


Alle Buchstaben A–Z
Zahlen und Sonderzeichen
Deutsche Umlaute: ä ö ü Ä Ö Ü ß
Sonderzeichen: € § ° und mehr
Zeilenumbrüche (Enter)


Das Tastaturlayout ist DE-QWERTZ – Windows muss auf Deutsch eingestellt sein.

WLAN Hotspot (Access Point)

Der ESP32 erstellt einen eigenen WLAN-Hotspot:

SSIDRD-TastaturPasswortrettung123IP-Adresse192.168.4.1Reichweiteca. 10–20 m

Der Hotspot funktioniert ohne Router und ohne Internet – das iPhone verbindet sich direkt mit dem ESP32.

Captive Portal

Sobald das iPhone mit dem Hotspot verbunden ist, öffnet sich die Web-App automatisch – genau wie bei Hotel-WLANs. Dafür läuft auf dem ESP32 ein DNS-Server der alle Domains auf 192.168.4.1 umleitet. iOS erkennt dadurch dass kein echtes Internet vorhanden ist und zeigt das Captive Portal.

Web-App

Die Webseite wird direkt vom ESP32 ausgeliefert (kein Internet nötig). Sie enthält:


Texteingabe mit 6 Zeilen
SENDEN-Button – Text wird per USB als Tastatur eingegeben
8 Standard-Vorlagen für häufige Einsatzdokumentationen
Vorlagen verwalten: Neu erstellen, Bearbeiten, Löschen
Export / Import per Text-Copy-Paste
Hell/Dunkel-Modus
Spracheingabe über das Mikrofon-Symbol der iPhone-Tastatur


Vorlagen-Speicherung

Vorlagen werden im NVS-Flash des ESP32 dauerhaft gespeichert. Nach einem Neustart oder Stromausfall sind alle selbst erstellten Vorlagen noch vorhanden. Die Standard-Vorlagen werden beim ersten Start automatisch geladen.

RGB LED Status

LEDBedeutung🔴 Rot blinkendKein Gerät verbunden🟢 Grün dauerhaftiPhone verbunden


Standard-Vorlagen

VorlageInhaltEinsatzmeldungArt, Uhrzeit, Patient, Befund, MaßnahmenABCDE-SchemaAtemweg, Atmung, Kreislauf, Neurologie, ExposureNACA-ScoreScore 0–V mit BeschreibungÜbergabe NotaufnahmePatient, Ereignis, Vitalzeichen, TherapieReanimationUhrzeit, Rhythmus, Defis, Adrenalin, ROSCTraumaMechanismus, Verletzungen, Immobilisation, ZugangVitalzeichenRR, Puls, SpO2, AF, BZ, TemperaturÜbergabe LeitstelleFahrzeug, Ort, Diagnose, Zielklinik, Ankunft


Flashen (Firmware aufspielen)

Einmalige Vorbereitung

Schritt 1 – Arduino IDE installieren
Arduino IDE herunterladen und installieren:
https://www.arduino.cc/en/software

Schritt 2 – ESP32 Board-Support installieren


Arduino IDE öffnen
Datei → Einstellungen
Bei „Zusätzliche Boardverwalter-URLs" einfügen:


https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json


OK klicken
Werkzeuge → Board → Boardverwalter
„esp32" suchen → „esp32 by Espressif Systems" → Installieren (ca. 5 Minuten)


Schritt 3 – Adafruit NeoPixel Bibliothek installieren


Werkzeuge → Bibliotheken verwalten
„Adafruit NeoPixel" suchen → Installieren



Arduino IDE Einstellungen

Diese Einstellungen müssen genau so gesetzt sein:

EinstellungWertBoardESP32S3 Dev ModuleUSB ModeUSB-OTG (TinyUSB)USB CDC On BootDisabledUSB DFU On BootDisabledUpload ModeUART0 / Hardware CDCCPU Frequency240MHzFlash ModeQIO 80MHzFlash Size4MB (32Mb)Partition SchemeDefault 4MB with spiffsPSRAMQuad PSRAMCore Debug LevelNone


Firmware flashen

Schritt 1 – Projekt öffnen
Datei → Öffnen → ESP32_RD_Tastatur.ino auswählen

Schritt 2 – In Download-Modus wechseln

Der ESP32-S3-Zero hat nur eine BOOT-Taste (keine RESET-Taste):

1. BOOT-Taste auf dem Board gedrückt halten
2. USB-C Kabel einstecken (während BOOT gehalten)
3. BOOT-Taste loslassen
→ Windows erkennt den ESP32 im Download-Modus

Schritt 3 – COM-Port auswählen
Werkzeuge → Port → den neu erschienenen COM-Port auswählen (z.B. COM3 oder COM4)

Schritt 4 – Hochladen
Den Pfeil-Button (→ Upload) in der Arduino IDE klicken.

Compiling...    ca. 1 Minute
Uploading...    ca. 30 Sekunden
Done uploading  ✓

Schritt 5 – Neustart
USB-Kabel abziehen und neu einstecken. Der ESP32 startet automatisch.


Testen nach dem Flashen


USB-C Kabel in den Notebook stecken
Windows zeigt in der Taskleiste: „USB-Eingabegerät erkannt" ✓
iPhone → Einstellungen → WLAN → RD-Tastatur → Passwort: rettung123
Captive Portal öffnet sich automatisch
Vorlage antippen → SENDEN → Text erscheint am Notebook-Cursor ✓
LED leuchtet grün wenn iPhone verbunden ✓




Den ESP32 habe ich hier gekauft: https://www.berrybase.de/waveshare-esp32-s3-zero-m-s3fh4r2-dual-core-240mhz-wi-fi-bt-5-usb-c-ohne-header?srsltid=AfmBOooVH5ZJoUuzBtg6t_wYsJtiEjvnLxkPu51F66LTiPJdGQzgdBzI

Das Gehäuse habe ich hier bestellt: https://www.etsy.com/de/listing/1863888382/esp32-c3-super-mini-gehausecase-mit-snap?ls=s&ga_order=most_relevant&ga_search_type=all&ga_view_type=gallery&ga_search_query=esp32+nano+geh%C3%A4use&ref=sr_gallery-1-1&local_signal_search=1&content_source=03af90ae-5a97-4c88-b97a-ec7e22e4c310%253ALTe8c7526c92ae68ca293f48c53db1916ffb54ceba&organic_search_click=1&logging_key=03af90ae-5a97-4c88-b97a-ec7e22e4c310%3ALTe8c7526c92ae68ca293f48c53db1916ffb54ceba

Den USB A auf USB C Adapter hier: https://chipglobe.shop/produkte/usb-c-auf-usb-a-adapter/
