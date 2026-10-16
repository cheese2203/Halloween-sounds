# Halloween Sounds 🎃

Neun deutschsprachige Halloween-Audioansagen mit unterschiedlichen, düsteren bzw. kinderfreundlichen Retro-Synthesizer-Hintergründen. Die Dateien sind für eine private Halloween-Automation mit **ioBroker**, **Reolink-Personenerkennung**, **WLED** und einem **Amazon Echo Show** vorbereitet.

## Audio-Dateien

| Ansage | Kategorie | Ungefähre Dauer | Dateiname |
|---|---|---:|---|
| [Der Wächter des Hofes](./Halloween_01_Waechter_Analog_Mystery_Alexa.mp3) | Grusel | 24,9 s | `Halloween_01_Waechter_Analog_Mystery_Alexa.mp3` |
| [Die hungrigen Geister](./Halloween_02_Geister_Analog_Mystery_Alexa.mp3) | Grusel | 24,0 s | `Halloween_02_Geister_Analog_Mystery_Alexa.mp3` |
| [Der Fluch der Garage](./Halloween_04_Fluch_Garage_Analog_Mystery_Alexa.mp3) | Grusel | 27,8 s | `Halloween_04_Fluch_Garage_Analog_Mystery_Alexa.mp3` |
| [Der Süßigkeiten-Dämon](./Halloween_06_Daemon_Analog_Mystery_Alexa.mp3) | Grusel | 32,8 s | `Halloween_06_Daemon_Analog_Mystery_Alexa.mp3` |
| [Halloween-Horror-Ansage](./Halloween_Hof_Horror_Soundtrack_Laut_Alexa.mp3) | Grusel | 18,9 s | `Halloween_Hof_Horror_Soundtrack_Laut_Alexa.mp3` |
| [Der freundliche Garagengeist](./Halloween_Kinder_01_Garagengeist_Alexa.mp3) | Kinder | ca. 22,9 s | `Halloween_Kinder_01_Garagengeist_Alexa.mp3` |
| [Die verzauberte Garage](./Halloween_Kinder_02_Zaubergarage_Alexa.mp3) | Kinder | ca. 20,8 s | `Halloween_Kinder_02_Zaubergarage_Alexa.mp3` |
| [Der kleine Werwolf](./Halloween_Kinder_03_Kleiner_Werwolf_Alexa.mp3) | Kinder | ca. 23,0 s | `Halloween_Kinder_03_Kleiner_Werwolf_Alexa.mp3` |
| [Das kichernde Monster](./Halloween_Kinder_04_Kicherndes_Monster_Alexa.mp3) | Kinder | ca. 23,0 s | `Halloween_Kinder_04_Kicherndes_Monster_Alexa.mp3` |

## Audioformat

- **MP3**, MPEG-2 Layer III
- **24 kHz** Abtastrate, **48 kbit/s** Bitrate
- **Mono**
- Export ohne Xing-Header

Die Audiodateien sind für die Wiedergabe mittels SSML-`audio`-Tag über den ioBroker-Adapter **alexa2** vorbereitet. Ob die Wiedergabe klappt, hängt auch von Amazon Alexa, Gerät und Adapterzustand ab.

## Direkte HTTPS-Audio-URLs

Alexa benötigt für die SSML-Wiedergabe eine öffentlich erreichbare direkte Audio-URL. Für dieses Repository gilt:

```text
https://raw.githubusercontent.com/cheese2203/Halloween-sounds/main/DATEINAME.mp3
```

Beispiel:

```xml
<speak>
  <audio src="https://raw.githubusercontent.com/cheese2203/Halloween-sounds/main/Halloween_Hof_Horror_Soundtrack_Laut_Alexa.mp3"/>
</speak>
```

Beispiel für den ioBroker-JavaScript-Adapter (Geräte-ID anpassen):

```javascript
const echo = 'alexa2.0.Echo-Devices.DEINE_GERAETE_ID';
const url = 'https://raw.githubusercontent.com/cheese2203/Halloween-sounds/main/Halloween_Hof_Horror_Soundtrack_Laut_Alexa.mp3';
setState(echo + '.Commands.speak', '<speak><audio src="' + url + '"/></speak>');
```

## Automationsidee

Wenn die Hofkamera eine Person erkennt, wählt ein ioBroker-Skript zufällig **eine** der neun MP3s. Die WLED-Beleuchtung an der Garage pulsiert dazu rot. Nach Ende der ausgewählten Aufnahme kann ein Alexa-Wolfsgeheul abgespielt werden; danach wird die ursprüngliche Beleuchtung wiederhergestellt. Die Laufzeiten sind unterschiedlich und sollten bei der zeitlichen Steuerung berücksichtigt werden.

Das eigentliche ioBroker-Skript wird **nicht** in diesem Repository verwaltet.

## Hinweise

- Die kinderfreundlichen Ansagen sind milder gestaltet als die fünf Gruselversionen.
- Bei Nutzung einer gemeinsamen Zufallsauswahl können auch kleine Kinder eine intensive Gruselansage erhalten. Bei Bedarf die Gruppen separat verwenden.
- Lautstärke, Personenerkennung und Sicherheitsabstände vor einer Veranstaltung testen.
- Für die Verwendung oder öffentliche Weitergabe der Audios die jeweils geltenden Rechte und Nutzungsbedingungen der verwendeten Stimme und Tools beachten.

Viel Spaß an Halloween! 👻
