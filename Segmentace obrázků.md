### Segmentace clusteringem
- vybrání dimenzí pro atributovou oblast
- nalezení skupin podle vzdálenosti

### Segmentace k-clusteringem
- definovaný počet clusterů
- středy clusterů nejdřív náhodně rozloženy
	- body přiřazeny k nejbližšímu středu
	- střed clusteru znovu vypočítán
	- bod 1
- metody lepší než náhodní rozložení
	- pokud jsou středy clusterů příliš blízko, rozlož je znovu
	- vyber k uniformě rozložených středů v rozsahu distribuce
	- metoda 1 nebo 2 a poté provést kalkulaci na subsetu všech bodů (a výsledek použít jako úvodní rozložení středů clusterů)
- jednoduchý a poměrně rychlý
- je senzitivní na původní rozložení středů
- je senzitivní na outliers
- je nutné vybrat počet segmentů

### Mean shift
- Body clusterů se přiřazují k lokálnímu maximu hustoty bodů
- jednoduchý ale výpočetně náročný
- najde jakýkoliv počet clusterů
- není nutná žádná inicializace středů
- robustní vůči outliers
- jediný důležitý parametr je velikost okna

### Graph based segmentation
