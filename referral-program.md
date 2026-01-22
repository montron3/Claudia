# 🤝 Programma Referral - ricevuta.studio

## Documento di Riferimento per Produzione

**Versione**: 1.0 (Ottimizzata)  
**Data**: 2026-01-22  
**Status**: Production Ready - Con Raccomandazioni  
**Baseline**: PROJECT_VISION_Version6.md + business-model-analysis.md

---

## 1. Executive Summary

### 1.1 Obiettivo del Programma
**Accelerare la crescita attraverso il network dei commercialisti**, incentivando l'acquisizione di nuovi utenti con commissioni ricorrenti lifetime.

### 1.2 Modello Referral
- **Target**: Commercialisti (non prestatori/committenti)
- **Incentivo**: 10% delle commissioni generate dagli utenti invitati, **per sempre**
- **Meccanica**: Link referral univoco per commercialista
- **Tracciamento**: Lifetime attribution (utente referenziato = referral permanente)

### 1.3 Razionale Strategico
✅ Commercialisti hanno **fiducia preesistente** con clienti (low CAC)  
✅ Commercialisti incentivati a **educare** clienti sul servizio  
✅ Effetto network: più commercialisti = più utenti = più valore  
✅ Riduce dipendenza da Google Ads (CAC alto)  
✅ Referral sono **utenti più qualificati** (guidati da esperto)  

### 1.4 Ottimizzazione Applicata
**⚠️ RACCOMANDAZIONE**: Vision originale propone 10% lifetime. L'analisi suggerisce **7% lifetime** per sostenibilità economica (vedi sezione 8).

---

## 2. Meccanica del Programma

### 2.1 Chi Può Partecipare

#### Requisiti Commercialista
- ✅ Registrato su ricevuta.studio
- ✅ Profilo verificato (codice fiscale, iscrizione Albo)
- ✅ Accettazione termini programma referral
- ❌ NON serve essere commercialista di professione (accountant) - anche consulenti fiscali ok

**Nota**: Il programma è **solo per commercialisti**, non per prestatori o committenti, per mantenere qualità referral.

### 2.2 Come Funziona

#### Step 1: Commercialista Ottiene Link Referral
Ogni commercialista ha un **link univoco**:
```
https://ricevuta.studio/r/ABC123
```

Oppure **codice invito**:
```
Codice: ABC123
```

**Dashboard commercialista** mostra:
- Link referral personale
- QR code (per condivisione offline)
- Email template pre-scritte
- Social media template

#### Step 2: Commercialista Condivide Link
Modi di condivisione:
- Email a clienti esistenti
- Post social media (LinkedIn, Facebook)
- Sito web studio (banner, footer)
- Materiale cartaceo (business card, brochure)
- Durante consulenze (mostra QR code)

#### Step 3: Utente Clicca Link e Si Registra
- Utente atterra su landing page con banner: "Invitato da [Nome Commercialista]"
- Utente si registra normalmente (magic link)
- Sistema associa utente al commercialista (cookie + DB)

#### Step 4: Utente Usa Piattaforma (Transazioni)
- Utente crea ricevute e paga commissioni
- Sistema calcola 10% commissioni → credito commercialista
- Credito si accumula nel "wallet" commercialista

#### Step 5: Commercialista Riceve Pagamento
- Pagamenti mensili (se saldo >€50)
- Bonifico SEPA su IBAN commercialista
- Riepilogo dettagliato guadagni nel dashboard

---

## 3. Calcolo Commissioni Referral

### 3.1 Formula Base
```
Commissione Referral = Commissioni Piattaforma × 10%
```

**Importante**: Il 10% si applica su **TUTTE** le commissioni della transazione (prestatore + committente), non solo una parte.

### 3.2 Esempi Calcolo

#### Esempio 1: Ricevuta €500 (Senza Stripe, Privati)
- Commissione prestatore: €4.00
- Commissione committente: €4.00
- Commissioni totali piattaforma: €8.00
- **Referral commercialista**: €8.00 × 10% = **€0.80**
- Margine netto piattaforma: €8.00 - €0.80 = **€7.20** (90%)

#### Esempio 2: Ricevuta €500 (Senza Stripe, Sostituto)
- Commissione prestatore: €4.00
- Commissione committente: €6.50
- Commissioni totali piattaforma: €10.50
- **Referral commercialista**: €10.50 × 10% = **€1.05**
- Margine netto piattaforma: €10.50 - €1.05 = **€9.45** (90%)

