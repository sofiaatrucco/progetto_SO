# Progetto SO - Simulatore di trasporto marittimo

Un simulatore di trasporto marittimo di merci tra porti sviluppato in C, che utilizza meccanismi IPC di Unix per gestire la concorrenza tra navi, porti e condizioni meteorologiche.

## Descrizione

Il progetto simula un sistema di trasporto marittimo dove:
- Le **navi** si muovono su una mappa 2D per caricare e consegnare merci tra porti
- I **porti** generano offerte di merci e richiedono specifici tipi di prodotti
- Le **condizioni meteorologiche** influenzano le operazioni
- Le merci hanno una scadenza e devono essere consegnate in tempo

Ogni nave, porto e il sistema meteo sono implementati come processi separati che comunicano tra loro attraverso shared memory, semafori, code di messaggi e segnali.

## Funzionamento

Le navi cercano autonomamente merci da trasportare, negoziano con i porti e calcolano se riusciranno a consegnare prima della scadenza. I porti generano offerte giornaliere e gestiscono le richieste. Il meteo può rallentare le navi con tempeste o bloccare temporaneamente i porti con mareggiate.

La simulazione avanza a ritmo di un giorno al secondo, con report giornalieri che mostrano lo stato di navi, porti e merci. Termina quando finiscono i giorni configurati, quando non ci sono più merci disponibili, o quando tutte le navi sono affondate.

## Configurazione

Il comportamento è configurabile tramite variabili d'ambiente:
- `SO_NAVI`: numero di navi
- `SO_PORTI`: numero di porti
- `SO_MERCI`: tipi di merci diverse
- `SO_DAYS`: durata della simulazione
- `SO_CAPACITY`: capacità di carico delle navi
- `SO_SPEED`: velocità di navigazione
- `SO_BANCHINE`: numero di banchine per porto
- e altre...

## Note

Progetto sviluppato per il corso di Sistemi Operativi. Dimostra l'uso pratico di process management, shared memory, semafori, code di messaggi e signal handling in ambiente Unix.
