# Scansione

La scansione di file per malware può essere ottenuta attraverso vari metodi, come le regole Yara o sandboxing. Le applicazioni antivirus spesso scansionano l'intero albero di processo di un eseguibile per identificare il malware. Tuttavia, Raspirus è progettato in modo diverso. Si tratta di uno scanner di file leggero e on-demand ottimizzato per dispositivi di fascia bassa come il Raspberry Pi.

Raspirus ora sfrutta il potere della cassa `yara-x` e le regole Yara per il suo rilevamento di malware. Invece di affidarsi alle firme dei file, Raspirus utilizza un approccio flessibile e potente basato su regole, scansionando file per modelli e caratteristiche che corrispondono a comportamenti di malware conosciuti. Le regole di Yara sono memorizzate in un repository dedicato [here](https://github.com/Raspirus/yara-rules), e queste regole vengono regolarmente aggiornate per garantire il rilevamento di malware più ampio e preciso.

Non ci sono restrizioni sul tipo o la dimensione dei file che è possibile eseguire la scansione con Raspirus.

## Svantaggi

Mentre il passaggio alle regole di Yara migliora le capacità di rilevamento, ci sono ancora alcune limitazioni:

1. **Complessità delle regole**: Scrivere e mantenere le regole di Yara può essere complesso. Sebbene le regole offrano una maggiore flessibilità rispetto al semplice hash matching, esse richiedono un aggiornamento costante per coprire il malware nuovo e in continua evoluzione.

2. **Falsi Positivi**: A causa della natura basata su modelli delle regole di Yara, ci possono ancora essere casi in cui i file legittimi vengono contrassegnati come malware. Tuttavia, le regole sono progettate per ridurre al minimo queste occorrenze rispetto ad un approccio puramente basato sulla firma.

## Vantaggi

Raspirus, alimentato da Yara, offre diversi vantaggi distinti:

1. **Rilevamento Migliorato**: le regole Yara consentono a Raspirus di rilevare il malware in modo più accurato, anche se il malware è stato modificato leggermente o non ha un hash corrispondente in un database. Ciò consente una difesa più robusta contro vari tipi di malware.

2. **Efficienza**: Sebbene le regole di Yara siano più impegnative in termini di risorse rispetto all'abbinamento delle firme, Raspirus rimane ottimizzato per dispositivi a bassa risorsa come Raspberry Pi, fornendo scansioni veloci ed efficienti senza travolgere le risorse del sistema.

3. **Offline Capability**: Una volta scaricato e aggiornato il database delle regole di Yara, Raspirus continua a funzionare offline, mantenendo la comodità della scansione offline.

Raspirus non utilizza più la firma pura corrispondente a causa delle sue limitazioni nel rilevamento di malware modificati o nuovi. Al contrario, fornisce una soluzione di scansione più completa pur rimanendo leggero. Tuttavia, come qualsiasi strumento di sicurezza, non è destinato a sostituire un'applicazione antivirus a tutti gli effetti. Gli utenti dovrebbero essere cauti durante la scansione dei file di sistema interni per ridurre al minimo i falsi positivi.

Raspirus è in continua evoluzione e stiamo lavorando attivamente per migliorare la sua precisione di scansione ed espandere il database delle regole Yara.
