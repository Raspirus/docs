# Scannen

Das Scannen von Dateien nach Malware kann durch verschiedene Methoden wie Yara Rules oder Sandboxen erfolgen. Antivirus-Anwendungen durchsuchen häufig den gesamten Prozessbaum einer ausführbaren Datei, um Malware zu identifizieren. Raspirus ist jedoch anders gestaltet. Es ist ein leichtes, on-demand Datei-Scanner optimiert für Low-End-Geräte wie den Raspberry Pi.

Raspirus nutzt nun die Kraft der 'yara-x' Kiste und Yara Regeln für die Erkennung von Malware. Anstatt sich auf Dateisignaturen zu verlassen, verwendet Raspirus einen flexiblen und leistungsstarken regelbasierten Ansatz, um Dateien nach Mustern und Eigenschaften zu scannen, die mit bekannten Malware-Verhaltensweisen übereinstimmen. Yara Regeln werden in einem dedizierten Repository [here]gespeichert (https://github.com/Raspirus/yara-rules), und diese Regeln werden regelmäßig aktualisiert, um eine umfassendere und genauere Malware-Erkennung zu gewährleisten.

Es gibt keine Einschränkungen hinsichtlich Art oder Größe von Dateien, die Sie mit Raspirus scannen können.

## Nachteile

Während der Übergang zu den Yara-Regeln die Erkennungsmöglichkeiten verbessert, gibt es immer noch einige Einschränkungen:

1. **Regelkomplexe**: Das Schreiben und die Aufrechterhaltung von Yara-Regeln können komplex sein. Obwohl die Regeln mehr Flexibilität bieten als einfache Hash-Anpassung, erfordern sie ständige Aktualisierungen, um neue und sich entwickelnde Malware abzudecken.

2. **False Positives**: Aufgrund der musterbasierten Natur der Yara-Regeln kann es immer noch Fälle geben, in denen legitime Dateien als Malware gekennzeichnet werden. Allerdings sind die Regeln so konzipiert, dass diese Vorkommnisse im Vergleich zu einem rein unterschriftenbasierten Ansatz minimiert werden.

## Vorteile

Raspirus, angetrieben von Yara, bietet mehrere unterschiedliche Vorteile:

1. **Verbesserte Erkennung**: Yara-Regeln ermöglichen es Raspirus, Malware genauer zu erkennen, auch wenn die Malware leicht verändert wurde oder keinen passenden Hash in einer Datenbank hat. Dies ermöglicht eine robustere Verteidigung gegen verschiedene Malware-Typen.

2. **Effizienz**: Obwohl die Yara Regeln ressourcenintensiver sind als die Signatur-Übereinstimmung, Raspirus bleibt für Geräte mit geringem Ressourcenverbrauch wie Raspberry Pi optimiert und bietet schnelle und effiziente Scans ohne überwältigende Systemressourcen.

3. **Offline-Fähigkeit**: Sobald die Yara-Regeldatenbank heruntergeladen und aktualisiert wurde, funktioniert Raspirus weiterhin offline und behält den Komfort des Offline-Scannens bei.

Raspirus verwendet aufgrund seiner Einschränkungen bei der Erkennung modifizierter oder neuer Malware nicht mehr das reine Signaturpassen. Stattdessen bietet es eine umfassendere Scannerlösung bei gleichzeitig leichtem Gewicht. Wie jedes Sicherheitswerkzeug ist es jedoch nicht dazu gedacht, eine vollständige Antivirenanwendung zu ersetzen. Benutzer sollten vorsichtig sein, wenn sie interne Systemdateien scannen, um falsche Positive zu minimieren.

Raspirus entwickelt sich ständig weiter, und wir arbeiten aktiv daran, seine Scangenauigkeit zu verbessern und seine Yara Regeldatenbank zu erweitern.
