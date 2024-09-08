### Relazione del progetto di tesi

**Data**: [08/09/2024]  


#### Introduzione
Il progetto di tesi è iniziato con l’obiettivo di creare un classificatore basato su una rete neurale convoluzionale (CNN) per identificare la presenza o meno di sintomi da COVID-19 in immagini di lastre al torace. L'idea iniziale è stata ispirata da un progetto precedente svolto per il corso di Sistemi Intelligenti Avanzati, ma adattato a un contesto di immagini mediche.

#### Ricerca del dataset
Il primo passo è stato la ricerca di un dataset idoneo. Ho trovato un archivio di circa 30 GB di immagini di lastre al torace, già etichettate come COVID-positive o negative. Tuttavia, per semplificare il processo iniziale di addestramento, ho deciso di lavorare solo con una porzione ridotta del dataset, limitandomi a circa 3 GB di immagini. L'idea è di aggiungere progressivamente nuove immagini, per migliorare l’addestramento del modello e analizzare eventuali differenze nelle prestazioni.

#### Struttura della rete e approccio
Dopo aver analizzato la complessità del dataset, mi sono reso conto che la struttura delle immagini, a differenza di altri dataset di esempio come quello dei muffin e dei Chihuahua, richiedeva un'attenzione particolare ai dettagli. Le lastre al torace forniscono informazioni visive più complesse e sottili, richiedendo un'architettura di rete neurale più avanzata. Per questo motivo, ho deciso di adottare un modello standard con più strati convoluzionali, con l'obiettivo di migliorare l'estrazione delle caratteristiche delle immagini.

Dopo aver consultato la letteratura e confrontato diversi approcci, ho implementato una CNN con 4 strati convoluzionali, aumentando progressivamente il numero di filtri e includendo livelli di pooling e dropout per ridurre l’overfitting.

#### Preprocessing delle immagini
Uno degli aspetti più impegnativi è stato il preprocessing delle immagini. Il dataset non era perfettamente strutturato e le immagini richiedevano una preparazione adeguata. Ho dovuto sviluppare una funzione ad hoc che assegnasse correttamente le etichette (`label`) alle immagini, separando correttamente quelle positive da quelle negative. Durante questa fase, ho dovuto anche ridimensionare le immagini per adattarle all'input del modello.

#### Problemi riscontrati durante il training
Una delle difficoltà principali incontrate è stata la durata del processo di training. A causa della complessità del modello e del volume del dataset, il tempo richiesto per completare 50 epoche di addestramento risultava eccessivo. Con i 4 strati convoluzionali, il training richiedeva troppo tempo, e non sono mai riuscito a completare un intero ciclo di addestramento senza che la sessione venisse interrotta.

Per affrontare questo problema, ho deciso di implementare delle **callback** di Keras, in particolare il **ModelCheckpoint**, per salvare i progressi dell’addestramento a runtime. Questo mi permette di interrompere e riprendere l'addestramento in diverse sessioni, senza perdere i dati accumulati fino a quel momento.

#### Implementazione di funzioni per la gestione del training
Ho sviluppato diverse funzioni, tra cui:
- **train_model**: per avviare il processo di training.
- **load_model**: per caricare un modello precedentemente addestrato dai checkpoint.
- **continue_training**: per riprendere l'addestramento dal punto in cui era stato interrotto.

Queste funzioni mi facilitano nel gestire il processo di training in modo più efficiente, permettendomi di separare le fasi di addestramento in sessioni differenti. Inoltre, ho aggiunto delle callback personalizzate per salvare in tempo reale i valori di **accuracy** e **loss** sia per il training che per la validation, epoca per epoca, in un file CSV. Questo mi consente di monitorare costantemente l'andamento del training e di analizzare i dati anche in seguito, per generare grafici e valutare il miglioramento del modello.

#### Prossimi passi
Ora sono concentrato sulla stabilizzazione di queste funzioni e sull'ottimizzazione del processo di salvataggio dei dati durante il training. Una volta completato il modello, inizierò la fase di analisi degli errori, valutando le performance ottenute e cercando di migliorare ulteriormente la rete.

L'obiettivo finale è ottenere un modello CNN performante, che possa essere analizzato in dettaglio per capire le aree di miglioramento e le eventuali criticità nella classificazione delle immagini mediche.

#### Conclusioni
Il lavoro svolto finora ha permesso di stabilire una solida base per l'addestramento del modello, nonostante le difficoltà incontrate con il tempo di training e la gestione delle sessioni su Google Colab. Con l'implementazione delle callback per i checkpoint e la registrazione dei dati, posso ora monitorare e riprendere il training in modo più efficiente, concentrandomi sull'ottimizzazione del modello e sulla sua analisi futura.


