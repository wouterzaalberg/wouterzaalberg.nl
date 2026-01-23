# In Blauw Licht

CSS: `css/in-blauw-licht.css`
Foto's: `in-blauw-licht/foto 1.jpg` t/m `foto 32.jpg`

## Kleuren
- Intro panel: `#0d1418`
- Achtergrond: `#f0f0f0`
- Insert achtergrond: `#1a3a5c` (politieblauw)
- Highlight rood: `#c83232`

## Z-index Lagen
1. Politiestrepen: 1
2. Scroll container: 2
3. Foto blocks/Hero: 2
4. Navigatie: 100

## Hero Sectie
- Foto: 45vw breed, 100vh hoog, `left: 10vw`
- Donkere strip links: 10vw, `#0d1418`
- Titel: rechtsonder in foto, `bottom: 15vh`
- Intro panel: 55vw breed, fadet uit bij scroll
- Zoom: start na 2s, 12s duur, `scale(1.05)`

### Titel Blauw Licht Animatie
- Blauw licht sweep over letters (background-clip: text)
- Kleur: `#4a7fd4`
- Duur: 18s cyclus, sweep ~6s, pauze ~12s
- Start na 3s (na fade-in)

### Introtekst
- "Fotograaf Wouter Zaalberg" in rood (`#c83232`)
- > 1400px: 1.5rem, meer spacing, uitgelijnd op onderkant titel

## Scroll Systeem
- `position: fixed` container
- Foto's gecentreerd bij scrollen
- Formule: `scrollLeft = elementLeft - (viewportWidth - elementWidth) / 2`

## Foto Groottes
- Standaard: 60vh
- `size-full`: 90vh
- Padding: 12rem (responsive: 8rem → 6rem → 2rem)

## Insert Secties (foto 10, 21, 29)
- 100vw breed, politieblauw achtergrond (#1a3a5c)
- Foto: 85vh met zoom effect (12s, scale 1.05)
- Caption: 450px breed, 1.2rem, wit
- Fade-in animatie bij in beeld komen
- Achtergrond + caption faden uit bij verder scrollen

## Info Buttons
- Donker (#000, 70% opacity), rond
- Caption: `rgba(26, 36, 47, 0.9)`
- Klik buiten foto sluit alle captions

## Toggle Alle Onderschriften
- Positie: `bottom: 2rem`, `left: 2rem`
- Alleen zichtbaar vanaf foto 2
- Toggle tekst wisselt

## Politiestrepen Animatie
Trigger: bij foto 1 (begin pagina), achter de foto's

### Strepen
- 4 rode (bovenste 50vh)
- 5 blauwe (onderste 50vh)
- Diagonaal -65deg, 15% opacity

### Beweging
- Rood: van -60vh naar +120vh (omlaag)
- Blauw: van +60vh naar -120vh (omhoog)
- Horizontaal: -15vw naar +15vw

## End Panel
- 100vh, achtergrond `#1a2530`

## Responsive
- **> 1400px**: Grotere introtekst (1.5rem), meer spacing
- **< 1024px**: Intro gecentreerd, foto's 50vh/80vh
- **< 767px**: Verticaal scrollen, strepen verborgen
