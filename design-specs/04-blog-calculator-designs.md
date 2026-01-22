# 📝 Blog & Calculator Design Specifications - ricevuta.studio

> **Document Type**: Public-Facing Content Design Specifications  
> **Platform**: ricevuta.studio  
> **Version**: 1.0  
> **Created**: 2026-01-22  
> **Purpose**: Define design for blog section and free calculator tool

---

## 📰 Blog Section Design

### Overall Blog Philosophy

**Purpose**:
- Educational content about Italian fiscal regulations
- Platform credibility and SEO strategy
- User acquisition through valuable content
- Demonstrate expertise and transparency

**Tone**:
- Educational but accessible
- Friendly and informative
- Clear explanations of complex topics
- Links to official sources

---

### Blog Architecture

```
ricevuta.studio/
├── /blog (Blog homepage)
├── /blog/[slug] (Individual articles)
└── /blog/categoria/[name] (Category pages)
```

---

### Blog Homepage Layout

**Desktop Layout**:
```
┌────────────────────────────────────────────────────────────┐
│  TOP NAVIGATION                                            │
│  Logo | Blog | Calcolatore | Accedi | [Registrati]        │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ┌────────────────────────────────────────────────────┐   │
│  │  HERO SECTION                                      │   │
│  │  Blog - Tutto sulle Prestazioni Occasionali       │   │
│  │  Guide pratiche e aggiornamenti normativi         │   │
│  │                                                    │   │
│  │  [Search: Cerca articoli...]                      │   │
│  └────────────────────────────────────────────────────┘   │
│                                                            │
│  ┌──────────────────────┐  ┌──────────────────────────┐   │
│  │ FEATURED ARTICLE     │  │ CATEGORY FILTERS         │   │
│  │ (Large card w/image) │  │ □ Tutti                  │   │
│  │                      │  │ ☑ Normativa Fiscale      │   │
│  │                      │  │ □ Guide Pratiche         │   │
│  │                      │  │ □ Scadenze               │   │
│  │                      │  │ □ Aggiornamenti          │   │
│  └──────────────────────┘  └──────────────────────────┘   │
│                                                            │
│  ARTICLE GRID                                              │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐                   │
│  │ Article │  │ Article │  │ Article │                   │
│  │ Card    │  │ Card    │  │ Card    │                   │
│  └─────────┘  └─────────┘  └─────────┘                   │
│                                                            │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐                   │
│  │ Article │  │ Article │  │ Article │                   │
│  │ Card    │  │ Card    │  │ Card    │                   │
│  └─────────┘  └─────────┘  └─────────┘                   │
│                                                            │
│  [Carica Altri] [1] [2] [3]                               │
│                                                            │
├────────────────────────────────────────────────────────────┤
│  FOOTER                                                    │
└────────────────────────────────────────────────────────────┘
```

**Mobile Layout**:
- Single column
- Hero: Reduced height
- Filters: Horizontal scrollable chips
- Articles: Stacked cards

---

### Hero Section

**Desktop Visual**:
- Height: 320px
- Background: Gradient (primary-50 to primary-100)
- Centered content

**Elements**:
```html
<section class="blog-hero">
  <h1>Blog</h1>
  <p class="subtitle">
    Tutto sulle Prestazioni Occasionali
  </p>
  <p class="description">
    Guide pratiche, aggiornamenti normativi e consigli
    per gestire le tue ricevute in modo semplice e conforme.
  </p>
  <div class="search-bar">
    <input type="search" placeholder="Cerca articoli...">
    <button>🔍</button>
  </div>
</section>
```

**Styling**:
- H1: 48px, bold, primary-900
- Subtitle: 24px, semibold, primary-700
- Description: 18px, regular, gray-600
- Search bar: Large (52px height), white, shadow-lg
- Max width: 800px centered

---

### Article Card Component

**Card Layout**:
```
┌────────────────────────────────┐
│ [Cover Image]                  │
│                                │
├────────────────────────────────┤
│ 📁 Categoria  ·  ⏱ 5 min     │
│                                │
│ Titolo dell'Articolo           │
│ che può estendersi su          │
│ due righe                      │
│                                │
│ Breve descrizione dell'artico- │
│ lo che spiega di cosa tratta   │
│ in modo chiaro e conciso...    │
│                                │
│ 📅 15 Gen 2026  👤 Marco Rossi │
└────────────────────────────────┘
```