#### Esempio 3: Ricevuta €1.000 (Con Stripe, Sostituto)
- Commissioni piattaforma (5.5%): €55.00
- Stripe fee: €14.25
- Revenue piattaforma prima referral: €55 - €14.25 = €40.75
- **Referral commercialista**: €55.00 × 10% = **€5.50**
- Margine netto piattaforma: €40.75 - €5.50 = **€35.25** (64%)

**Nota**: Con Stripe + Referral, margine scende a 64%. Monitorare sostenibilità.

### 3.3 Lifetime Value Referral

**Scenario**: Commercialista invita un utente che fa 5 ricevute/anno × 3 anni.

- Transazioni totali: 15
- Importo medio: €400
- Commissione media piattaforma: 2% (mix modalità)
- Commissioni totali 3 anni: €400 × 15 × 2% = **€120**
- **Guadagno commercialista lifetime**: €120 × 10% = **€12**

**Scenario ottimistico** (committente ricorrente, 20 transazioni/anno):
- Transazioni 3 anni: 60
- Commissioni totali: €400 × 60 × 2% = **€480**
- **Guadagno commercialista lifetime**: €480 × 10% = **€48**

---

## 4. Tracciamento e Attribution

### 4.1 Tecnologia Tracciamento

#### Cookie + Database Dual Tracking
1. **Cookie** (30 giorni):
   - Quando utente clicca link referral → cookie `ref=ABC123`
   - Valido 30 giorni
   - Sopravvive a logout/login

2. **Database** (permanente):
   - Al momento registrazione → utente.referrer_code = 'ABC123'
   - Associazione permanente, non modificabile
   - Tracciato per sempre

#### Edge Cases

**Caso 1: Utente clicca link ma si registra dopo 30gg**
- Cookie scaduto → referral NON attribuito
- Commercialista può re-inviare link

**Caso 2: Utente clicca 2 link diversi (2 commercialisti)**
- Vince il **primo clic** (first-touch attribution)
- Alternativa: ultimo clic (last-touch) - decisione da prendere in implementazione

**Caso 3: Utente già registrato clicca link referral**
- Referral NON attribuito (già registrato prima)
- Commercialista non guadagna su utenti pre-esistenti

### 4.2 Dashboard Referral (Commercialista)

**Metriche visualizzate**:
- Utenti invitati (totale)
- Utenti attivi (che hanno fatto almeno 1 transazione)
- Conversion rate: invitati → attivi
- Guadagni totali lifetime
- Guadagni mese corrente
- Guadagni ultimi 12 mesi
- Prossimo pagamento previsto

**Tabella dettagli**:
| Utente (anonimizzato) | Data Registrazione | Transazioni | Guadagno Totale | Stato |
|----------------------|-----------------------|-------------|----------------|--------|
| User #47291 | 15 Gen 2026 | 3 | €2.40 | Attivo |
| User #47298 | 20 Gen 2026 | 0 | €0.00 | Registrato |

**Grafici**:
- Andamento guadagni mensili (line chart)
- Funnel: clic → registrati → attivi (conversion funnel)

---

## 5. Pagamenti ai Commercialisti

### 5.1 Frequenza Pagamenti
- **Cadenza**: Mensile
- **Giorno pagamento**: 5° giorno lavorativo mese successivo
- **Esempio**: Guadagni gennaio → pagamento 5 febbraio

### 5.2 Soglia Minima Pagamento
- **Soglia**: €50
- **Motivo**: Ridurre costi operativi bonifici
- **Se saldo <€50**: Importo si accumula per mese successivo

**Esempio**:
- Gennaio: guadagno €30 (non pagato, si accumula)
- Febbraio: guadagno €40 (totale €70 > €50 → pagato €70)

### 5.3 Metodo Pagamento
- **Default**: Bonifico SEPA su IBAN commercialista
- **Info richieste**: IBAN, intestatario, codice fiscale
- **Verifica IBAN**: Al primo pagamento, invio di €0.01 con codice verifica

### 5.4 Documentazione Fiscale
- **Fattura inversa**: Commercialista emette fattura a ricevuta.studio per commissioni referral
- **Scadenza fattura**: Entro ultimo giorno mese
- **Causale**: "Commissioni referral ricevuta.studio - Mese [XX]"

