# Wouter Zaalberg Portfolio Website

Portfolio website voor fotograaf Wouter Zaalberg. Fotografieprojecten over Nederland in "grote en kleine verhalen".

> **Let op**: Bij werk aan een specifieke pagina, lees eerst het bijbehorende docs bestand voor gedetailleerde specificaties:
> - `docs/homepage.md` - Homepage secties en logo carousel
> - `docs/a-better-port.md` - Haven animatie, intro states, infographics
> - `docs/toen-de-mijnen-verdwenen.md` - Drie delen, kaart, progress indicator
> - `docs/in-blauw-licht.md` - Politiestrepen animatie, captions
> - `docs/mijn-tatoeages.md` - Canvas tattoo animatie, story secties
> - `docs/de-exoten.md` - Complexe clusters, kreeft grid
> - `docs/het-noordzeekanaal-gebied.md` - Foto paren, hover captions
> - `docs/de-onmisbaren.md` - Titel foto-fill effect
> - `docs/een-plek-onder-de-zon.md` - Basis layout

## Sitestructuur

### Homepage (index.html)
- **Sectie 1 (Hero)**: Volledig scherm, achtergrondafbeelding, menu overlay in wit tekstvak
  - Hero name: `clamp(1rem, calc(0.5rem + 0.8vw), 1.4rem)`
  - Tagline: `clamp(1.3rem, calc(0.8rem + 0.8vw), 2.5rem)`, bij 1800px+: `2.3rem`
  - Social icons onder Contact (desktop only, 50% opacity, hover goud)
  - **Mobiel**: safe-area-inset support, scrollbare content, extra breakpoint voor korte schermen (max-height 700px)
