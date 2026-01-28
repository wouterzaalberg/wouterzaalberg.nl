# De Exoten

## Kleuren
- Body: wit `#ffffff`
- Grijze sectie: `#f0f0f0` (vanaf foto 8)
- Intro panel: `#e8e8e8`
- Tekst: `#1a1a1a`
- Titel letters (natuur palette):
  - D: bosgroen `#4a7c59`
  - e: oker `#8b6914`
  - E: donkergroen `#2d5a27`
  - x: olijfgroen `#6b8e23`
  - o: bruin `#8b4513`
  - t: petrol `#3d7a8c`
  - e: grasgroen `#5c8a4d`
  - n: taupe `#7a6b4e`

## Foto Formaten
- Groot: 70vh
- Midden: 45vh
- Klein: 35vh
- Extra-klein: 17vh

## Grid Systeem

### Basis
- Grid: **48 kolommen × 24 rijen** (dubbele precisie)
- Afmetingen: 100vw × 70vh
- Geen externe CSS laden (styles.css overschrijft grid)
- Foto's gebruiken `max-width: 100%; max-height: 100%;` (niet `width/height: 100%`)

### Foto Verhoudingen
Alle foto's zijn 4:3 (liggend) of 3:4 (staand).

**Berekening formules** (gebaseerd op cell aspect ratio ~1.27 op 16:9 scherm):
- **Liggend (4:3)**: breedte = hoogte × 1.33 / 1.27 ≈ hoogte × 1.05
- **Staand (3:4)**: breedte = hoogte × 0.75 / 1.27 ≈ hoogte × 0.59

**Voorbeelden:**
- Liggend, 12 rijen hoog → 12 × 1.05 ≈ 13 kolommen breed
- Staand, 15 rijen hoog → 15 × 0.59 ≈ 9 kolommen breed

### Werkwijze Foto's Plaatsen
1. Toon niet-geplaatste foto's als kleine thumbnails linksboven (2×2 cellen per foto)
2. Gebruiker geeft aan: fotonummer, kolom.rij start - kolom.rij eind, liggend/staand
3. Claude berekent ontbrekende dimensie automatisch
4. Verplaats foto van palet naar definitieve positie
5. Herhaal tot alle foto's geplaatst zijn

### Debug Modus
- `debug-mode` class op grid toont coördinaten
- `data-file` attribuut op foto's toont bestandsnamen
- Na voltooiing: verwijder `debug-mode` class van alle grids

### Uitlijning binnen cel
Foto's kunnen binnen hun cel uitgelijnd worden:
```css
.foto-X {
    display: flex;
    justify-content: flex-end;  /* rechts */
    align-items: center;
}
```

### CSS Syntax
```css
.foto-X { grid-column: START / EIND+1; grid-row: START / EIND+1; }
```
Let op: CSS grid gebruikt lijnnummers, dus kolom 3-9 wordt `grid-column: 3 / 10`

### Voorbeeld
Foto op kolom 5-19 (14 kolommen), onderkant rij 24:
- Liggend (4:3): 14 rijen → `grid-row: 11 / 25`
- Staand (3:4): 24 rijen → `grid-row: 1 / 25`

## Pagina Structuur

### Navigatie
- `horizontal-nav` linksboven (via styles.css)
- Terug link + paginanaam "De Exoten"
- z-index: 200 (boven intro grid)

### Opbouw
- **Intro**: Fullscreen kolom-grid + scroll transitie
- **Clusters**: Elk cluster = één 48×24 grid (100vw × 70vh)
- **Single photos**: Losse foto's van 70vh met caption ernaast
- **Hoofdstuk titels**: Buiten grid, tussen secties
- **Ruimte tussen secties**: gap 12rem in horizontal-scroll-content

### Single Photo Section Template
Voor losse grote foto's (70vh) met caption:
```html
<div class="single-photo-section">
    <div class="labeled-photo">
        <span class="vertical-label">Label<span class="accent">x</span>yz</span>
        <img src="de-exoten/X.jpg" alt="..." loading="lazy">
    </div>
    <div class="photo-caption-box">
        <h4 class="caption-title">Titel</h4>
        <p class="caption-text">Tekst...</p>
    </div>
</div>
```
- Foto: 70vh hoog, breedte automatisch
- Caption: 13vw breed (min 150px, max 280px)
- Gap foto-caption: 0.8rem
- Caption uitgelijnd op onderkant foto
- **Zoom effect**: foto zoomt naar scale 1.05 over 8s wanneer in beeld (overflow: hidden)

### Zoom Effect
- Alle single-photo-sections zoomen automatisch bij in beeld komen
- IntersectionObserver met threshold 0.3
- Transition: `transform 8s ease-out`, scale 1 → 1.05
- Grid foto's kunnen ook zoomen via `.zoomable` class:
```html
<div class="photo-item foto-35 zoomable">...</div>
```