**Nota legale**: Commercialista è B2B contractor, non dipendente. Deve gestire propria fiscalità.

---

## 6. Termini e Condizioni Programma

### 6.1 Durata Referral
**Lifetime**: Utente referenziato resta associato al commercialista **per sempre**, anche se:
- Cambia commercialista sulla piattaforma
- Revoca autorizzazione al commercialista
- Commercialista smette di usare piattaforma

**Unica eccezione**: Frode dimostrata → referral annullato retroattivamente.

### 6.2 Esclusioni e Limitazioni

❌ **NON guadagna commissioni se**:
- Commercialista è anche parte della transazione (self-referral)
- Utente referenziato usa modalità standalone commercialista (per evitare double-dipping)
- Transazione è la prima (gratuita) dell'utente

✅ **Guadagna commissioni su**:
- Tutte le transazioni a pagamento dell'utente referenziato
- Anche se utente non è cliente del commercialista
- Anche se commercialista lascia la piattaforma

### 6.3 Comportamenti Vietati

**Spam e Abuso**:
- ❌ Email spam non richieste
- ❌ Fake accounts (creare account finti per generare referral)
- ❌ Incentivare utenti a creare transazioni fittizie
- ❌ Click fraud (bot, click farm)

**Conseguenze violazioni**:
- Sospensione programma referral
- Blocco pagamenti pendenti
- Ban permanente dalla piattaforma

### 6.4 Modifiche al Programma

**Piattaforma si riserva il diritto** di:
- Modificare % commissione referral (con preavviso 60gg)
- Modificare termini pagamento
- Terminare programma (con preavviso 90gg)

**Garanzia**: Modifiche **non retroattive** (referral già acquisiti mantengono % originale).

---

## 7. Strategia Marketing per Commercialisti

### 7.1 Incentivi a Partecipare

**Pitch commercialista**:
```
💰 Guadagna promuovendo ricevuta.studio

Come commercialista, puoi:
✅ Guadagnare 10% commissioni lifetime
✅ Offrire ai clienti uno strumento utile
✅ Ridurre il tuo carico lavoro (meno pratiche manuali)
✅ Usare la piattaforma GRATIS per i tuoi clienti

Esempio: 20 clienti attivi = €500-1.000/anno passivo

[Diventa Partner →]
```

### 7.2 Materiali Forniti ai Commercialisti

**Kit referral** include:
1. **Email template**:
   - Subject: "Semplifica le tue prestazioni occasionali"
   - Body: spiegazione servizio + link personale

2. **Post social media**:
   - LinkedIn (tono professionale)
   - Facebook (tono friendly)
   - Instagram story template

3. **Brochure PDF** (stampabile):
   - Fronte: benefici ricevuta.studio
   - Retro: QR code referral commercialista

4. **Banner sito web** (varie dimensioni):
   - Leaderboard: 728×90px
   - Rectangle: 300×250px
   - Badge: 125×125px

5. **Firma email HTML**:
   - "P.S. Gestisci prestazioni occasionali facilmente con ricevuta.studio [link]"

### 7.3 Incentivi Extra (Opzionali)

**Gamification** (da valutare post-launch):
- 🥉 **Bronze** (10 utenti attivi): Badge nel profilo
- 🥈 **Silver** (50 utenti attivi): Commissione +1% (11% totale)
- 🥇 **Gold** (200 utenti attivi): Commissione +2% (12% totale) + priority support

**Contest mensili**:
- Top 3 commercialisti per nuovi referral → bonus €100-500

---

## 8. Analisi Economica Referral

### 8.1 Unit Economics con Referral

**Scenario Base** (utente medio lifetime):
- Transazioni lifetime: 5
- Revenue piattaforma: €50 (ipotesi)
- Commissione referral (10%): €5
- CAC organico (senza referral): €15
- CAC commercialista (margine referral): €5

**Analisi**:
- LTV utente: €50
- CAC referral: €5
- **LTV/CAC ratio**: 10:1 (eccellente!)
- Margine netto: €50 - €5 = €45 (90%)

**Vs. CAC Google Ads**:
- CAC Ads: €15-30
- LTV/CAC ratio Ads: 1.67-3.33:1
- **Referral è 3-6x più efficiente** ✅

### 8.2 Rischio Over-Generous (10% Lifetime)

