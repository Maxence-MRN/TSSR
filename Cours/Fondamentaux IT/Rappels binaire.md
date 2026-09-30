## Base numéraire ##  
Binaire = base 2 (= 1 et 0)  
Octal = base 8 (très peu utilisée)  
Hexadécimale = base 16 (= de 0 à 9, puis lettres de A à F)  

Le 0 et le 1 sont la plus petite unité de base tolérée par les ordinateurs, appelés *bits (=contraction de binary digits)* **et dont l'unité est le b**  
Outre une valeur numérique, ces deux chiffres sont surtout des *symboles* où *0=False* et *1=True*  
---
## Calcul Base 2##
Tout nombre élevé à la puissance 0 = 1 (Pas de débat)  
Puis :  
- 2^1=2
- 2^2=4
- 2^3=8
- 2^4=16
- 2^5=32
- 2^6=64
- 2^7=128
- 2^8=256
- 2^9=512
- 2^10=1024  
*ETC...* Ce qui mène à comprendre que toutes les notions en informatiques sont liées à ces multiples.  
*Exemple :*
- Affichage écran : 1024x512
- Résolution : 2048p
- Processeur de PC : 64bits
- Jeux vidéos Old Gen : 8bits et 16bits  

---
## Les Octets ##  

Un octet vaut 8 bits, et s'exprime en *Bytes* (unité B, à ne pas confondre avec bits, soit b)  


### Tableau de conversion d'un Octet : ###

| Bit      | b7  | b6  | b5  | b4  | b3 | b2 | b1 | b0 |
|----------|-----|-----|-----|-----|----|----|----|----|
| Poids    | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |

Ainsi, les unités standardisées ont une conversion classique où :  
- Un ko (ou kB) = 1000 octets
- Un Mo (ou MB) = 1 000 000 octets
- Un Go (ou GB) = 1 000 000 000 octets  
*Etc...*
---
## Du binaire au décimal ##  

Pour convertir efficacement le binaire vers décimal, il faut employer les puissances de 2 et les employer dans un matrice vide, simple à remplir.  

| 2⁷ (128) | 2⁶ (64) | 2⁵ (32) | 2⁴ (16) | 2³ (8) | 2² (4) | 2¹ (2) | 2⁰ (1) |
|----------|---------|---------|---------|--------|--------|--------|--------|
|          |         |         |         |        |        |        |        |
**La matrice se lit donc de droite à gauche (tel un manga), et le 1 et 0 sont donc des symboles True/False**  
Pour rappel, un Octet ne peut pas excéder 255 (poids converti en valeur décimale)  

## Du décimal au binaire ##  
Pour convertir du décimal au binaire, on se sert de la même matrice et on opère par soustraction :  
``*Exemple avec le nombre 42 :*
- Puis-je valider la case 2^7 - non car 128 est supérieur  
- Puis-je valider la case 2^6 - non car 64 est supérieur  
- Puis-je valider la case 2^5 - oui car 32 est inférieur, il me reste 10  
- Puis-je valider la case 2^4 - non car 16 est supérieur  
- Puis-je valider la case 2^3 - oui car 8 est inférieur, il me reste 2 
- Puis-je valider la case 2^2 - non car 4 est supérieur  
- Puis-je valider la case 2^1 - oui, et il me reste 0  
- Je ne peux donc pas valider 2^0
- Résultat : 00101010 ``  

De la même manière, convertir 299 (C'est possible si on ne s'arrête évidemment pas au calcul d'@IP) donne 100101011 (et on dépasse les 8octets)
---
## Hexadécimal ##  
Permet de passer d'une base 10 (= décimale) à une base 16 (et inversement).  
*Pour coder en Hexa, il faut plus de symboles qu'en base 10, d'où l'introduction des lettres où :*  
- A = 10
- B = 11
- C = 12
- D = 13
- E = 14
- F = 15  
De 0 à F, ça fait donc 16 possibilités.
*Cela implique de retenir la tâble des puissances de 16, où :*  
- 16^0=1 (et équivalant à 2^0)  
- 16^1=16 (et équivalant à 2^4)
- 16^2=256 (et équivalant à 2^8)  
- 16^3=4096 (et équivalant à 2^12)
- *Etc...*  
Ainsi, pour convertir 5C en décimale, on reprend la même matrice que précédemment, **mais à l'exponentielle 16. Et à l'instar de la matrice vue avant, la première colonne est donc x^0.**  
*Ainsi :*  
- C est au rang 0
- 5 est au rang 1
- *Formule résultante :*  
- 5x16^1 + Cx16^0
- 5x16 + 12x1
- 80+12
- 92  

*Une règle universelle existe :*
- Soit le nombre 999 en base N
  - son résultat en base 10 sera :
  - 9xN^2 + 9xN^1 + 9xN^0 (car 3 chiffre, donc on pousse à la 3e colonne de la matrice pour exposant 2)  

## Algèbre Binaire ##

En plus des signes 1 et 0, des mots-clefs vont permettre de manipuler l'information :
- NOT (non)
- AND (et)
- OR (ou)
- NOR (Non ou)
- NAND (Non Et)
- XORD (Ou exclusif)
- XNOR (Non ou exclusif)  

Apparaissent alors les tables de l'algèbre de Boole.  
La première est la plus simple :  

### La table du NOT ###  

| A | S |
|---|---|
| 0 | 1 |
| 1 | 0 |

Le A est le point d'entrée d'une information dans un programme qui appliquera une *Inversion de l'information*  

### La table du AND ###  

| A | B | S |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |  

Les deux points d'entrées A et B génèreront une sortie S en fonction de la véracité de l'information. On est capable par ce mot-clef d'influer sur le traitement de deux informations :  
**L'information est vraie en sortie UNIQUEMENT si A et B sont vraies**  

### Les tables restantes, traduites en phrases simples###  

- OR : Information vraie en sortie si A ou B sont vraies
- NOR : Information fausse si A ou B sont vraies
- NAND : information fausse si A et B sont vraies
- XOR : information vraie UNIQUEMENT si A OU B sont vraies, mais pas les deux
- XNOR : Information fausse UNIQUEMENT si A OU B sont vraies, mais pas les deux.