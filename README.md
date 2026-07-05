# VoiceLAB Web

> Infosite rund um den Aufbau eines Voice-Targeting-LABs — lokal in Hyper-V und in der Cloud auf Azure.  
> Gehostet unter [https://www.voicelab.ovh](https://www.voicelab.ovh/)

**Autor:** Pawel Kostelnik · Niederkassel, Germany

![VoiceLAB Hero Illustration](solid/src/images/hero-top-illustration.svg)

## Inhaltsverzeichnis
- [Highlights](#highlights)
- [Projektstruktur](#projektstruktur)
- [Schnellstart](#schnellstart)
- [Lokale Entwicklung](#lokale-entwicklung)
- [Anpassung](#anpassung)
- [Deployment](#deployment)
- [Technologie-Stack](#technologie-stack)
- [Lizenzhinweis](#lizenzhinweis)

## Highlights
- Drei eigenstaendige Landingpages (`index.html`, `ellie/`, `solid/`) fuer unterschiedliche Stories und Zielgruppen
- Responsives Layout auf Basis von Bootstrap 5, optimiert fuer Desktop, Tablet und Mobile
- Sanfte Motion-Effekte mit ScrollReveal und Anime.js fuer eine moderne User Experience
- Eingebettete PowerShell-Skripte (Modale) fuer Hyper-V VM-Provisionierung, AD DS Setup, Domain-Join und OOS-Voraussetzungen
- Strukturierte Sass-Teilstuecke in `solid/src/scss` erleichtern Branding- und Theme-Anpassungen
- SEO-Grundausstattung: OpenGraph, Twitter Cards, JSON-LD (Schema.org), Canonical URLs
- Besucherstatistik via Fastcounter (datenschutzkonform dokumentiert)
- Produktionsfertige Assets in den jeweiligen `dist/`-Ordnern fuer schnelle Bereitstellung

## Projektstruktur
```text
voicelab-web/
├── index.html              # Haupt-Landingpage (inkl. Impressum, Datenschutz, PS-Skript Modale)
├── .gitignore              # Git-Ausschluesse (DS_Store, Synology-Konflikte, node_modules …)
├── README.md
├── ellie/
│   ├── index.html          # Alternative Landingpage "Ellie"
│   └── dist/               # Kompilierte Ellie-Assets (Bootstrap, CSS, JS)
└── solid/
    ├── index.html           # Landingpage "Solid" (Template-Showcase)
    ├── LICENSE              # GPL-3.0
    ├── CHANGELOG.md
    ├── README.md
    ├── dist/                # Ausgelieferte CSS- und JS-Dateien
    └── src/
        ├── images/          # SVG-Illustrationen & Feature-Icons
        ├── js/main.js       # ScrollReveal + Anime.js Animations-Logik
        └── scss/            # Sass-Quellcode in Modulen
            ├── style.scss           # Haupt-Einstiegsdatei
            ├── _normalize.scss
            ├── abstracts/           # Variablen, Mixins, Funktionen
            ├── base/                # Basis-Styles, Typografie, Helfer
            ├── components/          # Buttons, Formulare
            └── layout/              # Hero, Features, Pricing, CTA, Footer …
```

## Schnellstart
1. Repository klonen oder als ZIP herunterladen.
2. Beliebige `index.html` direkt im Browser oeffnen oder per lokalem Webserver ausliefern.
3. Inhalte in den HTML-Dateien anpassen, um eigene Texte, Logos oder Links einzubinden.

## Lokale Entwicklung
- Verwende einen schlanken Webserver wie `npx serve .` oder die VS Code Erweiterung "Live Server", um Hot-Reloading zu erhalten.
- Sass aenderst du am komfortabelsten mit dem offiziellen Compiler: `npm install --global sass` und danach `sass solid/src/scss/style.scss solid/dist/css/style.css --watch`.
- Javascript-Anpassungen findest du in `solid/src/js/main.js`; die gebaute Version liegt in `solid/dist/js/`.

## Anpassung
- **Branding:** Passe Farben, Typografie und Abstaende in `solid/src/scss/abstracts/_variables.scss` an.
- **Sektionen:** Die Layout-Partial-Dateien (`solid/src/scss/layout/`) enthalten klar getrennte Bereiche wie Hero, Features oder Pricing.
- **Assets:** SVG-Grafiken liegen unter `solid/src/images/` und koennen mit individuellen Illustrationen ersetzt werden.
- **Animationen:** ScrollReveal- und Anime.js-Settings werden in `solid/src/js/main.js` gesetzt; hier laesst sich Timing oder Sequenz einfach justieren.

## Deployment
- Project-Ordner oder einen der Unterordner (`ellie`, `solid`) auf einen beliebigen Static-Host (z. B. GitHub Pages, Azure Static Web Apps, Netlify) laden.
- Stelle sicher, dass CSS- und JS-Dateien relativ verlinkt bleiben, wenn du Unterverzeichnisse oder benutzerdefinierte Domains nutzt.
- Fuer CI/CD-Workflows empfiehlt sich ein automatisiertes Sass-Build vor dem Deploy (z. B. ueber GitHub Actions oder Azure DevOps Pipelines).

## Technologie-Stack

| Technologie | Version | Quelle | Einsatz |
|---|---|---|---|
| **HTML5** | – | – | Semantische Seitenstruktur, OpenGraph, JSON-LD |
| **Bootstrap** | 5.2.1 | lokal (`dist/`) | Responsive Grid, Modale, Navbar (`index`, `ellie`) |
| **Sass / SCSS** | – | `solid/src/scss/` | Modulare Stylesheet-Architektur (`solid`) |
| **ScrollReveal** | 4.0.9 | CDN (unpkg) | Scroll-getriggerte Einblendanimationen (alle Seiten) |
| **Anime.js** | 3.2.2 | CDN (unpkg) | SVG-/Motion-Animationen (nur `solid`) |
| **Font Awesome** | Kit `0073c7b349` | CDN (kit.fontawesome.com) | Icons (`index`, `ellie`) |
| **Google Fonts** | – | CDN (fonts.googleapis.com) | Heebo + Titillium Web (`index`, `ellie`); IBM Plex Sans (`solid`) |
| **Fastcounter** | – | fastcounter.de (ID 37745) | Besucherstatistik (`index`, `ellie`) |

> **Hinweis:** `solid/` nutzt **kein** Bootstrap und kein Font Awesome — Layouts werden dort vollstaendig ueber eigenes SCSS gesteuert.

## Lizenzhinweis
- Das `solid/`-Verzeichnis steht unter der **GPL-3.0**-Lizenz (siehe `solid/LICENSE`).
- Bootstrap ist unter der **MIT**-Lizenz lizenziert (Copyright 2011–2022 The Bootstrap Authors & Twitter, Inc.).
- Anime.js ist unter der **MIT**-Lizenz lizenziert.
- ScrollReveal ist unter der **GPL-3.0**-Lizenz lizenziert (nicht-kommerzielle Nutzung; kommerzielle Nutzung erfordert eine separate Lizenz).
- Die uebrigen Projektdateien unterliegen dem Copyright des Autors. Fuer Details bitte die jeweiligen Header in den Quelldateien beachten.
