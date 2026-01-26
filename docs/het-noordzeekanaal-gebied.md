# Het Noordzeekanaal Gebied

## Basis
- Achtergrond: `#f5f5f5`
- 17 foto's op 70vh
- Gap: 12rem (responsive: `clamp(4rem, 8vw, 12rem)`)

## Volgorde
Foto 2 → Intro panel → Foto 1 → Foto paar 3+4 → Foto 5 → etc.

## Grote Foto's (90vh)
- Foto 5
- Foto 15

## Foto Paren
- 3+4
- 6+7
- 10+11
- Gap binnen paar: 0.5rem
- Scrollen als één geheel
- Mobiel: beide foto's eerst, dan caption eronder (`.pair-caption`)

## Bijschriften (info button)
- Toggle via "i" button (`.nzkg-info-btn`) - niet hover
- Button: rechtsonder op foto, blauw accent `#2d6a8a`
- Bij foto paren: button op rechter foto
- Klik opent caption, andere captions sluiten automatisch
- Klik buiten caption sluit alles
- Mobiel: buttons verborgen, captions altijd zichtbaar onder foto

### Caption styling
- Positie: `bottom: 2rem`, gecentreerd
- Achtergrond: `rgba(0, 0, 0, 0.7)`
- Padding: `1rem 1.5rem`
- Max-width: 600px

### Format
- **caption-main**: wit, 0.95rem (naam + functie)
- **caption-detail**: 85% wit, 0.8rem (beschrijving)
- **caption-location**: 70% wit, 0.75rem, italic

## Leaflet Kaart
- Kader (`.nzkg-map-insert`): 100vh, blauw gradient
- Kaart (`.nzkg-map-inner`): 70vh, verticaal gecentreerd met titel
- Scroll fix: `margin-top: -80px`, `padding-top/bottom: calc(2rem + 80px)`
- Zoom levels: 10 (mobiel) / 11 (desktop klein) / 12 (desktop groot)
- Positie: center `[52.45, 4.75]`

## Responsive Breakpoints
- **Desktop groot (> 1400px)**: originele styling
- **Desktop klein (768-1400px)**:
  - Gap: `clamp(4rem, 8vw, 12rem)`
  - Titel panel: `max-width: clamp(300px, 45vw, 500px)`
  - Titel: `font-size: clamp(2.5rem, 5vw, 4rem)`
  - Subtitle: `max-width: clamp(250px, 40vw, 400px)`
  - Kaart: `min-width: 50vw`, zoom level 11
  - End panel: `height: auto`, `min-height: 70vh`
- **Mobiel (< 767px)**: verticaal scrollen
  - Titel/subtitle fade-in: opacity 0→1, translateY 20px→0, 0.8s ease-out
  - Caption fade-in: opacity 0→1, translateY 15px→0, 0.6s ease-out
  - Captions onder foto's met transparante achtergrond

## End Panel
- Achtergrond: `#1a1a1a`
- Hoogte: 100vh
- Breedte: 33vw, max 600px, min 300px
- Scroll fix: `margin-top: -80px`, `padding-top: 80px`

## Lazy Loading
- Eerste 6 foto's: `loading="eager"`
- Rest: `loading="lazy"` met `rootMargin: 500px`

## Scroll
- Titel panel (`.nzkg-title-panel`) is geen scroll-stop
- Scrollen gaat direct van eerste foto naar tweede foto
- Zie `docs/horizontal-scroll.md` voor de verbeterde scroll logica
