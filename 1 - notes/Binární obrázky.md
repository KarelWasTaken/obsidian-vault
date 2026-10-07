---
date: 2026-09-30 19:20
tags:
  - complete
  - computervision
source: "[[First principles of computer vision]]"
keys:
  - "[[zpracování obrazu]]"
  - "[[computer vision]]"
---

# Binární obrázky (Binary Images)

## 1. Prahování (Thresholding)
Převod stupňů šedi (grayscale) na binární matici pixelů ($0$ nebo $1$):
$$\text{Grayscale obraz} \xrightarrow{\text{threshold } T} B(x,y) = \begin{cases} 1 & \text{pokud } f(x,y) \ge T \\ 0 & \text{jinak} \end{cases}$$
- **Výběr prahu:** Zkoumání histogramu intenzit; ideální práh leží v minimu mezi dvěma modálními vrcholy (popředí a pozadí).
- **Backlighting (zadní prosvícení):** Ideální průmyslová kontrola scény pro získání perfektního binárního kontrastu siluety.

## 2. Geometrické vlastnosti binárních objektů
Matematické momenty pro popis tvaru v diskrétním pixelovém prostoru:
- **Obsah (Plocha / Nultý moment):**
  $$A = m_{00} = \sum_{x} \sum_{y} B(x,y)$$
- **Těžiště / Střed plochy (První momenty):**
  $$\bar{x} = \frac{m_{10}}{m_{00}}, \quad \bar{y} = \frac{m_{01}}{m_{00}}$$
- **Orientace (Osa nejmenšího druhého momentu):**
  Směr hlavní osy setrvačnosti minimalizující sumu čtverců vzdáleností bodů od osy.
- **Kulatost (Kompaktnost):**
  Poměr hlavních os orientace, popř. $4\pi A / P^2$.
- **Invariantní příznaky:** Minimální a maximální centrální moment setrvačnosti, celkový obsah (škálovaný).

## 3. Segmentace propojených komponent (Connected Component Labeling)
Algoritmus označování souvislých oblastí:
1. Nalezení neoznačeného počátečního pixelu (*seed*) s hodnotou $B = 1$.
2. Přiřazení nového unikátního označení (label).
3. Šíření označení na všechny bezprostřední sousedy s $B = 1$ (do vyčerpání souvislé oblasti).
4. Opakování kroku 1 pro zbytek obrazu.

### Definice sousedství:
- **4-sousedství:** Pouze horizontální a vertikální směry.
- **8-sousedství:** Včetně diagonál (riziko paradoxů propojenosti popředí a pozadí).
- **6-sousedství:** Asymetrické přiblížení šestiúhelníkové mřížce bez křížových paradoxů.

## 4. Morfologické a iterativní operace (Skeletonizace)

### Eulerova charakteristika ($E$)
Topologický invariant zachovávající počet objektů a vnitřních děr:
$$E = \text{počet samostatných tvarů} - \text{počet děr}$$
- Eulerova charakteristika celého obrazu se rovná součtu Eulerových charakteristik nepřekrývajících se podoblastí.

### 16 algoritmů iterativních modifikací
- Každý pixel má 64 různých možných konfigurací svého $3 \times 3$ okolí.
- Změna hodnoty pixelu ($0 \to 1$ nebo $1 \to 0$) je řízena pravidlem změny Eulerovy charakteristiky:
  - **Algoritmus 4 (Skeletonizace):** Ztenčuje objekty na kostru o tloušťce jednoho pixelu při zachování topologické souvislosti.
  - **Algoritmus 7 (Dilatace):** Rozšiřuje a vyplňuje hraniční objekty.

---

### References
- [[First principles of computer vision]]
- [[Zpracování obrazu]]
- [[Segmentace obrázků]]
