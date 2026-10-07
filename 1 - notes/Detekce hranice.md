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

# Detekce hranice a křivek (Boundary & Contour Detection)

## 1. Prokládání úseček a křivek do okrajů
- **Lineární regrese:** Minimalizace součtu čtverců kolmých nebo vertikálních vzdáleností bodů od přímky.
- **Polynomiální křivky a spline křivky:** Prokládání složitějších kontur za pomoci derivací a podmínek spojitosti vyšších řádů.

## 2. Aktivní obrysy (Snakes / Active Contours)
- Deformovatelný model křivky, který se pod vlivem vnitřních a vnějších sil iterativně posouvá a deformuje tak, aby dokonale obepnul hranice objektu:
  - Využití: segmentace orgánů v medicíně, sledování (tracking) deformujících se objektů napříč video snímky.
- **Reprezentace:** Uspořádaný seznam 2D bodů $v(s) = [x(s), y(s)]$ spojených úsečkami.
- **Energetická funkce:**
  $$E_{snake} = \int \left( E_{internal}(v(s)) + E_{image}(v(s)) + E_{constraint}(v(s)) \right) ds$$
  - **Vnitřní energie ($E_{internal}$):** Zajišťuje elasticitu (penalizace roztažení) a hladkost/tuhost (penalizace ostrých záhybů křivky pomocí 1. a 2. derivace).
  - **Obrazová energie ($E_{image}$):** Přitahuje křivku k vysokým hodnotám gradientu v obraze (k okrajům).

## 3. Houghova transformace (Hough Transform)
Geniální metoda pro detekci geometrických tvarů (přímek, kružnic) i v přítomnosti silného šumu, přerušení a zastření:
- **Princip duality:**
  - Bod v obrazové rovině $(x, y)$ odpovídá přímce (resp. sinusoidě) v parametrickém prostoru.
  - Body ležící na stejné přímce v obrazu se v parametrickém prostoru **protínají v jednom společném bodě**.
- **Normální reprezentace přímky (Hesseho tvar):**
  $$x \cos\theta + y \sin\theta = \rho$$
  - Parametry: $\rho$ (kolmá vzdálenost od počátku) a $\theta$ (úhel normály).
  - Překonává problém nekonečné směrnice vertikálních přímek ($y = ax + b$).
- **Akumulátor:** Diskretizovaná matice parametrů $(\rho, \theta)$. Každý hranový bod „hlasuje“ pro všechny dvojice, kterými může procházet. Lokální maxima v akumulátoru představují detekované přímky.

## 4. Zobecněná Houghova transformace (Generalized Hough Transform)
- Umožňuje detekovat libovolný obecný tvar bez analytické rovnice:
  - Model tvaru je popsán tzv. **R-tabulkou** (vzdálenosti a úhly hranových bodů vůči zvolenému referenčnímu středu objektu pro jednotlivé sklony gradientu).
  - V obraze každý hranový bod se známým směrem gradientu hlasuje pro pravděpodobnou polohu středu objektu.
  - Rozšíření parametrů o měřítko ($s$) a rotaci ($\phi$) zvyšuje dimenzionalitu akumulátoru na 4D.

---

### References
- [[First principles of computer vision]]
- [[Detekce okrajů]]
- [[Segmentace obrázků]]
