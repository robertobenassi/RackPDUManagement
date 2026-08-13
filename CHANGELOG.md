# Changelog

Tutte le modifiche rilevanti del progetto sono documentate in questo file.

## [1.0.0] - 2026-08-13

Prima release pubblica.

### Verifica di progetto
- Verifica automatica e permanente della ridondanza N+1 su tutti gli scenari di
  guasto (normale, perdita via A, perdita via B), applicata a generale, fasi e
  interruttori. Ogni barra di carico mostra il valore attuale e il valore di caso
  peggiore. Verdetto per rack e riepilogo globale di impianto.
- Modellazione opzionale dell'alimentazione a monte: sorgenti con taglia unitaria,
  cosφ di uscita, unità in parallelo, ridondanza N+1 e autonomia batteria. Ogni PDU
  dichiara da quale sorgente è alimentata, da cui derivano le topologie reali
  (UPS singolo su entrambe le vie, 2N, parallelo, UPS nel rack). Segnalazione
  esplicita quando le due vie risalgono alla stessa sorgente.
  Disattivata di default: a modello spento nulla di ciò che sta sopra le PDU entra
  nei calcoli.
- Verifica di capacità delle sorgenti in kW e kVA separatamente, con autonomia
  stimata anche in condizioni di guasto.
- Conteggio delle prese C13/C19 per lato e tipo spina per apparato (C14/C20), con
  segnalazione delle prese insufficienti.

### Motore di calcolo
- Tensione fase-neutro configurabile e fattore di potenza reale.
- cosφ e fattore di contemporaneità a tre livelli: apparato, rack, progetto.
- Potenza attiva e apparente distinte (kW e kVA).
- Calcolo della corrente di neutro con squilibrio vettoriale e contributo della
  terza armonica, con contenuto armonico configurabile.
- Soglie di attenzione e allarme configurabili.
- Potenza termica (BTU/h), portata d'aria richiesta e peso stimato per rack.

### Interfaccia
- Gestione multi-rack (12U, 24U, 42U, 45U, 48U) con riepilogo globale di impianto.
- Libreria di profili PDU predefiniti, con tutti i campi editabili.
- Ottimizzatore del bilanciamento con bin-packing a due livelli (fase e
  interruttore) calcolato sul caso peggiore, su uno o entrambi i lati.
- Trascinamento degli apparati nel rack, con evidenziazione del bersaglio valido o
  non valido e scambio di posizione tra apparati di pari altezza.
- Pannello parametri in gruppi tematici, con una riga di spiegazione per ogni
  campo, anteprima dell'effetto sui calcoli e ripristino dei valori predefiniti.
- Interfaccia italiano/inglese, con lingua iniziale dedotta dal browser,
  annulla/ripeti, ricerca e filtri sugli apparati.
- Salvataggio su file JSON, esportazione CSV, stampa del singolo rack o di tutti,
  salvataggio automatico locale.
