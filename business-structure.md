# 🏢 Struttura del Business - ricevuta.studio

## Documento di Riferimento per Produzione

**Versione**: 1.0  
**Data**: 2026-01-22  
**Status**: Production Ready

---

## 1. Identità del Business

### 1.1 Denominazione
- **Nome**: ricevuta.studio
- **Dominio**: ricevuta.studio (acquisito)
- **Claim**: "prestazione occasionale facile"

### 1.2 Posizionamento
**Facilitatore digitale per la gestione della burocrazia delle prestazioni occasionali in Italia**

- Non è un servizio di consulenza fiscale
- È uno strumento tecnologico programmato secondo normative vigenti
- Complementare al commercialista, non sostitutivo

---

## 2. Value Proposition

### 2.1 Problema Risolto
La complessità e l'ansia legate alla gestione burocratica delle prestazioni occasionali:
- Calcoli fiscali complessi (ritenute, contributi INPS, marca da bollo)
- Documentazione da produrre (ricevute, F24, CU)
- Scadenze fiscali da rispettare
- Paura di commettere errori

### 2.2 Soluzione Offerta
Piattaforma SaaS che automatizza:
- ✅ Generazione ricevute conformi
- ✅ Calcolo automatico ritenute e contributi
- ✅ Creazione F24 pre-compilati
- ✅ Generazione Certificazione Unica (CU)
- ✅ Sistema di notifiche per scadenze
- ✅ Guide step-by-step per adempimenti
- ✅ Archivio documenti centralizzato

### 2.3 Differenziatori Chiave
1. **Approccio friendly**: linguaggio semplice, tono amichevole
2. **Prima transazione gratuita**: riduce barriera all'ingresso
3. **Multi-actor**: serve prestatore, committente E commercialista
4. **Gestione Stripe integrata**: opzionale ma completa
5. **Sistema notifiche proattivo**: l'utente non dimentica scadenze
6. **Referral per commercialisti**: incentivi economici per partnership

---

## 3. Target Market Segmentation

### 3.1 Segmento Primario: Prestatori Occasionali
**Caratteristiche**:
- Privati senza P.IVA
- Reddito occasionale < €5.000/anno (no INPS) o €5.000-€30.000 (con INPS)
- Età: 18-65 anni
- Tech-savvy o digitalizzati

**Pain Points**:
- Ansia per burocrazia
- Timore di sbagliare calcoli
- Non sanno come fare ricevuta
- Paura sanzioni fiscali

**Dimensione stimata**: 500.000-1.000.000 persone/anno in Italia

### 3.2 Segmento Secondario: Committenti
**Caratteristiche**:
- Privati o P.IVA che ingaggiano occasionali
- PMI con collaboratori saltuari
- Professionisti che non vogliono dipendere dal commercialista

**Pain Points**:
- Calcolo ritenute d'acconto
- Generazione F24 e CU
- Gestione scadenze multiple
- Coordinamento con prestatori

**Dimensione stimata**: 200.000-400.000 soggetti/anno

### 3.3 Segmento Terziario: Commercialisti
**Caratteristiche**:
- Studi professionali con clienti occasionali
- Commercialisti individuali
- Tech-forward, cercano efficienza

**Pain Points**:
- Tempo speso su pratiche ripetitive
- Clienti che li disturbano per piccole cose
- Necessità automazione per scalare

**Dimensione stimata**: 15.000-20.000 studi in Italia

---

## 4. Architettura del Servizio

### 4.1 Modalità Operative

#### Modalità Completa (Tutti Registrati)
- Prestatore, committente e commercialista sulla piattaforma
- Collaborazione sincrona
- Massima efficienza

#### Modalità Standalone
**A. Solo Prestatore**:
- Prestatore usa piattaforma, committente no
- Sistema guida prestatore su cosa chiedere al committente
- Notifiche proattive

**B. Solo Committente**:
- Committente usa piattaforma, prestatore no
- Sistema genera documenti committente
- Notifiche su cosa far fare al prestatore

**C. Solo Commercialista**:
- Commercialista gestisce tutto per clienti non registrati
- Può inviare documenti via email ai clienti
- Gestione centralizzata

### 4.2 Flusso Operativo Standard

#### Fase 1: Setup Iniziale
1. Registrazione utente (magic link)
2. Inserimento dati anagrafici/fiscali
3. Scelta modalità operativa
4. Tutorial interattivo (opzionale)

#### Fase 2: Creazione Ricevuta
1. Inserimento dati prestazione
2. Calcolo automatico (lordo/netto/ritenute/INPS)
3. Verifica marca da bollo (se >€77.47)
4. Revisione dati
5. Conferma e pagamento commissione

