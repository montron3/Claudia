# Regole Fiscali Certe - Prestazioni Occasionali

> **Documento creato da Claudia**  
> Fonte: Analisi di 1_lavoro_autonomo_e_obblighi.md, 2_copertura_previdenziale.md, 3_prestazioni_gestione_separata.md, 4_redditi_e_dichiarazioni.md, F24.md, Ritenuta.md, PROJECT_VISION_Version6.md  
> Data: 2026-01-22

## Premessa

Questo documento raccoglie tutte le **regole fiscali certe e ben definite** relative alle prestazioni di lavoro autonomo occasionale, utili per l'implementazione della piattaforma **ricevuta.studio**.

Queste regole **NON richiedono approvazione esterna** in quanto sono chiaramente stabilite dalla normativa vigente e dai documenti ufficiali INPS e Agenzia delle Entrate.

---

## 1. Gestione Separata INPS - Soglia €5.000

### 1.1 Regola Base
**L'iscrizione alla Gestione Separata INPS diventa obbligatoria al superamento di €5.000 annui lordi**.

| Parametro | Valore | Riferimento |
|-----------|--------|-------------|
| **Soglia obbligatoria** | €5.000/anno | File 2_copertura_previdenziale.md |
| **Periodo di riferimento** | Anno solare (1 gennaio - 31 dicembre) | File 2_copertura_previdenziale.md |
| **Calcolo** | Somma di tutti i compensi lordi dell'anno | File 2_copertura_previdenziale.md |
| **Effetto soglia** | Solo l'importo ECCEDENTE €5.000 è soggetto a contribuzione | File 2_copertura_previdenziale.md |

### 1.2 Aliquote Contributive 2025

#### Lavoratore NON pensionato e NON iscritto ad altra forma previdenziale
| Componente | Aliquota | A carico di |
|------------|----------|-------------|
| Quota lavoratore | 11,24% | Prestatore (trattenuta dal compenso) |
| Quota committente | 22,48% | Committente (aggiuntiva) |
| **TOTALE** | **33,72%** | - |

**Riferimento**: File 2_copertura_previdenziale.md, Circolare INPS n. 27/2025

#### Lavoratore GIÀ pensionato O iscritto ad altra forma previdenziale
| Componente | Aliquota | A carico di |
|------------|----------|-------------|
| Quota lavoratore | 8,00% | Prestatore (trattenuta dal compenso) |
| Quota committente | 16,00% | Committente (aggiuntiva) |
| **TOTALE** | **24,00%** | - |

**Riferimento**: File 2_copertura_previdenziale.md, Circolare INPS n. 27/2025

### 1.3 Massimale Contributivo 2025
| Parametro | Valore |
|-----------|--------|
| Massimale annuo | €120.607 |
| Effetto | I compensi eccedenti non sono soggetti a contribuzione |

**Riferimento**: File 2_copertura_previdenziale.md

### 1.4 Comportamento Sistema ricevuta.studio
**Da implementare**:
- ✅ Tracciamento automatico del totale annuo per prestatore
- ✅ Alert a €4.500: "Stai per raggiungere il limite INPS (€5.000)"
- ✅ Notifica a €5.000+: "Hai superato il limite INPS - Iscrizione alla Gestione Separata obbligatoria"
- ❌ Il sistema NON blocca la creazione di ricevute al superamento
- ❌ Il sistema NON suggerisce apertura P.IVA

**Riferimento**: PROJECT_VISION_Version6.md, sezione "Limite €5.000/anno"

---

## 2. Ritenuta d'Acconto (Withholding Tax)

### 2.1 Aliquota Standard
**Il committente sostituto d'imposta deve operare una ritenuta del 20% sui compensi lordi**.

| Parametro | Valore | Riferimento |
|-----------|--------|-------------|
| **Aliquota residenti Italia** | 20% | File 4_redditi_e_dichiarazioni.md, Art. 25 DPR 600/1973 |
| **Aliquota non residenti** | 30% (tassazione definitiva) | File Ritenuta.md |
| **Base di calcolo** | 100% del compenso lordo | File 4_redditi_e_dichiarazioni.md |
| **Natura** | Acconto IRPEF (recuperabile in dichiarazione) | File 4_redditi_e_dichiarazioni.md |