### Caption Animaties
- **Fade-in**: alle captions faden in met lichte opwaartse beweging
- Transition: `opacity 0.6s ease-out, transform 0.6s ease-out`
- IntersectionObserver met threshold 0.2
- **Expand classes** voor overflow richting:
  - `.expand-up`: breidt naar boven uit
  - `.expand-down`: breidt naar beneden uit
  - `.expand-left`: breidt naar links uit
  - `.expand-right`: breidt naar rechts uit
- **Meerdere alinea's**: `p + p` krijgt `margin-top: 0.8em`

### Tekstkaders (Responsive)
```css
padding: clamp(1rem, 2vw, 1.5rem);
font-size: clamp(0.7rem, 1vw, 0.85rem);
border: 2px solid #a8c8e8;
```

### Workflow per cluster
1. Laad alle foto's van cluster als thumbnails linksboven (2×2 cellen)
2. Gebruiker geeft coördinaten per foto
3. Plaats foto's één voor één
4. Voeg bijschriften toe als grid-items
5. Voeg verticale labels toe met animatie
6. Test en pas aan
7. Ga naar volgende cluster

### Debug modus
- Tijdens bouwen: debug aan (coördinaten zichtbaar)
- Na voltooiing: debug uit (class verwijderen)

### Secties
1. Intro (bestaand, niet aanpassen)
2. Beverrat cluster (foto 8-15 + diana airbug)
3. Wolhandkrab cluster (16-17)
4. Hemelboom cluster (18-24 + info)
5. Hoornaar cluster (25-34)
6. Foto 35 + grid 36-39
7. Rivierkreeft cluster (40 + grid + 41)
8. Vederkruid (42-49)
9. Vlinderstruik (50)
10. Grote Waterteunisbloem (51-53)
11. Watercrassula (54-55)
12. Kleine waterteunisbloem (56 + 57-61)
13. Japanse oester (62)
14. Muskusrat (63-70)
15. End panel

## Intro Grid (Desktop)

### Kolom-gebaseerde Grid
- 5 kolommen × 4 rijen, 100vw × 100vh, fixed position
- Elke kolom is een flex container met 4 cellen
- Lege cellen in rij 2, kolommen 2-4 (witte ruimte voor titel)
- Foto's swappen random elke 2 seconden
- Link naar `css/styles.css` voor fonts en nav styling

### Titel Animatie
- "De Exoten" gecentreerd in witte ruimte (rij 2, kolommen 2-4)
- Elke letter heeft eigen kleur (natuur palette)
- Letters faden random in
- Start na 1.5 seconden, 150-250ms tussen letters
- Titel grootte: `clamp(5rem, 12vw, 12rem)`
- **"t" in cursief**: Minion Pro font, italic, met aangepaste margins (`margin-left: -0.12em`, `margin-right: 0.18em`)

### Scroll Transitie (5 stappen)
1. **Scroll 1-5**: Kolommen scrollen weg
   - Kolommen 1, 3, 5: omhoog (translateY negatief)
   - Kolommen 2, 4: omlaag (translateY positief)
2. **Na 3 scrolls (60%)**: Introtekst verschijnt onder titel
3. **Na 3 scrolls**: Stierkikker fadet in (z-index: 150)
4. **Na 5 scrolls**: Intro wordt scrollbaar (position: absolute)
5. **Horizontaal scrollen**: Intro scrollt mee naar links

### Introtekst Panel
- Positie: `top: 70%` van titel wrapper
- Breedte: `min-width: 600px`, `max-width: 32vw`
- Transparante achtergrond
- Font: Scala Sans (niet cursief, `font-style: normal`)

### Stierkikker
- Eerste item na intro in horizontal scroll
- `margin-left: -20vw` (dichter bij intro)
- `margin-right: 12rem` (afstand tot deel 1)
- Fadet in tegelijk met introtekst
- Wanneer visible: `z-index: 150` (boven intro grid)

## Structuur
1. Intro grid sectie (fullscreen grid + scroll transitie)
2. Hoofdstuk titel
3. Grijze sectie:
   - Wasbeer (foto 8)
   - Beverrat cluster (9-15)
   - Wolhandkrab cluster (16-17)
   - Hemelboom (18-24 + info kaart)
   - Hoornaar boog (25-34)
   - Foto 35 + grid 36-39
   - Rivierkreeft (40 + grid + 41)
