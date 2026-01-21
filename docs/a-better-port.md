# A Better Port

CSS: `css/a-better-port.css`

## Kleuren
- Lichte achtergrond: `#e8e4df`
- Geel accent: `#e1c85a` (veiligheidshesje)
- Geel transparant: `rgba(225, 200, 90, 0.85)`
- Donker overlay: `rgba(30, 40, 50, 0.85)`

## Intro Sectie (3 states)
- **State 0**: Tekstpaneel + gele titel "A BETTER PORT"
- **State 1**: Foto 1 gecentreerd (80vh), gele achtergrond
- **State 2**: Foto 2 schermvullend (100vh)
- Transities: 0.8s ease fade

### Hero titel
- Transparant met gele outline (`-webkit-text-stroke: 2px`)
- Links van foto/panel, rechts uitgelijnd
- `bottom: 11vh`

### Intro tekst
- Breedte: zelfde als foto 1 (via JS)
- Achtergrond: `rgba(255, 255, 255, 0.35)`
- Onderkant op 10vh van viewport

## Achtergrond Systeem

### Leaflet kaart (intro)
- CartoDB dark tiles, grayscale
- Positie: `[52.413, 4.82]`, zoom 13
- Non-interactief

### Scheepvaart animatie
- Canvas overlay met bewegende bootjes
- 12 routes gebaseerd op havencoördinaten
- Kleur: `rgba(225, 200, 90, 0.4)`
- Collision detection per route
- Stopt bij state 2

### Rotating background (na intro)
- 3 achtergrondafbeeldingen, 15% opacity
- Breedte: 300% voor scroll effect

## Dark Overlay
- Foto 1-2: opacity 0.8
- Foto 3-19: 0.8 → 0 (lichter)
- Foto 19-41: opacity 0
- Foto 42-44: 0 → 0.8 (donkerder)
- Foto 44+: opacity 0.8

## Foto Layout
- Standaard: 70vh
- `size-full`: 100vh
- Padding: 10rem tussen foto's
- Foto paren: 3+4, 11+12, 13+14, 15+16, 21+22, 32+33, 38+39

## Info Buttons
- Wit, rond, italic "i"
- Rechts onderaan foto
- Één caption tegelijk open

## Quote Panels
- Gele achtergrond, 100vw x 100vh
- Reveal effect via IntersectionObserver
- Decoratieve lijnen boven/onder

## Infographic Panels

### Panel 1 (na foto 6)
- Achtergrond: olietanker.jpg
- "Een haven ter waarde van 4,4 miljard euro"
- Horizontale staafgrafiek

### Panel 2 (na foto 24)
- "Een haven in verandering"
- Donut charts: opslagcapaciteit
- Progress bars: zonnepanelen

## Text-Photo Combo (foto 17)
- 50% geel tekstvak, 50% foto
- Titel: "9 maanden van huis"
- Zoom effect op foto

## Responsive (< 767px)
- Verticaal scrollen
- Haven animatie behouden in intro
- Titel: `left: calc(5vw + 1.25rem)`, `bottom: 38%`
- Verkorte introtekst via `.mobile-short`
- Aparte secties voor foto 1 en 2
- Map positie: `[52.39, 4.85]`
