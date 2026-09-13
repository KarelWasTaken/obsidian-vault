- Zpracování obrázku do stavu, který je jasnější nebo je jedodušší jej analyzovat.
- Získávání konkrétních informací z obrázku, které jsou relevantní pro dané použití.

### Zpracování pixelů
Každý pixel lze vyjádřit  (u barevných obrázků každá z barev)

Matematická transformace intenzity na každém pixelu (ztmavení, zesvětlení, inverze, zvýšení kontrastu)
### LSIS a konvoluce

LSIS (linear shift invariant system) $f_{(x)}$ -> LSIS -> $g_{(x)}$
- je lineární ($\alpha f_1 + \beta f_2$ -> LSIS -> $\alpha g_1 + \beta g_2$)
- je nezávislý na posunutí ($f_{(x-a)}$ -> LSIS -> $g_{(x-a)}$)

Konvoluce
- značená *
- produkt 2 funkcí
- obsah překrytí funkcí pro střed horizontálně převrácené funkce h v každém bodě funkce f
- je LSIS
- konvoluce funkce b + unit impuse function -> funkce b
- impulse response (point spread function) = funkce se kterou konvolujeme (při vložení unit impulse function je tato funkce vrácena)
- $a * b$ = $b * a$
- $(a * b) * c = a * (b * c)$
- tzn. dvě konvoluce po sobě lze konvolvovat do jedné konvoluce
- jednoduše rozšířitelná do více dimenzí


### Lineární obrázkové filtry
- impulse response = konvoluční mask/kernel/filter
- problém hranic
	- konvoluční filtr přesahuje rozměry obrázku
	- řešení:
		- ignorovat hranice
		- rozšířit obrázek konstantní hodnotou (např. průměrem pro celý obrázek)
		- rozšířit obrázek odrazem hraničních pixelů
	- některé filtry
		- impulse function - výstup stejný jako vstup
		- box function - rozostření (uhlazení), ale nemá přirozený efekt (vystupují čáry)
		- fuzzy filter (Gausův kernel) - rozostření, ale více kontextu z pixelů blízko
			- rozděliztelné - vertikální komponent konvolvovaný s horizontálním komponentem (výpočetně levnější)
### Nelineární obrázkové filtry
- median filtering
	- medián z $K^2$ hodnot kolem pixelu
	- odstranění "salt and pepper" zrnění za cenu malé ztráty detailu
	- na realistickém zrnění velká ztráta detailu
- Bilateral filter
	- Gaussian blur jen na pixelech s podobnou intenzitou (složení ze dvou komponent, liší se pro každý pixel)

### Template matching korelací
- minimalizace rozdílu mezi template a částí obrázku
- maximalizace cross-correlation
	- korelace je kovoluce bez převracení hodnot
	- musí být normalizovaná (jinak nejvyšší pro vysoké hodnoty)