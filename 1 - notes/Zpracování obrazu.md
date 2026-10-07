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

# Zpracování obrazu (Image Processing)

## 1. Cíle zpracování obrazu
- Zpracování obrazových dat do stavu, který je pro člověka čitelnější nebo pro následné algoritmy jednodušší k analýze.
- Získávání a extrakce konkrétních příznaků (features) relevantních pro danou úlohu.

## 2. Bodové operace (Point Operations)
Každý pixel je zpracován nezávisle na svém okolí:
- Matematická transformace intenzity: $g(x,y) = T(f(x,y))$
- Operace: ztmavení, zesvětlení, zvýšení/snížení kontrastu, prahování (thresholding), inverze hodnot (negativ).

## 3. LSIS systémy a konvoluce
Lineární posuvově invariantní systém (**LSIS** – *Linear Shift-Invariant System*):
$$f(x) \xrightarrow{\text{LSIS}} g(x)$$
- **Linearita:** $\alpha f_1 + \beta f_2 \xrightarrow{\text{LSIS}} \alpha g_1 + \beta g_2$
- **Posuvová invariance:** $f(x - a) \xrightarrow{\text{LSIS}} g(x - a)$

### Konvoluce ($*$)
- Základní matematická operace LSIS systémů pro filtraci obrazu.
- Představuje integrál (či diskrétní sumu) překryvu vstupní funkce $f$ s otočenou impulsní odezvou $h$:
  $$(f * h)(x) = \int_{-\infty}^{\infty} f(\tau) h(x - \tau) \, d\tau$$
- **Vlastnosti konvoluce:**
  - Komutativita: $a * b = b * a$
  - Asociativita: $(a * b) * c = a * (b * c)$ (dvě po sobě jdoucí konvoluce lze sloučit do jediné filtrační masky).
  - Impulsní odezva (*point spread function*, PSF): odezva systému na Diracův impuls ($\delta$).

## 4. Lineární obrazové filtry (Konvoluční masky / Kernely)
- **Řešení okrajových podmínek (boundary problem):**
  - Ignorování okrajů (oříznutí obrazu o velikost masky).
  - Rozšíření konstantní hodnotou (např. černou barvou nebo průměrem obrazu).
  - Rozšíření zrcadlením (odraz hraničních pixelů – nejčastější a nejpřirozenější).
- **Základní typy filtrů:**
  - **Impulse filter:** Identita (výstup je totožný se vstupem).
  - **Box filter (průměrovací):** Rovnoměrné rozostření; vytváří však nepříjemné obdélníkové artefakty.
  - **Gaussian filter (Gaussovský kernel):** Přirozené rozostření s váhami klesajícími se vzdáleností od středu. Je **separabilní** na 1D horizontální a 1D vertikální komponent, což radikálně zlevňuje výpočet z $O(K^2)$ na $O(2K)$.

## 5. Nelineární obrazové filtry
- **Mediánový filtr (Median filter):**
  - Nahrazuje hodnotu pixelu mediánem z okolí velikosti $K \times K$.
  - Mimořádně efektivní pro odstranění šumu typu „sůl a pepř“ (*salt and pepper*) bez rozmazání ostrých hran.
- **Bilaterální filtr (Bilateral filter):**
  - Kombinuje prostorovou vzdálenost s podobností intenzity pixelů.
  - Vyhlazuje plochy, ale striktně zachovává výrazné hrany.

## 6. Template matching korelací
- Hledání vzoru v obraze:
  - Minimalizace rozdílu mezi vzorem (template) a výřezem obrazu (SSD – *Sum of Squared Differences*).
  - Maximalizace vzájemné křížové korelace (**cross-correlation**):
    - Korelace je matematicky konvoluce bez prostorového převrácení kernelu.
    - Pro spolehlivé výsledky musí být **normalizovaná** (NCC), jinak falešně preferuje oblasti s vysokým jasem.

---

### References
- [[First principles of computer vision]]
- [[Zpracování obrazu 2]]
- [[Detekce okrajů]]
