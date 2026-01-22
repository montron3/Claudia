# 📊 Dashboard Design Specifications - ricevuta.studio

> **Document Type**: Dashboard UI/UX Design Specifications  
> **Platform**: ricevuta.studio  
> **Version**: 1.0  
> **Created**: 2026-01-22  
> **Purpose**: Define comprehensive design for all 4 dashboards (Prestatore, Committente, Commercialista, Admin)

---

## 📌 Dashboard Design Philosophy

### Core Principles

**1. Information Hierarchy**
- Most important information visible immediately
- Progressive disclosure for complex data
- Clear visual separation between sections

**2. Scannable Layout**
- Card-based design for quick scanning
- Consistent widget spacing and alignment
- Visual grouping of related information

**3. Actionable Insights**
- Data with context and recommended actions
- Clear CTAs for next steps
- Proactive notifications and alerts

**4. Customizable Experience**
- Drag-and-drop widget reordering
- Show/hide sections based on user needs
- Persistent user preferences

---

## 🎨 Common Dashboard Layout

### Overall Structure

```
┌─────────────────────────────────────────────────────┐
│  TOP NAVIGATION BAR (64px height)                   │
│  Logo | Page Title | Search | Notifications | User │
├──────────┬──────────────────────────────────────────┤
│          │                                           │
│ SIDEBAR  │  MAIN CONTENT AREA                       │
│ (240px)  │  - Dashboard Header                      │
│          │  - Widget Grid (customizable)            │
│ - Home   │  - Quick Actions                         │
│ - Items  │                                           │
│ - Stats  │                                           │
│ - Docs   │                                           │
│ - Help   │                                           │
│          │                                           │
│          │                                           │
└──────────┴──────────────────────────────────────────┘
```

### Top Navigation Bar

**Height**: 64px  
**Background**: White  
**Border Bottom**: 1px solid `--color-gray-200`  
**Shadow**: `--shadow-sm`

**Elements** (Left to Right):
1. **Logo** (180px)
   - `ricevuta.studio` wordmark
   - Clickable, returns to dashboard home
   
2. **Page Title** (flexible)
   - H2 size, semibold
   - Current page/section name
   
3. **Global Search** (300px)
   - Icon + input field
   - Placeholder: "Cerca ricevute, utenti..."
   - Keyboard shortcut: Cmd/Ctrl + K
   
4. **Notification Bell** (40px icon button)
   - Badge with unread count
   - Dropdown shows recent notifications
   
5. **User Menu** (40px avatar + name)
   - Avatar circle
   - Name (on desktop)
   - Dropdown: Profile, Settings, Logout

**Mobile Behavior**:
- Logo only on left
- Hamburger menu on right
- Search accessible from menu

---

### Sidebar Navigation

**Width**: 240px (64px collapsed)  
**Background**: White or `--color-gray-50`  
**Border Right**: 1px solid `--color-gray-200`

**Navigation Items**:
```
┌─────────────────────┐
│ [Icon] Dashboard    │ ← Active (blue accent)
│ [Icon] Ricevute     │
│ [Icon] Collaboratori│
│ [Icon] Documenti    │
│ [Icon] Scadenze     │
│ [Icon] Statistiche  │
│ ─────────────────── │
│ [Icon] Impostazioni │
│ [Icon] Supporto     │
└─────────────────────┘
```

**Item States**:
- **Active**: Background `--color-primary-50`, left border 3px `--color-primary-600`
- **Hover**: Background `--color-gray-100`
- **Default**: Gray text

**Collapse Behavior**:
- Desktop: Toggle button at bottom
- Collapsed: Show icons only
- Mobile: Slide-out drawer

---

### Dashboard Header

**Location**: Top of main content  
**Spacing**: Padding `--space-8` (32px)