**Dimensions**:
- Width: 100% (grid: 3 columns desktop, 1 mobile)
- Aspect ratio: 16:9 for image
- Total height: ~420px

**Visual Styling**:
- Background: White
- Border: 1px solid gray-200
- Border Radius: 12px (lg)
- Shadow: sm (hover: md)
- Padding: 20px
- Transition: All 250ms

**Cover Image**:
- Height: 200px
- Object-fit: cover
- Border radius: 8px
- Placeholder: Gradient if no image

**Category Badge**:
- Background: primary-100
- Color: primary-700
- Padding: 4px 12px
- Border radius: full
- Font size: 12px
- Font weight: medium

**Reading Time**:
- Icon: Clock
- Color: gray-500
- Font size: 14px

**Title**:
- Font size: 20px
- Font weight: semibold
- Color: gray-900
- Line clamp: 2 lines
- Line height: 1.4

**Description**:
- Font size: 14px
- Color: gray-600
- Line clamp: 3 lines
- Line height: 1.6
- Margin top: 12px

**Metadata Row**:
- Font size: 14px
- Color: gray-500
- Icons: 16px
- Flex layout with gap

**Hover State**:
- Shadow: md
- Title: primary-600
- Transform: translateY(-2px)
- Cursor: pointer

---

### Featured Article Card

**Larger Prominent Card**:
```
┌───────────────────────────────────────────────────┐
│                                                   │
│   [Large Cover Image - 400px height]             │
│                                                   │
├───────────────────────────────────────────────────┤
│                                                   │
│   🏆 ARTICOLO IN EVIDENZA                        │
│                                                   │
│   Titolo Grande dell'Articolo in Evidenza        │
│   che Cattura l'Attenzione                       │
│                                                   │
│   Descrizione più lunga che fornisce maggiori    │
│   dettagli sull'argomento trattato nell'articolo │
│   per invogliare il lettore a continuare...      │
│                                                   │
│   📁 Categoria  ⏱ 8 min  📅 15 Gen  👤 Autore   │
│                                                   │
│   [Leggi Articolo →]                             │
│                                                   │
└───────────────────────────────────────────────────┘
```

**Visual Differences**:
- 2x width of standard card (or full width)
- Larger image (400px height)
- Badge: "Articolo in Evidenza"
- Title: 30px (larger)
- Description: 4-5 lines
- CTA button included
- Optional: Gradient overlay on image with text

---

### Category Filter Sidebar

**Desktop Sidebar** (Right side):
```
┌──────────────────────────┐
│ Filtra per Categoria     │
├──────────────────────────┤
│ ○ Tutti (48)             │
│ ● Normativa Fiscale (12) │
│ ○ Guide Pratiche (15)    │
│ ○ Scadenze (8)           │
│ ○ Aggiornamenti (7)      │
│ ○ Domande Frequenti (6)  │
├──────────────────────────┤
│ Filtra per Tag           │
├──────────────────────────┤
│ [#INPS] [#Ritenuta]      │
│ [#Marca da Bollo]        │
│ [#CU] [#F24]             │
│ [Vedi tutti...]          │
└──────────────────────────┘
```

**Visual**:
- Background: gray-50
- Border: gray-200
- Border radius: lg
- Padding: 20px
- Sticky position (scrolls with page)

**Radio Options**:
- Font size: 14px
- Hover: background gray-100
- Active: primary-600 color, bold
- Count in gray-500

**Tags**:
- Pill shape (border-radius: full)
- Background: white
- Border: gray-300
- Padding: 6px 12px
- Font size: 12px
- Hover: border primary-600
- Click: Toggle filter

**Mobile**: 
- Horizontal scrollable chip list
- Below hero section

---

### Individual Article Page Layout

