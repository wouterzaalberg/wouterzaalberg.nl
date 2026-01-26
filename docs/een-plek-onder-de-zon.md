# Een Plek Onder de Zon

## Basis
- Achtergrond: groen `#2d5a27`
- Navigatie: wit
- 14 foto's op 70vh
- Gap: 8rem

## Foto's
- Locatie: `een-plek-onder-de-zon/`
- Bestandsnamen: Foto 1.jpg - Foto 14.jpg

## Intro Panel
- Na eerste foto
- `width: fit-content` - past aan titelbreedte
- Titel: `white-space: nowrap` - altijd één regel
- Titel kleur: wit met geel accent `#f0c040` voor "Zon"

## Scroll
- Intro panel is geen scroll-stop (scrollen gaat direct van foto 1 naar foto 2)
- `allItems` selector bevat alleen `.photo-item` en `.end-panel`

## End Panel
- Achtergrond: donkergroen `#1a3d1a`
- 70vh hoogte

## Responsive
- Foto's: `max-width: calc(100vw - 8rem)` via styles.css
- Verticale foto's schalen mee bij smalle viewports
