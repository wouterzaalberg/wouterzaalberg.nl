# Horizontale Scroll Logica

## Overzicht
Alle projectpagina's met horizontale scroll gebruiken dezelfde scroll logica. Dit document beschrijft de huidige implementatie en wijzigingen.

## Originele implementatie (voor terugzetten indien nodig)

```javascript
let scrollQueue = 0;
let isAnimating = false;

function processScrollQueue() {
    if (scrollQueue !== 0) {
        const newIndex = currentIndex + scrollQueue;
        scrollQueue = 0;
        scrollToIndex(newIndex);

        setTimeout(() => {
            isAnimating = false;
            if (scrollQueue !== 0) {
                processScrollQueue();
            }
        }, 500);
    } else {
        isAnimating = false;
    }
}

container.addEventListener('wheel', (e) => {
    e.preventDefault();

    if (e.deltaY > 0) {
        scrollQueue++;
    } else if (e.deltaY < 0) {
        scrollQueue--;
    }

    if (!isAnimating) {
        isAnimating = true;
        processScrollQueue();
    }
}, { passive: false });
```

### Probleem met trackpads
- Trackpads genereren veel kleine scroll events snel achter elkaar
- Elk event verhoogt scrollQueue met 1
- Resultaat: 5-6 items vooruit in plaats van 1

## Verbeterde implementatie (januari 2026)

### Aanpassingen:
1. **Delta threshold**: Accumuleer deltaY tot drempel bereikt
2. **Momentum detectie**: Negeer events met afnemende delta (trackpad "coasting")
3. **Richting lock**: Voorkom richting wisselen tijdens één scroll actie

### Waarom dit werkt voor beide input types:
- **Muis**: Grote deltaY per event (~100-120), haalt threshold in één klik
- **Trackpad**: Kleine deltaY per event (~1-10), moet accumuleren

### Code:
```javascript
let isAnimating = false;

// Improved scroll handling - works for both mouse and trackpad
let accumulatedDelta = 0;
let lastDelta = 0;
let scrollDirection = 0;
const DELTA_THRESHOLD = 50;  // Minimum delta to trigger scroll
const COOLDOWN = 500;        // Ms to wait after scroll
const MOMENTUM_THRESHOLD = 0.5; // Ignore if delta drops below this ratio

// Trigger scroll in direction
function triggerScroll(direction) {
    if (isAnimating) return;
    isAnimating = true;
    const newIndex = currentIndex + direction;
    scrollToIndex(newIndex);
    setTimeout(() => {
        isAnimating = false;
        accumulatedDelta = 0;
        lastDelta = 0;
        scrollDirection = 0;
    }, COOLDOWN);
}

// Smooth scroll handling (desktop only)
if (window.innerWidth > 767) {
    container.addEventListener('wheel', (e) => {
        e.preventDefault();
        const delta = Math.abs(e.deltaY);
        const direction = e.deltaY > 0 ? 1 : -1;

        if (isAnimating) return;

        // Momentum detection: ignore decreasing deltas (trackpad coasting)
        if (lastDelta > 0 && delta < lastDelta * MOMENTUM_THRESHOLD) {
            lastDelta = delta;
            return;
        }

        // Reset if direction changes
        if (scrollDirection !== 0 && direction !== scrollDirection) {
            accumulatedDelta = 0;
        }

        scrollDirection = direction;
        accumulatedDelta += delta;
        lastDelta = delta;

        // Trigger scroll when threshold reached
        if (accumulatedDelta >= DELTA_THRESHOLD) {
            triggerScroll(direction);
        }
    }, { passive: false });
}
```

### Constanten uitleg:
- **DELTA_THRESHOLD (50)**: Minimale geaccumuleerde deltaY voor scroll trigger
- **COOLDOWN (500)**: Wachttijd na scroll voordat nieuwe scroll mogelijk is
- **MOMENTUM_THRESHOLD (0.5)**: Negeer deltas die minder dan 50% van vorige zijn

## Keyboard Navigatie (januari 2026)
Alle pagina's ondersteunen pijltjestoetsen:
- **→** of **↓**: volgende item
- **←** of **↑**: vorige item

```javascript
document.addEventListener('keydown', (e) => {
    if (e.key === 'ArrowRight' || e.key === 'ArrowDown') {
        e.preventDefault();
        triggerScroll(1);
    } else if (e.key === 'ArrowLeft' || e.key === 'ArrowUp') {
        e.preventDefault();
        triggerScroll(-1);
    }
});
```

**Let op**: de-exoten.html gebruikt continue scroll (geen snap), dus keyboard navigatie scrollt daar met vaste afstand (300px).

## Scroll Grenzen Fix (januari 2026)
Scroll events aan het begin/einde van de pagina worden niet meer "geconsumeerd":

```javascript
function triggerScroll(direction) {
    if (isAnimating) return;

    // Don't consume scroll if already at boundary
    const newIndex = currentIndex + direction;
    if (newIndex < 0 || newIndex >= allItems.length) {
        accumulatedDelta = 0;
        return;
    }
    // ... rest van functie
}
```

## Pagina's met horizontale scroll
- een-plek-onder-de-zon.html
- de-onmisbaren.html
- het-noordzeekanaal-gebied.html
- de-exoten.html
- mijn-tatoeages.html
- a-better-port.html
- in-blauw-licht.html
- toen-de-mijnen-verdwenen.html
