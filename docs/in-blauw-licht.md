# In Blauw Licht

CSS: `css/in-blauw-licht.css`
Foto's: `in-blauw-licht/foto 1.jpg` t/m `foto 32.jpg`

## Kleuren
- Intro panel: `#0a0a0c`
- Lichtgrijs: `#f0f0f0`
- Achtergrond gradient: donker (0-5%) → lichtgrijs (50-100%)

## Z-index Lagen
1. Scroll container: 2
2. Politiestrepen: 50
3. Navigatie: 100

## Hero Sectie
- Foto: 45vw breed, 100vh hoog, `left: 10vw`
- Donkere strip links: 10vw, `#0a0a0c`
- Titel: rechtsonder in foto, `bottom: 15vh`
- Intro panel: 55vw breed
- Zoom: start na 2s, 12s duur, `scale(1.05)`

## Scroll Systeem
- `position: fixed` container
- Foto's gecentreerd bij scrollen
- Formule: `scrollLeft = elementLeft - (viewportWidth - elementWidth) / 2`

## Foto Groottes
- Standaard: 60vh
- `size-full`: 90vh
- Padding: 12rem (responsive: 8rem → 6rem → 2rem)

## Info Buttons
- Donker (#000, 70% opacity), rond
- Caption: `rgba(26, 36, 47, 0.9)`
- Klik buiten foto sluit alle captions

## Toggle Alle Onderschriften
- Positie: `bottom: 2rem`, `left: 2rem`
- Alleen zichtbaar vanaf foto 2
- Toggle tekst wisselt

## Politiestrepen Animatie
Trigger: bij foto 10

### Strepen
- 4 rode (bovenste 50vh)
- 5 blauwe (onderste 50vh)
- Diagonaal -65deg, 15% opacity

### Beweging
- Rood: van -50vh naar +60vh (omlaag)
- Blauw: van +50vh naar -60vh (omhoog)
- Horizontaal: -15vw naar +15vw

## End Panel
- 100vh, achtergrond `#1a2530`

## Responsive
- **< 1024px**: Intro gecentreerd, foto's 50vh/80vh
- **< 767px**: Verticaal scrollen
