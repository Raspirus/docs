# FAQ

Unten sind einige häufig gestellte Fragen zu Raspirus. Klicken Sie auf eine beliebige Frage, um die Antwort zu erweitern.

## Allgemein

??? question "Woher kommt das Raspirus-Logo? "\
Das Raspirus-Logo enthält ein rotes Monster namens **Stuart**, das eine virusfressende Kreatur darstellen soll. Das Logo wurde mit [DALL-E](https://openai.com/product/dall-e-2) generiert, mit zusätzlicher Bildbearbeitung und Zusammenführung.

```
Stuart ist ein freundliches Monster – außer wenn er hungrig nach Viren ist. Du kannst zusätzliche Medien und Assets im [dedizierten Repository](https://github.com/Raspirus/media). Du kannst diese Bilder für dein eigenes Kunstwerk verwenden und sie in den [Diskussionsforen](https://github.com/orgs/Raspirus/discussions).  
```

??? question "Kann ich Raspirus offline verwenden?"\
Ja! Raspirus funktioniert offline außer Updates. Die YARA-Regeldatenbank ist lokal gebaut und eine Internetverbindung wird nur benötigt, wenn Sie die neuesten Regeln aus unserem GitHub Repository abrufen.

## Installation & Kompatibilität

??? question "Was sind die Mindestanforderungen an das System?"\
Raspirus ist leichtgewichtig und arbeitet auf den meisten Systemen, einschließlich Low-Power-Geräten wie dem Raspberry Pi 3B+. Für die beste Erfahrung empfehlen wir jedoch,

```
- **RAM:** ~1 GB  
- **Speicher:** ~200 MB  
- **CPU:** Dual-Core-Prozessor (höhere Leistung bei schnelleren Scans)  
- **Anzeige:** Benötigt für die GUI (keine strikte Mindestgröße. aber kleinere Bildschirme können die Benutzbarkeit beeinträchtigen)  
```

??? question "Problem bei der Installation von Raspirus auf Linux"\
\*\*Installieren oder führen Sie keine Aktionen als `sudo` Benutzer aus. \* Führen Sie immer Befehle als Hauptbenutzer aus und verwenden Sie `sudo` nur, wenn es nötig ist.

```
Der Wechsel zum `sudo`-Benutzer und die Durchführung der Installation wird das Setup **zerbrechen**.  
```

??? question "Warum kann ich Verzeichnisse oder Dateien nicht auswählen?"\
Um die Art des Assets zu ändern, klicken Sie auf das **orangefarbene Icon** neben dem Auswahlmenü. Sie können wählen unter:

```
- **USB-Laufwerke**  
- **Ordner**  
- **Einzelne Dateien**  
```

??? question "Welche Betriebssysteme und Architekturen werden unterstützt?"\
Raspirus unterstützt mehrere Betriebssysteme und CPU-Architekturen:

```
- **Windows:** Windows 10 & 11 (x86_64)  
- **Linux:** Debian-basierte Distributionen (Debian, Ubuntu, PopOS, Mint, etc.). (x86_64, ARM64)  
- **macOS:** Intel & Apple Silicon (x86_64, aarch64)  

Zusätzlich Raspirus wird **inoffiziell unterstützt** am:  

- OpenSUSE (x86_64, ARM64)  
- Arch-basierte Linux-Distributionen (x86_64, ARM64)  

**Experimental support:** RISC-V 64 unter Linux.  
```

## Anpassung

??? question "Wie füge ich meine eigenen YARA-Regeln hinzu?"\
Raspirus holt Regeln aus dem [yara-rules repository](https://github.com/Raspirus/yara-rules) und baut die Datenbank lokal.

```
Wenn du neue Regeln beitragen möchtest:  
- Öffne ein **Issue** oder reiche eine **Pull-Request (PR)** im [yara-rules repository](https://github.com/Raspirus/yara-rules).  

Wenn Sie lieber Ihre eigenen Regeln verwenden möchten:  
- Ändern Sie die Konfigurationsdatei, um stattdessen Regeln aus Ihrem eigenen Repository zu holen.  
```

---

## Bekannte Probleme

??? warning: "Remote-Installationsfehler: App erkennt keinen Bildschirm"\
Wenn Sie Raspirus über Remote-Zugriff installieren du einen Fehler siehst, der andeutet, dass die App **keinen Bildschirm erkennt**.

```
Dies geschieht, weil das System keinen Bildschirm registriert, wenn die App aus dem CLI ausgeführt wird, selbst wenn einer physisch verbunden ist.  
```

??? warning "Abhängigkeitsprobleme bei der Installation von Raspirus"\
Wenn Abhängigkeitsprobleme auftreten:* Versuchen Sie die **AppImage** Version.
* Wenn Probleme weiterhin auftreten, überlegen Sie **herunterstufen oder upgraden Sie Ihr OS**.

```
Melde diese Probleme immer auf [Discord](https://discord.gg/raspirus) oder [GitHub](https://github.com/Raspirus/raspirus/issues), damit wir weiter untersuchen können.  
```

---

## Wichtige GitHub Probleme zu prüfen

Bevor Sie ein Problem melden, überprüfen Sie bitte die folgenden häufig referenzierten Probleme:

??? note "Commonly Reported Issues"* **[#852 - No armv7 (32-bit) support](https://github.com/Raspirus/raspirus/issues/852)**
* **[#891 - Fehlende Fonts](https://github.com/Raspirus/raspirus/issues/891)**
* **[#902 - "Failed to open yar file" error](https://github.com/Raspirus/raspirus/issues/902)**
* **[#937 - ARM64 deb installiert nicht auf RaspiOS (Debian 12 Bookworm)](https://github.com/Raspirus/raspirus/issues/937)**

Dies ist keine vollständige Liste – nur eine Auswahl häufig gemeldeter Probleme. Wenn dir ein Fehler aufgetreten ist, überprüfe zuerst die [GitHub Probleme](https://github.com/Raspirus/raspirus/issues), um festzustellen, ob eine Lösung bereits existiert, bevor du Unterstützung anforderst.

## Fehlerbehebung

Wir helfen Ihnen gerne wenn möglich, aber unsere Zeit ist begrenzt. Wenn du eine Lösung für ein Problem findest, überlege es zu teilen:

- Wenn ein **existierendes Problem** dein Problem behebt, füge einen Kommentar mit deiner Behebung hinzu.
- Wenn Sie ein **neues Problem** und eine Problemumgehung entdecken, öffnen Sie ein Problem und dokumentieren Sie die Lösung für andere.

Ihre Beiträge helfen Ihnen, Raspirus für alle zu verbessern! 🚀
