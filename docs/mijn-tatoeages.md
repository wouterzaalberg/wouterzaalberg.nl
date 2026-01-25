# Mijn Tatoeages

## Structuur
- Intro: grote foto (1a.jpg) + grijs panel (#2a2a2a) met logo
- Story secties: Portret + Tattoo + Tekstpanel
- Elke sectie: `min-width: 100vw`

## Afmetingen (desktop) - Vloeiende schaling met clamp()
- Foto's: `clamp(45vh, 35vw, 60vh)`
- Intro foto: `clamp(45vh, 38vw, 70vh)`
- Tekstpanel: `clamp(320px, 26vw, 480px)` breed, 100vh hoog
- Intro panel: `clamp(45vh, 38vw, 70vh)` hoog, `clamp(320px, 26vw, 480px)` breed
- Gap foto's: `clamp(0.3rem, 0.5vw, 0.8rem)` (schaalt met schermgrootte)
- Padding-top tekstpanel: `clamp(18vh, 12vw, 21vh)`

## Tekstpanel Uitlijning
- `.story-text-panel`: `padding-top: clamp(18vh, 12vw, 21vh)`
- `.story-text-content`: `padding: 0 2rem 3rem 1.5rem`
- Centrering: `justify-content: center` op `.tattoo-story`

## Elementen
- Persoonsnaam: onder portretfoto, `font-weight: 600`, gekleurd
- Scroll pijl: rechtsonder, geanimeerd
- Logo: `mijn-tattoos/logo.png`, max 250px

## Blur Achtergronden
- Locatie: `mijn-tattoos/Blurs/`
- `.story-text-bg` met `opacity: 0.7`

## Tattoo Teken Effect (Canvas)

### Symbolen
1. Mijnlamp (Davy safety lamp)
2. Hamer en beitel (gekruist)
3. Steenkool (hoekig brok)
4. Schachtbok (A-frame)
5. Penning (rond, nummer "45")

### Technisch
- Canvas: `position: fixed`, `pointer-events: none`, `z-index: 5`
- Foto's en tekstpanelen: `z-index: 10` (canvas blijft achter content)
- Lijn: `rgba(255, 255, 255, 0.12)`, `lineWidth: 0.8`
- Eerste symbool: linksonder (120px, 150px van onder)
- Volgende: random in marges
- Max 15 symbolen, oude verwijderd
- Sparkle effect bij tekenpunt

### Hint Tekst
- Positie: `bottom: 2rem`, `left: 2rem`
- "Terwijl jij de foto's bekijkt, wordt deze pagina ondergetatoeëerd"
- Fade-in na 2s, fade-out na eerste symbool

## Responsive
- **Desktop (≥ 1400px)**: Vloeiende schaling via `clamp()` - foto's naast tekstpanel
- **768-1399px**: Aangepaste layout (zie onder)
- **< 1200px**: Kleinere gap (`0.2rem`)
- **< 1024px**: Kleinere fontsizes in tekstpanel
- **< 767px**: Mobiele layout (zie onder)

## Tablet/Small Desktop (768-1399px)

### Story Layout
- Foto's naast elkaar (horizontaal), tekst eronder
- Beide foto's: `height: 45vh`
- Tekst in 3 kolommen (`column-count: 3`)
- Persoonsnaam verborgen

### Breedte Synchronisatie (JavaScript)
- ResizeObserver meet foto breedtes
- Tekstpanel krijgt `width = foto1 + foto2 + gap (16px)`
- Zorgt dat tekst exact zo breed is als de foto's samen

### CSS Structuur
- `.tattoo-story`: `display: flex`, `flex-wrap: wrap`, `justify-content: center`
- `.story-photo`: `display: block` (geen flex-direction)
- `.story-text-panel`: `flex-basis: 100%` (forceert wrap naar nieuwe regel)
- `.story-text-content`: `column-count: 3`, `column-gap: 2rem`

## Mobiel (< 767px)

### Tattoo Canvas Effect
- Zichtbaar alleen tijdens intro sectie
- Kleinere symbolen: 30-50px (desktop: 55-90px)
- Stopt volledig bij scrollen voorbij intro

### Story Layout
Elke story sectie heeft de volgende structuur:
1. **Portretfoto**: 100vw (volle breedte)
2. **Titel + naam**: h2 (goud) + h3 (wit)
3. **Eerste alinea**: volle breedte (~4 regels)
4. **Tweede alinea + tattoo foto**: tekst links, foto float rechts (45%)
   - Tekst stopt gelijk met onderkant foto (`max-height` via JS)
5. **"Lees meer" knop**: toont overige tekst

### CSS Classes (mobiel)
- `.mobile-story-content`: container voor hele story
- `.mobile-text-with-photo`: container met float foto
- `.float-photo`: tattoo foto (45%, float right)
- `.visible-text`: tekst naast foto
- `.extra-text`: verborgen tekst (getoond bij expanded)
- `.read-more-btn`: toggle knop

### Animaties (mobiel)
- Tekst fade-in: opacity 0→1, translateY 15px→0, 0.6s ease-out
- Extra tekst fade-in bij "Lees meer": 0.5s animatie

### Foto Popup (mobiel)
- Tik op kleine tattoo foto om te vergroten
- Tik ergens om te sluiten
- Alleen voor `.float-photo` afbeeldingen

### Progress Indicator (mobiel)
- Positie: linksonder (1.5rem)
- Toont scroll percentage (0-100%)