**Elements**:
```html
<div class="dashboard-header">
  <div class="header-content">
    <h1>Dashboard</h1>
    <p class="subtitle">Benvenuto, Marco! Ecco la tua situazione.</p>
  </div>
  <div class="header-actions">
    <button class="btn-primary">
      <svg>+</svg> Nuova Ricevuta
    </button>
  </div>
</div>
```

**Visual**:
- H1: Large, bold title
- Subtitle: Gray-500, regular weight
- Primary action button: Prominent on right
- Responsive: Stack on mobile

---

### Widget Grid System

**Layout**: CSS Grid  
**Columns**: 12-column system  
**Gap**: 24px (--space-6)  
**Padding**: 32px (--space-8)

**Widget Sizes**:
- **Small**: 4 columns (1/3 width)
- **Medium**: 6 columns (1/2 width)
- **Large**: 8 columns (2/3 width)
- **Full**: 12 columns (full width)

**Responsive Behavior**:
- Desktop (1024px+): 12 columns
- Tablet (768-1023px): 8 columns
- Mobile (<768px): Stack vertically (full width)

---

### Standard Widget Component

**Structure**:
```html
<div class="widget widget-size-medium">
  <div class="widget-header">
    <h3 class="widget-title">Titolo Widget</h3>
    <button class="widget-menu">⋮</button>
  </div>
  <div class="widget-body">
    <!-- Content -->
  </div>
  <div class="widget-footer">
    <a href="#">Vedi tutto →</a>
  </div>
</div>
```

**Visual Styling**:
- Background: White
- Border: 1px solid `--color-gray-200`
- Border Radius: `--radius-lg` (12px)
- Shadow: `--shadow-sm`
- Padding: `--space-6` (24px)
- Hover: Shadow transitions to `--shadow-md`

**Widget Header**:
- Flex layout (space-between)
- Title: H3, semibold
- Menu: Icon button for actions (customize, hide, etc.)

**Widget Body**:
- Flexible content area
- Min height: 120px
- Max height: Depends on content (scrollable if needed)

**Widget Footer**:
- Optional
- Links to detailed views
- Subtle gray text with arrow

---

## 👤 Dashboard Prestatore (Service Provider)

### Widget Layout (Desktop)

```
┌────────────────────────────────────────────────────────────┐
│  DASHBOARD HEADER                                          │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ┌─────────────────┐  ┌─────────────────┐  ┌───────────┐ │
│  │ Guadagni Annui  │  │ Tracker €5.000  │  │ Ricevute  │ │
│  │ Small           │  │ Medium          │  │ Small     │ │
│  └─────────────────┘  └─────────────────┘  └───────────┘ │
│                                                            │
│  ┌──────────────────────────────────────────────────────┐ │
│  │ Scadenze Prossime                                    │ │
│  │ Full Width                                           │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                            │
│  ┌──────────────────────────┐  ┌──────────────────────┐  │
│  │ Situazione Fiscale       │  │ Committenti          │  │
│  │ Medium                   │  │ Medium               │  │
│  └──────────────────────────┘  └──────────────────────┘  │
│                                                            │
│  ┌──────────────────────────────────────────────────────┐ │
│  │ Statistiche Mensili (Grafico)                       │ │
│  │ Full Width                                           │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                            │
│  ┌──────────────────────────┐  ┌──────────────────────┐  │
│  │ Marche da Bollo          │  │ Azioni Rapide        │  │
│  │ Medium                   │  │ Medium               │  │
│  └──────────────────────────┘  └──────────────────────┘  │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

### Widget Specifications

#### 1. Guadagni Annui (Small Widget)

**Content**:
```
Guadagni Annui 2026
────────────────────
€ 12.450,00
────────────────────
↑ +15% rispetto 2025
```

**Visual**:
- Large amount: 36px, bold, primary color
- Year label: Small, gray
- Comparison: Small, green if positive, red if negative
- Icon: Arrow up/down

#### 2. Tracker €5.000 INPS (Medium Widget)

**Content**:
```
Limite INPS €5.000
──────────────────────────────────
[████████████░░░░░░] 78% (€3.900)
──────────────────────────────────
Restano €1.100 al limite
⚠️ Riceverai un avviso a €4.500
```

**Visual**:
- Progress bar: 
  - Green if <75%
  - Amber if 75-90%
  - Red if >90%
- Large percentage: Bold
- Remaining amount: Gray, medium size
- Warning icon + text: Amber color
- **Tooltip**: Hover to explain INPS threshold

**Interaction**:
- Click progress bar: Show detailed breakdown
- Link: "Cosa significa?" → Opens explanation modal

#### 3. Ricevute (Small Widget)

**Content**:
```
Ricevute Totali
───────────────
      24
