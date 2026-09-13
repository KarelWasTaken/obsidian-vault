Grayscale obrázek ---threshold---> charakteristická funkce
Výběr thresholdu podle histogramu (mezi dvěma modusy)

Většina objektů má konečné množství stabilních konfigurací - užitečné pro sledování 3D objektů (stačí je rozložit na rovinu)

Když je možná kontrola prostředí -> backlighting

### Geometrické vlastnosti
- obsah (Zeroth moment)
- střed obsahu (first moment)
- orientace (podle osy nejmenšího second moment)
- kulatost (poměr os orientace)

Neměnné získané vlastnosti:
- minimum second moment
- maximum second moment
- obsah

Počítání integrací (v prostoru) a sumou (v pixelovém prostoru)

### Segmentace binárních obrázků
Označení spojených bodů
1. Nalezení neoznačenéno "seed" bodu s b = 1, pokud takový neexistuje, kód je ukončen.
2. Přiřazení nového označení bodu
3. Přiřazení označení "seed" bodu jeho sousedům a sousedům sousedů, dokud žádný soused s b = 1 nezbývá
4. Pokračovat bodem 1

Určování sousedů
- 4 směry / 8 směry (i s diagonály) - oba mají problémy
- 6 směrů - asymetrie, přiblížení hexagonální mřížce

Postupné označování:
- možnost segmentace obrázku jedním průchodem
- v případě, kdy nový pixel spojuje dva rozdílně označené regiony -> poznačit, že dvě označení jsou ekvivalentní (opravení ve druhém průchodu)

### Iterativní modifikace (např. skeletonizace)

Eulerova charakteristika
- počet samostatných tvarů - počet děr
	- Např. $E_b = -1$, $E_i = 2$, $E_n = 1$
- E obrázku = suma E nepřekrývajících se oblastí obrázku

Sousedství pixelu na základě E*
- Každý pixel má 64 různých možných sousedství
- Vzory sousedství jsou klasifikovány rozdílem E, který způsobí změna prostředního pixelu z 0 na 1
- 4 možná sousedství ($N_{+1}$, $N_0$, $N_{-1}$, $N_{-2}$)

16 možných algoritmů pro iterativní modifikaci:
1. Specifikace sousedství $S$
2. Pro každý pixel ($i,j$)
	1. $a_{ij} = 1$ pokud $(i,j) \in S$, jinak $0$
	2. $b_{i,j} =$ současná hodnota pixelu $(i,j)$
	3. $c_{i,j} =$ nová hodnota pixelu $(i,j)$

| $a_{ij}$ | $b_{i,j}$ | $c_{i,j}$ | //  | alg. 0 | ... | alg. 4 | ... | alg. 7 | ... | alg. 15 |
| -------- | --------- | --------- | --- | ------ | --- | ------ | --- | ------ | --- | ------- |
| 0        | 0         | ?         | //  | 0      | ... | 0      | ... | 0      | ... | 1       |
| 0        | 1         | ?         | //  | 0      | ... | 1      | ... | 1      | ... | 1       |
| 1        | 0         | ?         | //  | 0      | ... | 0      | ... | 1      | ... | 1       |
| 1        | 1         | ?         | //  | 0      | ... | 0      | ... | 1      | ... | 1       |
-> 16 možností různých konfigurací $c_{i,j}$
- alg. 4 zužuje objekty ($S \in N_0$) (skeletonizace)
- alg. 7 rozšiřuje objekty ($S \in N_0$)