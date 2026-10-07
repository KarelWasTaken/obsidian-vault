---
date: 2026-09-30 19:20
tags:
  - complete
  - computervision
source: "[[First principles of computer vision]]"
keys:
  - "[[computer vision]]"
---

# Vision introduction (Úvod do počítačového vidění)

## 1. Kdy použít klasické zpracování obrazu?
- Když je úkol exaktně popsatelný a algoritmizovatelný.
- Když nelze získat dostatek trénovacích dat pro neuronové sítě (NN).
- Když je nutná plná interpretovatelnost a transparentnost výpočtu (abychom věděli, jak přesně algoritmus funguje).

## 2. Lidské vidění vs. počítačové vidění
- Až **60 % lidského mozku** se nějakým způsobem podílí na vidění a jeho interpretaci.
- **Proč využívat software, když máme dokonalý vnitřní vizuální aparát?**
  - Automatizace rutinních a monotónních úkolů.
  - Lidské vidění je převážně **kvalitativní**, nikoliv kvantitativní (snadno podléhá optickým iluzím a kontextu).
  - Překonání lidských fyzických limitů (rychlost snímání, mikroskopické měření, neviditelná spektra).
- **Proč je v pořádku nenapodobovat lidský mozek?**
  - Člověk je univerzální, ale ve specifických exaktních úkolech (měření mikrometrů, rychlé počítání pixelů) selhává.
  - Biologický vizuální kortex přesně nechápeme, proto je efektivnější stavět na matematických a fyzikálních principech.

## 3. Základní model počítačového vidění
$$\text{3D scéna} \xrightarrow{\text{světlo}} \text{optický snímač} \xrightarrow{\text{digitalizace}} \text{počítačové zpracování} \xrightarrow{} \text{výstup / rozhodnutí}$$

- **Definice oboru:**
  - Automatizace lidského zpracování obrazu.
  - Úkol zpracování a extrakce sémantické informace z obrazu.
  - **Inverze počítačové grafiky** (grafika tvoří 2D obraz z 3D popisu; vidění rekonstruuje 3D popis z 2D obrazu).

## 4. Reprezentace obrazu a pixel
Obrázek je reprezentován jako **2D diskrétní pole (matice) pixelů**.
Každý pixel nese hodnoty:
- **Světlost (intenzita):** Grayscale hodnota.
- **Barva:** Vektory kanálů (např. RGB, HSV, Lab).
- *(Hloubka / vzdálenost):* U RGB-D snímačů.
- *(Materiálové vlastnosti / odrazivost):* Pokročilé modely odrazu světla (BRDF).

## 5. Praktické aplikace
- **Průmysl a výroba:** Kontrola kvality, robotické navádění.
- **OCR a digitalizace:** Čtení SPZ, skenování a rozpoznávání tištěného textu.
- **Biometrika:** Detekce obličejů, rozpoznávání duhovky.
- **Sledování objektů (tracking):** Optická myš, Microsoft Kinect, sledování trajektorií.
- **Autonomní systémy:** Autonomní řízení vozidel, drony.
- **Medicína:** Analýza rentgenů, CT, magnetické rezonance.
- **Zábava a VFX:** Vizuální efekty ve filmu, filtry v reálném čase.

---

### References
- [[First principles of computer vision]]
- [[Zpracování obrazu]]
