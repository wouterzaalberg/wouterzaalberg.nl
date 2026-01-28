# De Onmisbaren

## Basis
- Achtergrond: donkergrijs `#2a2a2a`
- Navigatie: wit
- 9 foto's (1.jpg - 9.jpg) op 70vh
- Gap: 12rem

## Intro Sectie (100vw x 100vh)
- Foto 1: absoluut, 100vh, links van center (`translateX(-110%)`)
- Intro panel: verticaal gecentreerd, rechts van center (`translate(-10%, -50%)`)
- Caption onder foto 1

## Titel met Foto-Fill
- Font: Oswald, `clamp(6rem, 2rem + 8vw, 12rem)` - vloeiende groei van 768px tot 2000px
- Achtergrond: `achterdetitel.jpg` + witte overlay (25%)
- Animatie: `bgZoom` 100% → 115% over 20s
- `-webkit-background-clip: text`

## Captions
- Naam: Scala Sans, vet (600), wit
- Functie: italic, 70% wit

## Zoom Effect
- `zoom-active` class na 3 seconden in beeld
- `scale(1)` → `scale(1.05)` over 20s
- Eerste foto: start na 2 seconden

## End Panel
- Achtergrond: `#1a1a1a`
- Hoogte: 100vh
- Breedte: 33vw, max 600px, min 300px

## Lazy Loading
- Eerste 5 foto's: `loading="eager"`
- Rest: `loading="lazy"` met `rootMargin: 500px`

## Responsive Breakpoints
- **Desktop (768px - 2000px+)**: titel groeit vloeiend via clamp
- **Desktop klein (768-1400px)**:
  - Intro panel: `max-width: clamp(280px, 45vw, 500px)`
  - Intro foto: `object-fit: cover; object-position: center top` (cropped, niet uitgerekt)
- **Kleine schermhoogte (< 1000px, desktop)**:
  - Foto's 2-9: 80vh (in plaats van 70vh)
  - Foto's groeien naar beneden: `align-self: flex-start; padding-top: 10vh`
  - Intro foto blijft 100vh
- **Mobiel (< 767px)**:
  - Verticale layout, foto's 100vw
  - Navigatie met gradient achtergrond
  - Caption fade-in animatie (opacity 0→1, translateY 15px→0)
  - Titel/intro tekst fade-in animatie

## Scroll Gedrag
- Scroll aan grenzen wordt niet "geconsumeerd"
- Keyboard navigatie: pijltjestoetsen (←→↑↓)
