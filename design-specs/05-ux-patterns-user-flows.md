# 🎯 UX Patterns & User Flows - ricevuta.studio

> **Document Type**: UX/Interaction Design Specifications  
> **Platform**: ricevuta.studio  
> **Version**: 1.0  
> **Created**: 2026-01-22  
> **Purpose**: Define user experience patterns, interaction flows, and usability guidelines

---

## 📌 UX Philosophy

### Core UX Principles

**1. Progressive Disclosure**
- Show essential information first
- Reveal complexity on demand
- Avoid overwhelming users with options
- Use "Show more" / "Advanced options" patterns

**2. Prevent Errors**
- Validate input in real-time
- Provide clear field requirements
- Use appropriate input types (date picker, number, dropdown)
- Disable invalid actions rather than show errors

**3. Provide Feedback**
- Immediate visual feedback for actions
- Loading states for async operations
- Success/error messages with next steps
- Progress indicators for multi-step processes

**4. Maintain Context**
- Clear navigation breadcrumbs
- Highlight current page/section
- Preserve user state (don't lose data on navigation)
- Remember preferences and settings

**5. Reduce Cognitive Load**
- One primary action per screen
- Clear visual hierarchy
- Consistent patterns across platform
- Familiar UI conventions

---

## 🔐 Authentication Flows

### Magic Link Registration/Login

**Flow**:
```
┌────────────────────────────────────────────────────────┐
│ 1. Landing Page                                        │
│    User clicks "Registrati" or "Accedi"                │
│    ↓                                                   │
│ 2. Email Input Modal                                   │
│    "Inserisci la tua email"                            │
│    [email@example.com]                                 │
│    [Continua →]                                        │
│    ↓                                                   │
│ 3. Email Sent Confirmation                             │
│    ✉️ "Controlla la tua email"                         │
│    "Abbiamo inviato un link magico a email@..."        │
│    "Clicca il link per accedere (valido 15 minuti)"   │
│    [Invia di nuovo] [Cambia email]                     │
│    ↓                                                   │
│ 4. User Clicks Link in Email                           │
│    Opens in same or new browser                        │
│    ↓                                                   │
│ 5. Authentication & Redirect                           │
│    Loading screen: "Accesso in corso..."               │
│    ↓                                                   │
│ 6a. First Time User → Onboarding                       │
│ 6b. Returning User → Dashboard                         │
└────────────────────────────────────────────────────────┘
```

**Modal Design**:
```
┌──────────────────────────────────────┐
│                [×]                   │
│                                      │
│  Accedi a ricevuta.studio            │
│                                      │
│  Inserisci la tua email per          │
│  ricevere un link di accesso         │
│                                      │
│  ┌────────────────────────────────┐ │
│  │ email@example.com              │ │
│  └────────────────────────────────┘ │
│                                      │
│  [Continua →]                        │
│                                      │
│  ──────── o ────────                 │
│                                      │
│  Continuando accetti i               │
│  Termini e la Privacy Policy         │
│                                      │
└──────────────────────────────────────┘
```

**UX Considerations**:
- No password required (magic link only)
- Clear explanation of process
- Email validation before sending
- Resend option (cooldown: 60 seconds)
- Link expiry: 15 minutes
- Handle "link already used" gracefully
- Support opening in different browser/device

---

## 🎓 First-Time User Onboarding

### Onboarding Flow (Post-Login)

**Step 1: Role Selection**
```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  Benvenuto su ricevuta.studio! 👋                   │
│                                                      │
│  Chi sei? Seleziona il tuo ruolo principale:        │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │  👤 Prestatore                                 │ │
│  │  Offro prestazioni occasionali                 │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │  🏢 Committente                                │ │
│  │  Acquisto prestazioni occasionali              │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │  💼 Commercialista                             │ │
│  │  Gestisco clienti prestatori/committenti       │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  [Salta per ora]                      [Continua →]  │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Details**:
- Large clickable cards (not small radios)
- Icon + title + description per option
- Can skip and set later
- "Continua" disabled until selection
- Progress indicator: 1/4 steps

**Step 2: Profile Setup (Role-Specific)**

**For Prestatore**:
```
┌──────────────────────────────────────────────────────┐
│  [Progress: ████░░░░ 2/4]                           │
│                                                      │
│  Completa il tuo profilo                            │
│                                                      │
│  Nome e Cognome *                                   │
│  ┌────────────────────────────────────────────────┐ │
│  │ Mario Rossi                                    │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  Codice Fiscale *                                   │
│  ┌────────────────────────────────────────────────┐ │
│  │ RSSMRA85M01H501U                               │ │
│  └────────────────────────────────────────────────┘ │
│  ✓ Codice fiscale valido                            │
│                                                      │
│  IBAN (opzionale)                                   │
│  ┌────────────────────────────────────────────────┐ │
│  │ IT60X0542811101000000123456                    │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  [← Indietro]                        [Continua →]  │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Details**:
- Real-time validation (codice fiscale format)
- Visual checkmark on valid input
- Helper text below fields
- Optional fields marked clearly
- Auto-format IBAN with spaces
- Can skip and complete later

**Step 3: Quick Tour**
```
┌──────────────────────────────────────────────────────┐
│  [Progress: ████████░░ 3/4]                         │
│                                                      │
│  [Illustration: Dashboard Overview]                 │
│                                                      │
│  La tua Dashboard                                   │
│                                                      │
│  Qui troverai:                                      │
│  ✓ Tutte le tue ricevute                            │
│  ✓ Scadenze e notifiche                             │
│  ✓ Statistiche e guadagni                           │
│  ✓ Tracker limite €5.000 INPS                       │
│                                                      │
│  [← Indietro]  [Salta tour]          [Avanti →]    │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Details**:
- 3-4 slides max (don't overwhelm)
- Visual illustrations
- Key benefits highlighted
- Can skip entire tour
- Dots indicate progress

**Step 4: First Action Prompt**
```
┌──────────────────────────────────────────────────────┐
│  [Progress: ████████████ 4/4]                       │
│                                                      │
│  Sei pronto! 🎉                                     │
│                                                      │
│  Cosa vuoi fare per primo?                          │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │  📄 Crea la tua prima ricevuta                 │ │
│  │  (GRATUITA - nessuna commissione!)             │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │  🧮 Prova il calcolatore                       │ │
│  │  Calcola ritenute e contributi                 │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │  📚 Esplora le guide                           │ │
│  │  Scopri come funzionano le prestazioni        │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  [Vai alla Dashboard]                               │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Details**:
- Celebrate completion (emoji, confetti animation)
- Offer clear next actions
- Highlight free first transaction
- Can go directly to dashboard
- No "dead end" - always a clear path forward

---

## 📄 Core Flow: Creating a Ricevuta

### Multi-Step Form Pattern

**Step Navigation**:
```
[1. Dati Base] → [2. Importi] → [3. Opzioni] → [4. Revisione]
    ACTIVE      INCOMPLETE    INCOMPLETE    INCOMPLETE
```

**Step 1: Dati Base**
```
┌──────────────────────────────────────────────────────┐
│  Nuova Ricevuta - Dati Base                    [×]   │
│  ─────────────────────────────────────────────────   │
│  [1.Dati] → [2.Importi] → [3.Opzioni] → [4.Revisione]│
│                                                      │
│  Committente *                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │ Seleziona committente...           [▼]        │ │
│  └────────────────────────────────────────────────┘ │
│  [+ Aggiungi nuovo committente]                     │
│                                                      │
│  Data Prestazione *                                 │
│  ┌────────────────────────────────────────────────┐ │
│  │ 15/01/2026                         [📅]        │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  Descrizione Prestazione *                          │
│  ┌────────────────────────────────────────────────┐ │
│  │ Consulenza informatica sviluppo software      │ │
│  │                                                │ │
│  │                                                │ │
│  └────────────────────────────────────────────────┘ │
│  Caratteri: 150/500                                 │
│                                                      │
│  [Annulla]                           [Avanti →]     │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Patterns**:
- **Dropdown with Search**: Committente dropdown with autocomplete
- **Quick Add**: "+ Aggiungi nuovo" opens inline form or modal
- **Date Picker**: Native calendar picker
- **Textarea with Counter**: Show character limit and current count
- **Validation**: Mark required fields with *
- **Save Draft**: Auto-save every 30 seconds (with indicator)
- **Navigation**: "Avanti" disabled until required fields valid

**Step 2: Importi**
```
┌──────────────────────────────────────────────────────┐
│  Nuova Ricevuta - Importi                      [×]   │
│  ─────────────────────────────────────────────────   │
│  [1.Dati] ✓ [2.Importi] → [3.Opzioni] → [4.Revisione]│
│                                                      │
│  Calcola da:                                        │
│  ○ Importo Lordo      ● Importo Netto               │
│                                                      │
│  Importo Netto *                                    │
│  ┌────────────────────────────────────────────────┐ │
│  │ € 1.000,00                                     │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │ 📊 Riepilogo Automatico                        │ │
│  │ ────────────────────────────────────────       │ │
│  │ Importo Lordo:        € 1.670,13               │ │
│  │ Ritenuta 20%:         € 334,03                 │ │
│  │ INPS 33.72%:          € 336,10                 │ │
│  │ Importo Netto:        € 1.000,00               │ │
│  │ ────────────────────────────────────────       │ │
│  │ ⚠️ Marca da bollo richiesta (€2,00)            │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  [← Indietro]                        [Avanti →]     │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Patterns**:
- **Real-Time Calculation**: Update breakdown immediately on input
- **Toggle Input Mode**: Switch between gross/net easily
- **Visual Breakdown**: Clear table with calculations
- **Warning Indicators**: Marca da bollo alert
- **Previous Step Checkmark**: Show completed steps
- **Data Persistence**: Previous step data saved

**Step 3: Opzioni**
```
┌──────────────────────────────────────────────────────┐
│  Nuova Ricevuta - Opzioni Aggiuntive           [×]   │
│  ─────────────────────────────────────────────────   │
│  [1.Dati]✓ [2.Importi]✓ [3.Opzioni] → [4.Revisione] │
│                                                      │
│  Modalità Pagamento                                 │
│  ┌────────────────────────────────────────────────┐ │
│  │ Bonifico bancario                  [▼]        │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  ☐ Applica split payment                            │
│     ℹ️ Cos'è lo split payment?                      │
│                                                      │
│  ☐ Includi note aggiuntive                          │
│  ┌────────────────────────────────────────────────┐ │
│  │ (opzionale)                                    │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  ☑ Invia ricevuta via email                         │
│     A: committente@example.com                      │
│                                                      │
│  [← Indietro]                        [Avanti →]     │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Patterns**:
- **Optional Fields**: Clearly marked as "(opzionale)"
- **Contextual Help**: Info tooltips for complex concepts
- **Smart Defaults**: Pre-check common options
- **Conditional Fields**: Show email field only if checkbox checked
- **Skip Option**: Can proceed without filling optional fields

**Step 4: Revisione e Conferma**
```
┌──────────────────────────────────────────────────────┐
│  Nuova Ricevuta - Revisione                    [×]   │
│  ─────────────────────────────────────────────────   │
│  [1.Dati]✓ [2.Importi]✓ [3.Opzioni]✓ [4.Revisione]  │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │ 📄 Anteprima Ricevuta                          │ │
│  │                                                │ │
│  │ [Visual Preview of Receipt]                   │ │
│  │                                                │ │
│  │ Prestatore: Mario Rossi                        │ │
│  │ CF: RSSMRA85M01H501U                           │ │
│  │                                                │ │
│  │ Committente: ABC S.r.l.                        │ │
│  │ P.IVA: 12345678901                             │ │
│  │                                                │ │
│  │ Prestazione: Consulenza informatica...         │ │
│  │ Data: 15/01/2026                               │ │
│  │                                                │ │
│  │ Importo Lordo:    € 1.670,13                   │ │
│  │ Ritenuta:         € 334,03                     │ │
│  │ INPS:             € 336,10                     │ │
│  │ Netto:            € 1.000,00                   │ │
│  │                                                │ │
│  │ [✏️ Modifica]                                  │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  ☑ Ho letto e accetto che questa ricevuta          │
│     necessita di verifica professionale            │
│                                                      │
│  [← Indietro]      [Salva Bozza]    [Genera →]     │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Patterns**:
- **Full Preview**: Show receipt exactly as it will appear
- **Edit Access**: Click section to edit (returns to that step)
- **Confirmation Checkbox**: Legal disclaimer acknowledgment
- **Multiple Actions**: 
  - Save as draft (no generation)
  - Generate receipt (commits)
- **Loading State**: "Generazione in corso..." on submit

**Success Screen**
```
┌──────────────────────────────────────────────────────┐
│                                                      │
│             🎉 Ricevuta Creata!                     │
│                                                      │
│  La tua ricevuta #RIC-2026-001 è pronta            │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │  [📥 Scarica PDF]     [✉️ Invia Email]       │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  Cosa fare ora:                                     │
│  ☐ Applica marca da bollo (se richiesta)            │
│  ☐ Firma la ricevuta                                │
│  ☐ Invia al committente                             │
│  ☐ Archivia copia                                   │
│                                                      │
│  Prossimi passi:                                    │
│  • F24 da pagare entro: 16 Feb 2026                │
│  • CU disponibile a: Marzo 2027                     │
│                                                      │
│  [Crea Altra Ricevuta]    [Vai alla Dashboard]     │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**UX Patterns**:
- **Celebration**: Visual feedback for success
- **Immediate Actions**: Download/email available instantly
- **Next Steps Checklist**: Clear guidance on what to do
- **Future Reminders**: Proactive deadline notifications
- **Clear Paths Forward**: Multiple options to continue

---

## 🔔 Notification Patterns

### Notification Center

**Access**: Bell icon in top navigation with badge count

**Dropdown Panel**:
```
┌────────────────────────────────────────────────────┐
│  Notifiche (3)                         [Segna tutte]│
├────────────────────────────────────────────────────┤
│                                                    │
│  ● Scadenza Imminente                             │
│    F24 da pagare entro 5 giorni                   │
│    [Vedi Dettagli]                    2 ore fa    │
│                                                    │
│  ● Soglia INPS                                    │
│    Hai raggiunto €4.500 (90% del limite)          │
│    [Scopri di più]                    1 giorno fa │
│                                                    │
│  ○ Marca da Bollo                                 │
│    Ricevuta #045 necessita marca da bollo         │
│    [Completa]                         3 giorni fa │
│                                                    │
├────────────────────────────────────────────────────┤
│  [Vedi Tutte le Notifiche →]                      │
└────────────────────────────────────────────────────┘
```

**Visual Hierarchy**:
- **Unread**: Bold, filled dot, white background
- **Read**: Normal weight, hollow dot, gray-50 background
- **Priority**: Red dot for urgent, amber for warnings, blue for info
- **Action Buttons**: Contextual actions per notification
- **Timestamp**: Relative time (2 ore fa, 1 giorno fa)
- **Max 5 in dropdown**: Link to full page for more

### In-App Notifications (Toasts)

**Success Toast**:
```
┌────────────────────────────────────┐
│ ✓ Ricevuta salvata con successo   │
│   [Visualizza] [×]                 │
└────────────────────────────────────┘
```

**Error Toast**:
```
┌────────────────────────────────────┐
│ ✕ Impossibile salvare ricevuta     │
│   Controlla i dati e riprova       │
│   [Riprova] [×]                    │
└────────────────────────────────────┘
```

**Warning Toast**:
```
┌────────────────────────────────────┐
│ ⚠ Attenzione: zona grigia normativa│
│   Ti consigliamo consulenza         │
│   [Scopri di più] [×]              │
└────────────────────────────────────┘
```

**Info Toast**:
```
┌────────────────────────────────────┐
│ ℹ️ Nuova guida disponibile          │
│   "Come applicare marca da bollo"  │
│   [Leggi] [×]                      │
└────────────────────────────────────┘
```

**Positioning**: 
- Top-right corner (desktop)
- Top-center (mobile)
- Stack multiple toasts
- Auto-dismiss: 5s (can close manually)
- Slide-in animation

---

## ⚠️ Error Handling Patterns

### Form Validation Errors

**Inline Field Error**:
```
Codice Fiscale *
┌────────────────────────────────────┐
│ RSSMRA85M01                        │
└────────────────────────────────────┘
✕ Codice fiscale non valido (16 caratteri richiesti)
```

**Visual**:
- Red border on input
- Red X icon
- Red error message below
- Remove error on valid input

**Multiple Errors Summary**:
```
┌────────────────────────────────────────────────────┐
│ ⚠️ Correggi i seguenti errori:                     │
│                                                    │
│ • Codice fiscale non valido                       │
│ • Importo deve essere maggiore di €0              │
│ • Data prestazione richiesta                      │
│                                                    │
│ [Chiudi]                                          │
└────────────────────────────────────────────────────┘
```

### Page-Level Errors

**Network Error**:
```
┌────────────────────────────────────────────────────┐
│                                                    │
│               [🌐 Icon]                            │
│                                                    │
│         Connessione Persa                          │
│                                                    │
│    Non riusciamo a connetterci al server.          │
│    Controlla la tua connessione internet.          │
│                                                    │
│    [Riprova]                                       │
│                                                    │
└────────────────────────────────────────────────────┘
```

**404 Not Found**:
```
┌────────────────────────────────────────────────────┐
│                                                    │
│               [🔍 Icon]                            │
│                                                    │
│         Pagina Non Trovata                         │
│                                                    │
│    La pagina che stai cercando non esiste.         │
│                                                    │
│    [Vai alla Dashboard]  [Contatta Supporto]      │
│                                                    │
└────────────────────────────────────────────────────┘
```

**Permission Denied**:
```
┌────────────────────────────────────────────────────┐
│                                                    │
│               [🔒 Icon]                            │
│                                                    │
│         Accesso Negato                             │
│                                                    │
│    Non hai i permessi per visualizzare             │
│    questa risorsa.                                 │
│                                                    │
│    [Torna Indietro]                                │
│                                                    │
└────────────────────────────────────────────────────┘
```

---

## 🎯 Decision Points & Modals

### Confirmation Dialog (Destructive Action)

**Delete Confirmation**:
```
┌────────────────────────────────────────────────────┐
│                                             [×]    │
│                                                    │
│  Eliminare questa ricevuta?                       │
│                                                    │
│  Ricevuta #RIC-2026-045                           │
│  Committente: ABC S.r.l.                          │
│  Importo: €1.000,00                               │
│                                                    │
│  ⚠️ Questa azione non può essere annullata.        │
│                                                    │
│  [Annulla]                    [Elimina Ricevuta]  │
│                                                    │
└────────────────────────────────────────────────────┘
```

**UX Patterns**:
- **Show Context**: Display what will be deleted
- **Warning**: Clear consequence statement
- **Button Hierarchy**: 
  - Destructive action: Red, right side
  - Cancel: Secondary, left side
- **Confirmation Required**: Consider "type DELETE to confirm" for critical actions
- **Focus**: Default focus on Cancel (safe option)

### Gray Area Warning Modal

**Fiscal Gray Area Alert**:
```
┌────────────────────────────────────────────────────┐
│                                             [×]    │
│                                                    │
│  ⚠️ Attenzione: Zona Grigia Normativa             │
│                                                    │
│  Hai raggiunto €15.000 di ricevute quest'anno.    │
│  La normativa non definisce chiaramente il        │
│  limite massimo per prestazioni occasionali.      │
│                                                    │
│  Ti consigliamo di:                               │
│  • Consultare un commercialista                   │
│  • Valutare apertura P.IVA                        │
│  • Verificare la tua situazione specifica         │
│                                                    │
│  [📖 Leggi Approfondimento]                       │
│                                                    │
│  ☑ Ho capito e procedo comunque                   │
│                                                    │
│  [Annulla]                         [Continua]     │
│                                                    │
└────────────────────────────────────────────────────┘
```

**UX Patterns**:
- **Non-Blocking**: Can proceed after acknowledgment
- **Educational**: Explain the issue
- **Recommendations**: Clear next steps
- **Checkbox**: Must acknowledge to continue
- **Link**: Deep dive article in blog
- **Track Decision**: Log user acknowledgment

---

## 🔍 Search Patterns

### Global Search

**Search Bar (Top Nav)**:
```
┌────────────────────────────────────────────┐
│ 🔍  Cerca ricevute, utenti...              │
└────────────────────────────────────────────┘
```

**Search Results Dropdown**:
```
┌────────────────────────────────────────────────────┐
│  Risultati per "ABC"                               │
├────────────────────────────────────────────────────┤
│  Ricevute (3)                                      │
│  📄 #RIC-045 - ABC S.r.l. - €1.000                │
│  📄 #RIC-038 - ABC S.r.l. - €800                  │
│  📄 #RIC-022 - ABC S.r.l. - €1.200                │
│  [Vedi tutte le ricevute →]                       │
├────────────────────────────────────────────────────┤
│  Committenti (1)                                   │
│  🏢 ABC S.r.l. - 12 ricevute                      │
│  [Vedi dettagli →]                                │
├────────────────────────────────────────────────────┤
│  Nessun risultato in: Prestatori, Documenti       │
└────────────────────────────────────────────────────┘
```

**UX Patterns**:
- **Instant Search**: Results while typing (debounced)
- **Grouped Results**: By entity type
- **Max 3 per group**: Link to see all
- **Highlight Match**: Bold matching text
- **Keyboard Navigation**: Arrow keys + Enter
- **Recent Searches**: Show below empty search
- **No Results**: Suggest alternatives or help

---

## 📱 Mobile-Specific Patterns

### Bottom Navigation (Mobile)

```
┌────────────────────────────────────┐
│                                    │
│  [Content Area]                    │
│                                    │
├────────────────────────────────────┤
│ [🏠]  [📄]  [➕]  [📊]  [👤]       │
│ Home  Docs  New  Stats  Account    │
└────────────────────────────────────┘
```

**UX Patterns**:
- **Fixed Bottom**: Always visible
- **5 Items Max**: Most important actions
- **Center Action**: Primary CTA (New) in center
- **Active Indicator**: Color + bold label
- **Large Touch Targets**: 48px minimum

### Mobile Drawer Menu

**Slide-Out Menu**:
```
┌────────────────────────────────────┐
│  [×]                               │
│                                    │
│  👤 Mario Rossi                    │
│  Prestatore                        │
│                                    │
│  ────────────────────────           │
│                                    │
│  🏠 Dashboard                      │
│  📄 Ricevute                       │
│  👥 Collaboratori                  │
│  📂 Documenti                      │
│  📅 Scadenze                       │
│  📊 Statistiche                    │
│                                    │
│  ────────────────────────           │
│                                    │
│  ⚙️ Impostazioni                   │
│  💬 Supporto                       │
│  🚪 Logout                         │
│                                    │
└────────────────────────────────────┘
```

### Pull-to-Refresh

**Visual Feedback**:
1. User pulls down from top
2. Loading spinner appears
3. "Aggiornamento..." text
4. Content refreshes
5. Spinner disappears

### Swipe Actions (Lists)

**Swipe Left/Right on List Item**:
```
┌────────────────────────────────────┐
│ ← Elimina  | Ricevuta #045  | Modifica → │
└────────────────────────────────────┘
```

**Options**:
- Swipe right: Primary action (Edit)
- Swipe left: Destructive action (Delete)
- Color-coded backgrounds
- Icon + label

---

## ♿ Accessibility Patterns

### Focus Management
- Visible focus indicators (3px outline)
- Logical tab order
- Focus trap in modals
- Return focus on close

### Screen Reader Support
- Semantic HTML (header, nav, main, article)
- ARIA labels on interactive elements
- Announce dynamic content changes
- Skip links for navigation

### Keyboard Shortcuts
```
Ctrl/Cmd + K    → Global search
Ctrl/Cmd + N    → New ricevuta
Esc             → Close modal/dropdown
Tab             → Next field
Shift + Tab     → Previous field
Enter           → Submit/confirm
Space           → Toggle checkbox
Arrow keys      → Navigate lists
```

### Color Accessibility
- Never rely on color alone
- Use icons + text for status
- WCAG AA contrast minimum
- Color-blind friendly palette

---

## 🎯 Performance Patterns

### Loading States
- Skeleton loaders for content
- Spinners for actions
- Progress bars for uploads
- Optimistic UI updates

### Infinite Scroll vs Pagination
- **Dashboards**: Paginate (predictable)
- **Feeds**: Infinite scroll (discovery)
- **Tables**: Pagination with page size options
- **Search Results**: Pagination with "Load more"

### Caching Strategy
- Cache frequently accessed data
- Refresh stale data in background
- Local storage for preferences
- Service worker for offline support

---

*These UX patterns ensure a consistent, intuitive, and accessible experience across the entire platform.*
