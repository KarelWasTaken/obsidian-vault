### Fourierova transformace
- každá periodická funkce může být zapsána jako suma sinusoidů
- reprezentuje signál $f_{(x)}$ amplitudami a fázemi sinusoidů, které ho tvoří
- Opakem inverzní fourierova transformace
- Oběma směry je transformace bezztrátová
- je komplexní - nese informaci i o amplitude i o fázi
- širší funkce -> užší fourierova transformace
- jednoduchá transformace derivace funkce i jejího posunutí bez nutnosti přepočítat transformaci

### Convolution theorem
- konvoluce = násobek fourierových transformací (a naopak) -> výpočetní zlevnění
- vizualizace ve frekvenční oblasti

### Filtrace obrázků ve frekvenční oblasti
- low pass filter (eliminace vyšších frekvencí z frekvenční oblasti) = rozostření obrázku
- high pass filter (eliminace nižších frekvencí z frekvenční oblasti) = zůstanou pouze oblasti se změnou (např. okraje)
- fáze drží většinu informace o struktuře obrázku
- hybridní obrázky (jeden je low pass a jeden high pass filtrovaný) -> z blízka je vidět high pass filtered obrázek, z dálky druhý
### Dekonvoluce ve frekvenční oblasti
- dekonvoluce motion bluru
	- odhadneme funkci motion bluru pomocí akcelerometru v mobilu
	- jednoduché ve frekvenční oblasti -> dělení fourierových tranformací
	- problém - zvýraznění šumu (motion blur funguje jako low pass filter, ve vyšších frekvencích hlavně šum)
	- Potlačení šumu: Weinerova dekonvoluce

### Teorie samplingu a aliasing 
- aliasing = vzorkovací frekvence je přiliš nízká a vzinká nesprávný signál, vytváří artefakty v obrázku
- předejití aliasingu
	- low pass filter už na snímači
	- mírné rozostření při čtení každého pixelu fyzickým box filterem