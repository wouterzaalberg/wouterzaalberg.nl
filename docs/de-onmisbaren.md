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
- Font: Oswald, 12rem (responsive via clamp)
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
- 100vh

## Responsive Breakpoints
- **Desktop groot (> 1400px)**: titel 12rem, originele positionering
- **Desktop klein (768-1400px)**:
  - Titel: `clamp(6rem, 8vw, 9rem)`
  - Intro panel: `max-width: clamp(280px, 45vw, 500px)`
  - Intro foto: `width: clamp(280px, 45vw, 500px)`
- **Mobiel (< 767px)**:
  - Verticale layout, foto's 100vw
  - Navigatie met gradient achtergrond
  - Caption fade-in animatie (opacity 0→1, translateY 15px→0)
  - Titel/intro tekst fade-in animatie
