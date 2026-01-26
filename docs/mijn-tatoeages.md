# Mijn Tatoeages

## Structuur
- Intro: grote foto (1a.jpg) + grijs panel (#2a2a2a) met logo
- Story secties: Portret + Tattoo + Tekstpanel
- Elke sectie: `min-width: 100vw`

## Desktop Layout (≥ 768px)

### Responsive Systeem
- Minimum ondersteunde resolutie: **1280x650**
- Foto's + tekstpanel gecentreerd als groep (`justify-content: center`)
- Vaste padding: 4rem links en rechts
- Gap tussen elementen: 1rem

### Afmetingen
- Foto hoogte: `clamp(58vh, 62vh, 68vh)`
- Foto max-height: `clamp(550px, 55vh, 700px)`
- Tekstpanel breedte: `clamp(260px, 22vw, 450px)`
- Padding-top: `clamp(12vh, 16vh, 20vh)`

### Tekstpanel Paginering
- **Actief bij viewport hoogte < 1100px**
- Splitst tekst per alinea
- Titel (h2) en naam (h3) op elke pagina
- Knoppen (1, 2, 3...) onder het tekstpanel
- Wrapper class: `.text-panel-wrapper`

### Grote schermen (hoogte ≥ 1100px)
- Geen paginering
- Tekstpanel mag doorlopen naar beneden indien nodig
- `height: auto` op tekstpanel

### Portrait+Portrait Detection
- JavaScript detecteert stories met twee staande foto's
- Class `.portrait-portrait` toegevoegd
- Centering handelt uitlijning automatisch af

## Elementen
- Persoonsnaam: verborgen op desktop (`display: none`)
- Scroll pijl: rechtsonder, geanimeerd (alleen vaste pijl, niet in intro)
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
5. Mijnkar
6. Penning (rond)

### Technisch
- Canvas: `position: fixed`, `pointer-events: none`, `z-index: 5`
- Foto's en tekstpanelen: `z-index: 10` (canvas blijft achter content)
- Lijn: `rgba(255, 255, 255, 0.12)`, `lineWidth: 0.8`
- Eerste symbool: linksonder (120px, 150px van onder)
- Volgende: random in marges
- Max 15 symbolen, oude verwijderd
- Sparkle effect bij tekenpunt

### Hint Tekst
- Positie: `bottom: 2.5rem`, `left: 2.5rem`
- "Terwijl jij de foto's bekijkt, wordt deze pagina ondergetatoeëerd"
- Fade-in na 2s

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

## Geteste Resoluties
- 1280x650 (minimum) ✓
- 1600x900 ✓
- 1920x1080 ✓
- 1920x1200 ✓
- 2400x1300 ✓
