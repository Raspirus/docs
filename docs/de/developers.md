# Entwickler

Willkommen beim Raspirus Entwickler Guide! Auf dieser Seite finden Sie alles, was Sie brauchen, um effektiv zu helfen, von der Einrichtung Ihrer Umgebung bis zum Verständnis der Architektur und der Aktualisierung der YARA-Regeln.

---

## Setup

Um mit der Entwicklung zu beginnen, folgen Sie diesen Schritten:

1. Repository klonen:
   ```sh
   git clone https://github.com/Raspirus/raspirus.git
   cd raspirus
   ```
2. [Rust]installieren (https://www.rust-lang.org/tools/install).
3. Installieren Sie das Raspirus-Paket:
   ```sh
   Ladungsinstallation .
   ```
4. Entwicklung beginnen:
   ```sh
   Güterlauf
   ```
5. Oder bauen Sie Raspirus:
   ```sh
   Güterbau
   ```

### Probleme bei der Fehlerbehebung

Wenn du Probleme beim Bau oder Betrieb von Raspirus findest:

- Stellen Sie sicher, dass Rust korrekt installiert ist.
- Überprüfen Sie, dass Logs und Konfigurationsdateien korrekt erstellt werden.
- Prüfen Sie auf Abhängigkeitskonflikte und fehlende Pakete.

---

## Dokumentation

Da Raspirus in Rust geschrieben ist, kannst du Entwicklerdokumentation generieren mit:

```sh
frachtsdoc --no-deps --open
```

Dies öffnet die generierte Dokumentation in Ihrem Browser.

---

## Architektur

Raspirus folgt einer **frontend-backend** Architektur, wobei beide Komponenten in Rust geschrieben sind.

### Frontend

- Verwendet **eised-rs** für GUI-Rendering.
- Priorität für die Benutzererfahrung – idealerweise sollten Benutzer niemals die Einstellungsseite öffnen müssen.
- Entworfen für **Touch-Support** und minimiert die Eingabe der Tastatur.
- Plug-and-play: Kann bei Bedarf durch ein anderes Frontend ersetzt werden.
- Einfache Struktur, ähnlich einer Website mit nur wenigen Seiten.

### Backend

- **Multi-Threadd** für effizientes Scannen.
- Behandelt Scannen, Regelverarbeitung und Einstellungsverwaltung.
- Implementiert **YARA-Regeln** zur Malware-Erkennung.
- Gut dokumentierte Funktionen – im Zweifel überprüfen Sie den Code direkt.
- Trotz seiner Komplexität wird es einfacher, zu navigieren, sobald man mit ihm beginnt.

---

## Konfiguration

Die Konfigurationsdatei ist im Standardordner für Systemkonfigurationen gespeichert:

```json
{
  "config_version": "6",
  "rules_version": "v1.1. ",
  "min_matches": 0,
  "max_matches": 20,
  "max_threads": 12,
  "logging_is_active": true
  "mirror": "https://api. ithub.com/repos/Raspirus/yara-rules/releases/latest",
  "language": "en",
  "dark_mode": true
}
```

### Schlüsselfelder

- `config_version`: Legt fest, ob eine ältere Konfiguration überschrieben werden muss.
- `rules_version`: Trackt die zuletzt heruntergeladene YARA-Regelversion.
- `min_matches`: Mindestanzahl an Regeln, die erforderlich sind, um eine Datei kennzeichnen zu können.
- `max_matches`: Maximale Übereinstimmung mit Regeln, bevor weitere Prüfungen angehalten werden.
- `max_threads`: Anzahl der CPU-Threads, die zum Scannen verwendet werden.
- `logging_is_active`: Aktiviert /deaktiviert Protokollierung (nützlich, wenn der Speicher begrenzt ist).
- `mirror`: API Endpunkt für das Abrufen von Regelaktualisierungen.
- `language`: Aktuelle Sprache (unterstützt `fr`, `en`, `it`, `de`).
- `dark_mode`: Schaltet den dunklen Modus der Anwendung um.

---

## Spiegel

Die Einstellung `mirror` in der Konfigurationsdatei sollte auf eine Git-API verweisen. Benutzerdefinierte Spiegel müssen JSON mit der folgenden Struktur versorgen:

```json
{
  "tag_name": "v1.1",
  "zipball_url": "http://example.com/download.zip"
}
```

- `tag_name`: Gibt die Version für Update-Prüfungen an.
- `zipball_url`: Direkter Link auf das `.zip` Archiv mit YARA Regeln.

---

## Updater

Raspirus hat einen **Built-from-scratch Updater** dass:

1. Prüft die neueste verfügbare Version mit dem konfigurierten Spiegel.
2. Lädt das `.zip` Archiv in den Cache.
3. Kompiliert alle `.yar`-Dateien in ein `.yarac` (kompilierte YARA-Regeln).
4. Speichert die kompilierten Regeln in:
   - **Linux/macOS**: `~/.local/share/raspirus`
   - **Windows**: `%appdata%\Roaming\Raspirus\Data`
   - **macOS (App Bundle)**: `/Applications/Raspirus/data`

### Archivstruktur freigeben

Die Aktualisierung `.zip` sollte **nicht kompilierte YARA `.yar` Dateien enthalten**. Die Ordnerstruktur innerhalb des Archivs spielt keine Rolle, da Dateien rekursiv hinzugefügt werden.

📌 **Windows Users:** Wenn Windows Defender die kompilierten YARA-Regeln durchführt, kann ein optionales Skript die Defender-Scan deaktivieren. Siehe [dieses Skript](https://github.com/Raspirus/yara-rules/blob/main/scripts/windows.ps1).