**Desktop Layout**:
```
┌────────────────────────────────────────────────────────────┐
│  TOP NAVIGATION                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ┌────────────────────────────────────────────────────┐   │
│  │ ARTICLE HEADER                                     │   │
│  │                                                    │   │
│  │ 📁 Categoria                                       │   │
│  │                                                    │   │
│  │ Titolo Completo dell'Articolo                     │   │
│  │ che Può Estendersi su Più Righe                   │   │
│  │                                                    │   │
│  │ 📅 15 Gen 2026  ⏱ 8 min  👤 Marco Rossi          │   │
│  │                                                    │   │
│  │ [Cover Image - Full Width]                        │   │
│  │                                                    │   │
│  └────────────────────────────────────────────────────┘   │
│                                                            │
│  ┌──────────────────────────┐  ┌──────────────────────┐   │
│  │ ARTICLE CONTENT          │  │ SIDEBAR              │   │
│  │                          │  │                      │   │
│  │ [Rich Text Content]      │  │ Indice               │   │
│  │ - Headings               │  │ - Section 1          │   │
│  │ - Paragraphs             │  │ - Section 2          │   │
│  │ - Lists                  │  │ - Section 3          │   │
│  │ - Quotes                 │  │                      │   │
│  │ - Code blocks            │  │ Condividi            │   │
│  │ - Images                 │  │ [FB] [TW] [LI]       │   │
│  │ - Callouts/Alerts        │  │                      │   │
│  │                          │  │ Articoli Correlati   │   │
│  │                          │  │ - Article 1          │   │
│  │                          │  │ - Article 2          │   │
│  │                          │  │ - Article 3          │   │
│  │                          │  │                      │   │
│  │                          │  │ [CTA Card]           │   │
│  │                          │  │ Prova il Calcolatore │   │
│  └──────────────────────────┘  └──────────────────────┘   │
│                                                            │
│  ┌────────────────────────────────────────────────────┐   │
│  │ RELATED ARTICLES (Cards)                           │   │
│  └────────────────────────────────────────────────────┘   │
│                                                            │
│  ┌────────────────────────────────────────────────────┐   │
│  │ COMMENTS / FEEDBACK (Optional)                     │   │
│  └────────────────────────────────────────────────────┘   │
│                                                            │
├────────────────────────────────────────────────────────────┤
│  FOOTER                                                    │
└────────────────────────────────────────────────────────────┘
```

---

### Article Header

**Visual**:
- Max width: 800px (centered)
- Padding: 48px 0

**Category Badge**: Same as card

**Title**:
- Font size: 48px
- Font weight: bold
- Color: gray-900
- Line height: 1.2
- Margin: 16px 0

**Metadata**:
- Font size: 16px
- Color: gray-600
- Icons: 20px
- Flex layout with separators (·)

**Cover Image**:
- Width: 100%
- Max height: 500px
- Object-fit: cover
- Border radius: 16px
- Margin top: 32px

---

### Article Content Styling

**Container**:
- Max width: 720px (comfortable reading)
- Line height: 1.75 (generous spacing)
- Font size: 18px
- Color: gray-800

**Typography Elements**:

**H2 (Section Headers)**:
```css
font-size: 32px;
font-weight: 600;
color: gray-900;
margin: 48px 0 24px;
```

**H3 (Subsection Headers)**:
```css
font-size: 24px;
font-weight: 600;
color: gray-900;
margin: 32px 0 16px;
```

**Paragraph**:
```css
font-size: 18px;
line-height: 1.75;
color: gray-800;
margin-bottom: 20px;
```

**Lists** (ul/ol):
```css
margin: 24px 0;
padding-left: 24px;
```

**List Items**:
```css
margin-bottom: 12px;
padding-left: 8px;
```

**Blockquote**:
```css
border-left: 4px solid primary-600;
padding: 16px 24px;
background: gray-50;
margin: 32px 0;
font-style: italic;
color: gray-700;
```

**Code Inline**:
```css
background: gray-100;
padding: 2px 6px;
border-radius: 4px;
font-family: monospace;
font-size: 16px;
color: error-700;
```

**Code Block**:
```css
background: gray-900;
color: gray-100;
padding: 24px;
border-radius: 8px;
overflow-x: auto;
font-family: monospace;
font-size: 14px;
line-height: 1.6;
margin: 32px 0;
```

**Images in Content**:
```css
width: 100%;
max-width: 100%;
height: auto;
border-radius: 8px;
margin: 32px 0;
```

**Links**:
```css
color: primary-600;
text-decoration: underline;
hover: color: primary-700;
```

---

### Special Content Components

#### Info Callout (Alert Box)

```
┌────────────────────────────────────────┐
│ ℹ️ Informazione                        │
│                                        │
│ Testo informativo che fornisce         │
│ dettagli aggiuntivi importanti.        │
└────────────────────────────────────────┘
```

**Visual**:
- Background: info-50
- Border-left: 4px solid info-500
- Padding: 20px
- Border-radius: 8px
- Icon: 24px

**Variants**:
- **Success**: Green theme, checkmark icon
- **Warning**: Amber theme, warning icon
- **Error**: Red theme, alert icon
- **Tip**: Purple theme, lightbulb icon