───────────────
3 in attesa marca da bollo
```

**Visual**:
- Count: Large, bold, center-aligned
- Warning text: Amber if pending items
- Link: "Vedi tutte" in footer

#### 4. Scadenze Prossime (Full Width Widget)

**Content**:
```
Scadenze Prossime
─────────────────────────────────────────────────────────────
┌──────────────┬────────────────────────────┬──────────────┐
│ 15 Feb 2026  │ F24 Ritenuta - Committente │ [Dettagli]   │
│ 5 giorni     │ ABC S.r.l.                 │              │
├──────────────┼────────────────────────────┼──────────────┤
│ 28 Feb 2026  │ Marca da bollo - Ricevuta  │ [Completa]   │
│ 18 giorni    │ #RIC-2024-045              │              │
└──────────────┴────────────────────────────┴──────────────┘
[Vedi calendario completo →]
```

**Visual**:
- Table layout
- Date column: Bold, countdown in gray below
- Description: Two lines (type + reference)
- Action button: Small, contextual
- Urgency indicator:
  - Red text if <7 days
  - Amber if 7-30 days
  - Gray if >30 days
- Max 5 items, scrollable or "Vedi tutto"

#### 5. Situazione Fiscale (Medium Widget)

**Content**:
```
La Tua Situazione Fiscale
─────────────────────────────────────
✓ Prestazione Occasionale Pura
  (Sotto €5.000 - Senza obbligo INPS)
─────────────────────────────────────
Dati anagrafici completi
Codice fiscale: RSSMRA85M01H501U
IBAN: IT02...1234
─────────────────────────────────────
[Aggiorna Dati]
```

**Visual**:
- Status: Large text with icon (✓ or ⚠️)
- Status description: Gray, parentheses
- Data list: Small, monospace for fiscal code/IBAN
- Alert box (if issues): Amber background
- CTA button: Update data

**States**:
- **Below €5k**: Green checkmark, "Pura"
- **Above €5k**: Amber warning, "Con INPS - Iscrizione obbligatoria"
- **Missing data**: Red alert, "Dati incompleti"

#### 6. Committenti (Medium Widget)

**Content**:
```
Committenti Attivi (8)
──────────────────────────────────
[Avatar] ABC S.r.l.
         12 ricevute · €8.400

[Avatar] Consulenze XYZ
         5 ricevute · €3.200

[Avatar] Mario Rossi
         7 ricevute · €2.100
──────────────────────────────────
[Vedi tutti i committenti →]
```

**Visual**:
- List item per committente
- Avatar: 40px circle (or initials)
- Name: Bold
- Stats: Gray, small text
- Click: Navigate to committente details
- Max 3-5 items, link to full list

#### 7. Statistiche Mensili (Full Width Widget)

**Content**:
```
Andamento Guadagni Mensili
──────────────────────────────────────────────────────────
[Line/Bar Chart showing monthly earnings]

