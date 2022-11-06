-> Prima devo trovare il modello di rete neurale overparametrizzzato per scoprire se un problema può essere risolto, poi si passa a capire il modello minimale di tale rete.
-> quando possibile, cioè classification a 2 classi, uso la binarylogit per dare la struttura più semplice (è più semplice della cross entropy?) (emanuele).  Devo togliere il linear quando possibile, perché introduce ciò che vuole. La rete impara ciò che vuoi, dipende da come la addestri.
-> se vogliamo un node embedding che torni con la sequenza di grado, allora faccio training node-wise per far vedere che impara anche la sequenza di grado del power law col CM, l'etichetta è la degree sequence... basta cambiare il modo di fare training. 
Dovremmo quindi vedere come sarà il training che dovremo fare quando servirà a ciò che servirà

-> provare per esempio due modelli di dimensione diversa: 1-8-2 e 1-32-32-8 per mostrare che aumentando la capacità del modello posso risolvere dataset più pesanti e difficili

-> provare con la SGC  (studiare DGI)

-> training con e senza dropout (quando c'è il linear) - con e senza batchnorm

-> studio in funzione di $r=\frac{p1}{p2}$   con stessa initi random

-> studio in funzione della perturbazione random del grafo regolare che tende a 0

-> studio con variando gli exp della power law

-> vedere come cambiano i pesi in tensorboard durante il training (histogram)


?) ha ancora senso vedere che succede a 0 epoche?



### Plots del node embedding
- plot in due colori diversi per le due classi  (ER)
- grafo regolare feature uguali per tutti, anche con pesi random -> non va con la GCN
- varie distribuzioni piatte non centrate in zero -> trovare le situazioni patologiche
- binary classification per avere dim=1 (regular graph)
- provare entrambe dim=2 e dim=1 sia per reg che per ER, che per CM powerlaw  -> plottare la PCA durante il training (ovviamente solo per dim>1), graph e node emb.
  anche t-sne -> -> -> Con la PCA dobbiamo verificare l'unica cosa che abbiamo da vedere: che la dimensione di embedding ritorna come la dimensione dei parametri necessari per descrivere il grafo
- marker size dei node embedding in funzione del k-max del grafo relativo
- scatter della media dei node embedding dei nodi che hanno lo stesso grado

### Altri plots
Graph embedding VS kmax


##### Grafo random con due densità: ER a due blocchi (SBM?)
-> gli embedding si dovrebbero disporre su un minimo di Dim=2
##### 



# DOING
risolvere l'errore dell'id