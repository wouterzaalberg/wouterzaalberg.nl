# Mijn Tatoeages

## Structuur
- Intro: grote foto (1a.jpg) + grijs panel (#2a2a2a) met logo
- Story secties: Portret + Tattoo + Tekstpanel
- Elke sectie: `min-width: 100vw`

## Afmetingen (desktop)
- Foto's: 58vh
- Tekstpanel: 420px breed, 100vh hoog
- Intro panel: 70vh hoog, 420px breed
- Gap foto's: 0.5rem

## Tekstpanel Uitlijning
- Foto's 58vh, verticaal gecentreerd → bovenkant op 21vh
- `.story-text-panel`: `padding-top: 21vh`
- `.story-text-content`: `padding: 0 3rem 3rem 3rem`

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
- Canvas: `position: fixed`, `pointer-events: none`, `z-index: 50`
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
- **< 1200px**: Foto's 50vh, panel 300px
- **< 1024px**: Foto's 45vh, panel 280px
- **< 767px**: Verticaal, volle breedte
