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
- Responsive varianten:
  - `.mobile-short`: korte tekst voor mobiel
  - `.desktop-small`: medium tekst voor kleinere desktop
  - `.desktop-large`: volledige tekst voor grote schermen
  - `.desktop-only`: alleen op desktop (alle formaten)

## Scroll Handling (desktop)
- Momentum detection voor trackpad/muis
- Delta threshold: 50px om scroll te triggeren
- Cooldown: 500ms tussen scrolls
- Queue-based: meerdere scrolls worden niet gestapeld
- Map interlude wheel handler: zelfde threshold/momentum logica als hoofdscroll

## Achtergrond Systeem

### Leaflet kaart (door hele pagina)
- CartoDB dark tiles, grayscale
- Positie: `[52.410, 4.78]`, zoom 14
- Dynamische brightness op basis van fotonummer (dag/nacht cyclus):
  - Foto 1-10: donker (nacht)
  - Foto 10-25: geleidelijk lichter (ochtend → middag)
  - Foto 25-30: maximale brightness (middag)
  - Foto 30-46: geleidelijk donkerder (avond → nacht)

### Scheepvaart animatie
- Canvas overlay met bewegende bootjes
- 11 routes gebaseerd op havencoördinaten (WGS84, zelfde als Google Maps)
- Dual-lane systeem: schepen naar zee rechts, schepen van zee links (8px offset)
- Kleur: `rgba(225, 200, 90, 0.4)`
- Collision detection per route
- Opacity varieert mee met dag/nacht cyclus
- Stopt bij end panel

### Statische schepen (aangemeerd)
- 6 stilliggende schepen in havens
- Coördinaten + hoek in graden
- Grotere schepen via `size` parameter

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

## Map Interlude (tussen foto 19 en 21)
- Kaart met fotolocatie markers
- 44 markers (foto 7 en 29 uitgesloten)
- Coördinaten uit Google Maps
- Popup toont alleen "Foto [nummer]" + thumbnail

### Zoom controls
- `+` / `−` knoppen rechtsonder
- `Reset` knop voor originele view
- Dragging ingeschakeld bij interlude
- Automatische reset bij navigatie weg

### Overlay
- Titel: "De Haven in Beeld"
- Subtitel: "Klik op een locatie om de foto te zien"
- Klikbare "Scroll voor meer" knop
- **< 1400px**: links gepositioneerd en links uitgelijnd (voorkomt marker overlap)

## Responsive - Small Desktop (768-1400px)
- Sustainability chart bars: 20px hoogte
- Map overlay: links uitgelijnd

## Responsive - Kleine hoogte (max-height 1000px)
- Sustainability chart bars: 16px hoogte
- Kleinere gaps (0.2rem) en font-size (0.8rem)

## Responsive (< 767px)
- Verticaal scrollen
- Haven animatie behouden in intro
- **Titel**: `font-size: 5.5rem`, `top: 40%`, gele outline
- **Introtekst**: `top: calc(40% + 16rem + 1rem)`, onder de titel, verkorte tekst via `.mobile-short`
- **Map positie**: `[52.39, 4.80]`, zoom 12.5
- **Aparte secties** voor foto 1 en 2 met info buttons en captions
- **Captions**: header 0.85rem, tekst 0.8rem

### Special photo layouts (`.abp-benzolweg`)
Foto's met geel kader boven en onder, onderschrift zichtbaar in onderste kader:
- Foto 5 (Benzolweg)
- Foto 23 (Hemwegcentrale)
- Foto 29 (Neo Orbis)
- Foto 34 (Schrootmetalen terminal)
- Foto 45 (EVOS terminal nacht)

### Diptych pairs (`.abp-diptych`)
Foto paren naast elkaar op mobiel (totaal 95vw, 2px gap):
- Foto 11+12 (Kees-Jan AEB / Afval Energie Bedrijf)
- Foto 21+22 (Frits / Actievoerder)
- Foto 26+27 (Biomassacentrale)

### Tight pairs (`.abp-tight-pair`)
Foto paren met minimale ruimte ertussen (0.5rem):
- Foto 13+14
- Foto 32+33

### Infographics
- **"Een haven ter waarde"**: compacte bars (18px hoogte, 0.4rem gap), bar animaties van 0 naar doelwaarde
- **"Haven in verandering"**: geschaald (donut 85%, chart 90%)

### Text-photo combo ("9 maanden van huis")
- Geel tekstvak met `padding: 3rem 1.5rem 1rem`
- Tekst dicht bij foto via `justify-content: flex-end`
