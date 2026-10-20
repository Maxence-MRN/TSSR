# Puissance de calcul d'un processeur

## Formule
La puissance de calcul d'un processeur s'exprime en FLOPS **(Floating Point Operation Per Second)**.
De manière simplifiée, le calcul prend en compte les paramètres du processeur suivant :
- Fréquence
- Nb d'octets (64bits = 8octets pour rappel)
- Le nombre de core
- HyperThread ou non
- Si c'est un CISC ou un RISC (paramètre non intégré dans la formule simplifiée)

La formule est donc la suivante : 
FLOPS = Nombre de core x octets x Fréquence
Et si HyperThread, alors on multiplie par 2 à l'arrivée.

## Exemple

Un Core I7 à Fréquence 3.8GHz, 64bits (Donc 8octets) 8 cores sans HyperThreading donnera :

3.8 x 8 x 8 = 243
la fréquence est en GHz (et non MHz), la puissance de calcul du processeur est de 243 Go/s