### 2.2 Esclusioni
| Situazione | Regola |
|------------|--------|
| Compensi inferiori a €25,82 | Esentati da ritenuta (solo enti pubblici/privati non commerciali) |
| Spese = Compenso | Non si applica ritenuta se documentate come "strettamente necessarie" |

**Riferimento**: File Ritenuta.md, File 4_redditi_e_dichiarazioni.md (Risoluzione AE 49/E 2013)

### 2.3 Versamento
| Parametro | Valore |
|-----------|--------|
| **Scadenza** | Giorno 16 del mese successivo al pagamento |
| **Modello** | F24 |
| **Codice tributo** | 1040 |
| **Sezione F24** | Erario |
| **Principio** | Cassa (quando materialmente pagato) |

**Riferimento**: File 4_redditi_e_dichiarazioni.md

---

## 3. Marca da Bollo (Revenue Stamp)

### 3.1 Soglia e Importo
| Parametro | Valore | Riferimento |
|-----------|--------|-------------|
| **Soglia obbligatoria** | €77,47 | PROJECT_VISION_Version6.md |
| **Importo marca** | €2,00 | Standard nazionale |
| **Quando applicare** | Ricevute con importo superiore a €77,47 | PROJECT_VISION_Version6.md |

### 3.2 Comportamento Sistema
**Da implementare**:
- ✅ Calcolo automatico della necessità marca da bollo
- ✅ Indicazione nel PDF ricevuta dove applicarla
- ✅ Sistema OCR per acquisizione numero seriale marca
- ✅ Tracking conservazione 10 anni

**Riferimento**: PROJECT_VISION_Version6.md, sezione "Marca da Bollo"

---

## 4. Categoria Fiscale - Redditi Diversi

### 4.1 Qualificazione Fiscale
I compensi da lavoro autonomo occasionale sono classificati come **"Redditi Diversi"** ai sensi dell'art. 67 comma 1 lettera l) del TUIR (DPR 917/1986).

**Riferimento**: File 4_redditi_e_dichiarazioni.md

### 4.2 Determinazione Base Imponibile
**Formula**: 
```
Reddito Imponibile = Compensi Percepiti - Spese Specificamente Inerenti
```

| Elemento | Regola |
|----------|--------|
| Compensi | Ammontare lordo percepito nell'anno |
| Spese deducibili | Solo quelle SPECIFICAMENTE collegate alla singola prestazione |
| Documentazione | Obbligatoria per tutte le spese dedotte |
| Periodo spese | Possono essere di anni diversi se documentate |
| Limite spese | Non possono superare i compensi percepiti |

**Riferimento**: File 4_redditi_e_dichiarazioni.md, Art. 71 comma 2 TUIR

### 4.3 Rimborsi Spese
| Tipo Spesa | Trattamento Fiscale |
|------------|---------------------|
| Viaggio, vitto, alloggio riaddebitate | Imponibili (incluse nel compenso) |
| Viaggio, vitto, alloggio pagate direttamente dal committente | Non imponibili |
| Spese "strettamente necessarie" = Compenso | Reddito = 0, no ritenuta se documentate |

**Riferimento**: File 4_redditi_e_dichiarazioni.md, Risoluzione AE 69/E 2003, Risoluzione AE 49/E 2013

---

## 5. Versamenti con Modello F24

### 5.1 Modalità di Presentazione

#### Contribuenti CON Partita IVA
| Parametro | Valore |
|-----------|--------|
| **Modalità** | Solo telematica (obbligatoria) |
| **Canali** | F24web, F24online, home banking, intermediari |

#### Contribuenti SENZA Partita IVA
| Parametro | Valore |
|-----------|--------|
| **Modalità** | Cartacea o telematica |
| **Dove cartaceo** | Sportelli bancari, Poste Italiane |
| **Limite contanti** | €0 (non ammesso pagamento in contanti) |
| **Mezzi ammessi** | Assegni bancari e circolari, bancomat, carte di credito |

**Riferimento**: File F24.md

### 5.2 Codici Tributo

#### Ritenuta d'Acconto (Sezione Erario)
| Campo | Valore |
|-------|--------|
| Codice tributo | 1040 |
| Descrizione | Ritenute su redditi di lavoro autonomo |
| Anno riferimento | AAAA |
| Importo | Sempre con 2 decimali |

**Riferimento**: File 4_redditi_e_dichiarazioni.md

#### Contributi INPS (Sezione INPS)

