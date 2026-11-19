# GTK 3 – Dialoge, Menüs, PCManFM

GTK 3 zeichnet PCManFM, Dateidialoge („Öffnen/Speichern"), Firefox-Menüs und viele ältere Programme.
Dieses Paket sorgt dafür, dass sie dunkel und in den Farben des Desktops erscheinen.

## So greifen die Dateien ineinander

GTK liest beim Start einer Anwendung zwei Dateien:

- `settings.ini` – **Verhalten**: dunkles Thema bevorzugen, Symbolsatz, Schrift, Cursor, Animationen.
- `gtk.css` – **Aussehen**: überschreibt Farben und Rahmen des Themas mit der Catppuccin-Mocha-Palette.

Das Thema bleibt `Adwaita-dark`; `gtk.css` färbt es um. Dadurch bleiben Layout und Bedienelemente
vertraut, nur die Farben passen zum Rest des Desktops.

| Einstellung (`settings.ini`) | Wert | Wirkung |
| --- | --- | --- |
| `gtk-application-prefer-dark-theme` | `1` | Dunkle Variante bevorzugen |
| `gtk-theme-name` | `Adwaita-dark` | Grundthema |
| `gtk-icon-theme-name` | `Adwaita` | Symbole (`adwaita-icon-theme`) |
| `gtk-font-name` | JetBrainsMonoNL Nerd Font 10 | Schrift aller Dialoge und Menüs |
| `gtk-cursor-theme-name` / `-size` | Adwaita / 20 | Passt zu `XCURSOR_SIZE` in Hyprland |
| `gtk-enable-animations` | `0` | Keine Animationen – wirkt schneller |

## Was `gtk.css` umfasst

Die Datei färbt die benannten Themenfarben (`theme_bg_color`, `theme_selected_bg_color`, `borders`, `warning_color` …)
und überschreibt danach gezielt Widgets: Fenster, Kopfleisten, Eingabefelder (Fokus = Akzentrahmen),
Buttons (Hover = Akzent), Reiter, Listen, Seitenleisten, Menüs, Statusleiste und Scrollbalken.
Alle Ecken sind eckig (`border-radius: 0`), damit GTK-Fenster zu Waybar und Terminal passen.

## Eigene Anpassungen

Ein Akzent in anderer Farbe, zum Beispiel Grün statt Blau:

```css
/* ~/.config/gtk-3.0/gtk.css – ersetze #89b4fa durch #a6e3a1 */
@define-color theme_selected_bg_color #a6e3a1;
```

Test ohne Neustart der ganzen Sitzung: das betroffene Programm neu starten. Fehler im CSS meldet GTK im Terminal,
wenn du das Programm von dort startest (`GTK_DEBUG=interactive pcmanfm` öffnet den GTK-Inspector).

## Fehlersuche

- **Programm bleibt hell:** Es nutzt eine eigene Themenlogik (z. B. Electron). Prüfe `gsettings get org.gnome.desktop.interface color-scheme`.
- **Falsche Symbole:** `adwaita-icon-theme` installieren; das Paket hängt davon ab.
- **GTK-4-Programme:** siehe [GTK 4](https://aco-gtk4.readthedocs.io/en/latest/).

## Farbpalette (Catppuccin Mocha)

Alle Komponenten nutzen dieselben Farben, damit Terminal, Launcher, Dateimanager und Dialoge zusammenpassen:

| Rolle | Farbe | Verwendung |
| --- | --- | --- |
| Hintergrund | `#1e1e2e` | Fenster, Terminal |
| Tiefer Hintergrund | `#181825` | Leisten, Listen, Seitenleisten |
| Fläche | `#313244` | Eingabefelder, Buttons, Auswahl |
| Text | `#cdd6f4` | Schrift |
| Akzent | `#89b4fa` | Fokus, Rahmen, Auswahl |
| Treffer | `#94e2d5` | Suchtreffer |

## Anpassen und zurücksetzen

`~/.config/gtk-3.0` ist ein Link auf deine bearbeitbare Kopie unter
`~/.local/share/arch-dotfiles/config/gtk-3.0/`. Dort kannst du alles ändern; `pacman -Syu` überschreibt
deine Änderungen **nicht**. Bringt ein Update neue Vorgaben mit, landen sie als `.pacnew`-Datei neben deiner
Version, und du übernimmst, was du willst (`aco sync` führt zusammen, `aco status` zeigt den Zustand).
Zurück zu den Vorgaben: `aco deactivate gtk-3.0` stellt die früheren Einstellungen wieder her,
`aco install gtk-3.0` aktiviert die Paketvorgaben erneut.