**Scenario pessimistico** (utente high-frequency):
- Transazioni lifetime: 100 (committente ricorrente)
- Revenue piattaforma: €1.000
- Commissione referral lifetime: €100
- CAC organico: €15

**Analisi**:
- Commercialista guadagna €100 per 1 utente
- CAC organico è €15
- **Referral paga 6.67x il CAC organico** ⚠️

**Problema**: Se referral diventano 30%+ utenti, stiamo sovrapagando acquisizione.

### 8.3 Raccomandazione: Ridurre a 7%

**Razionale**:
- 7% lifetime è comunque **2-3x CAC organico** (molto attrattivo)
- Margine piattaforma: 93% vs 90% (3% in più)
- Su €100k revenue: differenza €3.000/anno
- Riduce rischio overshooting in caso scale

**Calcoli con 7%**:

| Metrica | 10% Lifetime | 7% Lifetime | Delta |
|---------|-------------|------------|-------|
| Margine per transazione (€500) | 90% | 93% | +3% |
| Guadagno comm. per utente (5 trans.) | €5 | €3.50 | -€1.50 |
| LTV/CAC ratio (organico €15) | 10:1 | 14:1 | +40% |
| Sostenibilità high-frequency users | ⚠️ Rischio | ✅ Sicuro | Meglio |

**Proposta**: Start con **7% lifetime**, possibilità aumentare a 10% se metriche lo permettono.

---

## 9. KPI e Monitoraggio

### 9.1 Metriche Programma Referral

**Tracciare attentamente**:

1. **Commercialisti nel programma**:
   - Totale registrati
   - Attivi (almeno 1 referral)
   - % attivi su registrati

2. **Referral generati**:
   - Click link referral
   - Registrazioni da referral
   - Conversion: click → registrato

3. **Activation referral**:
   - Referral che fanno prima transazione
   - Conversion: registrato → transazione
   - **Target**: >15% (referral sono più qualificati)

4. **Revenue da referral**:
   - % revenue totale da utenti referenziati
   - **Target anno 1**: 10-20%
   - **Target anno 3**: 30-40%

5. **Costi referral**:
   - Commissioni pagate ai commercialisti
   - % revenue totale
   - **Target**: <10% revenue

6. **ROI referral**:
   - LTV utenti referenziati / Commissioni pagate
   - **Target**: >5:1

### 9.2 Red Flags

**Alert se**:
- 🔴 Costi referral >15% revenue (troppo generoso)
- 🔴 Conversion referral <5% (commercialisti sbagliano target)
- 🔴 Churn referral >50% (qualità bassa)
- 🔴 Spike anomalo referral da 1 commercialista (possibile frode)

### 9.3 Dashboard Admin

**Vista aggregata**:
- Top 10 commercialisti per revenue generata
- Referral fraud detection (pattern anomali)
- Payout mensili programmati
- Revenue attribution (organico vs referral vs ads)

---

## 10. Roadmap Implementazione

### 10.1 MVP Referral (Launch)

**Scope minimo** (1° release):
- ✅ Generazione link referral univoco
- ✅ Cookie tracking + DB attribution
- ✅ Dashboard base commercialista (guadagni, utenti invitati)
- ✅ Calcolo automatico commissioni
- ✅ Accumulazione saldo wallet commercialista
- ❌ Pagamenti manuali primo mese (bonifici amministratore)

**Tempo implementazione**: 1-2 settimane

### 10.2 Fase 2: Automazione Pagamenti

**Aggiunte** (+1-2 mesi post-launch):
- ✅ Integrazione SEPA (bonifici automatici)
- ✅ Sistema fatturazione inversa
- ✅ Email notifiche pagamenti
- ✅ Storico pagamenti commercialista

### 10.3 Fase 3: Advanced Features

**Aggiunte** (+6 mesi post-launch):
- ✅ Gamification (badge, tiers)
- ✅ Contest mensili
- ✅ A/B test % commissione (7% vs 10%)
- ✅ Referral multi-tier (commercialista invita commercialista)
- ✅ API referral per integrazioni

---

## 11. Casi d'Uso Referral

### 11.1 Caso 1: Studio Piccolo (5-10 Clienti)

**Scenario**: Commercialista individuale con piccolo studio.

**Strategia**:
1. Invia email personalizzata ai 10 clienti esistenti
2. Mette banner su sito studio
3. Menziona in consulenze