**Lavoratore NON pensionato e NON iscritto ad altra gestione:**
| Campo | Valore |
|-------|--------|
| Causale contributo | CXX |
| Descrizione | Gestione Separata - iscrizione esclusiva |
| Matricola INPS | Codice fiscale committente |
| Periodo riferimento | MM/AAAA |

**Lavoratore GIÀ pensionato O iscritto ad altra gestione:**
| Campo | Valore |
|-------|--------|
| Causale contributo | C10 |
| Descrizione | Gestione Separata - già pensionato o altra assicurazione |
| Matricola INPS | Codice fiscale committente |
| Periodo riferimento | MM/AAAA |

**Riferimento**: File 2_copertura_previdenziale.md

### 5.3 Scadenze
| Tipo Versamento | Scadenza |
|-----------------|----------|
| Ritenute d'acconto | Giorno 16 del mese successivo al pagamento |
| Contributi INPS | Giorno 16 del mese successivo al pagamento |
| Pagamenti entro 12/01 | Considerati anno precedente (principio cassa allargato) |

**Riferimento**: File 4_redditi_e_dichiarazioni.md, File 2_copertura_previdenziale.md

### 5.4 Regole di Arrotondamento
- Utilizzare sempre **2 decimali**
- Arrotondare il 3° decimale: ≥5 arrotonda per eccesso, <5 per difetto
- Esempio: €1.234,567 → €1.234,57

**Riferimento**: File F24.md

---

## 6. Certificazione Unica (CU)

### 6.1 Obblighi e Scadenze
| Parametro | Valore |
|-----------|--------|
| **Scadenza** | 16 marzo dell'anno successivo |
| **Destinatari** | Prestatore + Agenzia delle Entrate |
| **Modalità invio** | Solo telematica |
| **Contenuto** | Compensi lordi, ritenute, contributi INPS |

**Riferimento**: File 4_redditi_e_dichiarazioni.md

### 6.2 Codici Causale
| Situazione | Codice Causale |
|------------|----------------|
| Lavoro autonomo occasionale generico | M |
| Obbligazioni di fare/non fare/permettere | M1 |
| Prestazioni occasionali sotto €5.000 (no INPS) | O |

**Riferimento**: File 4_redditi_e_dichiarazioni.md

### 6.3 Dati da Indicare
- Punti 1-4: Dati anagrafici prestatore
- Punto 5: Redditi diversi (Causale M, M1 o O)
- Punto 34-35: Dati previdenziali se reddito annuo > €5.000

**Riferimento**: File 4_redditi_e_dichiarazioni.md

---

## 7. Denuncia UniEmens

### 7.1 Quando Obbligatoria
**Obbligatoria per committenti quando il prestatore supera €5.000 annui**.

| Parametro | Valore |
|-----------|--------|
| **Frequenza** | Mensile |
| **Scadenza** | Ultimo giorno del mese successivo al pagamento |
| **Modalità** | Telematica via Cassetto Previdenziale |
| **Contenuto** | Dati retributivi e contributivi |

**Riferimento**: File 2_copertura_previdenziale.md

### 7.2 Dati da Includere
- Codice fiscale prestatore
- Importo compenso del mese
- Contributi calcolati (quota lavoratore + quota committente)
- Periodo di riferimento

**Riferimento**: File 2_copertura_previdenziale.md

---

## 8. Modello 770 (per Committenti Sostituti d'Imposta)

### 8.1 Obbligo
**I committenti sostituti d'imposta devono presentare il Modello 770**.

| Parametro | Valore |
|-----------|--------|
| **Scadenza** | 31 ottobre dell'anno successivo |
| **Contenuto** | Riepilogo ritenute operate e versate |
| **Modalità** | Telematica |

**Riferimento**: File 4_redditi_e_dichiarazioni.md

---

## 9. Obblighi del Prestatore

### 9.1 Comunicazioni al Committente
Il prestatore deve:
- ✅ Comunicare il proprio status (sotto/sopra €5.000) all'inizio dell'incarico
- ✅ Comunicare TEMPESTIVAMENTE se supera la soglia €5.000 durante l'anno
- ✅ Fornire codice fiscale e IBAN
- ✅ Emettere nota di pagamento (ricevuta) per ogni prestazione

**Riferimento**: File 2_copertura_previdenziale.md

