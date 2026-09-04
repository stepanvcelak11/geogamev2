# Koordinace mezi dvěma AI — kdo zvedá verzi (4. 9. 2026)

Na `index.html` pracovaly dnes dvě session naráz. Tenhle soubor je tu proto, aby
**číslo verze nezvedly obě** — to se u tohohle uživatele už jednou stalo a skončilo
to tím, že dvě různé verze nesly totéž číslo.

Na hosting se nahrává **osm souborů** podle `NAVOD.md`. Tenhle soubor mezi ně
nepatří, je jen pracovní.

## Kdo co udělal

**Session A (vizuál, běží dál):** zrušená lišta beden, tlačítko *Ukončit* přesunuté
do záložek, přejmenované panely (Karty / Síť / Služby) s úvodními odstavci,
zrušené popisky sloupců a řádků desky, nové proměnné rádiusů, světlejší ikony
v dolní liště, posunutý náhled příští vlny.

**Session B (herní logika, hotovo 4. 9.):** čtyři změny, žádný zásah do CSS ani HTML —
právě proto, aby si strany nepřepsaly práci.

1. **Ztráta přesnosti je plynulá.** Průnik k nulovému bodu nestojí paušál, ale svůj
   podíl na síle celé vlny. Nová funkce `waveLossMax()` = `min(85, 30+2,2×etapa)`
   je strop toho, kolik smí sebrat **jedna etapa**. Nová pole `S.waveDm` a
   `S.waveLoss` se nastavují v `startWave()`.
2. **Mírnější křivka odolnosti vln.** `waveScale()`: lineární člen 0,30 → **0,40**,
   exponent 1,175 → **1,13**.
3. **Strop délky vlny.** V `startWave()` konstanta `SPAWN_STROP=32` (sekund na
   vysypání vlny; zkrátí se jen rozestupy, počet ani síla vlivů se nemění).
4. **Nastavení → Omezit pohyb.** `SAVE.opts.lowmo`, funkce `lowMotion()` a
   `prefersLowMotion()`; pojistky v `punch()`, na dvou místech s `S.shake`,
   u kreslení částic a u titulní animace. Výchozí hodnota se bere ze systémového
   nastavení telefonu.

Obtížnost v téhle podobě **uživatel schválil**, takže se s ní nehýbe.
Naměřená čísla a zbývající návrhy jsou v `..\geogame-navrhy-v83.md`.

## Dohoda o vydání — POTVRZENO oběma stranami 4. 9.

**Vydání a číslo 84 si vzala session A** (ta, co dělá vizuál). Session B zůstává
na 83 a jednosouborovou kopii nesynchronizuje. Session A také nezávisle ověřila,
že se obě sady změn v `index.html` složily správně a nic se nepřepsalo.

Rozdělení práce, na kterém se strany domluvily:

- **CSS je celé session A**, dokud neřekne, že je venku (běží velká přestavba
  povrchu: `--ink2` na tmavý neutrál, nové `--sur*`, přepsané `--r1..--r4`
  a `--w1..--w4`, ~200 nových řádků na konci `<style>`).
- **Body 6–8** (velikost písma, malé telefony, široké obrazovky) si nechává
  session B, ale začne až po výslovném "jsem venku" od session A.
- Session B **nesáhá** do `loop()`, `buildBG()`, `glyph()`/`glyphKresli()`,
  `drawWorld()` a `newRun()` — session A tam má rozdělané odkrývání políček
  a kresbu desky. Zbytek herní logiky je session B.

### Původní návrh (pro záznam)

- Session B **nechala `const VERZE=83`** a **nesynchronizovala**
  `geogame-v83-jediny-soubor.html`.
- **Vydání si bere ten, kdo dodělá jako poslední** (podle stavu k 4. 9. session A).
  Ten udělá tohle:
  1. `const VERZE=84` v `index.html` (jedno místo, odtud se to rozsype)
  2. `copy index.html geogame-v84-jediny-soubor.html` (a starý v83 smazat)
  3. text „Co je nového“ v `renderOpts` (`it.act==='news'`) přepsat tak, aby pokrýval
     **obě** sady změn
  4. `NAVOD.md` — čísla verze a sekce „Co je nového ve verzi“

Do „Co je nového“ patří za session B tyhle tři řádky:

- Přesnost teď klesá plynule podle toho, kolik vlny projde — jedna etapa nesebere
  všechno, takže je čas to spravit
- Vlny nerostou na konci tak strmě a nejdelší etapy jsou kratší
- Nastavení → Omezit pohyb vypne třes obrazovky, záblesky a odletující částice

## Co ještě není hotové

Body **6, 7 a 8** z `geogame-navrhy-v83.md` — velikost písma (374 kusů textu pod
12 px, nejmenší 7,5 px), malé telefony (políčko desky 22–30 px proti doporučeným
44) a rozložení pro široké obrazovky (na notebooku zabírá deska 12 % plochy).
Všechno tři jsou **čistě CSS**, a proto je session B nechala session A.
