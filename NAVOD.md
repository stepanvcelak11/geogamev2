# GeoGame — verze 83

## Co nahrát na hosting

Všech osm souborů do kořene repozitáře, vedle sebe (ne do složky):

| Soubor | K čemu |
|---|---|
| `index.html` | hra |
| `sw.js` | offline režim |
| `manifest.webmanifest` | jméno, ikony, celá obrazovka |
| `icon-192.png`, `icon-512.png` | Android a Google Play |
| `icon-512-maskable.png` | adaptivní tvar ikony |
| `apple-touch-icon-180.png` | ikona pro iOS plochu |
| `icon.svg` | vektorová záloha |

**GitHub → repozitář → Add file → Upload files → vybrat všech osm → Commit changes.**
Poté Settings → Pages → větev `main`, složka `/ (root)` → Save.
Za minutu poběží na `https://tvoje-jmeno.github.io/nazev-repa/`.
V Chromu pak tři tečky → **Přidat na plochu**.

## Aktualizace

Nahraj nový `index.html` a `sw.js` se stejnými názvy. Nová verze se stáhne při dalším
spuštění s internetem a projeví se po zavření a otevření hry. Ručně:
**Nastavení → Zkontrolovat aktualizaci**. Číslo verze je dole pod mapou světa
a v hlavičce Nastavení.

Číslo verze se od verze 82 píše na **jediné místo** — `const VERZE=83;` v `index.html`.
Odtud se rozsype do stránky i do adresy, kterou se registruje `sw.js`. Jinam se nesahá.

## Bez hostingu

`geogame-v83-jediny-soubor.html` stáhni do telefonu a otevři v Chromu.
Funguje offline, jen se sám neaktualizuje.

Od verze 82 je tenhle soubor **přesná kopie `index.html`**. Hra si sama pozná, že běží
ze staženého souboru, a manifest si přepíše. Novou verzi tedy vyrobíš prostým zkopírováním
a není co udržovat dvakrát:

```
copy index.html geogame-v83-jediny-soubor.html
```

## Záloha postupu

**Nastavení → Záloha postupu → ZKOPÍROVAT**, v cílové verzi **Obnovit ze zálohy**.
Potřeba při přechodu mezi staženým souborem a hostovanou adresou nebo mezi zařízeními.

Od verze 82 si hra sama drží záchrannou kopii postupu:

- Když se hlavní uložení poškodí, hra ho **nepřepíše** — načte kopii a v Nastavení
  nabídne, co dál (**Nečitelný uložený postup**).
- Když se ukládání nedaří, protože v zařízení došlo místo, řekne to hláškou
  místo tichého selhání.
- Po vložení zálohy jde vrátit předchozí stav: **Nastavení → Vrátit obnovu**.

## Co je nového ve verzi 83

- **Stavět jde na každé pole, které sousedí s trasou** — i rohem. Konec náhodného
  odkrývání: místo šesti políček jich je podle území 28 až 69 a vytyčený pás je
  na desce vidět (oranžová přerušovaná hranice, mezníky).
- Slučování a terénní služby už neotvírají pole, ale posilují **četu** (+1 stanovisko).
  V HUDu je proto jedno číslo: `5/12 stanovisek`.
- Nový vzhled: všechno je odlité z plastu, pozadí je měřická deska, nadpisy mají
  ražený obrys, značky přístrojů se kreslí ve třech průchodech.
- Čitelnost: 47 míst mělo text v barvě s kontrastem pod mezí (rozpočet 1,4 : 1).
  Teď je pod mezí nula, měřeno na skutečně vykreslené hře ve všech třech motivech.

## Co je ve hře

12 území s vlastními bossy · 21 přístrojů · pátá mistrovská řada · 13 druhů vlivů,
elity a pravidla vln · vývojový strom 3 patra × 8 cest s možností přeladit ·
6 režimů · obchod s denní nabídkou · sezónní cesta · trofejní cesta · 25 úspěchů ·
sbírka karet · laboratoř · příslušenství · encyklopedie · zkouška z geodézie
(36 otázek) · zakázka dne · terénní služby · offline provoz
