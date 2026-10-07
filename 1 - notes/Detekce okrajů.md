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

# Detekce okrajů (Edge Detection)

## 1. Co je okraj (Edge)?
Okraj je lokální místo v obraze, kde dochází k prudké a výrazné změně intenzity jasu.
- **Fyzikální příčiny vzniku okrajů:**
  - Změna materiálu a povrchové odrazivosti (*albedo*).
  - Skoková změna geometrické hloubky (silueta a hranice objektu vůči pozadí).
  - Orientace povrchu vůči zdroji světla (lomy ploch).
  - Stíny a světelné diskontinuity.
- **Měřené atributy okraje:** Pozice, velikost gradientu (výraznost) a směrová orientace (kolmice k hraně).

## 2. Detekce pomocí 1. derivace (Gradientní metody)
- Vektor gradientu intenzity obrazu:
  $$\nabla f = \left[ \frac{\partial f}{\partial x}, \frac{\partial f}{\partial y} \right]^T$$
- **Velikost gradientu (strmost hrany):** $\|\nabla f\| = \sqrt{\left(\frac{\partial f}{\partial x}\right)^2 + \left(\frac{\partial f}{\partial y}\right)^2}$
- **Směr hrany:** $\theta = \arctan\left(\frac{\partial f / \partial y}{\partial f / \partial x}\right)$
- **Operátory:**
  - **Sobelův operátor:** Konvoluční masky $3 \times 3$ kombinující vyhlazení ve směru hrany a diferenciaci napříč hranou (odolnější vůči šumu než jednoduché diference).

## 3. Detekce pomocí 2. derivace (Laplaceův operátor)
- Laplaceův operátor ($\nabla^2 f = \frac{\partial^2 f}{\partial x^2} + \frac{\partial^2 f}{\partial y^2}$):
  - Okraj odpovídá **průchodu druhou derivací nulou (*zero-crossing*)**.
  - Je izotropní (nerozlišuje směr hrany, reaguje ve všech směrech stejně).
- **Laplacian of Gaussian (LoG):**
  - Protože 2. derivace extrémně zesiluje šum, obraz se nejprve vyhladí Gaussovským filtrem.
  - Díky linearitě lze operátory sloučit do jediné konvoluční masky: $\nabla^2(f * G) = f * (\nabla^2 G)$.

## 4. Cannyho detektor hran (Canny Edge Detector)
Optimální a celosvětově nejpoužívanější algoritmus detekce hran:
1. **Vyhlazení obrazu:** Konvoluce s 2D Gaussovským filtrem k potlačení šumu.
2. **Výpočet gradientu:** Zjištění velikosti a směru gradientu pomocí Sobelových masek.
3. **Non-maximum suppression (NMS):** Ztenčení hran – potlačení všech pixelů, které nejsou lokálním maximem ve směru gradientu.
4. **Hysterezní prahování (Hysteresis Thresholding):**
   - Dva prahy: vysoký ($T_{high}$) a nízký ($T_{low}$).
   - Pixely nad $T_{high}$ jsou jisté hrany; pixely mezi $T_{low}$ a $T_{high}$ jsou přijaty pouze tehdy, pokud jsou souvisle napojeny na jistou hranu.

## 5. Detekce rohů (Corner Detection)
- Roh je singulární bod, kde se protínají hrany s různou orientací (změna intenzity ve všech směrech).
- **Harrisův detektor rohů:** Zkoumá vlastní čísla matice druhých momentů (autokorelační matice):
  - Obě vlastní čísla malá $\to$ homogenní plocha.
  - Jedno velké, jedno malé $\to$ hrana (edge).
  - Obě vlastní čísla velká $\to$ **roh (corner / klíčový bod)**.

---

### References
- [[First principles of computer vision]]
- [[Detekce hranice]]
- [[Zpracování obrazu]]
