# 📋 Raccomandazioni Strategiche - ricevuta.studio

## Documento Executive per Decision Making

**Versione**: 1.0  
**Data**: 2026-01-22  
**Status**: Pronto per Implementazione  
**Autore**: Business Model & Pricing Analysis Team

---

## 1. Executive Summary

### 1.1 Valutazione Complessiva

**Rating Business Model**: ⭐⭐⭐⭐☆ (7.5/10)

**Verdetto**: **PROCEDERE con modifiche strategiche**

Il progetto ricevuta.studio ha **fondamenta solide** e affronta un **problema reale** in un mercato underserved. Tuttavia, richiede **ottimizzazioni critiche** prima del lancio per garantire sostenibilità economica e crescita scalabile.

### 1.2 Punti di Forza Principali

✅ **Problema chiaro e doloroso**: Burocrazia prestazioni occasionali in Italia  
✅ **Mercato esistente e quantificabile**: 500k-1M prestatori/anno  
✅ **Multi-sided platform**: Network effects potenziali  
✅ **Differenziazione forte**: Tono friendly vs competitor corporate  
✅ **Prima transazione gratis**: Barrier to entry bassa  
✅ **Referral commercialisti**: Growth lever potente (10% lifetime)  
✅ **Scalabilità tecnica**: SaaS puro, margini alti  

### 1.3 Criticità da Risolvere

🔴 **CRITICO - Margini Stripe troppo bassi**: 3-4% commissioni non coprono costi (Stripe mangia 1.4% + €0.25)  
🔴 **CRITICO - Retention incerta**: Utenti occasionali (1-2x/anno) = LTV basso  
🟡 **IMPORTANTE - MVP troppo complesso**: Modalità standalone aumentano scope 3x  
🟡 **IMPORTANTE - Referral 10% lifetime**: Rischio overshooting se scale  
🟢 **MINORE - Mancanza price anchoring**: Nessun piano premium per far sembrare base "economico"  

---

## 2. Raccomandazioni Pre-Launch (CRITICHE)

### 2.1 ⚠️ AZIONE IMMEDIATA: Aumentare Pricing Stripe

**Problema**:  
Con commissioni 1.5% + 1.5% = 3% totale e Stripe fee 1.4% + €0.25, i margini sono **troppo sottili** (<20% su ricevute <€500).

**Raccomandazione**:  
```diff
- Prestatore: 1.5% | Committente: 1.5% (privati) = 3.0% totale
- Prestatore: 1.5% | Committente: 2.5% (sostituto) = 4.0% totale

+ Prestatore: 2.5% | Committente: 2.5% (privati) = 5.0% totale
+ Prestatore: 2.5% | Committente: 3.0% (sostituto) = 5.5% totale
```

**Impatto**:
- Margini netti con Stripe: da 17-20% a **71-74%** ✅
- Prezzo rimane competitivo vs commercialista (€30-50)
- Break-even più veloce: mese 8 invece di 18

**Quando**: PRIMA del lancio (impossibile aumentare dopo senza backlash).

---

### 2.2 ⚠️ AZIONE IMMEDIATA: Semplificare MVP

**Problema**:  
Modalità standalone (solo prestatore, solo committente, solo commercialista) triplicano la complessità di sviluppo e testing.

**Raccomandazione**:  
**Eliminare modalità standalone da MVP** (V1).

**MVP V1 include SOLO**:
- ✅ Modalità completa (tutti registrati)
- ✅ Calcolatore gratuito
- ✅ Generazione ricevuta + F24 base
- ✅ Prima transazione gratis (senza Stripe)
- ✅ Dashboard base
- ✅ Sistema notifiche semplice
- ❌ ~~Modalità standalone~~ → V2 (post-validation)
- ❌ ~~Integrazione Stripe~~ → V2 (troppo complessa)

**Benefici**:
- Time to market: **2-3 mesi invece di 6**
- Focus su core value proposition
- Testing più facile
- Pivot più veloce se necessario