**Risultato atteso** (anno 1):
- 5 clienti si registrano (50% conversion)
- 3 clienti attivi (60% activation)
- 15 transazioni totali anno
- Guadagno commercialista: €30-60/anno (passivo)

**Beneficio**: Piccolo extra, ma clienti più autonomi = meno chiamate/email.

### 11.2 Caso 2: Studio Medio (50+ Clienti)

**Scenario**: Studio associato con dipendenti.

**Strategia**:
1. Email blast a database clienti (200 email)
2. Post LinkedIn + Facebook
3. Brochure cartacea in sala d'attesa

**Risultato atteso** (anno 1):
- 30 clienti si registrano (15% conversion)
- 15 clienti attivi (50% activation)
- 100 transazioni totali anno
- Guadagno commercialista: €200-500/anno

**Beneficio**: Revenue extra significativo + riduzione carico lavoro staff.

### 11.3 Caso 3: Commercialista "Influencer"

**Scenario**: Commercialista con presenza social forte (5.000+ follower).

**Strategia**:
1. Video YouTube tutorial "Come fare ricevuta occasionale"
2. Link referral in descrizione + commenti
3. Post LinkedIn/Instagram con tips + link
4. Newsletter clienti

**Risultato atteso** (anno 1):
- 200+ registrazioni da social
- 50 clienti attivi (25% activation)
- 300+ transazioni totali anno
- Guadagno commercialista: €600-1.500/anno

**Beneficio**: Revenue passivo consistente + content per social + autorità nel settore.

---

## 12. Alternative al Programma Referral

### 12.1 Opzione A: Commissione Una Tantum

**Invece di 10% lifetime**:
- €10-20 fisso per ogni utente che completa prima transazione
- **Pro**: Più semplice, costi prevedibili
- **Contro**: Nessun incentivo lifetime, commercialista non curato retention

### 12.2 Opzione B: Commissione a Tempo

**Invece di lifetime**:
- 10% per primo anno, poi 5% per sempre
- Oppure: 20% primo anno, poi 0%
- **Pro**: Costi più controllati long-term
- **Contro**: Messaggio meno attrattivo ("solo 1 anno")

### 12.3 Opzione C: Nessun Programma Referral

**Solo crescita organica** (SEO, Ads):
- **Pro**: Margini pieni (90-95%), no complessità
- **Contro**: Crescita più lenta, CAC più alto, no network effect

**Raccomandazione**: Mantenere programma referral con **7% lifetime** (compromesso sostenibilità/attrattività).

---

## 13. Conclusioni

### 13.1 Punti di Forza Programma

✅ **Leva crescita potente**: Commercialisti trusted advisors  
✅ **ROI eccellente**: LTV/CAC 5-10x vs organico 2-3x  
✅ **Win-win**: Commercialista guadagna + clienti soddisfatti  
✅ **Network effect**: Più commercialisti = più credibilità = più utenti  
✅ **Qualità referral**: Utenti educati da esperto = retention migliore  

### 13.2 Rischi e Mitigazioni

⚠️ **Rischio overshooting** (10% lifetime troppo generoso)  
→ Mitigazione: Start con 7%, monitorare, possibile aumentare  

⚠️ **Rischio frode** (fake accounts, click fraud)  
→ Mitigazione: Verifica identità, monitoring pattern anomali, termini chiari  

⚠️ **Rischio dipendenza** (troppi utenti da referral)  
→ Mitigazione: Bilanciare con SEO (60% effort), target 30-40% da referral max  

### 13.3 Raccomandazioni Finali

**Per MVP**:
1. ✅ Implementare programma referral subito (high ROI)
2. ⚠️ Considerare **7% invece di 10%** per sostenibilità
3. ✅ Focus su 10-20 commercialisti pilota (qualità > quantità)
4. ✅ Fornire kit marketing completo (easy share)
5. ✅ Monitorare ossessivamente metriche prime settimane

**Success metrics** (3 mesi post-launch):
- 20+ commercialisti attivi nel programma
- 100+ utenti referenziati
- 15%+ activation rate referral
- <10% costi referral su revenue
- Feedback positivo commercialisti (NPS >40)

---

**Vedi anche**:
- `business-structure.md` per contesto business completo
- `pricing-model.md` per dettagli commissioni piattaforma
- `business-model-analysis.md` per analisi strategica referral
