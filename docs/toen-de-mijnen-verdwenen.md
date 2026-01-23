# Toen de Mijnen Verdwenen

CSS: `css/toen-de-mijnen.css`
Font: Adobe Typekit Chloe (`https://use.typekit.net/qwc4lnx.css`)

## Kleuren

### Basis
- Achtergrond: `#1a1816`
- Achtergrond donker: `#0f0e0d`
- Tekst: `#f5f2ed`
- Tekst muted: `#8a857d`

### Per deel
- **Deel 1** (1965-1974): oranje `#c55a11`, bg `#1f1a15`
- **Deel 2** (1974-2000): grijs `#6b7a8a`, bg `#161a1d`
- **Deel 3** (2000-nu): groen `#8b9a6b`, bg `#181a16`

## Structuur
- Hero met instort-animatie
- Descent effect (scroll = afdalen in mijn)
- Chapter panels tussen delen
- Foto blokken met caption rechts
- Insert panels (paginabreed)
- Highlighted photos met gekleurd panel
- Progress indicator linksonder

## Titel Instort-animatie
- Na 5 seconden vallen letters naar beneden
- Staggered delays, random rotaties
- Na ~10 seconden fade terug naar origineel

## Progress Indicator
- Positie: `bottom: 2rem`, `left: 2rem`
- 0% bij titel, intro states = 0%, 1%, 2%
- Vanaf scroll: 3-100%
- Wit 50% opacity

## Descent Effect
- `.tdmv-intro-section` met `.descended` class
- Verticale slide (1.2s) simuleert afdaling

## Achtergronden
- Foto 1: `mijngang.jpg` (4% opacity)
- Deel 1 chapter: `achtergrond.jpg` (10% opacity)
- Faden uit via `.bg-hidden` class

## Interactieve Kaart (Leaflet)
- Insert panel na foto 5: "De mijnstreek"
- CartoDB grayscale tiles
- Oranje markers met foto popups
- 12 mijnen met productie + arbeiders data
- Klikbare mijnnamen in statistieken

## Insert Panels
| Insert | Deel | Fade-out trigger |
|--------|------|------------------|
| De Mijnstreek | 1 | Foto Zakia |
| Het grote slopen | 2 | Foto Zakia |
| Uit het dal | 3 | Foto Bart |
| Als expositie en in de media | 3 | - |

### "Uit het dal" details
- Foto 550px breed
- Statistieken: uitkeringen, gezondheid, arbeidsparticipatie, etc.
- Count-up animatie, bar charts

## Foto Groottes
- Standaard: 70vh
- `size-large`: 90vh

## Highlighted Photos (3, 12, 23a, 28)
- Gekleurd tekstpaneel ernaast
- Part-1: `rgba(197, 90, 17, 0.7)`
- Part-2: `rgba(107, 122, 138, 0.7)`
- Part-3: `rgba(139, 154, 107, 0.7)`

## Zoom Effect (foto 3, 12, 23a, 28, 40, 56, 65)
- Wrapper met `overflow: hidden`
- Class `zoom-delayed` → `zoom-active`
- 2s delay, 14s zoom naar `scale(1.06)`

## Chapter Panels
- Deel nummer, titel, periode, intro tekst
- Pijl rechts

## Soundscape knoppen
- **"Zet soundscape aan"**: onder introtekst in hero panel, gecentreerd
- **Aan/uit toggle**: fixed positie rechtsonder, verschijnt bij foto 2, verdwijnt bij terugscrollen naar intro

## Responsive (< 767px)
- **Verticaal scrollen** (geen horizontaal)
- **Descent effect uitgeschakeld**: alle 3 panelen (hero, foto 1, chapter 1) onder elkaar
- **Progress indicator**: verticale scroll berekening i.p.v. horizontaal
- **Dust particles verborgen** voor performance
- **Navigatie**: fixed met gradient achtergrond
- **Hero panel**: padding 1rem links/rechts, soundscape knop gecentreerd
- **Foto's**: 100% breedte, captions eronder met top border
- **Caption fade-in**: IntersectionObserver, opacity 0→1, translateY 15px→0, 0.6s ease-out
- **Photo-block gap**: 0 (overschrijft desktop 1.5rem), caption margin-top: 0.7rem
- **Highlighted photos**: foto boven, panel onder (verticaal gestapeld)
- **Achtergronden**: verborgen (::before/::after op intro-photo en intro-chapter)
- **Deel 1 chapter**: 100svh, gradient achtergrond, verkort intro tekst (.desktop-only)
- **Insert panels**:
  - Kaart: zoom 11, statistieken 2 kolommen
  - Timeline: periodes 1 en 3 zichtbaar (.desktop-only op 2 en 4)
  - Uit het dal: foto 280px, retail-leegstand en bevolkingstrend verborgen (.desktop-only)
  - Als expositie: 100% breedte, foto grid 95vw gecentreerd
- **Chapter panels**: 85svh min-height, tekst links uitgelijnd
- **End panel**: volle breedte, sluit direct aan op laatste insert