Gen    Feb    Mar    Apr    Mag    Giu    Lug    Ago ...
€1.2k  €1.8k  €2.1k  €1.5k  €2.3k  €1.9k  €2.0k  €1.7k
──────────────────────────────────────────────────────────
Media mensile: €1.850    |    Trend: ↑ +8%
```

**Visual**:
- Chart: Line or bar chart in primary blue
- Height: 300px
- Axis labels: Gray, small
- Hover: Tooltip with exact value
- Legend: Below chart with summary stats
- Toggle: View by month/quarter/year

#### 8. Marche da Bollo (Medium Widget)

**Content**:
```
Marche da Bollo
──────────────────────────────────
✓ 18 conservate
⚠️ 3 in attesa di applicazione
──────────────────────────────────
Ricevuta #045 (scad. 15 Feb)
Ricevuta #047 (scad. 20 Feb)
Ricevuta #049 (scad. 25 Feb)
──────────────────────────────────
[Gestisci Archivio]
```

**Visual**:
- Status summary: Icons + counts
- Warning list: Amber items with dates
- Link: Open marca da bollo manager
- Upload button: Add new photo

#### 9. Azioni Rapide (Medium Widget)

**Content**:
```
Azioni Rapide
─────────────────────────────
[📄] Crea Nuova Ricevuta

[👥] Aggiungi Committente

[📊] Esporta Dati Anno

[💬] Contatta Supporto
─────────────────────────────
```

**Visual**:
- Button list, stacked
- Icon + text label
- Hover: Background gray-50
- Full-width buttons
- Primary action (Crea Ricevuta) emphasized

---

## 🏢 Dashboard Committente (Client)

### Widget Layout (Desktop)

```
┌────────────────────────────────────────────────────────────┐
│  DASHBOARD HEADER                                          │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ┌─────────────────┐  ┌─────────────────┐  ┌───────────┐ │
│  │ Spesa Totale    │  │ Budget Tracker  │  │ Collab    │ │
│  │ Small           │  │ Medium          │  │ Small     │ │
│  └─────────────────┘  └─────────────────┘  └───────────┘ │
│                                                            │
│  ┌──────────────────────────────────────────────────────┐ │
│  │ Scadenze F24 Prossime                                │ │
│  │ Full Width                                           │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                            │
│  ┌──────────────────────────┐  ┌──────────────────────┐  │
│  │ Ritenute d'Acconto       │  │ Prestatori Attivi    │  │
│  │ Medium                   │  │ Medium               │  │
│  └──────────────────────────┘  └──────────────────────┘  │
│                                                            │
│  ┌──────────────────────────────────────────────────────┐ │
│  │ Statistiche Collaborazioni (Grafico)                 │ │
│  │ Full Width                                           │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

### Key Widget Differences

#### Budget Tracker (Medium Widget)

**Content**:
```
Budget Annuale
──────────────────────────────────
[████████░░░░] 65% usato
──────────────────────────────────
€13.000 / €20.000
Restano €7.000
──────────────────────────────────
📊 Proiezione fine anno: €19.500
⚠️ Possibile sforamento a Novembre
```

**Visual**:
- Progress bar (green <80%, amber 80-95%, red >95%)
- Large fraction display
- Projection with icon
- Warning if approaching limit

#### Ritenute d'Acconto (Medium Widget)

**Content**:
```
Ritenute d'Acconto Q1 2026
──────────────────────────────────
Trattenute:      €2.600
Versate:         €1.800
Da versare:      €800
──────────────────────────────────
Prossimo F24: 16 Feb (5 giorni)
──────────────────────────────────
[Dettaglio Ritenute]
```

**Visual**:
- Three-row summary with amounts
- Amounts: Monospace font, right-aligned
- Next payment: Bold, countdown in gray
- Link to detailed breakdown

---

## 💼 Dashboard Commercialista (Accountant)

### Widget Layout (Desktop)