#### Fase 3: Generazione Documenti
1. Sistema genera PDF ricevuta
2. Sistema genera F24 (se committente sostituto d'imposta)
3. Sistema genera CU (al momento opportuno)
4. Download immediato documenti

#### Fase 4: Gestione Post-Emissione
1. Notifiche scadenze (firma, marca bollo, F24)
2. Tracking adempimenti
3. Archivio documenti
4. Alert automatici

---

## 5. Funzionalità Core

### 5.1 Calcolatore Bidirezionale (Gratuito)
- Input: importo lordo → Output: netto, ritenute, INPS
- Input: importo netto desiderato → Output: lordo da richiedere
- Calcolo marca da bollo automatico
- Pubblico, accessibile senza registrazione
- Chiaro CTA verso SaaS

### 5.2 Generatore Documenti (SaaS)
- Ricevute conformi normativa
- F24 pre-compilati (codici tributo, importi, scadenze)
- CU autogenerata (inizio anno successivo)
- Template personalizzabili
- Branding professionale

### 5.3 Sistema Notifiche Intelligente
- Alert scadenze fiscali
- Promemoria adempimenti
- "Task list" con stato completamento
- Email + notifiche in-app
- Segna come "fatto" → notifica sparisce

### 5.4 Dashboard Analytics
**Prestatore**:
- Tracker €5.000 INPS (barra progressione)
- Totale guadagni annui
- Ricevute emesse
- Scadenze fiscali

**Committente**:
- Totale speso
- Ritenute versate
- Budget tracking (opzionale)
- Scadenze F24

**Commercialista**:
- Vista multi-cliente
- Documenti da revisionare
- Guadagni referral
- Calendario scadenze unificato

### 5.5 Gestione Marca da Bollo
- Calcolo automatico necessità
- Opzione 1: Marca fisica applicata
- Opzione 2: Foto + OCR numero seriale
- Indicazioni conservazione (10 anni)
- Archivio foto marche digitalizzate

### 5.6 Sistema Autorizzazioni
- Collegamento prestatore ↔ committente (bidirezionale)
- Autorizzazione commercialista (richiede consenso entrambi)
- Revoca immediata possibile da tutte le parti
- Log completo accessi

---

## 6. Tech Stack Raccomandato

### 6.1 Frontend
- **Framework**: Next.js 14+ (App Router)
- **UI Library**: React + Tailwind CSS
- **State Management**: Zustand o React Context
- **Forms**: React Hook Form + Zod validation

### 6.2 Backend
- **Runtime**: Next.js API Routes / Server Actions
- **Database**: PostgreSQL (Supabase o Railway)
- **Authentication**: NextAuth.js (magic link)
- **Payment**: Stripe Connect (split payments)
- **File Storage**: AWS S3 o Cloudflare R2

### 6.3 Infrastruttura
- **Hosting**: Vercel (ottimizzato Next.js)
- **CDN**: Vercel Edge Network
- **Email**: Resend o SendGrid
- **Monitoring**: Sentry + Vercel Analytics
- **Logs**: Structured logging + long-term storage

### 6.4 Feature Speciali
- **PDF Generation**: react-pdf o Puppeteer
- **OCR**: Tesseract.js o Google Vision API
- **Notifiche**: Email + Web Push
- **Blog**: MDX + gray-matter (build-time)

---

## 7. Go-to-Market Strategy

### 7.1 Fase 1: MVP Launch (Mesi 1-3)
**Obiettivo**: Validare product-market fit

**Scope Minimo**:
- Modalità completa (tutti registrati)
- Calcolatore gratuito
- Generazione ricevuta + F24 base
- Prima transazione gratis
- Sistema autorizzazioni base

**Canali**:
- SEO: 20 articoli blog ottimizzati
- Google Ads: keyword long-tail ("come fare ricevuta prestazione occasionale")
- Partnership 5-10 commercialisti pilota

**Target Utenti**: 100 utenti paganti (mese 3)

### 7.2 Fase 2: Product Expansion (Mesi 4-6)
**Obiettivo**: Aumentare retention e ridurre churn

**Aggiunte**:
- Modalità standalone (A, B, C)
- Dashboard analytics avanzate
- Template ricevute
- Sistema notifiche completo

**Canali**:
- Content marketing (blog)
- Referral commercialisti (programma attivo)
- Facebook/LinkedIn Ads (targeting PMI)

**Target Utenti**: 500 utenti paganti (mese 6)

### 7.3 Fase 3: Scale (Mesi 7-12)
**Obiettivo**: Crescita sostenibile

**Aggiunte**:
- Integrazione Stripe completa
- Esportazione dati per software contabilità
- API per commercialisti
- White-label per studi grandi

**Canali**:
- Partnership associazioni categoria (ODCEC)
- PR e media coverage
- Affiliazione con piattaforme freelance

**Target Utenti**: 2.000+ utenti paganti (mese 12)

---

## 8. Revenue Streams

### 8.1 Revenue Primario: Commissioni Transazionali
- **Senza Stripe**: 0.8-1.8% per ricevuta
- **Con Stripe**: 1.5-4.0% per ricevuta
- **Ricorrente**: utenti multi-ricevuta = MRR prevedibile

### 8.2 Revenue Secondario: Premium Features (Futuro)
- Piano commercialista "Pro" (€29/mese):
  - Gestione illimitata clienti
  - White-label documenti
  - Priorità supporto
  - API access

### 8.3 Revenue Terziario: Partnership/Affiliazioni
- Affiliazione con servizi complementari:
  - Assicurazioni professionali
  - Software contabilità
  - Piattaforme freelance

---

## 9. Metriche di Successo (KPI)

### 9.1 Acquisition
- **Traffico organico**: visitatori unici/mese
- **Conversion rate**: visitatore → registrato (target: 5-10%)
- **CAC** (Customer Acquisition Cost): target <€15

### 9.2 Activation
- **First transaction rate**: registrato → prima ricevuta (target: 40%+)
- **Time to value**: giorni da registrazione a prima ricevuta (target: <7gg)

### 9.3 Retention
- **Second transaction rate**: CRITICO (target: 30%+)
- **6-month retention**: utenti attivi dopo 6 mesi (target: 25%+)
- **Churn rate mensile**: target <10%

### 9.4 Revenue
- **ARPU** (Average Revenue Per User): target €15-25/anno
- **LTV** (Lifetime Value): target €30-50
- **LTV/CAC ratio**: target >3:1

### 9.5 Referral
- **Commercialisti attivi**: numero (target: 50 anno 1)
- **Utenti da referral**: % sul totale (target: 20%+)
- **Referral conversion**: referral → utente pagante (target: 15%+)

---

## 10. Risk Assessment

### 10.1 Rischi Principali

#### Rischio 1: Low Transaction Frequency (ALTO)
**Problema**: Utenti usano 1-2x/anno → basso LTV  
**Mitigazione**:
- Focus su committenti ricorrenti
- Partnership commercialisti (multi-cliente)
- Espansione servizi correlati

#### Rischio 2: Retention Post-Free (ALTO)
**Problema**: Utenti provano gratis e non tornano  
**Mitigazione**:
- Email nurturing aggressivo
- Incentivi "torna entro 30gg"
- Features che creano lock-in (storico, analytics)

#### Rischio 3: Complessità Normativa (MEDIO)
**Problema**: Normativa cambia, sistema obsoleto  
**Mitigazione**:
- Monitoring continuo aggiornamenti INPS/Agenzia Entrate
- Advisory board commercialisti
- Disclaimer robusto responsabilità

#### Rischio 4: Competizione (MEDIO)
**Problema**: Competitor entra con più risorse  
**Mitigazione**:
- First-mover advantage (SEO)
- Network effect (commercialisti)
- Differenziazione UX (friendly vs corporate)

#### Rischio 5: Margini Stripe (MEDIO)
**Problema**: Commissioni Stripe erodono margini  
**Mitigazione**:
- Aumentare pricing modalità Stripe (vedi pricing-strategy-analysis.md)
- Incentivare modalità senza Stripe
- Volume discounts con Stripe

### 10.2 Exit Criteria (Kill Switches)

**Valutare pivot/chiusura se**:
- Retention 6 mesi <15% (dopo 12 mesi launch)
- CAC >€30 sostenuto (rapporto LTV/CAC <2:1)
- Impossibilità migliorare unit economics
- Cambio normativo rende servizio obsoleto/illegale

---

## 11. Espansione Geografica (Futuro)

### 11.1 Mercati Target
1. **Svizzera** (Ticino): lingua italiana, normativa simile
2. **Spagna**: mercato grande, problema simile
3. **Francia**: prestazioni occasionali molto comuni

### 11.2 Requisiti Pre-Espansione
- Product-market fit solido in Italia (retention >30%)
- Revenue Italia >€100k/anno
- Team con competenze legali locali
- Budget marketing €20k+ per paese

---

## 12. Conclusioni

### 12.1 Punti di Forza
✅ Mercato esistente con pain point reale  
✅ Soluzione chiara e differenziata  
✅ Multi-actor con network effects  
✅ Prima transazione gratis = bassa barriera  
✅ Referral commercialisti = growth lever potente  
✅ Scalabile tecnologicamente  

### 12.2 Sfide Principali
⚠️ Retention: la metrica più critica  
⚠️ Frequency: utenti poco ricorrenti  
⚠️ Margini Stripe: servono aggiustamenti pricing  
⚠️ MVP scope: troppo ampio, semplificare  

### 12.3 Raccomandazione Finale
**PROCEDERE con MVP ridotto**

Priorità assoluta:
1. Modalità completa + calcolatore gratuito
2. SEO content (60% effort marketing)
3. Partnership 10 commercialisti pilota
4. Ossessione su retention metric

Evitare:
- Modalità standalone in MVP
- Integrazione Stripe in V1 (troppo complessa)
- Over-engineering dashboard analytics

---

**Prossimi Passi**:
1. Leggere `pricing-model.md` per dettagli pricing ottimizzato
2. Leggere `referral-program.md` per implementazione referral
3. Leggere `business-recommendations.md` per azioni specifiche