4. Vederkruid sectie (42-49)
5. Vlinderstruik (50)
6. Grote Waterteunisbloem (51-53)
7. Watercrassula (54-55)
8. Kleine waterteunisbloem (56 + grid 57-61)
9. Japanse oester (62)
10. Muskusrat sectie (63-70)
11. Einde deel panel
12. End panel (donkergroen #1a3d1a)

## Kreeft Grid
- Cirkelvorm in 48×24 grid
- Rij 1 (boven, 4 foto's): kolom 14-34, rij 4-9
- Rij 2 (midden, 5 foto's): kolom 10-38, rij 9-14 — kreeftcentraal breder (8 kol)
- Rij 3 (onder, 3 foto's): kolom 16-34, rij 14-19
- Foto's sluiten verticaal aan (geen gaps)

## Beverrat Cluster
- Kolom 2-3: foto 9+10 boven, diana airbug + foto 11 onder
- Kolom 4-5: foto 12 boven, foto 13+14 onder
- Kolom 6: tekstkader + foto 15

## Muskusrat Sectie
- Kolom 1: foto 63 (70vh) + label
- Kolom 2: foto 64 (18vh) + foto 65 (32vh), margin-top 8vh
- Kolom 3: foto 66 + 67 (28vh) + klem.jpg
- Apart grid voor foto 68-70

## Verticale Labels
- Cursieve accent letter: `<span class="accent">t</span>`
- **Meerdere woorden**: `<br>` na elk woord (bijv. `Chin<span class="accent">e</span>se<br>Wolhandkrab`)
- Voorbeelden: Wa**t**erteunisbloem, Vlinder**s**truik, Amerikaanse rivier**k**reeft
- **Letter animatie**: letters faden in willekeurige volgorde in wanneer label in beeld scrollt
- **Titel overlap fade**: labels faden uit wanneer ze de "De Exoten" titel kruisen

## Secties met margin-left: 12rem
rivierkreeft, vederkruid, vlinderstruik, waterteunisbloem, watercrassula, kleine-waterteunisbloem, japanse-oester, muskusrat

## Foto's
- Genummerd: 1.jpg - 70.jpg
- Cluster: cluster 1 foto 2-7.jpg
- Kreeft: kreeft1-11.jpg, kreeftcentraal.jpg
- Speciaal: beverrat.jpg, diana airbug a.jpg, info 1-3.jpg, klem.jpg

## Small Desktop (768-1400px)

### Intro Responsive
- **1600px**: Tekst panel max-width: 38vw
- **1400px**: Titel clamp(4rem, 10vw, 10rem), tekst panel 42vw
- **1100px**: Titel clamp(3rem, 9vw, 8rem), wrapper 70vw, tekst 50vw
- **900px**: Titel clamp(2.5rem, 8vw, 6rem), wrapper 80vw, tekst 60vw
- **768px**: Titel clamp(2rem, 7vw, 4rem), wrapper 90vw, tekst 75vw

### Algemeen
- Verticale labels: 1.1rem

### Bijschriften (uniforme styling)
- Padding: 0.5rem
- Border: 1px
- Titel: 0.65rem
- Tekst: 0.65rem, line-height 1.4
- Classes: alle caption boxes uniform gestyled
- **Responsive breedtes met clamp()**: bijv. `clamp(220px, 22vw, 320px)`

### Scroll
- Simpele horizontale scroll (geen snap)
- `scroll-snap-type: none`

### Desktop Foto Popup
- Klik om te vergroten, loslaten om te sluiten
- Alleen voor foto's kleiner dan 65vh
- Cursor: zoom-in op klikbare foto's
- **Uitgezonderd**: intro grid foto's

### Hoornaar Cluster
- "Op zoek in Zeeland" tekstkader: 100% breed
- Foto 23 verborgen
- Hoornaar boog foto's verkleind (20-22vh)

### Rivierkreeft Sectie
- Foto 40: single-photo-section (70vh) met caption
- Kreeft grid: 12 foto's in cirkelvorm
- Foto 41: single-photo-section (70vh) zonder caption

### End Panel
- Hoogte: 100vh
- Breedte: calc(100vw - 100px)
- align-self: flex-start (voorkomt vertical shift)

## Mobiel

### Titel Overlay
- 10 rijen herhaalde "De Exoten" tekst
- Letters: doorschijnend wit (15% opacity)
- Font: Scala Sans, 4.5rem, bold
- Rijen met variërende margin-left (-10% tot -55%)

### Gekleurde Letters Animatie
- Spelt "De Exoten" met 8 gekleurde letters
- Letters verschijnen na elkaar (350ms interval)
- Kleurcyclus animatie (8s):
  - Bosgroen: `#5a7a4a`
  - Grasgroen: `#6b8b5a`
  - Hemelsblauw: `#7a9db8`
  - Olijf/bruin: `#8a7a5a`
- Elke letter heeft andere animation-delay

### Bewegende Rijen
- Oneven rijen bewegen naar rechts
- Even rijen bewegen naar links
- Langzame animatie: 20s cyclus, -5% tot +5%

### Intro Carousel
- 4 foto's uit `de-exoten/carousel/`
- Interval: 4 seconden per foto
- Lichte zoom op actieve foto (scale 1 → 1.05)
- Hoogte: 68vh

### Witte Tussenstand
- Na alle foto's: witte achtergrond (10 seconden)
- Gekleurde letters faden uit
- "De Exoten" fadet in gecentreerd (4.5rem)
- Daarna: carousel herstart, letter animatie reset