#### Table of Contents (Sidebar)

```
┌──────────────────────────┐
│ Indice                   │
├──────────────────────────┤
│ • Introduzione           │
│ • Normativa INPS         │
│   - Limite €5.000        │
│   - Contributi           │
│ • Ritenuta d'Acconto     │
│ • Conclusioni            │
└──────────────────────────┘
```

**Visual**:
- Sticky sidebar (top: 100px)
- Background: white
- Border: gray-200
- Border-radius: lg
- Padding: 20px
- Font-size: 14px
- Active section: primary-600, bold

**Behavior**:
- Auto-scroll highlighting
- Click to jump to section
- Collapse on mobile

---

## 🧮 Free Calculator Design

### Calculator Philosophy

**Purpose**:
- Lead generation tool (no login required)
- Simple, fast gross ↔ net calculations
- Educational about deductions
- CTA to register for full features

**Key Features**:
- Bidirectional input (gross or net)
- Real-time calculation
- Breakdown display (ritenuta, INPS, marca da bollo)
- Responsive design

---

### Calculator Page Layout

**Desktop Layout**:
```
┌────────────────────────────────────────────────────────────┐
│  TOP NAVIGATION                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  HERO SECTION                                              │
│  ┌────────────────────────────────────────────────────┐   │
│  │                                                    │   │
│  │  Calcolatore Gratuito                             │   │
│  │  Prestazioni Occasionali                          │   │
│  │                                                    │   │
│  │  Calcola ritenute e contributi in tempo reale     │   │
│  │                                                    │   │
│  └────────────────────────────────────────────────────┘   │
│                                                            │
│  ┌──────────────────────────┐  ┌──────────────────────┐   │
│  │ CALCULATOR CARD          │  │ INFO CARD            │   │
│  │ (Interactive)            │  │ (Educational)        │   │
│  │                          │  │                      │   │
│  │ [Input Fields]           │  │ Come Funziona        │   │
│  │ [Calculation Display]    │  │ - Ritenuta 20%       │   │
│  │ [Breakdown Table]        │  │ - INPS 33.72%        │   │
│  │                          │  │ - Marca da bollo     │   │
│  │ [CTA: Crea Ricevuta]     │  │                      │   │
│  │                          │  │ [Link a Blog]        │   │
│  └──────────────────────────┘  └──────────────────────┘   │
│                                                            │
│  FAQ SECTION                                               │
│  ┌────────────────────────────────────────────────────┐   │
│  │ Domande Frequenti                                  │   │
│  └────────────────────────────────────────────────────┘   │
│                                                            │
├────────────────────────────────────────────────────────────┤
│  FOOTER                                                    │
└────────────────────────────────────────────────────────────┘
```

**Mobile Layout**:
- Single column
- Calculator full-width card
- Info card below
- FAQ accordion

---

### Calculator Hero Section

**Visual**:
- Height: 280px
- Background: Gradient (primary-50 to white)
- Centered content

**Elements**:
```html
<section class="calculator-hero">
  <h1>Calcolatore Gratuito</h1>
  <h2>Prestazioni Occasionali</h2>
  <p>
    Calcola ritenute, contributi INPS e importo netto
    in tempo reale. Nessuna registrazione richiesta.
  </p>
</section>
```

**Styling**:
- H1: 48px, bold, gray-900
- H2: 32px, semibold, primary-700
- Description: 18px, gray-600
- Max width: 800px centered

---

### Calculator Card Component

**Card Layout**:
```
┌────────────────────────────────────────┐
│ Calcolatore Ricevuta                   │
├────────────────────────────────────────┤
│                                        │
│ Calcola da:                            │
│ ○ Importo Lordo  ● Importo Netto      │
│                                        │
│ ┌────────────────────────────────────┐ │
│ │ € 1.000,00                         │ │
│ │ Importo Netto                      │ │
│ └────────────────────────────────────┘ │
│                                        │
│ Committente:                           │
│ ○ Privato  ● Sostituto d'Imposta      │
│                                        │
│ ────────────────────────────────────── │
│                                        │
│ 💰 RISULTATO                           │
│                                        │
│ Importo Lordo:       € 1.670,13        │
│ Ritenuta 20%:        € 334,03          │
│ INPS 33.72%:         € 336,10          │
│ Importo Netto:       € 1.000,00        │
│                                        │
│ ⚠️ Marca da bollo richiesta (€2,00)    │
│    (Importo lordo > €77,47)            │
│                                        │
│ ────────────────────────────────────── │
│                                        │
│ [📥 Scarica Dettaglio]  [🔗 Condividi] │
│                                        │
│ [✨ Crea Ricevuta Completa →]          │
│                                        │
└────────────────────────────────────────┘
```

