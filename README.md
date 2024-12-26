# sphaira

Ein Homebrew Menü für die Nintendo Switch.

Das Projekt wurde für den persönlichen Gebrauch entwickelt und enthält daher einige spezielle Funktionen, die sich als nützlich erwiesen haben.

[Weitere Details und Diskussionen im gbatemp-Forum](https://gbatemp.net/threads/sphaira-hbmenu-replacement.664523/).

## Vorschau

|                          |                          |
:-------------------------:|:-------------------------:
![Bild](assets/screenshots/2024121522512100-879193CD6A8B96CD00931A628B1187CB.jpg) | ![Bild](assets/screenshots/2024121522514300-879193CD6A8B96CD00931A628B1187CB.jpg)
![Bild](assets/screenshots/2024121522513300-879193CD6A8B96CD00931A628B1187CB.jpg) | ![Bild](assets/screenshots/2024121523084100-879193CD6A8B96CD00931A628B1187CB.jpg)
![Bild](assets/screenshots/2024121522505300-879193CD6A8B96CD00931A628B1187CB.jpg) | ![Bild](assets/screenshots/2024121522502300-879193CD6A8B96CD00931A628B1187CB.jpg)
![Bild](assets/screenshots/2024121523033200-879193CD6A8B96CD00931A628B1187CB.jpg) | ![Bild](assets/screenshots/2024121523070300-879193CD6A8B96CD00931A628B1187CB.jpg)

## Fehlermeldungen

Für Fehlermeldungen bitte den Issues-Tab nutzen und das Problem so detailliert wie möglich beschreiben!

Folgende Informationen werden benötigt:

- CFW-Typ (standardmäßig Atmosphere, aber eventuell auch Rajnx)
- CFW-Version
- Firmware-Version
- Beschreibung des Fehlers und Schritte zur Reproduktion

## Dateizuordnungen

sphaira unterstützt Dateizuordnungen. Wenn eine Anwendung beispielsweise .png-Dateien unterstützt, kann eine Zuordnungsdatei erstellt werden. Im Dateibrowser wird dann beim Klicken auf eine .png-Datei die zugeordnete Anwendung gestartet und die .png-Datei als argv[1] übergeben. Diese Funktion wurde hauptsächlich für das Laden von ROMs in Emulatoren und Frontends wie RetroArch, melonDS, mGBA etc. implementiert.

```ini:assets/romfs/assoc/example.ini
[config]
path=/switch/your_app.nro
supported_extensions=jpg|png|mp4|mp3
```

Das `path`-Feld ist optional. Wird es weggelassen, wird der Name der ini-Datei verwendet, um die nro-Datei zu finden. Beispiel: Bei einer Datei namens mgba.ini wird nach der nro-Datei unter /switch/mgba.nro und /switch/folder/mgba.nro gesucht.

Weitere Beispiele für Dateizuordnungen befinden sich im Verzeichnis `assets/romfs/assoc/`

## Danksagungen

- borealis
- stb
- yyjson
- nx-hbmenu
- nx-hbloader
- deko3d-nanovg
- libpulsar
- minIni
- gbatemp
- hb-appstore
- Allen Mitwirkenden an diesem Projekt!

---
---

## Sphaira - hbmenu Ersatz

Sphaira ist eine Alternative zum hbmenu. Es bietet die gleichen Grundfunktionen wie hbmenu (Start von Homebrew + nxlink), enthält aber zusätzlich viele weitere Features.

### HomeBrew

Der Hauptmenü-Tab listet alle .nro-Dateien auf, die sich in "/switch/" befinden. Von hier aus kannst du Programme starten, sortieren, löschen und Forwarder erstellen.
Mit den Tasten "L" und "R" navigierst du zu den anderen Menü-Tabs, die unten erklärt werden.

### DateiBrowser

Durch Drücken von "L" im Hauptmenü gelangst du zum Dateibrowser. Hier kannst du Dateien ausschneiden, kopieren, löschen, umbenennen und mehr.
Mit der "ZR"-Taste können mehrere Dateien/Ordner ausgewählt werden, um diese Funktionen auf die gesamte Auswahl anzuwenden.

Forwarder können erstellt werden, wenn die ausgewählte Datei eine Dateizuordnung hat (siehe Details unten).

### Appstore

Sphaira verfügt über einen Appstore, der die API von [https://hb-app.store/switch](https://hb-app.store/switch) nutzt. Du erreichst ihn durch Drücken von "R" im Hauptmenü.
Der Appstore bietet die gleichen Funktionen wie die hb-appstore App und installiert die Manifeste im selben Ordner wie hb-appstore, um die Kompatibilität zwischen beiden zu gewährleisten.

### Themes

Sphaira kommt mit 3 Themes: Abyss (Standard), Schwarz und Weiß (unfertig).
Eigene Themes können unter "/config/sphaira/themes/" hinzugefügt werden. Hier ist ein Beispiel des Abyss-Themes:

```ini
[meta]
name=Abyss
author=TotalJustice
version=1.0.0
; derzeit ungenutzt
preview=romfs:/theme/preview.jpg

[theme]
background=0x0f111aff
grid=0x0f115c30
selected=0x0f115cff
selected_overlay=0x529cffff
text=0xffbc41ff
text_selected=0x529cffff

icon_audio=romfs:/theme/icon_audio.png
icon_video=romfs:/theme/icon_video.png
icon_image=romfs:/theme/icon_image.png
icon_file=romfs:/theme/icon_file.png
icon_folder=romfs:/theme/icon_folder.png
icon_zip=romfs:/theme/icon_zip.png
icon_nro=romfs:/theme/icon_nro.png
```

Musik kann zu einem Theme hinzugefügt werden, sofern sie im bfstm-Format vorliegt. Füge dazu einfach einen Eintrag wie folgt hinzu: `music=/config/sphaira/themes/music/bgmusic_pcm.bfstm`

### Forwarder

Sphaira kann Forwarder für jede .nro-Datei erstellen und installieren. Dabei wird das Icon der .nro-Datei sowie Name und Autor verwendet.

Es können auch Forwarder für Dateien mit Dateizuordnung erstellt werden. Wenn zum Beispiel mgba installiert ist und sich ein Spiel unter "/roms/gba/game.gba" befindet, erscheint die Option "Forwarder installieren". In diesem Fall wird versucht, das Icon des Spiels zu extrahieren, andernfalls wird das Icon der .nro-Datei verwendet und der Name wird aus einer Kombination von .nro-Name und Spielname gebildet.

### Dateizuordnungen

Dateizuordnungen ermöglichen es, Dateierweiterungen (.gba, .nro etc.) mit einer Homebrew-App zu verknüpfen. Beim Klicken auf eine rom.gbc-Datei mit Zuordnung erscheint eine Liste aller Anwendungen, die diese Datei öffnen können.
Dies kann für Emulatoren, Mediaplayer, Texteditoren etc. verwendet werden.

Eigene Dateizuordnungen gehören in den Ordner "/config/sphaira/assoc/"

Das Format ist *sehr* einfach. Hier ein Beispiel für vgedit.ini:

```ini
[config]
supported_extensions=txt|json|cfg|ini|md|log
```

Und hier für mgba.ini:

```ini
[config]
supported_extensions=gba|gbc|sgb|gb
database=Nintendo - Game Boy|Nintendo - Game Boy Color|Nintendo - Game Boy Advance
```

"path": (optional) Vollständiger Pfad zur .nro-Datei. Wenn nicht angegeben, wird der Name der ini-Datei verwendet, z.B. verwendet mgba.ini die mgba.nro.
"supported_extensions": Liste der unterstützten Dateierweiterungen, getrennt durch |
"database": (optional) Name der ROM-Datenbank, definiert durch die linke Seite dieser Tabelle [https://gist.github.com/ITotalJustice/d5e82ba601ca13b638af9b00e33a4a86](https://gist.github.com/ITotalJustice/d5e82ba601ca13b638af9b00e33a4a86)

Alle RetroArch-Cores haben in sphaira integrierte Dateizuordnungen. Wenn du RetroArch über den Appstore herunterlädst und dann zu "/roms/gbc/game.gbc" navigierst, stehen Gambatte und mGBA zur Auswahl.

Spiele können im .zip-Format bleiben. Sphaira schaut in die .zip-Datei und erkennt die tatsächliche Erweiterung für die Anzeige von Icons/Dateizuordnungen.

### ROMs

ROMs sollten unter "/roms/system_name/" abgelegt werden, wobei system_name durch die Einträge auf der rechten Seite dieser Tabelle definiert ist: [https://gist.github.com/ITotalJustice/d5e82ba601ca13b638af9b00e33a4a86](https://gist.github.com/ITotalJustice/d5e82ba601ca13b638af9b00e33a4a86)
Dies entspricht dem Layout von EmulationStation. Die Einsortierung in spezifische Ordner ist notwendig, da viele ROMs verschiedener Systeme die gleichen Dateierweiterungen verwenden, z.B. .bin/.cue oder .chd.

ROMs können auch in Unterordnern abgelegt werden, zum Beispiel ist "/roms/psx/scooby-doo/scooby-doo.bin" gültig.

### Themezer

Themes können über Menü-Optionen -> Verschiedenes -> Themezer durchsucht und heruntergeladen werden. Themes werden nach "/themes/sphaira/Theme Name - By Author/" heruntergeladen.
Um Themes zu installieren, starte "NXThemes Installer" und navigiere zum entsprechenden Ordner.

### IRS

InfraRot-Sensor. Eine kleine Spielerei-App, die ich vor etwa 4 Jahren entwickelt habe und die die Ausgabe des Joycon-IRS anzeigt. Damit kannst du Selfies machen! 😊

### Web

Startet den eingebauten Webbrowser - er ist nicht besonders gut.

### Nxlink

Für Homebrew-Entwickler ist nxlink in sphaira integriert. Du musst keine speziellen Tasten drücken, führe einfach "nxlink *.nro" aus und sende deine nro wie gewohnt. Konsolenprotokollierung funktioniert mit "nxlink -s *.nro"
Standardmäßig ist dies im Hintergrund aktiviert. Zum Deaktivieren: Menü-Optionen -> Netzwerk -> Nxlink.

---

Das sind die wichtigsten Funktionen von sphaira. Wenn es dir so gut gefällt, dass du es anstelle des regulären hbmenu verwenden möchtest, kannst du die Option unter "Menü-Optionen -> hbmenu beim Beenden ersetzen" aktivieren. Dabei wird eine Sicherungskopie von hbmenu unter "/switch/hbmenu.nro" erstellt, falls du zurückwechseln möchtest.