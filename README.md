# FHEM Style: haus-automatisierung.com – Weiterentwicklung

Dieses Repository ist eine Weiterentwicklung des FHEM-Themes **haus-automatisierung.com** von **Matthias Kleine (klein0r)**. Das Theme verändert die Darstellung der FHEM-Weboberfläche und orientiert sich am Design von [haus-automatisierung.com](https://haus-automatisierung.com/).

- **Originalprojekt:** [klein0r/fhem-style-haus-automatisierung](https://github.com/klein0r/fhem-style-haus-automatisierung)
- **Weiterentwicklung und Pflege:** [meier81](https://github.com/meier81/fhem-style-haus-automatisierung)
- **Lizenz:** MIT (ursprünglicher Copyright-Hinweis bleibt erhalten)

## Entwicklungsstand

| Branch | Bedeutung |
| --- | --- |
| [main](https://github.com/meier81/fhem-style-haus-automatisierung/tree/main) | Stabile, freigegebene Version; derzeit unveränderter Theme-Stand aus dem bisherigen `version-2`-Branch |
| [dev](https://github.com/meier81/fhem-style-haus-automatisierung/tree/dev) | Laufende Weiterentwicklung und Testversionen |
| [version-3](https://github.com/meier81/fhem-style-haus-automatisierung/tree/version-3) | Historischer, experimenteller Entwicklungsstand des Originalprojekts als Referenz |

**Aktueller DEV-Stand: 2.20.0-dev9 (noch nicht als stabile Version freigegeben).**

Bisherige Änderungen:
- Veralteten Link „Theme-Fehler melden“ aus der Oberfläche entfernt
- FHEMWEB-Aktionsmenü `#moreCmds` gestaltet (26 px Höhe, 10 px Abstand nach oben)
- SCSS-Quelle und generierte CSS-Datei aktualisiert
- Versionsanzeige auf `2.20.0-dev9` angehoben
- Inhaltsbereich nutzt die verfügbare Fensterbreite mit 20 px rechtem Rand; Eingabeleiste wird gleich breit (Test ausstehend)
- Weißer Hintergrund für horizontal scrollbare Device-Tabellen ergänzt (Test ausstehend)
- Eingabeleiste auf Inhaltsbreite begrenzt und Zeilenumbruch in Device-Tabellen ergänzt (Test ausstehend)
- Dropdown-Höhe ohne feste 26px an die benachbarten Aktionslinks angeglichen (Zoom-Test ausstehend)

**Geplant:** bessere Bedienbarkeit auf Smartphones (responsive Navigation, Layout und Geräteansichten). Diese Änderungen sind noch nicht umgesetzt.

## Installation und Updates in FHEM

Es darf **nur einer** der beiden Theme-Update-Kanäle gleichzeitig in FHEM eingetragen sein, weil beide dieselben Theme-Dateien aktualisieren.

Zunächst die eingerichteten Update-Quellen prüfen:

```text
update list
```

Falls noch der Update-Kanal des Originalprojekts eingetragen ist, diesen entfernen:

```text
update delete https://raw.githubusercontent.com/klein0r/fhem-style-haus-automatisierung/version-2/controls_ha_theme.txt
```

Falls bereits der jeweils andere Kanal dieser Weiterentwicklung eingetragen ist, diesen vor dem Wechsel ebenfalls mit `update delete <vollständige URL>` entfernen.

### Entwicklungsversion (dev)

```text
update add https://raw.githubusercontent.com/meier81/fhem-style-haus-automatisierung/dev/controls_ha_theme_dev.txt
update check ha_theme_dev
update all ha_theme_dev
```

Der erste `update check` kann beim Wechsel der Update-Quelle sämtliche Theme-Dateien als aktualisierbar anzeigen. Die Ausgabe vor dem Installieren prüfen.

Für den jeweils anderen Kanal siehe die README im [main-Branch](https://github.com/meier81/fhem-style-haus-automatisierung/tree/main).

### Theme aktivieren

In FHEM den Style `hausautomatisierung_com` auswählen und die Weboberfläche neu laden.

Optionale Einstellungen für ein FHEMWEB-Device namens `WEB` (nur übernehmen, wenn sie zur eigenen Konfiguration passen):

```text
attr WEB JavaScripts codemirror/fhem_codemirror.js
attr WEB codemirrorParam { "theme": "blackboard", "lineNumbers":true, "lineWrapping": true, "height": "auto", "autocomplete": true }
attr WEB roomIcons Save.config:message_attention
```

## Entwicklung

Die Styles sind in `sass/` organisiert; die von FHEM verwendeten CSS- und JavaScript-Dateien liegen unter `www/`. Änderungen an SCSS sollten mit den ausgelieferten CSS-Dateien synchron gehalten werden.

Repository für die lokale Entwicklung klonen:

```bash
git clone -b dev https://github.com/meier81/fhem-style-haus-automatisierung.git
```

Das vorhandene Skript `prepare_update.sh` erzeugt die FHEM-Control-Datei des jeweiligen Branches. Beim Erstellen neuer Releases müssen die Einträge (Dateigrößen und Zeitstempel) mit den tatsächlich ausgelieferten Dateien übereinstimmen.

## Fehler und Verbesserungsvorschläge

Bitte Issues zur **Weiterentwicklung** in [diesem Repository](https://github.com/meier81/fhem-style-haus-automatisierung/issues) melden. Das Originalprojekt von klein0r bleibt davon unabhängig.

## Vorschau

![FHEM Style](https://raw.githubusercontent.com/meier81/fhem-style-haus-automatisierung/dev/preview.png)

## Credits und Lizenz

Ursprünglich entwickelt von **Matthias Kleine (klein0r)**. Weiterentwicklung durch **meier81**.

Das Projekt steht unter der **MIT-Lizenz**. Der ursprüngliche Copyright-Hinweis und die Lizenzbedingungen bleiben unverändert; siehe [LICENSE](LICENSE).

Smart-Home-Icons: [Smart House Icon Set](https://dribbble.com/shots/2084609-Smart-House-Icon-Set-Free).