- **Sectie 2 (About)**: Foto "werkterrein.jpg", zoom bij scroll
- **Sectie 3 (Work)**: Foto carousel met logo's, zoom bij scroll
  - **Mobiel**: Send grid in 3:4 verticale container (horizontale foto's worden gecropped)
- **Sectie 4 (Contact)**: Contactformulier, zoom bij scroll
- Caption links in sectie 2 en 4: goudkleur (`#cd9854`)
- Scroll per sectie (desktop only, > 767px)

### Projectpagina's
**Grote series** (horizontale scroll):
- wat-kost-een-stad.html, de-exoten.html, mijn-tatoeages.html, a-better-port.html, in-blauw-licht.html, toen-de-mijnen-verdwenen.html

**Kleine series**:
- de-buik-van-de-stad.html, het-noordzeekanaal-gebied.html, de-onmisbaren.html, een-plek-onder-de-zon.html

## Layout Conventies

### Homepage tekstvakken (secties 1-4)
- Positie: `left: 60%`, `width: 20%`
- Witte achtergrond: `rgba(255, 255, 255, 0.75)`, padding `2rem`

### Projectpagina navigatie
```html
<nav class="horizontal-nav">
    <a href="index.html" class="back-link">← Terug</a>
    <span class="nav-title">Paginanaam</span>
</nav>
```
- **Mobiel**: nav verdwijnt na 3 sec, verschijnt bij aanraking (auto-hide)

## Stijl & Design

### Fonts
- **Scala Sans**: Hoofdtekst
- **Scala Sans SC**: Koppen (small caps, uppercase)
- **Minion Pro**: Accenten

### Kleuren
- Goud accent: `#cd9854`
- Donkerblauw: `#1a3a52`

### Project kleuren (hero hover)
- Wat kost een stad: `#5c7a3d`
- De Exoten: `#2d5a27`
- Mijn Tatoeages: `#8b4513`
- A Better Port: `#1e4a6d`
- In Blauw Licht: `#1a3f5c`
- Toen de Mijnen verdwenen: `#8b2500`

## Interactie

### Horizontale scroll (projectpagina's)
- Queue-based scroll: meerdere scrolls worden opgeteld
- Timeout: 500ms
- Mobile: verticaal scrollen

### Zoom effecten
- Start `scale(1)`, zoom naar `scale(1.05)`
- Transition: 8s ease-out
- Trigger: IntersectionObserver, 30% threshold

## Pagina-specifieke Details

### Work Sectie (homepage sectie 3)
- Default foto: `de-onmisbaren/7.jpg`
- Logo's in `logo's/grijs/` en `logo's/kleur/`
- Logo grid gap: `0.4rem`
- Carousel: `data-image` voor enkele foto, `data-grid="true"` voor grid
- Staande foto's: `data-horizontal="false"`
- Info caption: geen achtergrond, tekst donkergrijs (`#4a4a4a`), wit voor FNV via `data-text-color`

### Mijn Tatoeages
- Structuur: Portret + Tattoo + Tekstpanel per verhaal
- Foto's: 58vh, tekstpanel: 420px breed
- Canvas animatie met mijnsymbolen
- Blur achtergronden in `mijn-tattoos/Blurs/`

### Toen de Mijnen Verdwenen
- Eigen CSS: `css/toen-de-mijnen.css`
- Drie delen met eigen kleuren:
  - Deel 1 (1965-1974): oranje `#c55a11`
  - Deel 2 (1974-2000): grijs `#6b7a8a`
  - Deel 3 (2000-nu): groen `#8b9a6b`
- Leaflet.js kaart voor "De Mijnstreek"
- Progress indicator linksonder
- Descent effect in intro
- Highlighted photos: 3, 12, 23a, 28

### A Better Port
- Eigen CSS: `css/a-better-port.css`
- Geel accent: `#e1c85a`
- Intro: 3 states (tekst → foto 1 → foto 2)
- Leaflet kaart + scheepvaart animatie in intro (2 boten met fade-out)
- Dark overlay varieert per scroll positie
- Info buttons op foto's
- Infographic panels na foto 6 en 24
- Responsive: clamp() formulas + height-based breakpoints
- Foto paren: 70vh default, 55vh bij ≤900px hoogte, 50vh bij ≤700px

### In Blauw Licht
- Eigen CSS: `css/in-blauw-licht.css`
- Achtergrond gradient: donker → lichtgrijs
- Politiestrepen animatie bij foto 10
- Toggle alle onderschriften knop
- Hero: 45vw foto + 55vw intro panel

### Het Noordzeekanaalgebied
- Lichte achtergrond `#f5f5f5`
- Hover captions op foto's
- Foto paren: 3+4, 6+7, 10+11
- Grote foto's (90vh): foto 5 en 15

### De Exoten
- Witte achtergrond, grijze sectie vanaf foto 8
- Complexe clusters: beverrat, kreeft grid, muskusrat
- Verticale labels met cursieve accent letter
- Foto formaten: 70vh, 45vh, 35vh, 17vh

### De Onmisbaren
- Donkergrijze achtergrond `#2a2a2a`
- Titel met foto-fill effect (Oswald font)
- Captions met naam + functie

### Een Plek Onder de Zon
- Groene achtergrond `#2d5a27`
- 24 foto's, gap 8rem

## End Panels

Alle projectpagina's eindigen met end panel:
- Standaard: 100vh hoogte, 33vw breed, max 600px, min 300px
- Scroll fix: `margin-top: -80px`, `padding-top: 80px`, `margin-right: -4rem`
- Kleuren per pagina: zie `css/styles.css`
- Contact: wouterzaalberg@gmail.com, 06 45 788 180
- Instagram link

## Responsive Breakpoints

### Breedte
- **1100-1400px**: Kleinere tekst, hogere tekstvakken
- **768-1100px**: Breder tekstvak (25%)
- **< 767px**: Verticaal, volledige breedte

### Hoogte (A Better Port)
- **> 900px**: Standaard formaten
- **≤ 900px**: Compactere intro, foto paren 55vh
- **≤ 700px**: Minimale intro (2 paragrafen verborgen), foto paren 50vh

## Bestandsstructuur

```
/
├── index.html
├── css/
│   ├── styles.css
│   ├── toen-de-mijnen.css
│   ├── a-better-port.css
│   └── in-blauw-licht.css
├── fonts/
├── images/
├── logo's/grijs/ en kleur/
├── [project mappen met foto's]
└── werk-in-opdracht/
```

## Notities
- "lees md" = lees CLAUDE.md (dit bestand)
- Geen emojis tenzij gevraagd
- Mobile breakpoint: 767px
- Lazy loading op afbeeldingen (behalve eerste)
- Reduced motion support aanwezig
