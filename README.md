[README.txt](https://github.com/user-attachments/files/23581402/README.txt)
READ ME – Sistema di Tracking Video con Marker Colorato

Descrizione generale
Questo programma esegue il tracciamento di un marker colorato presente in un video, permette di correggere manualmente il tracking tramite una gomma interattiva e calcola l’angolo del movimento rispetto a un punto fisso selezionato dall’utente. Al termine genera un video annotato e un file con gli angoli e l’escursione percentuale nel tempo.

Funzionalità principali

Rilevamento del marker tramite colore in HSV.

Selezione manuale del marker nel primo frame.

Selezione di un punto fisso sul corpo.

Scelta del frame considerato “0°”.

Tracking del marker con predizione della posizione.

Modalità gomma per correggere i frame problematici.

Navigazione frame-by-frame con tasti rapidi.

Generazione del video finale annotato.

Salvataggio tabella angoli/escursione in Excel o CSV.

Requisiti
Python 3
Librerie richieste: opencv-python, numpy, pandas, pathlib

Input richiesto
Il video da analizzare, impostato nella variabile:
video_path = Path("video.mp4")

Procedura operativa

5.1 Selezione marker e punto fisso

Viene mostrato il primo frame del video.

Cliccare prima sul marker colorato individuato dal programma.

Cliccare poi sul punto fisso.

Premere “s” quando entrambi sono selezionati.

5.2 Selezione del frame a 0°
Nella finestra “ZeroSel”:

Frecce sinistra/destra: muove di 1 frame.

A / D: muove di 5 frame.

W / S: muove di 30 frame.

Z: imposta il frame corrente come zero.

ENTER o S: conferma e passa al tracking.

5.3 Tracking e correzioni
Nella finestra “Tracking”:

Barra spaziatrice: pausa/continua.

E: attiva/disattiva la gomma per cancellare aree con disturbi.

Con il mouse si disegna sulla maschera di esclusione.

ENTER: conferma la correzione e passa al frame successivo.

Frecce o A/D in pausa: navigazione manuale dei frame.

F: termina il tracking ed esporta i risultati.

Q o ESC: esce dal programma.

La gomma viene memorizzata frame per frame e permette di migliorare il rilevamento del marker.

Output generati

6.1 Video annotato
Viene salvato un video con:

Posizione del marker

Punto fisso

Angolo calcolato

Escursione percentuale

Il nome prodotto è:
<nomevideo>_tracked.mp4
(oppure .avi se necessario).

6.2 Tabella con angoli ed escursione
Viene salvato un file Excel:
video.xlsx
Se Excel non può essere scritto, viene creato automaticamente un CSV.

La tabella contiene:

Tempo (s)

Angolo (gradi)

Escursione percentuale del movimento.

Dettagli sul calcolo dell’angolo
L’angolo è calcolato confrontando:

Il vettore iniziale (frame dichiarato come 0°)

Il vettore corrente dal punto fisso al marker

Il segno dell’angolo è determinato tramite prodotto vettoriale.

Note sulla maschera di cancellazione
La gomma permette di escludere porzioni del frame che interferiscono con la rilevazione del colore, come vestiti o riflessi. Ogni frame può avere una maschera indipendente.

Avvio
Eseguire il programma con:
python nome_script.py
