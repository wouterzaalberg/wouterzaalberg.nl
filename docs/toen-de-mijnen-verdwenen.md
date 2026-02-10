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
- Na 4 seconden vallen letters naar beneden
- Staggered delays, random rotaties
- Na ~9 seconden fade terug naar origineel

## Chapter 1 Titel Verdwijn-animatie
- "De wereld die verdween" — letters verdwijnen na enkele seconden
- Letters gesplitst in `<span class="vanish-letter">` via JS
- Verdwijnen in willekeurige groepjes van 1-3 letters, 400ms tussen groepen
- Fade out + translateY(8px) per groep
- Na 2 seconden pauze: alle letters tegelijk rustig terug (2s fade-in)
- Triggert via IntersectionObserver (50% threshold) op chapter panel
- Herhaalbaar bij opnieuw in beeld scrollen

## Progress Indicator
- Positie: `bottom: 2rem`, `left: 2rem`
- 0% bij titel, intro states = 0%, 1%, 2%
- Vanaf scroll: 3-100%
- Wit 50% opacity

## Descent Effect
- `.tdmv-intro-section` met `.descended` class
- Verticale slide (1.2s) simuleert afdaling

## Achtergronden
- **Hero panel (titel)**: `achtergrond1.jpg` (50% opacity), `background-position: center bottom`
- **Foto 1**: horizontaal gespiegeld via `scaleX(-1)` (origineel is gespiegeld voor homepage)
- **Foto 1 achtergrond**: `aardlaag.jpg` via `::before` (z-index -1), donker vlak `::after` 82% opacity (z-index 0)
- **Deel 1 chapter**: `aardlaag.jpg` via `::before` (z-index -1, verticaal gespiegeld `scaleY(-1)`), donker vlak `::after` 82% opacity (z-index 0)
- Faden uit via `.bg-hidden` class
- Dust particles: z-index 1 (boven dark overlay)

## Spiegel Foto's (Desktop Only)
Toggle knoppen onder bijschriften om historische foto's te tonen:

| Foto | Knoptekst | Spiegel tekst | Caption overlay |
|------|-----------|---------------|-----------------|
| 4 | "Bekijk de OVS" | "Bekijk de oefenmijn" | Ja - OVS leermijn beschrijving |
| 10 | "Bekijk de houtproductie" | "Bekijk de productiebossen" | Nee |
| 11 | "Bekijk de Wilhelmina in 1970" | "Bekijk de Wilhelminaberg" | Nee |
| 22 | "Bekijk Staatsmijn Hendrik" | "Bekijk de laatste gebouwen" | Nee |

### Technisch
- Alle spiegel foto's in `.tdmv-spiegel-container` wrapper
- Spiegel foto neemt exacte afmetingen van originele foto over (JS legt originele breedte vast, CSS `object-fit: cover`)
- Class `spiegel-active` wordt toegevoegd bij toggle naar spiegel foto
- Fade transitie: 0.5s bij wisselen
- Knop styling: zelfde als caption maar met groene kleur (`#6b8e23`)
- Caption wrapper: `.tdmv-caption-wrapper` (flex column)
- Caption overlay: `.tdmv-spiegel-caption` (verschijnt bij spiegel foto)

