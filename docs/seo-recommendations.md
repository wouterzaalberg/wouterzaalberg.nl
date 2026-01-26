# SEO Aanbevelingen

## Geimplementeerd

### 1. robots.txt
- Toegevoegd met sitemap referentie
- Blokkeert oude/niet-bestaande paden

### 2. sitemap.xml
- Alle 11 pagina's opgenomen
- Prioriteiten: homepage 1.0, grote series 0.9, kleine series 0.8

### 3. 404.html met redirects
- JavaScript-based redirects voor oude URL patronen
- Redirect map voor URLs zonder .html extensie
- Alternatieve spellingen (exoten, tatoeages, mijnen, etc.)
- Gebruiksvriendelijke fallback met navigatie

### 4. SEO Meta Tags (alle pagina's)
- Uitgebreide `<title>` tags met keywords
- `<meta name="description">` met 150-160 karakters
- `<meta name="keywords">` met relevante zoektermen
- `<link rel="canonical">` URLs
- Open Graph tags voor social media
- Twitter Card tags

### 5. Structured Data (homepage)
- JSON-LD Person schema voor fotograaf
- Locatie, beroep, social links

---

## Content Placeholders voor SEO Verbetering

### Homepage (index.html)

**[PLACEHOLDER: Hero Alt Text]**
Locatie: `<img>` tags in hero sectie
Huidige waarde: `alt="Wouter Zaalberg"`
Aanbeveling: Beschrijvende alt tekst per afbeelding, bijv. `alt="Aziatische hoornaars vallen bestrijder aan - foto uit De Exoten serie"`

**[PLACEHOLDER: About Sectie H2]**
Locatie: `.about-heading`
Overweeg: Toevoegen van meer context over specialisaties

### Project Pagina's

**[PLACEHOLDER: Intro Tekst per Project]**
Veel projectpagina's missen een zichtbare introductietekst voor zoekmachines.

Aanbeveling per pagina:
- **de-exoten.html**: Voeg een `<p class="seo-intro">` toe met ~100 woorden over invasieve soorten
- **mijn-tatoeages.html**: Intro tekst aanwezig, goed
- **a-better-port.html**: Intro tekst aanwezig, goed
- **in-blauw-licht.html**: Voeg intro toe over de politieserie
- **toen-de-mijnen-verdwenen.html**: Intro tekst aanwezig, goed
- **het-noordzeekanaal-gebied.html**: Voeg korte beschrijving toe
- **de-onmisbaren.html**: Voeg context toe over essentieel werk
- **een-plek-onder-de-zon.html**: Voeg beschrijving toe

**[PLACEHOLDER: Alt Teksten voor Foto's]**
Locatie: Alle `<img>` tags in projectpagina's
Huidige waarde: Vaak generiek of ontbrekend
Aanbeveling: Beschrijvende alt teksten per foto, bijv.:
- `alt="Beverrat zwemt in Nederlandse sloot"` i.p.v. `alt="foto 1"`
- `alt="Mijnwerker toont tatoeage van schachtbok"` i.p.v. `alt=""`

**[PLACEHOLDER: Figcaption Elementen]**
Locatie: Onder foto's
Aanbeveling: Voeg `<figure>` en `<figcaption>` toe voor context:
```html
<figure>
    <img src="foto.jpg" alt="Beschrijving">
    <figcaption>Korte beschrijving van de foto voor zoekmachines</figcaption>
</figure>
```

### End Panels

**[PLACEHOLDER: Gerelateerde Content Links]**
Locatie: End panels van elke projectpagina
Aanbeveling: Voeg korte beschrijvingen toe bij de "Bekijk ook" links:
```html
<a href="de-exoten.html">
    <strong>De Exoten</strong>
    <span>Invasieve soorten in Nederland</span>
</a>
```

---

## Technische Aanbevelingen

### Image Optimization
- Voeg `width` en `height` attributen toe aan alle `<img>` tags
- Overweeg WebP formaat naast JPG
- Implementeer lazy loading (al aanwezig op sommige pagina's)

### Performance
- Voeg `<link rel="preload">` toe voor hero afbeeldingen
- Overweeg critical CSS inline

### Accessibility (helpt ook SEO)
- Voeg `aria-label` toe aan navigatie elementen
- Zorg dat alle interactive elementen focusbaar zijn

---

## Google Search Console Acties

Na deployment:
1. Dien sitemap.xml in bij Google Search Console
2. Vraag indexering aan voor belangrijkste pagina's
3. Monitor 404 errors en voeg redirects toe indien nodig
4. Controleer Core Web Vitals scores

## Bing Webmaster Tools

1. Dien sitemap ook in bij Bing
2. Verifieer eigendom via CNAME of meta tag
