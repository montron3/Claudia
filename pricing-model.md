# 💰 Modello di Pricing - ricevuta.studio

## Documento di Riferimento per Produzione

**Versione**: 1.0 (Ottimizzata)  
**Data**: 2026-01-22  
**Status**: Production Ready - Pricing Rivisto  
**Baseline**: PROJECT_VISION_Version6.md + pricing-strategy-analysis.md

---

## 1. Executive Summary

### 1.1 Modello di Pricing Scelto
**Commissioni percentuali sull'importo lordo della ricevuta**

**Razionale**:
- ✅ Allineato al valore percepito (ricevute più alte = più valore)
- ✅ Scalabile automaticamente con inflazione
- ✅ Semplice da capire per utenti
- ✅ Standard nel settore fintech (Stripe, PayPal, Wise)
- ✅ Revenue cresce con crescita utenti + importi

### 1.2 Filosofia di Pricing
- **Trasparente**: costi chiari, no sorprese
- **Fair**: chi beneficia di più paga di più
- **Incentivante**: sconti per prime transazioni
- **Flessibile**: modalità con/senza gestione pagamento

### 1.3 Ottimizzazioni Applicate
Questo documento riflette **pricing ottimizzato** rispetto alla vision originale:
- 🔴 Commissioni Stripe aumentate: da 3-4% a 4.5-5.5%
- 🟢 Commissioni senza Stripe mantenute competitive: 0.8-1.8%
- 🟡 Prima transazione: strategia confermata ma con verifica identità

---

## 2. Pricing Tiers - Overview

### 2.1 Matrice Pricing Completa

| Modalità | Scenario | Comm. Prestatore | Comm. Committente | Totale |
|----------|----------|------------------|-------------------|--------|
| **Senza Stripe - Completa** | Privati | 0.8% | 0.8% | 1.6% |
| **Senza Stripe - Completa** | Sostituto imposta | 0.8% | 1.3% | 2.1% |
| **Con Stripe - Completa** | Privati | 2.5% | 2.5% | 5.0% |
| **Con Stripe - Completa** | Sostituto imposta | 2.5% | 3.0% | 5.5% |
| **Standalone - Prestatore** | N/A | 0.8% | - | 0.8% |
| **Standalone - Committente** | Sostituto imposta | - | 1.3% | 1.3% |
| **Standalone - Commercialista** | N/A | - | 1.8% | 1.8% |

**NOTA**: I valori "Con Stripe" sono **ottimizzati** rispetto alla vision originale (1.5% + 1.5% = 3%).

---

## 3. Modalità Senza Stripe (Pagamento Esterno)

### 3.1 Descrizione
Il committente paga il prestatore **al di fuori della piattaforma** (bonifico diretto, contanti, ecc.).

La piattaforma:
- Genera i documenti (ricevuta, F24, CU)
- NON gestisce il trasferimento di denaro
- Addebita solo commissioni per il servizio software

### 3.2 Pricing

#### Modalità Completa - Entrambi Privati
- **Prestatore**: 0.8% del lordo
- **Committente**: 0.8% del lordo
- **Totale piattaforma**: 1.6%

**Esempio** (ricevuta €500):
- Prestatore paga: €4.00
- Committente paga: €4.00
- Revenue piattaforma: €8.00
- Margine: ~95% (costi operativi minimi)

#### Modalità Completa - Committente Sostituto d'Imposta
- **Prestatore**: 0.8% del lordo
- **Committente**: 1.3% del lordo
- **Totale piattaforma**: 2.1%

**Esempio** (ricevuta €500):
- Prestatore paga: €4.00
- Committente paga: €6.50
- Revenue piattaforma: €10.50
- Margine: ~95%

**Razionale commissione maggiore committente**: Il committente sostituto d'imposta ha più valore dal servizio (generazione F24, CU, calcolo ritenute).

### 3.3 Modalità di Pagamento Commissioni

