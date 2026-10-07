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

# Zpracování obrazu 2 (Frekvenční oblast a Fourierova transformace)

## 1. Fourierova transformace (FT)
- **Základní myšlenka:** Každá periodická i neperiodická funkce může být rozložena na sumu (nebo integrál) sinusoidů o různých frekvencích, amplitudách a fázích.
- **Komplexní reprezentace:** Signál $f(x)$ je převeden do frekvenční oblasti $F(\omega)$:
  - **Amplituda (magnituda):** Informace o energii jednotlivých frekvencí v obraze.
  - **Fáze:** Nese klíčovou informaci o **prostorové struktuře a hranách** v obraze (lidské oko vnímá strukturu především z fázového spektra).
- **Vlastnosti:**
  - Plně **bezztrátová a reverzibilní** (přes inverzní Fourierovu transformaci - IFT).
  - Vztah šířky: širší funkce v prostorovém doméně odpovídá užšímu spektru ve frekvenční doméně a naopak.
  - Snadný výpočet derivací a posunů pouhým násobením ve frekvenční doméně.

## 2. Konvoluční teorém (Convolution Theorem)
Jedno z nejdůležitějších pravidel v digitálním zpracování signálu:
$$\mathcal{F}\{f * h\} = \mathcal{F}\{f\} \cdot \mathcal{F}\{h\}$$
- **Konvoluce v prostorovém doméně odpovídá prostému násobení ve frekvenční doméně.**
- Při velkých rozměrech konvoluční masky je výpočetně mnohem levnější provést Fast Fourier Transform (FFT), vynásobit spektra a provést IFT.

## 3. Filtrace obrazu ve frekvenční oblasti
- **Dolnopropustný filtr (Low-pass filter):**
  - Potlačuje vysoké frekvence a propouští nízké.
  - Výsledkem je **vyhlazení a rozostření** obrazu.
- **Hornopropustný filtr (High-pass filter):**
  - Potlačuje nízké (stejnosměrné) frekvence a propouští pouze vysoké.
  - Výsledkem je **zvýraznění hran a prudkých změn intenzity**.
- **Hybridní obrázky (Hybrid Images):**
  - Vytvoření iluze sloučením nízkých frekvencí jednoho obrázku a vysokých frekvencí druhého.
  - Zblízka divák vnímá vysokofrekvenční detaily, z dálky nízkofrekvenční siluetu.

## 4. Dekonvoluce ve frekvenční oblasti
- Odstranění pohybového rozmazání (**motion blur**):
  - Model: $g = f * h + n$ (kde $h$ je funkce rozmazání, $n$ je šum).
  - Přímé dělení $G(\omega) / H(\omega)$ ve frekvenční doméně vede k obrovskému zesílení šumu u vysokých frekvencí, kde se $H(\omega) \to 0$.
  - **Wienerova dekonvoluce:** Optimální filtr minimalizující střední kvadratickou chybu se zohledněním poměru signálu k šumu (SNR).

## 5. Teorie vzorkování a aliasing (Sampling & Aliasing)
- **Nyquistův-Shannonův teorém:** Vzorkovací frekvence musí být alespoň dvojnásobkem maximální frekvence obsažené v signálu ($f_s \ge 2 f_{max}$).
- **Aliasing:** Pokud je vzorkovací frekvence příliš nízká, vysoké frekvence se maskují jako falešné nízké frekvence a v obraze vznikají nežádoucí artefakty (moiré efekt, schodovité hrany).
- **Obrana proti aliasingu:**
  - Optický antialiasingový filtr (low-pass filter) před samotným senzorem kamery.
  - Mírné fyzické rozostření na úrovni jednotlivých buněk snímače.

---

### References
- [[First principles of computer vision]]
- [[Zpracování obrazu]]
