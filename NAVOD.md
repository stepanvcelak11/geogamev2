# GeoGame — verze 85

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

Číslo verze se od verze 82 píše na **jediné místo** — `const VERZE=85;` v `index.html`.
Odtud se rozsype do stránky i do adresy, kterou se registruje `sw.js`. Jinam se nesahá.

## Bez hostingu

`geogame-v85-jediny-soubor.html` stáhni do telefonu a otevři v Chromu.
Funguje offline, jen se sám neaktualizuje.

Od verze 82 je tenhle soubor **přesná kopie `index.html`**. Hra si sama pozná, že běží
ze staženého souboru, a manifest si přepíše. Novou verzi tedy vyrobíš prostým zkopírováním
a není co udržovat dvakrát:

```
copy index.html geogame-v85-jediny-soubor.html
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

## Co je nového ve verzi 86

- **Hrací deska je velká.** Nápověda tutoriálu a lišta vybraného stanoviska
  si ukrajovaly z výšky desky a políčko kvůli nim spadlo ze 42 na 25 px.
  Nápověda teď desku překrývá stejně jako panel a pruh pro lištu se drží,
  jen když ta lišta opravdu je.
- **Terč na konci trasy má popisek NULOVÝ BOD**, začátek trasy **ODSUD**.
  Byla to jediná věc na desce, o kterou jde prohra, a neměla vysvětlení.
- **Měřická čísla stanic z cesty zmizela.** Byla to ozdoba, ale hráč je četl
  jako údaj; jedno padalo těsně vedle terče a vypadalo jako odznak na něm.
- **Výběr měřické metody ukáže všech sedm.** Dřív jen ty, které hráč umí —
  o zbylých pěti se nedalo dozvědět, že existují. Zamčené jsou šedé a je
  u nich napsáno, ve které oblasti a za kolik pohárů se odemknou.
- **Okno území zhublo.** Mělo čtyři vždy otevřené sekce a pět velkých tlačítek
  pod sebou; hlavní akce byla až čtvrtá. Teď je nahoře sestava a hned pod ní
  start, zadání a cíle se rozbalují jedním řádkem a další režimy mají
  vlastní blok.

## Co je nového ve verzi 85

- **Mezníky** — druhá měna. Nedá se koupit ani nepadá z beden: dostaneš ji za tři
  hvězdy na území, za splněné denní úkoly, za zkoušku na plný počet a se 6% šancí
  ji najdeš po dokončeném měření. Kupuje **čas a vzhled, nikdy sílu** — síla se dál
  platí výzkumem, jinak by se ekonomika Laborky rozpadla.
- **Vzhledy přístrojů**: šest materiálů (tovární, terénní oranžová, noční šedá,
  muzejní mosaz, karbon, kamenný mezník). Mění barvu těla, obrysu i lesku — proto
  vypadají jako jiný odlitek, ne jako přebarvená ikona. Žádný obrázek navíc.
- V obchodě je záložka **Za mezníky**: balíček 200 výzkumu za 40, nejvýš jednou denně.
- **Sbírka je rovnou na stránce Vybavení**, hned pod sestavou. Samostatná obrazovka
  i tlačítko, které ji otvíralo, zmizely.
- **Stránky se jmenují podle toho, proč tam chodíš**: Obchod · Vybavení · Terén ·
  Laborka · Kariéra. Trvalá vylepšení se přestěhovala do Laborky.
- **Mapa světa je první věc na Terénu.**
- **Profil ožil** — medaile, hodnost a tři údaje v pilulkách místo jednoho řádku.
- Velikost písma jde zvětšit o 15 nebo 30 %, deska má tři opravdové stupně velikosti
  a na notebooku se ovládání složí vedle desky.

## Co je nového ve verzi 84

- **Tmavý povrch místo světlého.** Změřeno: syté barvy zabíraly 53 % obrazovky
  a na jedné stránce jich soupeřilo šest až sedm. Teď je světlých ploch 16 % a barva
  zbyla tam, kam patří — na tlačítko, na měnu a na vzácnost.
- **Spodní lišta**: ikony měly kontrast 2,6 : 1 (v kontrastním motivu 1,7 : 1), protože
  dvě pravidla se stejnou specificitou si přebíjela barvu. Vybraná záložka teď vystoupí
  nad lištu.
- **Mapa světa** je o dvě třetiny větší, jde ke krajům a je v soumraku. Zamčená území
  byla dřív světlejší než okolí, takže oko tahalo tam, kam se klepnout nedá. Jméno se
  ukazuje jen u území, kam se dá jít — dvanáct cedulek se nevešlo a překrývaly se.
- **Karty v obchodě**: ikona přístroje ležela na pozadí téže barvy, tedy kontrast
  1,00 : 1. Teď svítí z tmavého kotouče.
- **Bedny jsou jen ve Skladu** a odpočet u nich běží (dřív se překresloval jen ten
  na stránce Bitva, proto ve Skladu stál).
- Ukončit měření se přesunulo z křížku do nabídky pod ☰; z hrací plochy zmizely
  souřadnice a nápis, které v ní ležely.
- Obtížnost: přesnost klesá plynule podle toho, kolik vlny projde, vlny nerostou
  na konci tak strmě a v Nastavení přibylo **Omezit pohyb**.

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
