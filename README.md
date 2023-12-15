# Progetto sis - Architettura degli Elaboratori
## Specifiche del circuito
Si progetti il circuito sequenziale che controlla un macchinario chimico il cui scopo è portare una soluzione iniziale a pH
noto, ad un pH di neutralità. Il valore del pH viene espresso in valori compresi tra 0 e 14.
Il circuito controlla due valvole di erogazione: una di soluzione acida e una di soluzione basica.
Se la soluzione iniziale è acida, il circuito dovrà procedere all’erogazione della soluzione basica fintanto che la soluzione
finale non raggiunga la soglia di neutralità (pH compreso tra 7 e 8).
Analogamente, se la soluzione iniziale è basica, il circuito procederà all’erogazione di soluzione acida fino al
raggiungimento della soglia di neutralità.
Per pH acido si intende un valore strettamente inferiore a 7, mentre per basico si intende una soluzione con pH strettamente
maggiore a 8.
Il pH viene codificato in fixed-point, con 4 bit riservati per la parte intera e gli altri per la parte decimale.
Le due valvole hanno flussi differenti di erogazione.
La valvola relativa alla soluzione basica eroga una quantità di soluzione che permette di alzare il pH della iniziale di 0.25
ogni ciclo di clock.
La valvola relativa alla soluzione acida eroga una quantità di soluzione che permette di abbassare il pH della soluzione
iniziale di 0.5 ogni ciclo di clock.

Il circuito ha 3 ingressi nel seguente ordine:
+ RST (1 bit) • START(1 bit)
+ pH (8 bit, 4 parte intera e 4 per la parte decimale) Gli output sono i seguenti e devono seguire il seguente ordine:
+ FINE_OPERAZIONE (1 bit)
+ ERRORE_SENSORE (1 bit)
+ VALVOLA_ACIDO (1 bit)
+ VALVOLA_BASICO (1 bit)
+ PH_FINALE (8 bit)
+ NCLK (8 bit)

Input e output devono essere definiti nell’ordine sopra specificato (da sinistra verso destra). Le porte con più bit devono
essere descritte utilizzando la codifica con il bit più significativo a sinistra.
Il meccanismo è guidato come segue:
+ Quando il segnale RST viene alzato, il sistema torna da un qualsiasi stato allo stato di Reset, mettendo tutte le porte in
output a zero.
+ Per procedere, Il sistema riceve in input il segnale di START, con valore 1, e il segnale del pH iniziale per un solo
ciclo di clock. Il sistema potrà quindi procedere con la fase di elaborazione.
+ Se la soluzione iniziale è acida, viene aperta la valvola della soluzione basica, mettendo a 1 il relativo output.
Analogamente, se la soluzione iniziale è basica, viene aperta la valvola della soluzione acida mettendo a 1 la porta
VALVOLA_ACIDO.
+ Il sistema mantiene aperte le valvole per il tempo necessario al raggiungimento della soglia di neutralità (calcolata dal
sistema).
+ Una volta terminata l’operazione, il sistema deve chiudere tutte le valvole aperte, riportare il pH finale sulla porta in
output PH_FINALE e alzare la porta di FINE_OPERAZIONE.
+ La porta NCLK riporta quanti cicli di clock sono stati necessari per portare la soluzione a neutralità.
+ Si progetti il circuito sequenziale che controlla un macchinario chimico il cui scopo è portare una soluzione iniziale a pH
noto, ad un pH di neutralità. Il valore del pH viene espresso in valori compresi tra 0 e 14.

Il circuito controlla due valvole di erogazione: una di soluzione acida e una di soluzione basica.
Se la soluzione iniziale è acida, il circuito dovrà procedere all’erogazione della soluzione basica fintanto che la soluzione
finale non raggiunga la soglia di neutralità (pH compreso tra 7 e 8).
Analogamente, se la soluzione iniziale è basica, il circuito procederà all’erogazione di soluzione acida fino al
raggiungimento della soglia di neutralità.
Per pH acido si intende un valore strettamente inferiore a 7, mentre per basico si intende una soluzione con pH strettamente
maggiore a 8.
Il pH viene codificato in fixed-point, con 4 bit riservati per la parte intera e gli altri per la parte decimale.
Le due valvole hanno flussi differenti di erogazione.
La valvola relativa alla soluzione basica eroga una quantità di soluzione che permette di alzare il pH della iniziale di 0.25
ogni ciclo di clock.
La valvola relativa alla soluzione acida eroga una quantità di soluzione che permette di abbassare il pH della soluzione
iniziale di 0.5 ogni ciclo di clock.

Il circuito ha 3 ingressi nel seguente ordine:
+ RST (1 bit) • START(1 bit)
+ pH (8 bit, 4 parte intera e 4 per la parte decimale) Gli output sono i seguenti e devono seguire il seguente ordine:
+ FINE_OPERAZIONE (1 bit)
+ ERRORE_SENSORE (1 bit)
+ VALVOLA_ACIDO (1 bit)
+ VALVOLA_BASICO (1 bit)
+ PH_FINALE (8 bit)
+ NCLK (8 bit)

Input e output devono essere definiti nell’ordine sopra specificato (da sinistra verso destra). Le porte con più bit devono
essere descritte utilizzando la codifica con il bit più significativo a sinistra.
Il meccanismo è guidato come segue:
+ Quando il segnale RST viene alzato, il sistema torna da un qualsiasi stato allo stato di Reset, mettendo tutte le porte in
output a zero.
+ Per procedere, Il sistema riceve in input il segnale di START, con valore 1, e il segnale del pH iniziale per un solo
ciclo di clock. Il sistema potrà quindi procedere con la fase di elaborazione.
+ Se la soluzione iniziale è acida, viene aperta la valvola della soluzione basica, mettendo a 1 il relativo output.
Analogamente, se la soluzione iniziale è basica, viene aperta la valvola della soluzione acida mettendo a 1 la porta
VALVOLA_ACIDO.
+ Il sistema mantiene aperte le valvole per il tempo necessario al raggiungimento della soglia di neutralità (calcolata dal
sistema).
+ Una volta terminata l’operazione, il sistema deve chiudere tutte le valvole aperte, riportare il pH finale sulla porta in
output PH_FINALE e alzare la porta di FINE_OPERAZIONE.
+ La porta NCLK riporta quanti cicli di clock sono stati necessari per portare la soluzione a neutralità.
+ Se il valore del pH non è valido (> 14) il sistema deve riportare l’errore alzando l’output ERRORE_SENSORE

Lo schema generale del circuito deve rispettare la FSMD riportata di seguito: Se il valore del pH non è valido (> 14) il sistema deve riportare l’errore alzando l’output ERRORE_SENSORE

## Documentazione
Per tutta la documentazione del progetto visionare il file Relazione.pdf