**Quando implementare standalone**: Solo se retention 6 mesi >30% e PMF validato.

---

### 2.3 🟡 AZIONE CONSIGLIATA: Ridurre Referral a 7%

**Problema**:  
10% lifetime è **generoso** (2-3x standard) e rischia di erodere margini se scale con high-frequency users.

**Raccomandazione**:  
```diff
- Commercialista guadagna: 10% commissioni lifetime
+ Commercialista guadagna: 7% commissioni lifetime
```

**Analisi**:
| Metrica | 10% Lifetime | 7% Lifetime |
|---------|-------------|-------------|
| Margine piattaforma (senza Stripe) | 90% | 93% |
| Guadagno comm. per utente (5 trans.) | €5.00 | €3.50 |
| LTV/CAC ratio vs organico | 3.3:1 | 4.7:1 |
| Sostenibilità high-frequency | ⚠️ Rischio | ✅ Sicuro |

**Alternativa conservativa**: Start con 7%, aumentare a 10% dopo 1 anno se metriche permettono.

**Contro-argomento**: 10% è più attrattivo per commercialisti. Ma 7% è comunque **2x CAC organico**, molto competitivo.

---

### 2.4 ✅ AZIONE CONFERMATA: Prima Transazione Gratis

**Validazione**: Strategia corretta ✅

**Ma aggiungere**:
- **Verifica identità obbligatoria** (upload documento)
- Device fingerprinting anti-abuse
- Limite 1x per codice fiscale (non per email)

**Costo abuse prevention**: €0.50-1 per verifica (Stripe Identity o Onfido).  
**ROI**: Vale la pena per evitare abusi (utenti multipli account).

---

## 3. Roadmap Consigliata (Prioritizzata)

### 3.1 Fase 0: Pre-Launch (Mesi -2 a 0)

**Obiettivo**: Setup fondamenta

- [ ] Registrare dominio e setup hosting
- [ ] Design system e mockup UI (vedi design-specs/)
- [ ] Setup analytics (Vercel Analytics + Posthog)
- [ ] **SEO**: Pubblicare 20 articoli blog ottimizzati
- [ ] **Partnership**: Contattare 20 commercialisti, chiudere 5 pilota
- [ ] Legal: Privacy policy, T&C, disclaimer fiscale
- [ ] Setup Stripe account (anche se non in MVP, per verifica identità)

**KR (Key Results)**:
- 20 articoli pubblicati, 5 keyword top 10 Google
- 5 commercialisti pilota confermati (email commitment)
- 500+ visitatori organici/mese pre-launch

---

### 3.2 Fase 1: MVP Launch (Mesi 1-3)

**Obiettivo**: Validare product-market fit

