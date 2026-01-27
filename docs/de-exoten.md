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

## Intro Grid (Desktop)

### Fullscreen Grid
- 5x4 foto grid, 100vw x 100vh, fixed position
- Witte overlay (15% opacity) over foto's
- Geen click-to-zoom op grid foto's
- Foto's swappen random elke 2 seconden (alleen src swap, geen beweging)

### Titel Animatie
- "De Exoten" gecentreerd over grid
- Elke letter heeft eigen kleur (natuur palette)
- Letters faden random in (zoals vertical labels)
- Start na 1.5 seconden, 150-250ms tussen letters
- Transition: 0.6s ease-out

### Scroll Transitie
- Bij scrollen: grid fadet uit, content fadet in
- 5 scroll-stappen voor volledige transitie
- Terugscroll brengt grid terug
- 600ms delay na fade voordat horizontaal scrollen mag

### Intro Content (achter grid)
- Gecentreerde wrapper met tekst + foto
- **Tekstkader**: 25vw (min 280px), 60vh, `#e8e8e8`
- **Koptekst**: "Er woedt een onzichtbare oorlog in Nederland" (h2, small caps)
- **Stierkikker foto**: 60vh
- **Bijschrift**: rechts van foto, uitgelijnd op onderkant, 180px breed
- Gap tussen tekst en foto: 2rem

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
- 3 rijen, gap 0.4rem, 70vh hoog
- Groottes: xs (12vh), sm (15vh), md (16.5vh), lg (18vh)
- Foto's 3:4 verhouding

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
- Voorbeelden: Wa**t**erteunisbloem, Vlinder**s**truik
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

### Intro
- Tekstkader: 22vw (min 220px), 50vh
- Koptekst h2: 1.1rem
- Paragrafen: 0.75rem
- Foto: 50vh
- Bijschrift: 150px, 0.65rem tekst
- Gap: 1.5rem

### Algemeen
- Intro titel: clamp(3rem, 8vw, 8rem)
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
- Gecentreerd met margin-left: 8rem
- Caption margin-top: 10vh

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
