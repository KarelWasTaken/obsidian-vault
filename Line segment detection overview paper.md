Zdroj: A Comprehensive Review of Image Line Segment Detection and Description: Taxonomies, Comparisons, and Challenges (https://arxiv.org/pdf/2305.00264v2)

Současný přístup se skládá ze dvou procesů:
- detekce linek
- označení linek pro možnost jejich spojení napříč obrázky

Přínos studie:
- objektvní porovnání možných přístupů na otevřených datasetech

Line segment:
- low level feature obrázku definovaná jako dva koncové body nebo několik bodů s úhly a poloměry
- Vlastnosti:
	- opakovatelnost - musí být detekovatelné z různých úhlů, v různém světle
	- odlišnost - musí se odlišovat od jiných features v obrázku
	- přesnost - musí být spolehlivě nalezitelné
	- efektivita - nalezení musí být výpočetně levné
	- množství - musí jich být nalezen dostatek pro pozdější zpracování
- nesou povětšinou více strukturální informace o obrázku než bodové features

Typy detekce
- Global Hough-based
	- Jde o přenášení do Hough space, kde je každá lineární funkce bod a naopak (idk jak to realne funguje)
	- Protože to nefungovalo s vertikálními čarami, přenáší se to do Hough space jako goniometrické funkce
- Local-based
- Learning-based 
- Hybrid-based

Obecné výzvy:
- nestabilní koncové body linkových segmentů 
- nedostatečně dobré metody
- nedostatečný výkon v náročných sénářích
- nedostatek spolehlivě anotovaných datasetů