### 9.2 Iscrizione INPS
Quando il prestatore supera €5.000:
- ✅ Deve iscriversi alla Gestione Separata INPS (una tantum)
- ✅ Utilizzare il servizio online INPS "Iscrizione alla Gestione Separata"
- ✅ Conservare numero matricola per comunicazioni future

**Riferimento**: File 2_copertura_previdenziale.md

### 9.3 Dichiarazione dei Redditi
- ✅ Includere i redditi diversi nel Modello Redditi (ex Unico)
- ✅ Indicare ritenute subite per recupero crediti IRPEF
- ✅ Indicare contributi INPS versati (se applicabili)

**Riferimento**: File 4_redditi_e_dichiarazioni.md

---

## 10. Obblighi del Committente

### 10.1 Prima del Pagamento
- ✅ Verificare se il prestatore ha superato €5.000 annui
- ✅ Richiedere comunicazione scritta dello status previdenziale
- ✅ Registrare il prestatore nel Cassetto Previdenziale INPS (se > €5.000)

### 10.2 Al Momento del Pagamento
**Se prestatore < €5.000:**
- ✅ Trattenere ritenuta 20% (solo IRPEF)
- ❌ NO contributi INPS

**Se prestatore ≥ €5.000:**
- ✅ Trattenere ritenuta 20% (IRPEF)
- ✅ Trattenere contributo INPS quota lavoratore (11,24% o 8%)
- ✅ Calcolare contributo INPS quota committente (22,48% o 16%)

### 10.3 Entro il 16 del Mese Successivo
- ✅ Versare ritenuta IRPEF con F24 (codice 1040)
- ✅ Versare contributi INPS con F24 (codice CXX o C10) se applicabili

### 10.4 Entro Fine Mese Successivo
- ✅ Inviare denuncia UniEmens (se applicabile)

### 10.5 Entro 16 Marzo Anno Successivo
- ✅ Emettere Certificazione Unica (CU)
- ✅ Inviare CU telematicamente ad Agenzia Entrate

