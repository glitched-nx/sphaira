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
# sphaira

A homebrew menu for the switch.

[See the gbatemp thread for more details / discussion](https://gbatemp.net/threads/sphaira-hbmenu-replacement.664523/).

## showcase

|                          |                          |
:-------------------------:|:-------------------------:
![Img](assets/screenshots/2024121522512100-879193CD6A8B96CD00931A628B1187CB.jpg) | ![Img](assets/screenshots/2024121522514300-879193CD6A8B96CD00931A628B1187CB.jpg)
![Img](assets/screenshots/2024121522513300-879193CD6A8B96CD00931A628B1187CB.jpg) | ![Img](assets/screenshots/2024121523084100-879193CD6A8B96CD00931A628B1187CB.jpg)
![Img](assets/screenshots/2024121522505300-879193CD6A8B96CD00931A628B1187CB.jpg) | ![Img](assets/screenshots/2024121522502300-879193CD6A8B96CD00931A628B1187CB.jpg)
![Img](assets/screenshots/2024121523033200-879193CD6A8B96CD00931A628B1187CB.jpg) | ![Img](assets/screenshots/2024121523070300-879193CD6A8B96CD00931A628B1187CB.jpg)

## bug reports

for any bug reports, please use the issues tab and explain in as much detail as possible!

please include:

- CFW type (i assume Atmosphere, but someone out there is still using Rajnx)
- CFW version
- FW version
- The bug itself and how to reproduce it

## ftp

ftp can be enabled via the network menu and listens on port 5000, no username or password is required.

## mtp

mtp can be enabled via the network menu.

## file assoc

sphaira has file assoc support. lets say your app supports loading .png files, then you could write an assoc file, then when using the file browser, clicking on a .png file will launch your app along with the .png file as argv[1]. This was primarly added for rom loading support for emulators / frontends such as retroarch, melonds, mgba etc.

```ini
[config]
path=/switch/your_app.nro
supported_extensions=jpg|png|mp4|mp3
```

the `path` field is optional. if left out, it will use the name of the ini to find the nro. For example, if the ini is called mgba.ini, it will try to find the nro in /switch/mgba.nro and /switch/folder/mgba.nro.

see `assets/romfs/assoc/` for more examples of file assoc entries

## Credits

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
- haze
- everyone who has contributed to this project!
