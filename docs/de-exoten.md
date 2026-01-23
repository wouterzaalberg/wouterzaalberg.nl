# De Exoten

## Kleuren
- Body: wit `#ffffff`
- Grijze sectie: `#f0f0f0` (vanaf foto 8)
- Intro panel: `#e8e8e8`
- Tekst: `#1a1a1a`

## Foto Formaten
- Groot: 70vh
- Midden: 45vh
- Klein: 35vh
- Extra-klein: 17vh

## Structuur
1. Intro sectie (foto 1 + titel + beverrat + tekstvak)
2. Cluster 1 (foto's 2-7, gap 0.4rem)
3. Hoofdstuk titel
4. Grijze sectie:
   - Wasbeer (foto 8)
   - Beverrat cluster (9-15)
   - Wolhandkrab cluster (16-17)
   - Hemelboom (18-24 + info kaart)
   - Hoornaar boog (25-34)
   - Foto 35 + grid 36-39
   - Rivierkreeft (40 + grid + 41)
5. Vederkruid sectie (42-49)
6. Vlinderstruik (50)
7. Grote Waterteunisbloem (51-53)
8. Watercrassula (54-55)
9. Kleine waterteunisbloem (56 + grid 57-61)
10. Japanse oester (62)
11. Muskusrat sectie (63-70)
12. Einde deel panel
13. End panel (donkergroen #1a3d1a)

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

## Secties met margin-left: 12rem
rivierkreeft, vederkruid, vlinderstruik, waterteunisbloem, watercrassula, kleine-waterteunisbloem, japanse-oester, muskusrat

## Foto's
- Genummerd: 1.jpg - 70.jpg
- Cluster: cluster 1 foto 2-7.jpg
- Kreeft: kreeft1-11.jpg, kreeftcentraal.jpg
- Speciaal: beverrat.jpg, diana airbug a.jpg, info 1-3.jpg, klem.jpg

## Small Desktop (768-1400px)

### Algemeen
- Intro titel: 6rem
- Intro wrapper: 80vh, justify-content: flex-start
- Verticale labels: 1.1rem

### Bijschriften (uniforme styling)
- Padding: 0.5rem
- Border: 1px
- Titel: 0.65rem
- Tekst: 0.65rem, line-height 1.4
- Classes: `.photo-caption-box`, `.caption-box`, `.foto-32-caption`, `.muskusrat-caption-box`

### Desktop Foto Popup
- Klik om te vergroten, loslaten om te sluiten
- Alleen voor foto's kleiner dan 65vh
- Cursor: zoom-in op klikbare foto's

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

### Intro Carousel
- Hoogte: 60vh
- Foto interval: 5 seconden
- Foto's: cluster 1 foto 2-7.jpg
- Bijschriften onder foto (zwart, links uitgelijnd)

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