**Dimensions**:
- Width: 500px (desktop), 100% (mobile)
- Background: White
- Border: 2px solid primary-200
- Border-radius: xl (16px)
- Shadow: lg
- Padding: 32px

---

### Input Section

**Radio Toggle**:
```html
<div class="toggle-group">
  <input type="radio" name="mode" id="lordo" value="lordo">
  <label for="lordo">Importo Lordo</label>
  
  <input type="radio" name="mode" id="netto" value="netto" checked>
  <label for="netto">Importo Netto</label>
</div>
```

**Visual**:
- Segmented control style
- Background: gray-100
- Active: primary-600 background, white text
- Border-radius: md
- Padding: 8px per option
- Font-size: 14px, font-weight: medium

**Amount Input**:
```html
<div class="amount-input">
  <span class="currency">€</span>
  <input type="number" value="1000.00" step="0.01">
  <span class="label">Importo Netto</span>
</div>
```

**Visual**:
- Large input: 80px height
- Font-size: 36px
- Font-weight: bold
- Color: primary-900
- Currency symbol: Left side, gray-500
- Label: Below, gray-600, 14px
- Border: 2px solid gray-300
- Focus: Border primary-600

**Committente Type Radio**:
- Same toggle style as mode
- "Privato" vs "Sostituto d'Imposta"
- Info tooltip: Explains difference

---

### Results Display

**Section Header**:
```html
<div class="results-header">
  <h3>💰 RISULTATO</h3>
</div>
```

**Visual**:
- Icon + uppercase text
- Font-size: 16px
- Font-weight: 700
- Color: gray-900
- Margin: 24px 0 16px

**Results Table**:
```html
<table class="results-table">
  <tr>
    <td>Importo Lordo:</td>
    <td>€ 1.670,13</td>
  </tr>
  <tr class="deduction">
    <td>Ritenuta 20%:</td>
    <td>- € 334,03</td>
  </tr>
  <tr class="deduction">
    <td>INPS 33.72%:</td>
    <td>- € 336,10</td>
  </tr>
  <tr class="total">
    <td>Importo Netto:</td>
    <td>€ 1.000,00</td>
  </tr>
</table>
```

**Visual**:
- Width: 100%
- Font-size: 18px
- Row padding: 12px 0
- Left column: Gray-700, regular
- Right column: Gray-900, semibold, right-aligned
- Deduction rows: Color error-600 (red)
- Total row: Bold, larger (20px), border-top 2px
- Monospace font for numbers

**Marca da Bollo Alert**:
```html
<div class="alert alert-warning">
  <svg>⚠️</svg>
  <p>
    Marca da bollo richiesta (€2,00)
    <br>
    <small>(Importo lordo > €77,47)</small>
  </p>
</div>
```

**Visual**:
- Background: warning-50
- Border-left: 4px solid warning-500
- Padding: 16px
- Border-radius: md
- Icon: 24px
- Font-size: 14px

---

### Action Buttons

**Secondary Actions**:
```html
<div class="button-group">
  <button class="btn-secondary">
    <svg>📥</svg> Scarica Dettaglio
  </button>
  <button class="btn-secondary">
    <svg>🔗</svg> Condividi
  </button>
</div>
```

**Primary CTA**:
```html
<button class="btn-primary btn-large">
  <svg>✨</svg> Crea Ricevuta Completa →
</button>
```

**Visual**:
- Full-width button
- Height: 52px
- Font-size: 18px
- Font-weight: 600
- Icon + text + arrow
- Margin-top: 24px
- Hover: Slight lift, shadow increase

---

### Info Sidebar Card

