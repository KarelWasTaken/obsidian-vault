### Vepsání úseček a křivek do okrajů
- propojení lineární funkcí - minimalizace průměrné druhé mocniny vzálenosti
- propojení polynomickou funkcí - pomocí derivací
### Aktivní obrysy
- iterativně se zmenší, aby přesně obepínal požadovaný objekt
- může být použit k trackování deformujících se objektů napříč snímky
- reprezentace: seřazený list 2D souřadnic, které jsou propojeny rovnými úsečkami o shodné délce
- na obrázek použijeme druhou mocninu výraznosti gradientu a rozmažeme jej
- maximalizujeme sumu výraznosti gradientu na všech bodecsh obrysu
- přidáme požadavky na elasticitu a hladkost (pomocí derivací -> minimalizace vzdálenosti mezi body a rozdíly mezi kroky)
- možné přidat další požadavky (např. penalizace vzdálenosti od známého tvaru objektu)
- možné algoritmus změnit, aby se obrys místo zmenšování rozpínal

### Hough transform
- každý bod v bodové oblasti je přímkou v parametrové oblasti (přímka odpovídá všem přímkám, které prochází bodem) a naopak (bod v parametrové oblasti odpovídá přímce v bodobé oblasti)
- po vektorizaci parametrové oblasti lze najít bod s největším počtem průniků (nález přímky)
- kvůli výpočetni náročnosti využití parametrů goniometrických funkcí
- problém při určení parametrů rozlišení vektorizované parametrové oblasti, nutného počtu půniků
- možné hledat i kruhy, jiné tvary, ale s větším počtem parametrů náročnost výpočtu stoupá (vícedimenzionální vektorová reprezentace průniků)

### Obecný Hough transform
- reprezentace objektu vzdáleností od referenčního bodu a úhlem od horizontální přímky uvnitř objektu
- vytvoření tabulky, kdy pro každý úhel okraje jsou definované vzdálenosti a úhly
- ve vektorizované parametrové oblasti pro každý bod hlasovat ve všech místech, kde by pro daný bod mohl být referenční bod
- možné přidání parametrů velikosti a úhlu, opět vznikají další dimenze v parametrové oblasti

### Poznámky k Hough transform
- funguje na nespojitých okrajích
- poměrně necitlivý na šum
- efektivní pro jednoduché tvary
- možnost hledání komplexních tvarů pomocí Obecného Hough transform
- Při komplexnějších problémech problém výpočetní náročnosti