```
┌────────────────────────────────────────────────────────────┐
│  DASHBOARD HEADER                                          │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ┌─────────────────┐  ┌─────────────────┐  ┌───────────┐ │
│  │ Clienti Attivi  │  │ Documenti       │  │ Guadagni  │ │
│  │ Small           │  │ Small           │  │ Small     │ │
│  └─────────────────┘  └─────────────────┘  └───────────┘ │
│                                                            │
│  ┌──────────────────────────────────────────────────────┐ │
│  │ Coda Revisione Documenti (Priorità)                  │ │
│  │ Full Width                                           │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                            │
│  ┌──────────────────────────┐  ┌──────────────────────┐  │
│  │ Calendario Unificato     │  │ Alert & Anomalie     │  │
│  │ Medium                   │  │ Medium               │  │
│  └──────────────────────────┘  └──────────────────────┘  │
│                                                            │
│  ┌──────────────────────────────────────────────────────┐ │
│  │ Statistiche Multi-Cliente                            │ │
│  │ Full Width                                           │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

### Key Widget Differences

#### Coda Revisione Documenti (Full Width Widget)

**Content**:
```
Documenti da Revisionare (12)
─────────────────────────────────────────────────────────────
┌────────┬─────────────────────┬─────────────┬────────────┐
│ 🔴 URG │ Ricevuta #RIC-045   │ Mario Rossi │ [Revisiona]│
│        │ €1.200 - Scad 2 gg  │ (Prestatore)│            │
├────────┼─────────────────────┼─────────────┼────────────┤
│ 🟡 MED │ F24 Ritenute Feb    │ ABC S.r.l.  │ [Revisiona]│
│        │ €850 - Scad 5 gg    │ (Committente│            │
├────────┼─────────────────────┼─────────────┼────────────┤
│ 🟢 LOW │ CU 2025             │ Laura Bianc │ [Revisiona]│
│        │ Da verificare       │ (Prestatore)│            │
└────────┴─────────────────────┴─────────────┴────────────┘
[Filtra: Tutti | Urgenti | Per Cliente]
```

**Visual**:
- Priority indicators: Color-coded circles
- Sortable columns
- Client name with role badge
- Action buttons per row
- Filter options in footer

#### Alert & Anomalie (Medium Widget)

**Content**:
```
Alert & Anomalie (5)
──────────────────────────────────
⚠️ 2 clienti oltre soglia €5.000
   (INPS non iscritti)

🔴 1 ricevuta senza marca da bollo
   (Scad. imminente)

⚠️ 3 F24 in ritardo
   (Verificare pagamento)
──────────────────────────────────
[Gestisci Alert]
```

**Visual**:
- Grouped by severity
- Icon + count + description
- Click: Navigate to issue detail
- Badge with total count in header

---

## 🔧 Dashboard Admin (Internal - Creator)

### Widget Layout

```
┌────────────────────────────────────────────────────────────┐
│  ADMIN DASHBOARD                                           │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐  │
│  │ Utenti│  │ Ricevute│ │Revenue│  │ MRR   │  │ Churn │  │
│  │ Small │  │ Small  │  │ Small │  │ Small │  │ Small │  │
│  └───────┘  └───────┘  └───────┘  └───────┘  └───────┘  │
│                                                            │
│  ┌──────────────────────────┐  ┌──────────────────────┐  │
│  │ Funnel Conversion        │  │ Statistiche Utenti   │  │
│  │ Medium                   │  │ Medium               │  │
│  └──────────────────────────┘  └──────────────────────┘  │
│                                                            │
│  ┌──────────────────────────────────────────────────────┐ │
│  │ Revenue nel Tempo (Grafico)                          │ │
│  │ Full Width                                           │ │
│  └──────────────────────────────────────────────────────┘ │
│                                                            │
│  ┌──────────────────────────┐  ┌──────────────────────┐  │
│  │ Attività Sistema         │  │ Errori & Performance │  │
│  │ Medium                   │  │ Medium               │  │
│  └──────────────────────────┘  └──────────────────────┘  │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

### Key Metrics Widgets

#### Funnel Conversion (Medium Widget)

**Content**:
```
Conversion Funnel
──────────────────────────────────
Visitatori       →  1.250  (100%)
Registrati       →    345  (27.6%)
Prima Ricevuta   →    198  (57.4%)
Seconda Ricevuta →    142  (71.7%)
Utente Pagante   →    128  (90.1%)
──────────────────────────────────
[Analisi Dettagliata]
```

**Visual**:
- Funnel visualization with bars
- Percentages showing conversion
- Color coding: Green if above target, red if below

---

## 🎨 Common Dashboard Elements

### Empty State

**When**: No data to display in widget

**Visual**:
```
┌──────────────────────────────┐
│                              │
│     [📭 Illustration]        │
│                              │
│   Nessuna ricevuta ancora    │
│                              │
│   [Crea Prima Ricevuta]      │
│                              │
└──────────────────────────────┘
```

- Friendly illustration (not just text)
- Clear explanation
- CTA button to create first item
- Subtle gray colors

### Loading State

**Visual**:
```
┌──────────────────────────────┐
│ Widget Title                 │
│ ─────────────────────────    │
│ [Skeleton Loader Animation]  │
│                              │
│ ░░░░░░░░░░░░░                │
│ ░░░░░░░░░                    │
│ ░░░░░░░░░░░░░░               │
└──────────────────────────────┘
```

- Skeleton loaders matching content shape
- Shimmer animation
- Header visible, body loading

### Error State

**Visual**:
```
┌──────────────────────────────┐
│ Widget Title                 │
│ ─────────────────────────    │
│     [⚠️ Icon]                │
│                              │
│  Errore nel caricamento      │
│  [Riprova]                   │
│                              │
└──────────────────────────────┘
```

- Error icon (amber or red)
- Clear error message
- Retry button
- Optional: "Contatta supporto" link

---

## 📱 Mobile Adaptations

### Mobile Dashboard Layout

**Approach**: Single column, stacked widgets

```
┌──────────────────────┐
│ Mobile Header        │
│ [☰] [Logo] [🔔] [👤]│
├──────────────────────┤
│                      │
│ ┌──────────────────┐ │
│ │ Key Metric 1     │ │
│ └──────────────────┘ │
│                      │
│ ┌──────────────────┐ │
│ │ Key Metric 2     │ │
│ └──────────────────┘ │
│                      │
│ ┌──────────────────┐ │
│ │ Scadenze (List)  │ │
│ └──────────────────┘ │
│                      │
│ [+ Nuova Ricevuta]   │
│                      │
└──────────────────────┘
```

**Optimizations**:
- Show only essential widgets by default
- "Show more" expansion for secondary widgets
- Fixed CTA button at bottom
- Swipeable cards for horizontal browsing
- Collapsible sections

### Mobile Widget Adaptations

**Graphs**: 
- Simplified to show key data points
- Touch-friendly tooltips
- Horizontal scroll for time-series

**Tables**:
- Convert to card list
- Show only essential columns
- "View details" button per row

**Forms**:
- Full-width inputs
- Larger touch targets
- Native mobile keyboards

---

## ♿ Accessibility Requirements

### Keyboard Navigation
- Tab through all interactive elements
- Arrow keys for lists and grids
- Escape to close modals/dropdowns
- Enter/Space to activate

### Screen Readers
- ARIA labels for all widgets
- Announce dynamic content updates
- Descriptive link text (not "click here")
- Landmarks for page regions

### Visual Accessibility
- High contrast mode support
- Scalable text (up to 200%)
- Color + icon for status
- Focus indicators visible

---

## 🎯 Performance Targets

### Load Times
- Initial page load: <2s
- Widget lazy loading: <500ms per widget
- Data refresh: <1s
- Chart rendering: <800ms

### Optimization Strategies
- Lazy load below-fold widgets
- Paginate long lists (max 20 items)
- Cache frequently accessed data
- Optimize images and icons
- Minimize JavaScript bundle size

---

*This dashboard design provides a foundation for all user roles while maintaining consistency and usability.*