**Content**:
```
┌────────────────────────────────┐
│ Come Funziona il Calcolo       │
├────────────────────────────────┤
│                                │
│ 📊 Ritenuta d'Acconto          │
│ 20% dell'importo lordo         │
│ Applicata da sostituto         │
│ d'imposta                      │
│                                │
│ 🏛️ Contributi INPS             │
│ 33.72% se sotto €5.000/anno    │
│ 24% se sopra (già iscritto)    │
│                                │
│ 🏷️ Marca da Bollo              │
│ €2,00 se lordo > €77,47        │
│ Da applicare fisicamente       │
│                                │
│ ────────────────────────────   │
│                                │
│ Vuoi saperne di più?           │
│ [📖 Leggi la Guida Completa]   │
│                                │
│ ────────────────────────────   │
│                                │
│ 💡 Con ricevuta.studio puoi:   │
│ ✓ Generare ricevute complete   │
│ ✓ Calcolare F24 automatici     │
│ ✓ Gestire scadenze             │
│ ✓ Archiviare documenti         │
│                                │
│ [Registrati Gratis →]          │
│                                │
└────────────────────────────────┘
```

**Visual**:
- Width: 380px
- Background: white
- Border: gray-200
- Border-radius: lg
- Shadow: sm
- Padding: 24px
- Sticky (top: 100px)

**Section Styling**:
- Icon: 24px
- Title: 16px, semibold, gray-900
- Description: 14px, gray-600
- Spacing: 20px between sections

---

### FAQ Accordion

**Section Layout**:
```
Domande Frequenti
──────────────────────────────────────────────────

▼ Cos'è la ritenuta d'acconto?
  La ritenuta d'acconto è...

▶ Chi deve applicare la ritenuta?

▶ Come funzionano i contributi INPS?

▶ Quando serve la marca da bollo?

▶ Il calcolatore è gratuito?
```

**Visual**:
- Max width: 800px centered
- Margin: 64px 0

**Accordion Item**:
- Border: 1px solid gray-200
- Border-radius: md
- Margin-bottom: 12px
- Padding: 20px
- Hover: Background gray-50

**Question (Collapsed)**:
- Font-size: 18px
- Font-weight: 600
- Color: gray-900
- Icon: Chevron right

**Question (Expanded)**:
- Icon: Chevron down
- Answer padding-top: 16px
- Answer font-size: 16px
- Answer color: gray-700

---

## 🎨 Shared Components

### Top Navigation (Public Pages)

**Visual**:
- Height: 64px
- Background: White
- Border-bottom: gray-200
- Shadow: sm

**Elements**:
```
[Logo] | Blog | Calcolatore | [Accedi] [Registrati]
```

**Button Styles**:
- "Accedi": Secondary (outlined)
- "Registrati": Primary (filled)

---

### Footer

**Layout**:
```
┌────────────────────────────────────────────────────────┐
│                                                        │
│  [Logo]                                                │
│  Prestazione occasionale facile                        │
│                                                        │
│  Prodotto        Risorse           Legale             │
│  - Calcolatore   - Blog            - Privacy          │
│  - Dashboard     - Guide           - Termini          │
│  - Documenti     - FAQ             - Compliance       │
│                  - Contatti        - Cookie           │
│                                                        │
│  ──────────────────────────────────────────────────    │
│                                                        │
│  © 2026 ricevuta.studio - P.IVA XXXXXXXXXXX           │
│  [Social Icons: LinkedIn, Twitter, Email]             │
│                                                        │
└────────────────────────────────────────────────────────┘
```

**Visual**:
- Background: gray-900
- Color: gray-300
- Padding: 64px 32px 32px
- Links: Hover → white
- Social icons: 24px, gray-400, hover → white

---

## 📱 Mobile Optimizations

### Blog Mobile
- Single column cards
- Horizontal scroll for filters (chips)
- Collapsible sidebar content (accordion)
- Simplified article header
- Reading progress bar

### Calculator Mobile
- Full-width card
- Larger touch targets (52px height inputs)
- Simplified toggle controls
- Bottom sheet for detailed breakdown
- Sticky CTA button

---

## ♿ Accessibility

### Blog
- Semantic HTML (article, header, nav)
- Alt text for all images
- ARIA labels for interactive elements
- Keyboard navigation for filters
- Focus indicators visible
- Screen reader announcements for dynamic content

### Calculator
- Label associations for inputs
- ARIA live region for results
- Clear focus order
- Error announcements
- Keyboard-only operation possible
- High contrast numbers

---

## 🎯 Performance

### Blog
- Lazy load images below fold
- Pagination (20 articles per page)
- Optimized cover images (WebP, responsive)
- Code syntax highlighting on-demand
- CDN for static assets

### Calculator
- Client-side calculation (instant)
- No API calls (pure JavaScript)
- Minimal dependencies
- Local storage for preferences
- Fast initial load (<1s)

---

*This design provides a professional, user-friendly experience for public-facing content while maintaining brand consistency and accessibility.*
