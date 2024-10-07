# Differenze tra SHAP e LIME

LIME (Local Interpretable Model-agnostic Explanations) e SHAP (SHapley Additive exPlanations) sono entrambi metodi per spiegare le predizioni di modelli di machine learning, ma hanno differenze significative:

## Base Teorica:

### LIME: 
Si basa su approssimazioni lineari locali. LIME genera spiegazioni lineari su una regione specifica del modello vicino all'input da spiegare. Modifica leggermente l'input e costruisce un modello interpretabile (ad es. una regressione lineare) che approssima il comportamento del modello complesso solo in quella regione.

### SHAP: 
Si basa sui valori di Shapley dalla teoria dei giochi, che garantiscono una distribuzione equa dei contributi delle caratteristiche di input alla predizione. SHAP è teoricamente giustificato per fornire una spiegazione consistente e basata su contributi globali e locali.

## Output Interpretability:

### LIME: 
Fornisce spiegazioni locali, ma poiché è una approssimazione locale, non garantisce che il modello interpretabile rifletta correttamente il comportamento globale del modello.

### SHAP: 
Fornisce spiegazioni locali che sono consistenti e additive, con garanzie matematiche che i contributi di tutte le caratteristiche sommate corrispondono alla predizione del modello.

## Calcolo dei contributi:

### LIME: 
Esegue una selezione casuale delle caratteristiche da modificare per costruire l'approssimazione lineare.

### SHAP: 
Calcola tutti i possibili contributi combinati delle caratteristiche, il che può essere più computazionalmente intenso, ma più accurato.

## Velocità:

### LIME: 
È generalmente più veloce perché costruisce un modello semplice per approssimare il comportamento locale.

### SHAP: 
Può essere più lento, specialmente con modelli complessi, perché calcola i contributi di tutte le possibili combinazioni di feature.


In sintesi, LIME è più veloce e meno preciso, mentre SHAP è più accurato ma richiede maggiori risorse computazionali.
