# Gestione Rack con PDU

**Italiano** · [English](README.en.md)

Strumento a file singolo per la progettazione e la **verifica elettrica** dei rack di
sala dati: distribuzione del carico sulle PDU, bilanciamento delle fasi, verifica
della ridondanza N+1 e dimensionamento delle sorgenti a monte.

Nessuna installazione, nessun server, nessuna dipendenza esterna: si apre facendo
doppio clic sul file `index.html`. Tutti i dati restano sul computer di chi lo usa.

## A cosa serve

La domanda a cui risponde non è "quanto assorbe questo rack", ma **"cosa succede
quando cade una via di alimentazione"**. È il caso che conta in fase di progetto e
quello che sfugge guardando solo il funzionamento normale: due PDU al 45% sembrano
tranquille, ma in caso di guasto una delle due va al 90%.

## Funzionalità principali

### Verifica di progetto
- **Ridondanza N+1**: gli scenari di guasto (normale, perdita via A, perdita via B)
  sono ricalcolati a ogni modifica su generale, fasi e interruttori. Ogni barra di
  carico mostra il valore attuale e, con un marcatore, quello di caso peggiore.
- **Alimentazione a monte** (opzionale): ogni PDU può dichiarare da quale sorgente è
  alimentata. Da qui derivano le topologie reali — un solo UPS su entrambe le vie,
  due UPS indipendenti 2N, parallelo N+1, UPS installato dentro il rack. Se le due
  vie risalgono alla stessa sorgente il sistema segnala che la ridondanza è solo a
  valle. La sezione è **disattivata di default**: chi ha già svolto la verifica a
  monte con altri strumenti non trova ipotesi imposte.
- **Prese**: conteggio C13/C19 per lato con tipo spina per apparato, perché si può
  avere corrente disponibile e nessuna presa libera.

### Motore di calcolo
- Tensione fase-neutro e fattore di potenza configurabili; potenza attiva e
  apparente distinte (kW e kVA).
- **cosφ e contemporaneità a tre livelli**: apparato, rack, progetto. Un rack di
  storage può avere un cosφ diverso da uno di server.
- **Corrente di neutro**: squilibrio vettoriale delle tre fasi più contributo della
  terza armonica, che sugli alimentatori switching carica il neutro anche a fasi
  perfettamente bilanciate.
- Soglie di attenzione e allarme configurabili.
- Potenza termica (BTU/h), portata d'aria richiesta e peso stimato.

### Uso quotidiano
- Multi-rack con riepilogo globale di impianto.
- Libreria di profili PDU, tutti i campi restano editabili.
- Ottimizzatore del bilanciamento con bin-packing su fase **e** interruttore,
  calcolato sul caso peggiore.
- Trascinamento degli apparati nel rack, con scambio di posizione tra apparati di
  pari altezza.
- Interfaccia italiano/inglese: la lingua iniziale segue quella del browser ed è
  commutabile in ogni momento. Annulla/ripeti, ricerca e filtri.
- Salvataggio su file JSON, esportazione CSV, stampa del singolo rack o di tutti.

## Uso online

L'applicazione è utilizzabile direttamente dal browser, senza scaricare nulla:

**https://robertobenassi.github.io/RackPDUManagement/**

## Uso offline

1. Scarica `index.html`
2. Aprilo con un browser recente (Firefox, Chrome, Edge, Safari)
3. Aggiungi gli apparati e configura le PDU

I dati non vengono trasmessi da nessuna parte. Il salvataggio automatico usa
l'archivio locale del browser; per conservare o condividere un progetto usa
**Scarica configurazione**, che produce un file JSON.

I file di configurazione salvati con versioni precedenti dello strumento si
aprono senza modifiche.

## Avvertenza

Lo strumento è un ausilio alla progettazione e non sostituisce la verifica di un
professionista abilitato né il rispetto delle norme applicabili (CEI 64-8,
IEC 60364 e successive). L'autonomia delle batterie è una **stima** basata su una
legge esponenziale con esponente configurabile: va sempre confrontata con le curve
di scarica del costruttore prima di essere riportata in un documento di progetto.
Verifica sempre i risultati contro i dati di targa degli apparati installati.

## Licenza

Doppia licenza:

- **Uso non commerciale**: [GPL-3.0](LICENSE), gratuito e open source.
- **Uso commerciale**: richiede una licenza commerciale. Per informazioni,
  contattare l'autore.

## Autore

Roberto Benassi — [robertobenassi.com](https://www.robertobenassi.com)
