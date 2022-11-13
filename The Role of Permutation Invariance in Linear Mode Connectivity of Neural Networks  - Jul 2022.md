[2110.06296.pdf]
[[randomnetwork]] [[lotteryticket]]



we conjecture that if the permutation invariance of neural networks is taken into account,
SGD solutions will likely have no barrier in the linear interpolation between them.
Our conjecture has implications for lottery ticket hypothesis, distributed training and ensemble methods


Conclusions:
In a nutshell, this conjecture suggests that if one considers permutation invariance, there is essentially no loss barrier between different solutions and they all exist in the same basin in the loss landscape.
(questo va nella direzione di Vidal e altri che vedono lo spazio della soluzione degenere per spiegare l'efficacia della overparametrization)
Essentially it postulates that randomness in terms of permutation does not impact the quality of the final result.
If all basins in the loss landscape are basically the same function, there will be no need to search all of them. One can explore the same basin while looking for diverse solutions and this makes search much easier and would lead to substantially more efficient search algorithms.