#### Opzione A: Pagamento Separato (Default)
- Ogni parte paga la propria commissione indipendentemente
- Pagamento richiesto prima della generazione documenti
- Metodo: carta di credito/debito (Stripe Checkout)

#### Opzione B: Committente Paga per Entrambi (Opzionale)
- Il committente può offrire di pagare anche la commissione del prestatore
- Richiede autorizzazione esplicita del prestatore durante setup
- La commissione del prestatore viene **detratta dal netto** che riceve
- Semplifica il flusso per il prestatore

**Esempio** (ricevuta €500, committente sostituto):
- Commissione prestatore (0.8%): €4.00
- Commissione committente (1.3%): €6.50
- Committente paga: €10.50
- Prestatore riceve: €500 - €100 (ritenuta) - €4.00 (commissione) = €396.00 netto

---

## 4. Modalità Con Stripe (Pagamento Gestito)

### 4.1 Descrizione
Il committente paga tramite la piattaforma usando Stripe.

La piattaforma:
- Gestisce l'intero flusso di pagamento
- Trasferisce il netto al prestatore
- Trattiene automaticamente ritenute (se sostituto d'imposta)
- Trattiene commissioni servizio
- Genera automaticamente tutti i documenti

### 4.2 Pricing Ottimizzato

**⚠️ IMPORTANTE**: Pricing modificato rispetto a PROJECT_VISION_Version6.md per sostenibilità economica.

#### Modalità Completa - Entrambi Privati
- **Prestatore**: 2.5% del lordo
- **Committente**: 2.5% del lordo
- **Totale piattaforma**: 5.0%

**Esempio** (ricevuta €500):
- Lordo pagato da committente: €500
- Commissioni Stripe (~1.4% + €0.25): €7.25
- Commissioni piattaforma: €25.00
- Netto prestatore: €500 - €25.00 = €475.00
- Revenue piattaforma netto: €25.00 - €7.25 = **€17.75**
- Margine: ~71%

#### Modalità Completa - Committente Sostituto d'Imposta
- **Prestatore**: 2.5% del lordo
- **Committente**: 3.0% del lordo
- **Totale piattaforma**: 5.5%

**Esempio** (ricevuta €500, ritenuta 20%):
- Lordo pagato da committente: €500
- Commissioni Stripe: €7.25
- Commissioni piattaforma: €27.50
- Ritenuta 20%: €100
- Netto prestatore: €500 - €27.50 - €100 = €372.50
- Revenue piattaforma netto: €27.50 - €7.25 = **€20.25**
- Margine: ~74%

### 4.3 Flusso Tecnico Stripe

**Architettura**: Stripe Connect (Custom Accounts)

1. **Committente invia pagamento**:
   - Paga importo lordo via Stripe Checkout
   - Es: €500

2. **Piattaforma riceve pagamento**:
   - Stripe trattiene fee (~1.4% + €0.25): €7.25
   - Piattaforma riceve: €492.75

3. **Piattaforma distribuisce**:
   - Trattiene commissioni (5-5.5%): €25-27.50
   - Trattiene ritenute (se sostituto): €100 (da versare con F24)
   - Trasferisce netto a prestatore: €365-475

4. **Documenti generati automaticamente**:
   - Ricevuta PDF
   - F24 pre-compilato (se ritenute)
   - CU (a fine anno)

### 4.4 Tempistiche Trasferimento

- **Trasferimento prestatore**: 2 giorni lavorativi (standard Stripe)
- **Eccezione prima transazione**: 7 giorni (verifica antifrode)
- **Ritenute**: restano su conto piattaforma fino a versamento F24

---

## 5. Prima Transazione - Strategia Sconti

### 5.1 Obiettivo
Ridurre friction e incentivare trial del servizio.

### 5.2 Senza Stripe: Prima Transazione GRATUITA

| Modalità | Prima Transazione | Dalla 2° in poi |
|----------|-------------------|-----------------|
| Senza Stripe - Completa | **0% + 0%** (gratis) | 0.8% + 0.8% (o 1.3%) |
| Standalone - Prestatore | **0%** (gratis) | 0.8% |
| Standalone - Committente | **0%** (gratis) | 1.3% |
| Standalone - Commercialista | **0%** (gratis) | 1.8% |

**Esempio** (ricevuta €500, entrambi privati):
- Prima transazione: €0 commissioni → **GRATIS**
- Seconda transazione: €4 + €4 = €8 totale

### 5.3 Con Stripe: Prima Transazione SCONTATA

| Modalità | Prima Transazione | Dalla 2° in poi |
|----------|-------------------|-----------------|
| Con Stripe - Privati | **1.5% + 1.5%** = 3% | 2.5% + 2.5% = 5% |
| Con Stripe - Sostituto | **1.5% + 2.0%** = 3.5% | 2.5% + 3.0% = 5.5% |

**Esempio** (ricevuta €500, entrambi privati):
- Prima transazione: €7.50 + €7.50 = €15 totale
- Seconda transazione: €12.50 + €12.50 = €25 totale

**Nota**: Impossibile fare gratis con Stripe perché Stripe fee (~€7.25) sono comunque da pagare.

### 5.4 Condizioni e Abuse Prevention

**Per prevenire abusi**:

1. **Verifica Identità Obbligatoria**:
   - Prima transazione richiede verifica documento identità
   - Upload foto fronte/retro documento
   - Verifica automatica (provider: Stripe Identity o Onfido)
   - Verifica 1x per utente, vale forever

2. **Limite 1 Transazione Gratis per Persona**:
   - Tracciato via codice fiscale + documento identità
   - Anche creando nuovi account, non può riavere gratis

3. **Blocco Multi-Account**:
   - Device fingerprinting
   - IP tracking
   - Email + telefono verification

4. **Review Manuale se Sospetto**:
   - Flag transazioni anomale (importi molto alti, pattern strani)
   - Team può bloccare pre-approvazione

---

## 6. Modalità Standalone - Pricing

### 6.1 Solo Prestatore
**Scenario**: Prestatore usa piattaforma, committente NON registrato.

- **Commissione**: 0.8% del lordo
- **Prima transazione**: GRATIS (solo senza Stripe)
- **Cosa riceve**: 
  - Generazione ricevuta
  - Notifiche/guide su cosa chiedere al committente
  - No F24/CU (committente non registrato)

### 6.2 Solo Committente
**Scenario**: Committente usa piattaforma, prestatore NON registrato.

- **Commissione**: 1.3% del lordo (se sostituto d'imposta)
- **Prima transazione**: GRATIS (solo senza Stripe)
- **Cosa riceve**:
  - Generazione documenti committente (F24, CU)
  - Notifiche/guide su cosa far fare al prestatore
  - Ricevuta template (da far firmare al prestatore)

### 6.3 Solo Commercialista
**Scenario**: Commercialista gestisce tutto per clienti non registrati.

- **Commissione**: 1.8% del lordo (unica commissione, più alta)
- **Prima transazione**: GRATIS (solo senza Stripe)
- **Cosa riceve**:
  - Tutti i documenti (ricevuta, F24, CU)
  - Invio email automatico a prestatore/committente (da noreply@ricevuta.studio)
  - Dashboard centralizzata clienti

**Razionale 1.8%**: Commercialista gestisce complessità per 2+ persone, commissione più alta giustificata.

---

## 7. Calcolo Commissioni - Esempi Pratici

### 7.1 Esempio 1: Ricevuta €100 (Senza Stripe, Privati)

**Setup**:
- Importo lordo: €100
- Prestatore: privato
- Committente: privato
- Modalità: Senza Stripe, completa

**Calcoli**:
- Commissione prestatore: €100 × 0.8% = **€0.80**
- Commissione committente: €100 × 0.8% = **€0.80**
- Revenue piattaforma: **€1.60**
- Costo piattaforma (server, email, ecc.): ~€0.20
- Margine netto: **€1.40** (87%)

### 7.2 Esempio 2: Ricevuta €500 (Senza Stripe, Sostituto)

**Setup**:
- Importo lordo: €500
- Prestatore: privato
- Committente: P.IVA (sostituto d'imposta)
- Modalità: Senza Stripe, completa

**Calcoli**:
- Commissione prestatore: €500 × 0.8% = **€4.00**
- Commissione committente: €500 × 1.3% = **€6.50**
- Revenue piattaforma: **€10.50**
- Costo piattaforma: ~€0.30
- Margine netto: **€10.20** (97%)

### 7.3 Esempio 3: Ricevuta €1.000 (Con Stripe, Privati)

**Setup**:
- Importo lordo: €1.000
- Prestatore: privato
- Committente: privato
- Modalità: Con Stripe, completa

**Calcoli**:
- Lordo pagato: €1.000
- Commissioni Stripe (1.4% + €0.25): **€14.25**
- Commissioni piattaforma (5%): **€50.00**
- Netto prestatore: €1.000 - €50 = **€950**
- Revenue piattaforma: €50 - €14.25 = **€35.75**
- Margine: 71.5%

### 7.4 Esempio 4: Ricevuta €1.000 (Con Stripe, Sostituto)

**Setup**:
- Importo lordo: €1.000
- Prestatore: privato
- Committente: P.IVA (sostituto d'imposta, ritenuta 20%)
- Modalità: Con Stripe, completa

**Calcoli**:
- Lordo pagato: €1.000
- Commissioni Stripe: **€14.25**
- Commissioni piattaforma (5.5%): **€55.00**
- Ritenuta 20%: **€200.00**
- Netto prestatore: €1.000 - €55 - €200 = **€745**
- Revenue piattaforma: €55 - €14.25 = **€40.75**
- Margine: 74%

### 7.5 Esempio 5: Commercialista (€300, Senza Stripe)

**Setup**:
- Importo lordo: €300
- Commercialista usa piattaforma per cliente
- Modalità: Standalone commercialista, senza Stripe

**Calcoli**:
- Commissione commercialista: €300 × 1.8% = **€5.40**
- Revenue piattaforma: **€5.40**
- Margine: ~97%

---

## 8. Comparazione Competitiva (Stime)

### 8.1 Competitori Ipotetici

**Nota**: Mercato specifico Italia per prestazioni occasionali è molto frammentato. Comparazione con servizi simili.

| Servizio | Modello | Costo Tipico | Note |
|----------|---------|--------------|------|
| **Commercialista tradizionale** | Fee fissa | €30-50 per ricevuta | Manuale, lento, costoso |
| **Software contabilità (es. Fatture in Cloud)** | Abbonamento | €10-30/mese | Overkill per occasionali |
| **ricevuta.studio (Senza Stripe)** | % transazione | 1.6-2.1% per ricevuta | Automatico, scalabile, fair |
| **ricevuta.studio (Con Stripe)** | % transazione | 5-5.5% per ricevuta | Gestione pagamento inclusa |

**Posizionamento**: 
- **Più economico** del commercialista per ricevute >€50
- **Più flessibile** dei software ad abbonamento (pay-per-use)
- **Più completo** di generatori gratuiti online (F24, CU, notifiche)

### 8.2 Pricing Competitivo?

**SÌ**:
- Per ricevuta €500 senza Stripe: €10.50 vs €30-50 commercialista = **risparmio 65-79%**
- Per ricevuta €1.000 senza Stripe: €21 vs €30-50 commercialista = **risparmio 30-58%**
- Prima transazione gratis = **ROI immediato**

**Con Stripe**:
- Per ricevuta €500 con Stripe: €27.50 vs €30-50 commercialista = **risparmio 8-45%**
- Valore aggiunto: pagamento istantaneo, netto automatico, zero friction

---

## 9. Revenue Modeling

### 9.1 Assunzioni Base

**Scenario conservativo** (primo anno):
- Utenti registrati: 1.000
- Activation rate (prima transazione): 40% = 400 utenti
- Transazioni prima anno: 600 (alcuni multi-transazione)
- Importo medio ricevuta: €400
- Mix modalità: 70% senza Stripe, 30% con Stripe
- Mix scenario: 60% privati, 40% sostituto imposta

### 9.2 Calcolo Revenue Anno 1

#### Senza Stripe (420 transazioni)
- Privati (252 transazioni × €400 × 1.6%): €1.612
- Sostituto (168 transazioni × €400 × 2.1%): €1.411
- **Subtotale senza Stripe**: €3.023

#### Con Stripe (180 transazioni)
- Privati (108 transazioni × €400 × 5% - Stripe fee): €1.814
- Sostituto (72 transazioni × €400 × 5.5% - Stripe fee): €1.267
- **Subtotale con Stripe**: €3.081

**Revenue totale anno 1**: ~€6.100

**NOTA**: Questo è pessimistico. Con 2.000 utenti e retention migliore, revenue può essere 3-5x.

### 9.3 Revenue Projection (3 Anni)

| Anno | Utenti | Trans. | Revenue Senza Stripe | Revenue Con Stripe | Totale |
|------|--------|--------|----------------------|--------------------|--------|
| 1 | 1.000 | 600 | €3.023 | €3.081 | **€6.104** |
| 2 | 5.000 | 4.500 | €22.672 | €23.108 | **€45.780** |
| 3 | 15.000 | 18.000 | €90.688 | €92.430 | **€183.118** |

**Assunzioni**:
- Retention anno 2: 50%
- Multi-transazione: 1.5x/anno media (anno 2-3)
- Mix modalità stabile 70/30

---

## 10. Ottimizzazione e Testing

### 10.1 A/B Test da Eseguire (Post-Launch)

#### Test 1: Commissione Senza Stripe
- **Control**: 0.8% + 0.8% (privati)
- **Variant A**: 1.0% + 1.0%
- **Variant B**: 0.6% + 0.6%
- **Metrica**: Conversion rate + retention

#### Test 2: Prima Transazione Con Stripe
- **Control**: 1.5% + 1.5% sconto
- **Variant A**: Completamente gratis (piattaforma assorbe Stripe fee)
- **Metrica**: Activation rate + LTV

#### Test 3: Commissione Con Stripe
- **Control**: 2.5% + 2.5%
- **Variant A**: 3.0% + 3.0%
- **Variant B**: 2.0% + 2.0%
- **Metrica**: Conversion Stripe vs senza Stripe + margini

### 10.2 Trigger per Cambiamenti Pricing

**Aumentare prezzi se**:
- Retention 6 mesi >40% (strong PMF = pricing power)
- NPS >50 (alta soddisfazione)
- Market share >10% (leadership)
- Competitor alza prezzi

**Abbassare prezzi se**:
- Conversion <3% (troppo caro)
- Churn >15%/mese (non vale il prezzo)
- Competitor agguerisce con sottocosto
- Volume transazioni <50/mese dopo 6 mesi

---

## 11. Comunicazione Pricing agli Utenti

### 11.1 Pagina Pricing - Struttura

**Hero Section**:
```
💰 Prezzi Semplici e Trasparenti

Paga solo quando crei ricevute.
Nessun abbonamento, nessun costo fisso.

✨ Prima ricevuta GRATIS ✨
```

**Pricing Cards**:

**Card 1: Senza Gestione Pagamento**
```
Modalità Standard
da 0.8% per ricevuta

✅ Generazione ricevute
✅ F24 e CU automatici
✅ Notifiche scadenze
✅ Archivio documenti
✅ Prima transazione GRATIS

[Inizia Gratis →]
```

**Card 2: Con Gestione Pagamento**
```
Modalità con Stripe
da 2.5% per ricevuta

✅ Tutto della Modalità Standard
✅ Pagamento tramite piattaforma
✅ Trasferimento automatico
✅ Niente bonifici manuali
✅ Prima transazione SCONTATA 50%

[Inizia Gratis →]
```

**Sezione FAQ Pricing**:
- "Cosa significa 'da 0.8%'?"
- "Quando pago le commissioni?"
- "Posso cambiare modalità?"
- "Cosa include la prima transazione gratis?"

### 11.2 Trasparenza Costi

**Nel calcolatore gratuito**, mostrare:
```
Importo lordo: €500
Netto prestatore: €400 (con ritenuta 20%)

💰 Costi piattaforma
├─ Commissione prestatore: €4.00 (0.8%)
└─ Commissione committente: €6.50 (1.3%)

Totale risparmio vs commercialista: €35 (70%)
```

---

## 12. Raccomandazioni Implementazione

### 12.1 Priorità MVP

**Fase 1** (Launch):
- ✅ Modalità senza Stripe (più semplice)
- ✅ Prima transazione gratis
- ✅ Verifica identità base
- ✅ Pricing chiaro su sito

**Fase 2** (Post-validation, +3 mesi):
- ⏳ Modalità con Stripe
- ⏳ Stripe Connect setup
- ⏳ Pricing dinamico (A/B test)

**Fase 3** (Scale, +6 mesi):
- ⏳ Piano premium commercialisti
- ⏳ Volume discounts per grandi studi
- ⏳ API pricing per integrazioni

### 12.2 Monitoraggio Metriche Pricing

**Dashboard interna** (admin) deve tracciare:
- Revenue per modalità (Stripe vs senza)
- Margini per fascia importo ricevuta
- Conversion rate per pricing tier
- Churn correlato a pricing
- CAC/LTV ratio per canale acquisizione
- Transazioni perse per pricing (exit surveys)

### 12.3 Revisione Pricing

**Cadenza**: Ogni 6 mesi (o prima se metriche critiche).

**Checklist revisione**:
- [ ] Margini sostenibili? (target: >60% con Stripe, >90% senza)
- [ ] LTV/CAC ratio sano? (target: >3:1)
- [ ] Retention accettabile? (target: >30% a 6 mesi)
- [ ] Feedback utenti su pricing? (surveys, churn reasons)
- [ ] Competitor mosso prezzi?
- [ ] Costi operativi aumentati? (Stripe, server, support)

---

## 13. Conclusioni

### 13.1 Punti di Forza Pricing

✅ **Semplice**: % sul lordo, facile capire  
✅ **Fair**: chi usa di più paga di più  
✅ **Scalabile**: revenue cresce con utenti  
✅ **Competitivo**: molto più economico di commercialista  
✅ **Low-risk**: prima transazione gratis = trial senza rischi  
✅ **Flessibile**: con/senza Stripe per ogni esigenza  

### 13.2 Aree di Attenzione

⚠️ **Margini Stripe**: 71-74% accettabili ma monitorare costi  
⚠️ **Retention**: se <30%, pricing non importa (problema product)  
⚠️ **Frequency**: LTV dipende fortemente da transazioni/anno  
⚠️ **Abuse prevention**: verifica identità critica per prima gratis  

### 13.3 Next Steps

1. **Implementare pricing senza Stripe** in MVP
2. **Testare conversion** con prima transazione gratis
3. **Monitorare retention** ossessivamente (più importante di pricing)
4. **A/B test** commissioni dopo 500 utenti
5. **Aggiungere Stripe** solo se retention >30% a 6 mesi

---

**Vedi anche**:
- `business-structure.md` per contesto business
- `referral-program.md` per incentivi commercialisti
- `pricing-strategy-analysis.md` per analisi dettagliata e calcoli