**Scope**:
- ✅ Modalità completa (tutti registrati) - SOLO senza Stripe
- ✅ Calcolatore gratuito (landing page)
- ✅ Generazione ricevuta PDF
- ✅ Generazione F24 base (sostituto d'imposta)
- ✅ Prima transazione gratis
- ✅ Dashboard base (ricevute, scadenze)
- ✅ Sistema autorizzazioni (prestatore ↔ committente ↔ commercialista)
- ✅ Programma referral commercialisti (7% lifetime)

**Marketing**:
- 60% effort: SEO (blog content)
- 20% effort: Referral commercialisti (outreach, onboarding)
- 20% effort: Google Ads (keyword long-tail, budget €500/mese)

**Metrics to watch** (North Star):
- **Retention 30gg**: >40% ✅ (PMF strong) | 30-40% 🟡 (PMF ok) | <30% 🔴 (problema)

**Target fine Fase 1**:
- 100 utenti paganti
- 200 transazioni generate
- €600-1.000 revenue
- Retention 30gg >35%

**Decision point**: 
- Se retention >30% → Fase 2 ✅
- Se retention <25% → Pivot o Kill 🔴

---

### 3.3 Fase 2: Feature Expansion (Mesi 4-6)

**Obiettivo**: Aumentare retention e reduce churn

**Aggiunte** (solo se Fase 1 successo):
- ✅ Modalità standalone (A, B, C)
- ✅ Dashboard analytics avanzate (tracker €5k INPS, budget committente)
- ✅ Template ricevute ricorrenti
- ✅ Sistema notifiche completo (email + in-app)
- ✅ OCR marca da bollo (foto → numero seriale)
- ✅ Esportazione dati (CSV, Excel)

**Marketing**:
- Intensificare referral (target 50 commercialisti)
- PR: pitch a media tech/fintech italiani
- Partnership: piattaforme freelance (Fiverr Italia, ecc.)

**Target fine Fase 2**:
- 500 utenti paganti
- 1.500 transazioni
- €6.000-10.000 revenue
- Retention 6 mesi >30%

---

### 3.4 Fase 3: Scale + Stripe (Mesi 7-12)

**Obiettivo**: Crescita accelerata e monetizzazione Stripe

**Aggiunte**:
- ✅ Integrazione Stripe completa (pagamenti gestiti)
- ✅ Piano Premium commercialisti (€29/mese): white-label, API, unlimited
- ✅ Integrazioni software contabilità (export Teamsystem, Zucchetti)
- ✅ API pubblica (per partner)
- ✅ Widget embeddable (commercialisti possono mettere su loro sito)

**Marketing**:
- Partnership ODCEC (Ordini Dottori Commercialisti)
- Sponsorship eventi fiscalisti
- Affiliate program (oltre referral)

**Target fine Fase 3**:
- 2.000+ utenti paganti
- 10.000+ transazioni/anno
- €50.000-80.000 revenue/anno
- Break-even operativo

---

## 4. Metriche Critiche da Monitorare

### 4.1 North Star Metric

**Retention 6 mesi**: % utenti che fanno almeno 1 transazione dopo 6 mesi dalla prima.

**Target**: >30% (accettabile) | >40% (ottimo) | >50% (eccezionale)

**Perché critica**: Con utenti occasionali (low frequency), retention decide LTV e quindi unit economics.

---

### 4.2 Dashboard KPI Settimanale

**Acquisition**:
- Nuovi registrati
- Source (organico/referral/ads)
- CAC per source

**Activation**:
- % registrati → prima transazione (target: >40%)
- Time to first transaction (target: <7gg)

**Retention**:
- Retention 7gg / 30gg / 90gg / 180gg
- Churn rate settimanale
- **Red flag**: Churn >15%/settimana

**Revenue**:
- Transazioni settimana
- ARPU (Average Revenue Per User)
- MRR (Monthly Recurring Revenue) - se utenti multi-transazione

**Referral**:
- Commercialisti attivi (almeno 1 referral)
- % utenti da referral
- Costi referral / Revenue totale (target: <10%)

---

### 4.3 Kill Switches (Quando Fermare/Pivot)

**⛔ Considerare STOP se**:
1. Retention 6 mesi <15% dopo 12 mesi launch (non vale la pena)
2. CAC >€30 sostenuto per 6+ mesi (unit economics rotti)
3. Impossibilità alzare prezzi e margini restano <50%
4. Cambio normativo rende servizio illegale/obsoleto
5. Competitor con 10x risorse entra e undercut prezzi

**🔄 Considerare PIVOT se**:
1. Retention bassa ma engagement alto (problema pricing/value)
2. Un segmento (es. committenti) performe 3x altri (focus)
3. Feature secondaria ha traction maggiore di core (diventa core)

---

## 5. Risk Mitigation Plan

### 5.1 Rischio #1: Low Frequency Users (ALTO)

**Problema**: Utenti usano 1-2x/anno → LTV €5-10 (troppo basso).

**Mitigazioni**:
1. **Focus committenti ricorrenti**: Hanno frequency 10x prestatori
2. **Upsell servizi correlati**: Assicurazioni, software contabilità (affiliate)
3. **Email nurturing aggressivo**: "Tempo di fare un'altra ricevuta?"
4. **Referral incentives**: Utente invita amico → €5 credit
5. **Expand use cases**: Contratti consulenza, fatture forfettari (fuori scope iniziale)

**Metric to track**: Average transactions per user per year (target: >3).

---

### 5.2 Rischio #2: Retention Post-Free Transaction (ALTO)

**Problema**: Utenti provano gratis, non tornano mai a pagamento.

**Mitigazioni**:
1. **Onboarding excellence**: Tutorial interattivo, show value subito
2. **First transaction success**: Ensure documento generato è perfetto
3. **Email sequence**: 7 email nei 30gg post-prima transazione (educational)
4. **Incentivo "torna entro 30gg"**: 50% sconto seconda transazione
5. **Lock-in features**: Storico transazioni, calendar, analytics (valore cresce over time)

**Metric to track**: D30 retention (target: >40%).

---

### 5.3 Rischio #3: Complessità Normativa (MEDIO)

**Problema**: Normativa prestazioni occasionali cambia (INPS, ritenute, limiti).

**Mitigazioni**:
1. **Advisory board**: 3-5 commercialisti consultant (gratis uso platform)
2. **Monitoring normativo**: Alert automatici da Agenzia Entrate, INPS
3. **Update rapido**: Architettura permette cambio formule/calcoli in <24h
4. **Disclaimer robusto**: "Non è consulenza fiscale, può avere errori"
5. **Assicurazione professionale**: Per coprire errori (valutare post-scale)

**Metric to track**: Time to deploy normative fix (target: <48h).

---

### 5.4 Rischio #4: Competitor Aggueriti (MEDIO)

**Problema**: Player grande (Aruba, Fatture in Cloud) entra nel mercato.

**Mitigazioni**:
1. **First-mover advantage**: Occupy SEO keywords ASAP (20 articoli pre-launch)
2. **Network effect**: Commercialisti referral creano moat (switching cost)
3. **Differenziazione UX**: Friendly tone vs corporate (hard to copy)
4. **Feature velocity**: Ship fast, iterate, stay ahead
5. **Niche focus**: Specializzazione prestazioni occasionali (loro generalisti)

**Metric to track**: Organic traffic share, branded search volume.

---

### 5.5 Rischio #5: Abuse Prima Transazione Gratis (BASSO)

**Problema**: Utenti creano account multipli per infinite transazioni gratis.

**Mitigazioni**:
1. **Verifica identità**: Upload documento (€0.50-1 costo, worth it)
2. **Device fingerprinting**: FingerprintJS o simili
3. **Codice fiscale unique**: Non può riavere gratis con stesso CF
4. **Manual review**: Flag transazioni sospette (importi alti, pattern strani)
5. **Termini chiari**: "1 transazione gratis per persona" + ban se abuse

**Metric to track**: % transazioni free flagged / investigate.

---

## 6. Consigli Operativi

### 6.1 Team Minimo per MVP

**Fase 1** (Mesi 1-3):
- 1 Full-stack developer (Next.js, React, PostgreSQL)
- 1 Founder/PM (prodotto + marketing)
- 1 Commercialista advisor (part-time, equity o gratis uso)

**Fase 2** (+1 developer):
- 1 Frontend specialist
- 1 Backend specialist
- 1 Founder/PM
- 1 Marketer/growth (se traction)

**No-hire until**: Revenue >€10k/mese o funding.

---

### 6.2 Budget Consigliato (Bootstrap)

**Costi fissi mensili**:
- Hosting (Vercel Pro): €20
- Database (Supabase Pro): €25
- Email (Resend): €20
- Monitoring (Sentry): €26
- Dominio: €2
- **Totale infra**: ~€100/mese

**Costi variabili**:
- Stripe fee: 1.4% + €0.25 per transazione (solo con Stripe mode)
- Verifica identità: €0.50-1 per utente (prima transazione)
- Email transazionali: ~€0.01 per 100 email

**Marketing** (Fase 1):
- Google Ads: €500/mese
- Content writer (freelance): €300/mese (2 articoli)
- **Totale marketing**: €800/mese

**Budget totale Fase 1**: €1.000/mese × 3 mesi = **€3.000**  
**Break-even**: ~200 transazioni/mese (raggiungibile mese 2-3).

---

### 6.3 Tech Stack Definitivo

**Frontend**:
- Next.js 14+ (App Router, Server Actions)
- React + TypeScript
- Tailwind CSS + shadcn/ui
- React Hook Form + Zod (validation)

**Backend**:
- Next.js API Routes / Server Actions
- PostgreSQL (Supabase o Railway)
- Prisma ORM
- NextAuth.js (magic link)

**Payments** (Fase 3):
- Stripe Connect (Custom Accounts)
- Webhook per eventi

**Storage**:
- Cloudflare R2 (PDF, foto marche)
- Oppure Supabase Storage

**Email**:
- Resend (developer-friendly)
- React Email (template in React)

**Analytics**:
- Vercel Analytics (web vitals)
- Posthog (product analytics, funnels)
- Sentry (error tracking)

**Hosting**:
- Vercel (Next.js ottimizzato)
- Cloudflare DNS

---

## 7. Competitive Analysis

### 7.1 Competitor Diretti (Italia)

**Nessuno specifico per prestazioni occasionali** (opportunità!).

Indirect competition:
1. **Commercialisti tradizionali**: €30-50 per ricevuta, manuale
2. **Software contabilità** (Fatture in Cloud, Teamsystem): €10-30/mese abbonamento, overkill
3. **Generatori online gratis**: Esistono ma basic, no F24/CU, no supporto

**Posizionamento ricevuta.studio**:
- Più economico di commercialista
- Pay-per-use (no abbonamento)
- Completo (ricevuta + F24 + CU + notifiche)
- Friendly UX

---

### 7.2 Benchmark Internazionali

**Mercati simili**:
- **Francia**: Micro-entrepreneur regime (simplifié)
  - Competitor: Shine, Indy, FreelanceMe
  - Pricing: €10-30/mese flat
  
- **UK**: Self-employed / Sole Trader
  - Competitor: FreeAgent, Crunch
  - Pricing: £10-20/mese

**Insight**: All'estero è più abbonamento che pay-per-use. **Differenziatore italiano**: occasionali veri (1-2x/anno) → abbonamento non ha senso.

---

## 8. Marketing Strategy (Dettaglio)

### 8.1 SEO - Content Strategy (60% effort)

**Obiettivo**: Ownership keyword "prestazione occasionale" + varianti.

**Keyword targets** (search volume stimato):
- "prestazione occasionale" - 10k/mese
- "ricevuta prestazione occasionale" - 5k/mese
- "come fare prestazione occasionale" - 2k/mese
- "limite prestazione occasionale 2026" - 1k/mese
- "ritenuta acconto prestazione occasionale" - 1k/mese

**Content plan** (pre-launch: 20 articoli):

**Cluster 1: Basics** (5 articoli)
1. "Cosa sono le prestazioni occasionali: guida completa"
2. "Come fare una ricevuta per prestazione occasionale"
3. "Limiti e tetti delle prestazioni occasionali 2026"
4. "Differenza prestazione occasionale vs P.IVA"
5. "Prestazione occasionale: quando conviene?"

**Cluster 2: Fiscalità** (7 articoli)
6. "Ritenuta d'acconto: guida per prestazioni occasionali"
7. "Contributi INPS: quando sono obbligatori?"
8. "Marca da bollo su ricevuta: quando serve?"
9. "F24 per prestazioni occasionali: come compilarlo"
10. "Certificazione Unica (CU): guida completa"
11. "Dichiarazione redditi con prestazioni occasionali"
12. "Prestazione occasionale: regime fiscale 2026"

**Cluster 3: Pratici** (5 articoli)
13. "Template ricevuta prestazione occasionale (PDF gratis)"
14. "Calcolatore netto/lordo prestazione occasionale"
15. "Esempio ricevuta compilata passo-passo"
16. "Ricevuta prestazione occasionale: errori da evitare"
17. "Software per ricevute: quale scegliere?"

**Cluster 4: Avanzati** (3 articoli)
18. "Prestazioni occasionali per committente estero"
19. "Prestazione occasionale e disoccupazione: compatibilità"
20. "Sanzioni e controlli: cosa rischi?"

**Link building**:
- Guest post su blog commercialisti
- Partnership blog fiscalità (FISCOeTASSE, PMI.it)
- Forum (Il Commercialista, Contabilità Italia)

---

### 8.2 Referral - Outreach Plan (20% effort)

**Target**: 50 commercialisti anno 1

**Segmentation**:
- **Tier A** (top priority): Commercialisti con presenza social (LinkedIn 500+ followers)
- **Tier B**: Studi medi (5-20 dipendenti)
- **Tier C**: Freelance individuali

**Outreach sequence**:
1. **Email 1** (cold): Intro + problema/soluzione + invito call
2. **Email 2** (+3gg): Case study + referral 7% lifetime
3. **Email 3** (+7gg): Last chance + bonus "early partner"
4. **LinkedIn message** (parallelo)

**Incentivi early adopters** (primi 20 commercialisti):
- Badge "Partner Fondatore" su profilo
- Featured su blog ricevuta.studio
- 10% invece di 7% lifetime (grandfather clause)

---

### 8.3 Google Ads - Starter Budget (20% effort)

**Budget**: €500/mese (Fase 1)

**Campagne**:

**Campaign 1: Long-tail keywords** (€300/mese)
- "come fare ricevuta prestazione occasionale"
- "calcolo prestazione occasionale"
- "software ricevuta prestazione occasionale"
- **CPC stimato**: €0.30-0.80
- **Click/mese**: 375-1000
- **Conversion**: 5% = 19-50 registrazioni

**Campaign 2: Brand defense** (€100/mese)
- "ricevuta studio"
- "ricevuta.studio"
- **CPC**: €0.10-0.20
- **Protezione** da competitor su branded terms

**Campaign 3: Remarketing** (€100/mese)
- Utenti che hanno visitato calcolatore ma non registrato
- Display ads Google Network
- **Goal**: Bring back per prima transazione gratis

**ROI atteso**:
- €500 spend → 50 registrazioni → 20 prima transazione → 6 seconda transazione
- Revenue: €60-100 (mese 1-2), poi retention aumenta LTV
- Break-even: Mese 3-4

---

## 9. Legal & Compliance

### 9.1 Disclaimer Responsabilità (Critico)

**Su ogni pagina** (footer):
```
⚠️ Disclaimer
ricevuta.studio è un facilitatore tecnologico e NON fornisce 
consulenza fiscale. I documenti generati possono contenere errori. 
Si consiglia di far verificare da un commercialista abilitato prima 
dell'utilizzo ufficiale. L'utente è responsabile della correttezza 
dei dati inseriti e dell'uso dei documenti.
```

**Modal disclaimer** (al primo utilizzo SaaS):
```
Prima di continuare, conferma di aver compreso:

☐ ricevuta.studio NON è un commercialista
☐ I documenti generati possono avere errori
☐ Sei responsabile della verifica con un professionista
☐ La piattaforma è un ausilio, non una garanzia

[Confermo e accetto] [Non accetto]
```

---

### 9.2 GDPR Compliance

**Dati trattati**:
- Anagrafici: nome, cognome, codice fiscale, indirizzo
- Fiscali: IBAN, partita IVA, dati ricevute
- Documenti: PDF ricevute, foto marche da bollo
- Log: IP, azioni utente, timestamp

**Misure**:
- ✅ Privacy Policy completa (GDPR-compliant)
- ✅ Cookie consent (per analytics e marketing)
- ✅ Diritto accesso/cancellazione dati (self-service in dashboard)
- ✅ Encryption at rest (database) + in transit (TLS)
- ✅ Backup automatici (retention 10 anni per obbligo fiscale)
- ✅ DPO (Data Protection Officer): founder o consulente esterno

---

### 9.3 Termini e Condizioni

**Clausole critiche**:

1. **Limitazione responsabilità**:
   "La piattaforma è fornita 'as is'. Non garantiamo correttezza assoluta dei calcoli..."

2. **Diritti IP**:
   "Il codice è proprietà ricevuta.studio. Utente ha licenza d'uso non esclusiva..."

3. **Modifiche servizio**:
   "Ci riserviamo il diritto di modificare pricing e feature con preavviso 30gg..."

4. **Risoluzione dispute**:
   "Foro competente: Tribunale di [città]. Mediazione obbligatoria prima di causa..."

**Review legale**: Fare revisionare da avvocato specializzato tech/fintech (€500-1.000).

---

## 10. Conclusioni e Next Steps Immediati

### 10.1 Sintesi Raccomandazioni

**🔴 MODIFICARE SUBITO** (pre-launch):
1. Aumentare pricing Stripe: da 3-4% a 5-5.5%
2. Semplificare MVP: eliminare modalità standalone
3. Aggiungere verifica identità per prima transazione gratis

**🟡 CONSIDERARE FORTEMENTE**:
4. Ridurre referral commercialisti: da 10% a 7%
5. Focus SEO (60% effort): 20 articoli pre-launch

**✅ MANTENERE** (già ottimali):
6. Prima transazione gratis (con abuse prevention)
7. Pricing senza Stripe: 0.8-1.8% (competitivo)
8. Programma referral commercialisti (con % giusta)

---

### 10.2 Checklist Pre-Launch (2 settimane)

**Week 1**:
- [ ] Decisione finale pricing Stripe: 5-5.5% ✅
- [ ] Decisione finale referral: 7% o 10%
- [ ] Scope MVP confermato (no standalone)
- [ ] Setup repo e dev environment
- [ ] Design system + mockup 5 schermate chiave
- [ ] Setup Supabase/Railway database
- [ ] Articoli blog: primi 10 scritti e pubblicati

**Week 2**:
- [ ] Sviluppo calcolatore gratuito (landing page)
- [ ] Auth magic link funzionante
- [ ] Generazione ricevuta PDF base
- [ ] Stripe Identity integrato (verifica)
- [ ] Privacy policy, T&C, disclaimer drafted
- [ ] Google Ads account setup
- [ ] Outreach primi 10 commercialisti

---

### 10.3 Decision Framework (Come Decidere)

**Per ogni feature/decisione, chiedersi**:

1. **È essenziale per MVP?** (se no, postpone)
2. **Migliora retention?** (focus assoluto)
3. **Vale il costo/tempo?** (ROI >3:1?)
4. **Gli utenti lo chiedono?** (validate con interviste)
5. **Competitor ce l'ha?** (se no, forse non serve)

**Bias da evitare**:
- ❌ Feature creep (aggiungere troppo)
- ❌ Perfect is enemy of good (ship imperfect, iterate)
- ❌ Sunk cost fallacy (se non funziona, pivot o kill)

---

### 10.4 Final Thoughts

**Il progetto ricevuta.studio ha potenziale forte**, ma richiede:

✅ **Disciplina nell'esecuzione**: MVP snello, focus retention  
✅ **Pricing sostenibile**: Margini Stripe da fixare pre-launch  
✅ **Marketing intelligente**: SEO + referral, non solo ads  
✅ **Metriche ossessione**: Retention è north star, tutto il resto segue  

**Con le modifiche proposte**, probabilità successo passa da **45%** a **70%+**.

**Good luck! 🚀**

---

**Documenti correlati da leggere**:
1. `business-structure.md` - Overview completo business
2. `pricing-model.md` - Dettaglio pricing ottimizzato
3. `referral-program.md` - Meccanica referral commercialisti
4. `business-model-analysis.md` - Analisi approfondita strategica
5. `pricing-strategy-analysis.md` - Calcoli e scenari pricing

**Fine documento.**
