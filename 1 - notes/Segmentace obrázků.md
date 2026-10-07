---
date: 2026-09-30 19:20
tags:
  - complete
  - computervision
source: "[[First principles of computer vision]]"
keys:
  - "[[computer vision]]"
  - "[[zpracování obrazu]]"
---

# Segmentace obrázků (Image Segmentation)

## 1. Cíl segmentace
Rozdělení obrazu na souvislé, nepřekrývající se a sémanticky smysluplné oblasti (segmenty), které sdílejí společné vizuální charakteristiky (barvu, jas, texturu nebo pohyb).

## 2. Segmentace shlukováním (Clustering)
- Převod pixelů do příznakového prostoru (např. intenzita, RGB, Lab barevný prostor nebo prostor souřadnic a barev $[x, y, R, G, B]$).
- Hledání shluků bodů podle zvolené metriky vzdálenosti (např. eukleidovská vzdálenost).

## 3. K-Means clustering
- **Princip algoritmu:**
  1. Zvolení pevného počtu $K$ shluků a náhodná inicializace jejich středů (centroidů).
  2. Přiřazení každého bodu v příznakovém prostoru k nejbližšímu centroidu.
  3. Přepočítání pozice centroidů jako těžiště všech přiřazených bodů.
  4. Opakování kroků 2 a 3 do konvergence (středy se již významně neposouvají).
- **Vylepšení inicializace (proti lokálním minimům):**
  - K-Means++: pravděpodobnostní výběr vzdálených počátečních středů.
  - Uniformní rozmístění v rozsahu distribuce nebo předběžný výpočet na náhodném vzorku bodů.
- **Výhody a limity:**
  - Rychlý, intuitivní a snadno implementovatelný.
  - Citlivý na odlehlé hodnoty (*outliers*), vyžaduje předem stanovit počet $K$, předpokládá kulovité shluky.

## 4. Mean Shift algoritmus
- **Princip:** Neparametrická metoda hledání lokálních maxim hustoty pravděpodobnosti (modů) v příznakovém prostoru.
- **Postup:**
  - Kolem každého bodu je umístěno vyhledávací okno (kernel s poloměrem $h$).
  - Vypočte se vektor posunu do těžiště bodů uvnitř okna (*mean shift vector*).
  - Okno se posune ve směru vektoru; proces se opakuje, dokud okno nedosáhne lokálního maxima hustoty.
  - Všechny body, jejichž trajektorie skončí ve stejném vrcholu, tvoří jeden segment.
- **Výhody:**
  - Není nutné předem zadávat počet segmentů $K$.
  - Nachází shluky libovolného geometrického tvaru.
  - Vysoce robustní vůči šumu a odlehlým hodnotám.
  - Jediným klíčovým parametrem je šířka pásma (velikost okna $h$).

## 5. Grafové metody segmentace (Graph-Based Segmentation)
- Obraz je reprezentován jako vážený neorientovaný graf $G = (V, E)$, kde uzly $V$ jsou pixely a hrany $E$ představují podobnost sousedních pixelů:
  - **Min-Cut / Graph Cuts:** Rozdělení grafu na dvě části minimalizací váhy přestřižených hran.
  - **Normalized Cuts:** Zohledňuje velikost segmentů a předchází odřezávání izolovaných jednotlivých pixelů.

---

### References
- [[First principles of computer vision]]
- [[Binární obrázky]]
- [[Detekce okrajů]]
