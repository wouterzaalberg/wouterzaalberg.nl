# Wat kost een stad?

> **Status**: In ontwikkeling - nog NIET gekoppeld aan website (home/endpanels)

## Concept

Toont de dagelijkse behoefte van Amsterdam aan grondstoffen. Elke grondstof heeft:
- Vaste titel "Wat kost een stad?" (boven de foto)
- Een liggende foto (80vh)
- Een geanimeerd antwoord naast de foto (getal + eenheid)
- Uitklapbare berekening met bronnen

## Kleuren

- Hoofdkleur: Amsterdam rood `#c8102e`
- Achtergrond: donker `#1a1a1a`
- Tekst: wit/lichtgrijs

## Font

- **Limelight** (Google Fonts) - Art Deco stijl, Amsterdamse School
- Gebruikt voor: titel, vraag, geanimeerde getallen

## Structuur

### 1. Intro Gordijn
- Volledig scherm, Amsterdam rood (`#c8102e`)
- Titel "Wat kost een stad?" in Limelight font
- Ondertitel "De dagelijkse behoefte van Amsterdam"
- **3 Andreaskruisen** onder de titel, splitsen bij openen
- **Gordijn-animatie**: twee helften schuiven naar links/rechts
- Trigger: scroll, touch of klik

### 2. Grondstof Slides
- **Titel**: "Wat kost een stad?" (vast, Limelight font)
- **Foto**: 80vh hoog, start op 10vw van links
- **Antwoord** (rechts van foto, uitgelijnd op bovenkant):
  - Geanimeerd getal (Limelight, Amsterdam rood)
  - Eenheid (bijv. "koeien")
  - "klik hier voor berekening" link
  - Uitklapbaar berekening panel met bronnen

### 3. Navigatie (onderaan)
- 25 kleine icoontjes, transparante achtergrond
- Scroll omlaag → volgende grondstof
- Scroll omhoog → vorige grondstof
- Touch swipe werkt ook
- Klikken op icoon werkt ook

## Animaties

### Gordijn Effect
- Twee helften schuiven naar links/rechts
- Andreaskruisen splitsen mee (clip-path)
- Timing: 1s cubic-bezier(0.65, 0, 0.35, 1)

### Getal Animatie
- Telt op van 0 naar eindwaarde
- Elastisch einde met lichte overshoot
- Duur: 2.5s
- Vaste breedte voorkomt layout shift

### Berekening Panel
- Fade in/out met max-height transitie
- Link tekst wisselt: "klik hier voor berekening" ↔ "verberg berekening"

## Technische Details

- Eigen CSS: `css/wat-kost-een-stad.css`
- Google Font: Limelight
- `noindex, nofollow` meta tag
- Scroll navigatie met debounce (400ms)
- Touch swipe support

## Bestanden

- `wat-kost-een-stad.html`
- `css/wat-kost-een-stad.css`
- `wat-kost-een-stad/` - foto map (nog aan te maken)

## Data Structuur (JavaScript)

```javascript
const grondstoffen = [
    {
        vraag: "...", // niet meer gebruikt
        getal: 1234,
        eenheid: "koeien",
        berekening: "...",
        bronnen: [...]
    },
    // ... 25 items
];
```

## Te Doen

- [ ] 25 grondstoffen met echte data
- [ ] Foto's per grondstof
- [ ] Icoontjes voor navigatie (25 SVG's)
- [ ] Berekeningen en bronnen per grondstof
- [ ] Mobiele optimalisatie testen

## Notities

- Pagina nog niet zichtbaar op homepage
- Pagina nog niet in end panels
- Wacht op expliciete goedkeuring voor koppeling
