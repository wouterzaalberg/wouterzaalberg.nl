# Homepage (index.html)

## Secties

### Sectie 1 - Hero
- Volledig scherm met achtergrondafbeelding
- Menu overlay in wit tekstvak
- Default afbeelding: `de-exoten.jpg`
- Zoom animatie: `scale(1.05)`, 8s transition
- Cross-fade tussen twee img elementen bij hover

### Sectie 2 - About
- Foto: `werkterrein.jpg`
- Kop: "Nederland als werkterrein" (groen #2d5a27, Scala Sans SC)
- Caption linksonder: wit, italic, `left: 12%`, `bottom: 2rem`

### Sectie 3 - Work
- Default foto: `de-onmisbaren/7.jpg`
- Wit tekstvak met "Werk in opdracht"
- Logo carousel met slide effect
- Caption past aan bij geselecteerde foto

### Sectie 4 - Contact
- Foto: `contact.jpg`
- Kop "Contact": donker marineblauw (#1a2a3a)
- Telefoon/email: lichtblauw (#6a9fc7)
- Contactformulier: naam, email, bericht

## Tekstvak positionering
- `left: 60%`, `width: 20%`
- Achtergrond: `rgba(255, 255, 255, 0.75)`
- Padding: `2rem`

## Logo Carousel (sectie 3)

### Data attributen
- `data-image`: enkele foto
- `data-grid="true"` + `data-images`: meerdere foto's
- `data-horizontal="false"`: staande foto (33% positie)
- `data-grid-cols`: aantal kolommen

### Huidige logo configuratie
| Logo | Type | Foto's |
|------|------|--------|
| FNV | Enkel | de-onmisbaren/7.jpg |
| Politie | Staand | politie 1.jpg |
| GroenLinks-PvdA | Grid (3) | groenlinkspvda.jpg, pvda 3.jpg, pvda 1.jpg |
| PGGM | Grid (4) | pggm1-4.jpg |
| Welwonen | Grid (4) | welwonen 1-4.jpg |
| Send | Grid (4) | send 1-4.jpg |
| NZKG | Grid (4) | nzkg 6, 5, 8, 10.jpg |
| Cordaan | Grid (4) | cordaan 1, 2, 5, 4.jpg |
| Gem. Amsterdam | Grid (3) | gemamsterdam1-3.jpg |
| IG | Grid (4) | ig1-4.jpg |
| Meerwaarde | Grid (4) | meerwaarde 1-4.jpg |
| Gem. Almere | Grid (4) | wormer 1-4.jpg |
| DGZ | Grid (4) | dgz1-4.jpg |
| WKPA | Grid (4) | wkpa1-4.jpg |

## Scroll gedrag
- Desktop only (> 767px)
- Muiswiel scrollt naar volgende/vorige sectie
- Debounce: 800ms
- `passive: false` om default scroll te voorkomen

## Responsive
- **1100-1400px**: Kleinere tekst, tekstvak hoger (top: 10-12%)
- **768-1100px**: Breder tekstvak (25%)
- **< 767px**: Verticaal, volledige breedte

## Mobiele Hero Rotatie (< 767px)

### Foto rotatie
- 5 foto's uit grote series roteren elke 4 seconden
- Cross-fade transitie (1s)
- Foto's: de-exoten, mijn-tattoos, a-better-port, in-blauw-licht, toen-de-mijnen-verdwenen

### Serie highlight
- Bij rotatie licht de bijbehorende serie naam op in het menu
- Subtiele kleurverandering met glim animatie (0.6s)
- Kleuren per serie (vale tinten):
  - De Exoten: `#8aab7a` (zacht groen)
  - Mijn Tatoeages: `#d4b89a` (zacht bruin)
  - A Better Port: `#e8d89a` (zacht geel)
  - In Blauw Licht: `#8ab4cc` (zacht blauw)
  - Toen de Mijnen Verdwenen: `#d4937a` (zacht oranje)