### 10.6 Entro 31 Ottobre Anno Successivo
- ✅ Presentare Modello 770 (se sostituto d'imposta)

**Riferimento**: File 2_copertura_previdenziale.md, File 4_redditi_e_dichiarazioni.md

---

## 11. Formule di Calcolo

### 11.1 Calcolo Netto da Corrispondere al Prestatore

#### Caso A: Prestatore sotto €5.000 annui
```
Compenso Lordo: €1.000,00
Ritenuta 20%:   -€200,00
--------------------------
Netto da pagare: €800,00
```

#### Caso B: Prestatore oltre €5.000 annui (NON pensionato, NON altra gestione)
Ipotesi: reddito annuo €9.000, quindi base INPS = €4.000
```
Compenso Lordo:              €1.000,00
Ritenuta 20%:                -€200,00
Contributo INPS 11,24%:      -€112,40
---------------------------------------
Netto da pagare:             €687,60

Committente paga inoltre a INPS:
Contributo 22,48%:           €224,80
```

#### Caso C: Prestatore oltre €5.000 annui (GIÀ pensionato O altra gestione)
```
Compenso Lordo:              €1.000,00
Ritenuta 20%:                -€200,00
Contributo INPS 8%:          -€80,00
---------------------------------------
Netto da pagare:             €720,00

Committente paga inoltre a INPS:
Contributo 16%:              €160,00
```

**Riferimento**: File 2_copertura_previdenziale.md, File 4_redditi_e_dichiarazioni.md

### 11.2 Calcolo Base Imponibile INPS
```
Formula:
Reddito Annuo Totale - €5.000 = Base Imponibile INPS

Esempio:
€9.000 - €5.000 = €4.000 (base per calcolo contributi)
```

**Nota**: Solo l'eccedenza rispetto a €5.000 è soggetta a contribuzione.

**Riferimento**: File 2_copertura_previdenziale.md

---

## 12. Conservazione Documenti

### 12.1 Durata Conservazione
| Documento | Periodo |
|-----------|---------|
| Ricevute/Note di pagamento | 10 anni (obbligo fiscale) |
| Marche da bollo (foto/OCR) | 10 anni |
| F24 pagati | 10 anni |
| Certificazioni Uniche | 10 anni |
| Comunicazioni INPS | 10 anni |

**Riferimento**: PROJECT_VISION_Version6.md

### 12.2 Nota sulla Conservazione Sostitutiva
**La piattaforma ricevuta.studio NON effettua conservazione sostitutiva** dei documenti fiscali.

Gli utenti devono provvedere autonomamente alla conservazione secondo normativa vigente.

**Riferimento**: PROJECT_VISION_Version6.md

---

## 13. Commissioni Piattaforma ricevuta.studio

### 13.1 Struttura Commissioni

#### Modalità A: Solo Prestatore Registrato
| Figura | Commissione |
|--------|-------------|
| Prestatore | 0,8% |
| Committente (non registrato) | 0% |
| **Totale** | **0,8%** |

#### Modalità B: Solo Committente Registrato
| Figura | Commissione |
|--------|-------------|
| Prestatore (non registrato) | 0% |
| Committente | 1,3% (se sostituto d'imposta) |
| **Totale** | **1,3%** |

#### Modalità C: Entrambi Registrati
| Figura | Commissione |
|--------|-------------|
| Prestatore | 0,8% |
| Committente | 1,3% (se sostituto d'imposta) |
| **Totale** | **2,1%** |

### 13.2 Sconti per Pagamenti via Stripe
Con pagamento gestito da Stripe, commissioni ridotte:
| Modalità | Standard | Con Stripe |
|----------|----------|------------|
| Solo prestatore | 0,8% | 0,8% |
| Solo committente | 1,3% | 1,3% |
| Entrambi | 0,8% + 1,3% = 2,1% | 0,8% + 1,3% = 2,1% |

**Nota**: Le commissioni Stripe sono AGGIUNTIVE a quelle della piattaforma.

**Riferimento**: PROJECT_VISION_Version6.md

---

## 14. Note di Implementazione per ricevuta.studio

### 14.1 Funzionalità Core da Implementare
**Certezze da codificare:**
1. ✅ Tracker €5.000 con alert a €4.500
2. ✅ Calcolo automatico ritenuta 20%
3. ✅ Calcolo automatico INPS (33,72% o 24% a seconda dello status)
4. ✅ Verifica soglia marca da bollo €77,47
5. ✅ Generazione F24 con codici corretti (1040, CXX, C10)
6. ✅ Generazione Certificazione Unica
7. ✅ Calcolo bidirezionale lordo ↔ netto
8. ✅ Gestione scadenze (16 del mese, 31 ottobre, 16 marzo)
9. ✅ Storico documenti con conservazione 10 anni
10. ✅ Gestione OCR marche da bollo

### 14.2 Validazioni da Implementare
1. Codice fiscale valido (lato committente e prestatore)
2. IBAN valido (lato prestatore)
3. Importo lordo > 0
4. Verifica coerenza calcoli (lordo - ritenuta - INPS = netto)
5. Verifica massimale INPS €120.607
6. Verifica data pagamento (per principio di cassa)

### 14.3 Business Logic Certa
```javascript
// Pseudo-codice per logica certa
function calcolaNetto(lordo, annuoTotale, statusPrevidenziale) {
  const ritenuta = lordo * 0.20; // Sempre 20%
  
  let contributoINPS = 0;
  if (annuoTotale > 5000) {
    const baseINPS = Math.min(annuoTotale - 5000, 120607);
    if (statusPrevidenziale === 'esclusivo') {
      contributoINPS = baseINPS * 0.1124; // 11.24%
    } else {
      contributoINPS = baseINPS * 0.08; // 8%
    }
  }
  
  const netto = lordo - ritenuta - contributoINPS;
  return { netto, ritenuta, contributoINPS };
}

function verificaMarcaBollo(importo) {
  return importo > 77.47;
}
```

---

## Conclusioni

Questo documento raccoglie **tutte le regole fiscali certe** che possono essere implementate immediatamente nella piattaforma **ricevuta.studio** senza necessità di ulteriori verifiche o approvazioni esterne.

Le regole qui contenute sono basate su:
- Normativa vigente (TUIR, DPR 600/1973)
- Circolari INPS (in particolare n. 27/2025)
- Risoluzioni Agenzia delle Entrate
- Documentazione ufficiale presente nei file markdown del progetto

Per le **regole incerte o ambigue**, consultare il documento separato **regole_fiscali_grigie.md**.

---

**Versione**: 1.0  
**Data creazione**: 2026-01-22  
**Prossimo aggiornamento**: Alla pubblicazione di nuove circolari o normative