## Interactieve Kaart (Leaflet)
- Insert panel na foto 5: "De mijnstreek"
- CartoDB grayscale tiles
- Oranje markers met foto popups
- 12 mijnen met productie + arbeiders data
- Klikbare mijnnamen in statistieken
- **Statistieken styling**: mijnnaam 0.8rem, locatie+diepte 0.7rem wit (#fff), data 0.8rem
- **Bars**: productie 16px, arbeiders 10px

## Insert Panels
| Insert | Deel | Fade-out trigger |
|--------|------|------------------|
| De Mijnstreek | 1 | Foto Zakia |
| Het grote slopen | 2 | Foto Zakia |
| Uit het dal | 3 | Foto Bart |
| Als expositie en in de media | 3 | - |

### Het grote slopen - Kaart vergelijker
- Swipeable kaart (voor/na mijnsluitingen)
- Gele instructiebalk boven kaart: "Swipe over de kaart om de verschillen voor en na de mijnsluitingen te zien"
- Label verschijnt bij >70% of <30% swipe positie
- Layout links uitgelijnd met titel
- Statistieken (4 getallen): count-up animatie van 0 naar eindwaarde (1.5s, ease-out cubic)
  - 75.000 banen verloren (rood), 14.000 nieuwe banen (groen), 762 hectare, 535 miljoen gulden
  - Triggert via IntersectionObserver (30% threshold)

### "Uit het dal" details
- Foto 550px breed, bijschrift "Foto Ron Meyer"
- Statistieken: uitkeringen, gezondheid, arbeidsparticipatie, woningwaarde
- Demografische data: leeftijdsgroepen, migratieachtergrond
- Count-up animatie met data-prefix support (voor € teken)
- Bar charts

## Foto Groottes
- Standaard: 70vh
- `size-large`: 90vh

## Highlighted Photos (3, 18, 12, 23a, 28, 46, 56)
- Gekleurd tekstpaneel ernaast
- Part-1: `rgba(197, 90, 17, 0.7)` - foto 3, 18
- Part-2: `rgba(107, 122, 138, 0.7)` - foto 12, 23a, 28
- Part-3: `rgba(139, 154, 107, 0.7)` - foto 46, 56
- Horizontale foto's (23a, 56): panel loopt achter foto door met `margin-left: -80px` (desktop), panel direct onder foto op mobiel

## Zoom Effect (foto 3, 18, 12, 23a, 28, 40, 46, 56, 65)
- Wrapper met `overflow: hidden`
- Class `zoom-delayed` → `zoom-active`
- 2s delay, 14s zoom naar `scale(1.06)`

## Chapter Panels
- Deel nummer, titel, periode, intro tekst
- Pijl rechts

## Soundscape knoppen
- **"Zet soundscape aan"**: onder introtekst in hero panel, gecentreerd
- **Aan/uit toggle**: fixed positie rechtsonder, verschijnt bij foto 2, verdwijnt bij terugscrollen naar intro

## Responsive - Small Desktop (768-900px)
- **Hero**: kleinere gap, padding, title (clamp 3.5-5rem), text width 240px
- **Hero alignment**: centered met soundscape knop absoluut gepositioneerd
- **Highlighted panels**: zelfde hoogte als foto's (70vh), smaller width (180px)
- **Foto's en captions**: max-width calc(100vw - 4rem)
- **Mijnstreek insert**: 30vw grid kolommen, 50vh map hoogte

## Responsive - Short Screens (max-height 950px)
- **Info buttons**: "i" knop op foto's met captions, caption als overlay onderaan foto

## Responsive - Short Screens (max-height 1049px)
- **Het grote slopen**: vereenvoudigde tijdslijn (desktop-only periodes verborgen, geen details)
- **Mijnstreek insert**: statistieken met paginering (6+6 mijnen)
- **Uit het dal**: foto verborgen, Bevolkingstrend verplaatst naar row-2, statistieken 4+3 kolommen

## Responsive - Short Screens (max-height 750px)
- **Als expositie insert**: foto grid 3 kolommen (i.p.v. 2), kleinere foto's (180x126px)

## Responsive - Small Height (max-height 650px)
- **Mijnstreek insert**: 28vw grid, 45vh map, kleinere fonts en spacing
- **Chapter panels**: kleinere padding en fonts

## Responsive (< 767px)
- **Verticaal scrollen** (geen horizontaal)
- **Descent effect uitgeschakeld**: alle 3 panelen (hero, foto 1, chapter 1) onder elkaar
- **Progress indicator**: verticale scroll berekening i.p.v. horizontaal
- **Titel**: 3.5rem (groter dan desktop)
- **Dust particles**: ingeschakeld (opacity 0.5), stopt automatisch na foto 1
- **Navigatie**: fixed met gradient achtergrond
- **Hero panel**: padding 1rem links/rechts, soundscape knop gecentreerd
- **Foto's**: 100% breedte, captions eronder met top border
- **Caption fade-in**: IntersectionObserver, opacity 0→1, translateY 15px→0, 0.6s ease-out
- **Caption foto 1**: zichtbaar onder foto met fade-in animatie
- **Chapter titles fade-in**: opacity 0→1, translateY 20px→0, 0.8s ease-out
- **Photo-block gap**: 0 (overschrijft desktop 1.5rem), caption margin-top: 0.7rem
- **Highlighted photos**: foto boven, panel onder (verticaal gestapeld)
- **Achtergronden**: verborgen (::before/::after op intro-photo en intro-chapter)
- **Deel 1 chapter**: 100svh, gradient achtergrond, verkort intro tekst (.desktop-only)
- **Insert panels**:
  - Kaart mijnstreek: zoom 11, statistieken 3 kolommen, titel links uitgelijnd
  - Het grote slopen: touch support voor kaart slider, gele instructiebalk boven kaart
  - Uit het dal: titel links uitgelijnd, foto gecentreerd (80%, max 350px), statistieken links, gemeenten/demografie verborgen
  - Als expositie: oranje achtergrond (part 1 accent), 100% breedte
- **Story end divider**: `* * *` gecentreerd tussen foto 65 en "Als expositie" insert
- **Chapter panels**: 85svh min-height, tekst links uitgelijnd
- **End panel**: 100vw breedte, sluit direct aan op laatste insert
- **Navigatie**: auto-hide na 3 seconden, verschijnt bij aanraking

## Responsive - Extra Small Mobile (< 380px)
- **Hero panel**: padding `4rem 0.8rem 2.5rem`
- **Hero content**: gap `1rem`
- **Hero tekst**: `4vw`, line-height `1.6`
- **Titel**: `10.5vw`
