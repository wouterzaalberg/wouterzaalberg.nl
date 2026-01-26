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
- Font-size: `clamp(0.9rem, 0.5rem + 0.7vw, 1.5rem)`
- Subtitle: `clamp(0.7rem, 0.5rem + 0.3vw, 0.85rem)`

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
- Caption: 450px breed, wit
- Caption font-size: `clamp(0.85rem, 0.5rem + 0.7vw, 1.2rem)`
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

## Progress Indicator
- Positie: `bottom: 2rem`, `right: 2rem`
- Donkere kleur (past bij lichte achtergrond)
- Berekent scroll percentage (horizontaal desktop, verticaal mobiel)

## Politiestrepen Animatie
Trigger: bij foto 1 (begin) én vanaf foto 30 tot end panel (einde)

### Strepen
- 4 rode (bovenste 50vh)
- 5 blauwe (onderste 50vh)
- Diagonaal -65deg, 15% opacity
- z-index: 1 (achter end panel)

### Beweging
- Rood: van -60vh naar +120vh (omlaag)
- Blauw: van +60vh naar -120vh (omhoog)
- Horizontaal: -15vw naar +15vw

## End Panel
- 100vh, 33vw, max 600px, min 300px
- Achtergrond: `#1a2530`
- z-index: 2 (boven strepen)

## Responsive
- Tekst schaalt via clamp() functies
- **< 1024px**: Intro gecentreerd, foto's 50vh/80vh
- **< 767px**: Verticaal scrollen, strepen verborgen
  - Insert secties: foto 100%, caption eronder, 2rem blauw boven foto
  - Navigatie met gradient achtergrond
