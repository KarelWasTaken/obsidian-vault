- konverze 2D obrázku do bodů, kde se intenzita obrázku silně mění

### Co je okraj
- rychlá změna intenzity obrázku v malé oblasti
- druhy okrajů
	- rozdíl mezi materiály
	- rozdíl mezi hloubkou
	- rozdíl v reflektivitě na povrchu
	- rozdíl v nasvícení
- zjišťujeme
	- pozici
	- výraznost
	- orientaci

### Detekce okrajů pomocí gradientu
- detekce první derivací
- využití derivace pro detekci okrajů ve 2D
- okraj určován pomocí gradientového operátoru konvolucí (větší -> horší lokalizace, ale menší senzitivita na šum)
- sobel je často používaným opetátorem
### Detekce okrajů pomocí Laplacian operátoru
- detekce druhou derivací
- okraj v 1D prostoru leží na 0
- Laplacian odhalí okraje, ale ne jejich směr
- odstranění šumu - gausův filtr - možné derivovat gausův filtr už před konvolucí (tzn. i použít laplacian operátoru na gausův filtr)
- Laplacian operátor je lineární - stačí jen jedna konvoluce

### Detekce okrajů pomocí Canny
- vyhlazení obrázku gausovým filtrem
- výpočet gradientu obrázku pomocí operátoru sobel
- zjistit výraznost okraje na každém pixelu
- použití 1D laplacian operátoru přímo na směru okraje
- výrazné přechody přes nulu jsou deklarovány jako okraje

- větší úvodní rozostření - detekce jen výraznějších rohů

### Detekce rohů
- roh je místo, kde se dva okraje střetávají
- hledání eliptického disku na distribuci derivací s zjištění hlavních dvou os elipsy
- pokud jsou obě osy velké -> roh