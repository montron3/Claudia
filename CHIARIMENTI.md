# CHIARIMENTI DA VERIFICARE

> **Documento generato da Claudia** - Esperta Fiscale per Ricevuta.Studio
> Questo documento elenca tutte le informazioni **NON presenti** nei file sorgente che richiedono verifica con fonti ufficiali o consulenza professionale.

> ⚠️ **AGGIORNAMENTO**: Tutte le domande di questo documento sono state analizzate seguendo le regole di Claudia.
> Le risposte dettagliate, basate esclusivamente sui file di conoscenza disponibili, sono disponibili in **[RISPOSTE_CHIARIMENTI.md](RISPOSTE_CHIARIMENTI.md)**.

---

## 1. LIMITI E SOGLIE

### 1.1 Limite Massimo Totale Annuo

**Domanda**: Esiste un limite massimo alla somma di TUTTE le ricevute che un prestatore può emettere in un anno per il lavoro autonomo occasionale ex art. 2222 CC?

**Stato**: ⚠️ **DA VERIFICARE**

**Cosa dicono i file sorgente**:
- Il limite €5.000 riguarda SOLO l'iscrizione alla Gestione Separata INPS
- Non viene menzionato alcun limite massimo annuo che blocchi l'emissione di ricevute

**Azione richiesta**:
- [ ] Verificare con Agenzia delle Entrate
- [ ] Verificare con INPS
- [ ] Consultare normativa aggiornata

**Impatto su Ricevuta.Studio**: Se esiste un limite, il sistema dovrà tracciarlo e notificare l'utente.

---

### 1.2 Limite Massimo per Singolo Committente

**Domanda**: Esiste un limite massimo che un prestatore può ricevere da UN SINGOLO committente in un anno?

**Stato**: ⚠️ **DA VERIFICARE**

**Cosa dicono i file sorgente**:
- Per il lavoro autonomo occasionale ex art. 2222 CC: **NON risultano limiti**
- I limiti per singolo committente citati nella normativa (Legge di bilancio 2023) si riferiscono alle "prestazioni di lavoro occasionali" (art. 54-bis DL 50/2017), che è una tipologia DIVERSA

**Azione richiesta**:
- [ ] Confermare che per art. 2222 CC non esistono limiti per singolo committente
- [ ] Verificare eventuali interpretazioni dell'Agenzia delle Entrate
- [ ] Verificare se la continuità di rapporto con stesso committente può far riqualificare il rapporto

**Impatto su Ricevuta.Studio**: Determina se il sistema deve tracciare importi per coppia prestatore-committente.

---

### 1.3 Rischio Riqualificazione del Rapporto

**Domanda**: Quando il lavoro autonomo occasionale rischia di essere riqualificato come:
- Lavoro subordinato?
- Collaborazione coordinata e continuativa?
- Attività abituale (P.IVA)?

**Stato**: ⚠️ **DA APPROFONDIRE**

**Cosa dicono i file sorgente**:
- Menzionano la distinzione tra lavoro occasionale e altre tipologie
- Non forniscono criteri quantitativi specifici (numero di prestazioni, frequenza, ecc.)

**Azione richiesta**:
- [ ] Definire criteri di "occasionalità" vs "abitualità"
- [ ] Verificare orientamenti giurisprudenziali
- [ ] Definire soglie di warning per gli utenti

**Impatto su Ricevuta.Studio**: Il sistema potrebbe dover avvisare utenti a rischio riqualificazione.

---

## 2. ASPETTI FISCALI

### 2.1 Deducibilità Spese per il Prestatore

**Domanda**: Quali spese può dedurre il prestatore nella dichiarazione dei redditi?

**Stato**: ⚠️ **DA APPROFONDIRE**

**Cosa dicono i file sorgente**:
- "Spese specificamente inerenti alla produzione del reddito"
- Non forniscono elenco dettagliato di spese ammesse/non ammesse

**Azione richiesta**:
- [ ] Elenco tipologie di spese deducibili
- [ ] Documentazione richiesta per la deducibilità
- [ ] Limiti di deducibilità

**Impatto su Ricevuta.Studio**: Il calcolatore potrebbe includere una sezione spese.

---

### 2.2 Rimborsi Spese - Trattamento Dettagliato

**Domanda**: Come si trattano fiscalmente i diversi tipi di rimborsi spese?

**Stato**: ⚠️ **DA APPROFONDIRE**

**Cosa dicono i file sorgente**:
- Rimborsi viaggio/vitto/alloggio sostenuti dal lavoratore e rimborsati: imponibili
- Spese pagate direttamente dal committente: non imponibili (Risoluzione AE 49/E 2013)
- Spese anticipate in nome e per conto del cliente: non imponibili se documentate

**Azione richiesta**:
- [ ] Definire casistiche complete con esempi
- [ ] Chiarire trattamento per nota di pagamento vs ricevuta

**Impatto su Ricevuta.Studio**: Guida la compilazione della ricevuta e il calcolo del netto.

---

### 2.3 Committente Privato Non Sostituto d'Imposta

**Domanda**: Come funziona quando il committente è un privato (non P.IVA)?

**Stato**: ⚠️ **DA APPROFONDIRE**

**Cosa dicono i file sorgente**:
- Menzionano la distinzione tra sostituti d'imposta e non
- Non dettagliano completamente il flusso per committenti privati

**Azione richiesta**:
- [ ] Il privato deve comunque operare ritenuta? (risposta: NO, ma verificare)
- [ ] Come gestisce il prestatore la dichiarazione senza CU?
- [ ] Obblighi del privato committente

**Impatto su Ricevuta.Studio**: Determina il flusso "tra privati" nella piattaforma.

---

## 3. CONTRIBUTI INPS

### 3.1 Iscrizione Gestione Separata - Tempistiche

**Domanda**: Entro quando il prestatore deve iscriversi alla Gestione Separata dopo aver superato €5.000?

**Stato**: ⚠️ **DA VERIFICARE**

**Cosa dicono i file sorgente**:
- L'obbligo scatta al superamento di €5.000
- Non specificano un termine temporale per l'iscrizione

**Azione richiesta**:
- [ ] Verificare termine per iscrizione
- [ ] Verificare sanzioni per ritardata iscrizione

**Impatto su Ricevuta.Studio**: Determina i messaggi di notifica all'utente.

---

### 3.2 Contributi INPS - Chi Versa Cosa

**Domanda**: In caso di più committenti che concorrono al superamento della soglia €5.000, come si ripartisce l'obbligo di versamento?

**Stato**: ✅ **PRESENTE NEI FILE** (ma da confermare implementazione)

**Cosa dicono i file sorgente**:
- Ciascun committente calcola il contributo in misura proporzionale
- Rapporto tra il suo compenso e il totale degli importi riconosciuti

**Azione richiesta**:
- [ ] Definire algoritmo di ripartizione per il software
- [ ] Verificare con esempi pratici

**Impatto su Ricevuta.Studio**: Logica di calcolo per la ripartizione contributi.

---

### 3.3 Contributi INPS - Aliquote Anni Precedenti

**Domanda**: Quali erano le aliquote INPS negli anni precedenti al 2025?

**Stato**: ⚠️ **DA RECUPERARE**

**Cosa dicono i file sorgente**:
- Solo aliquote 2025 (33,72% e 24%)

**Azione richiesta**:
- [ ] Recuperare storico aliquote per anni precedenti
- [ ] Necessario per gestire ricevute retroattive o correzioni

**Impatto su Ricevuta.Studio**: Tabella storica aliquote per calcoli corretti.

---

## 4. DOCUMENTI

### 4.1 Formato Ricevuta - Campi Obbligatori

**Domanda**: Quali sono i campi obbligatori che una ricevuta/nota di pagamento deve contenere per legge?

**Stato**: ⚠️ **DA APPROFONDIRE**

**Cosa dicono i file sorgente**:
- Forniscono un esempio di nota di pagamento (par. 1.8)
- Non specificano quali campi sono obbligatori vs facoltativi

**Azione richiesta**:
- [ ] Elenco campi obbligatori per validità fiscale
- [ ] Elenco campi consigliati
- [ ] Requisiti formali (firma, data, ecc.)

**Impatto su Ricevuta.Studio**: Template ricevuta e validazioni.

---

### 4.2 F24 - Generazione Automatica

**Domanda**: Il sistema può generare un F24 compilato automaticamente?

**Stato**: ⚠️ **DA VERIFICARE**

**Cosa dicono i file sorgente**:
- Descrivono come compilare l'F24
- Non chiariscono se è possibile/legale generare F24 precompilati

**Azione richiesta**:
- [ ] Verificare se è consentito generare F24 precompilati
- [ ] Verificare formato file accettato da AE per F24 telematico
- [ ] Alternative: istruzioni di compilazione vs documento precompilato

**Impatto su Ricevuta.Studio**: Determina se generare F24 o solo istruzioni.

---

### 4.3 CU - Generazione Automatica

**Domanda**: Il sistema può generare una CU valida?

**Stato**: ⚠️ **DA VERIFICARE**

**Cosa dicono i file sorgente**:
- Descrivono struttura e campi della CU
- Non chiariscono requisiti tecnici per validità

**Azione richiesta**:
- [ ] Formato file CU accettato da AE
- [ ] Firma digitale richiesta?
- [ ] Il sistema può generare "bozza CU" vs "CU ufficiale"?

**Impatto su Ricevuta.Studio**: Determina funzionalità CU nella piattaforma.

---

## 5. COMUNICAZIONE ITL

### 5.1 Chi è Esente dalla Comunicazione

**Domanda**: Quali committenti sono esenti dall'obbligo di comunicazione preventiva all'ITL?

**Stato**: ✅ **PARZIALMENTE PRESENTE NEI FILE**

**Cosa dicono i file sorgente**:
- Solo committenti che operano come "imprenditori" sono obbligati
- Esclusi: privati non imprenditori, professionisti per attività non imprenditoriale

**Azione richiesta**:
- [ ] Confermare casistiche di esenzione
- [ ] Chiarire posizione di: associazioni, enti no-profit, condomini

**Impatto su Ricevuta.Studio**: Determina quando mostrare reminder comunicazione ITL.

---

## 6. MARCA DA BOLLO

### 6.1 Conservazione Marca da Bollo Fisica

**Domanda**: Se si inserisce solo il numero seriale nella ricevuta, come deve essere conservata la marca fisica?

**Stato**: ⚠️ **DA APPROFONDIRE**

**Cosa dicono i file sorgente**:
- Conservazione 10 anni
- Non dettagliano modalità di conservazione

**Azione richiesta**:
- [ ] Requisiti di conservazione (dove, come)
- [ ] Cosa succede se la marca fisica viene persa?
- [ ] È sufficiente la foto della marca?

**Impatto su Ricevuta.Studio**: Guida utente e funzionalità archivio marche.

---

### 6.2 Marca da Bollo Virtuale

**Domanda**: È possibile assolvere il bollo in modo virtuale per le ricevute di prestazione occasionale?

**Stato**: ⚠️ **DA VERIFICARE**

**Cosa dicono i file sorgente**:
- Non menzionano la possibilità di bollo virtuale per prestazioni occasionali

**Azione richiesta**:
- [ ] Verificare se è ammesso il bollo virtuale
- [ ] Requisiti per l'autorizzazione al bollo virtuale
- [ ] Costi e procedure

**Impatto su Ricevuta.Studio**: Potenziale funzionalità futura.

---

## 7. SANZIONI

### 7.1 Sanzioni per Errori nella Ricevuta

**Domanda**: Quali sono le sanzioni per errori nella compilazione della ricevuta?

**Stato**: ⚠️ **DA APPROFONDIRE**

**Cosa dicono i file sorgente**:
- Sanzioni per omessa comunicazione ITL (€500-2.500)
- Sanzioni per omesso F24 a saldo zero
- Non dettagliano sanzioni per errori nella ricevuta

**Azione richiesta**:
- [ ] Sanzioni per importo errato
- [ ] Sanzioni per ritenuta non applicata
- [ ] Sanzioni per marca da bollo mancante
- [ ] Procedure di ravvedimento

**Impatto su Ricevuta.Studio**: Guida utente e gestione errori.

---

### 7.2 Sanzioni per il Prestatore

**Domanda**: Quali sanzioni rischia il prestatore in caso di inadempimenti?

**Stato**: ⚠️ **DA APPROFONDIRE**

**Cosa dicono i file sorgente**:
- Focus principalmente su obblighi del committente
- Poco dettaglio su sanzioni specifiche per il prestatore

**Azione richiesta**:
- [ ] Omessa iscrizione Gestione Separata
- [ ] Omessa comunicazione superamento soglia
- [ ] Mancata applicazione marca da bollo

**Impatto su Ricevuta.Studio**: Messaggi di warning per gli utenti.

---

## 8. CASI PARTICOLARI

### 8.1 Prestazioni verso l'Estero

**Domanda**: Come funzionano le prestazioni occasionali per committenti esteri?

**Stato**: ⚠️ **NON PRESENTE NEI FILE**

**Azione richiesta**:
- [ ] Trattamento fiscale
- [ ] Obblighi IVA (se applicabili)
- [ ] Ritenuta d'acconto con committente estero
- [ ] Contributi INPS

**Impatto su Ricevuta.Studio**: Determina se gestire casi internazionali.

---

### 8.2 Prestazioni da Non Residenti

**Domanda**: Come funziona se il prestatore non è residente in Italia?

**Stato**: ✅ **PARZIALMENTE PRESENTE**

**Cosa dicono i file sorgente**:
- Ritenuta 30% a titolo d'imposta per non residenti

**Azione richiesta**:
- [ ] Obblighi contributivi INPS per non residenti
- [ ] Documentazione richiesta
- [ ] Convenzioni contro doppie imposizioni

**Impatto su Ricevuta.Studio**: Gestione utenti non residenti.

---

### 8.3 Prestazioni nel Settore Agricolo

**Domanda**: Ci sono regole speciali per prestazioni occasionali in agricoltura?

**Stato**: ⚠️ **MENZIONATO MA NON APPROFONDITO**

**Cosa dicono i file sorgente**:
- Menzionano "novità per il settore agricolo" nella Legge di bilancio 2023
- Non dettagliano le specificità

**Azione richiesta**:
- [ ] Regole specifiche settore agricolo
- [ ] Limiti diversi?
- [ ] Aliquote diverse?

**Impatto su Ricevuta.Studio**: Eventuale gestione caso agricoltura.

---

## 9. AGGIORNAMENTI NORMATIVI

### 9.1 Monitoraggio Normativo

**Domanda**: Come mantenersi aggiornati sui cambiamenti normativi?

**Stato**: ⚠️ **DA DEFINIRE**

**Azione richiesta**:
- [ ] Fonti ufficiali da monitorare (INPS, AE, ITL)
- [ ] Frequenza aggiornamenti (circolari INPS, risoluzioni AE)
- [ ] Processo di aggiornamento documentazione Ricevuta.Studio

**Impatto su Ricevuta.Studio**: Manutenzione e aggiornamento piattaforma.

---

## RIEPILOGO PRIORITÀ

| Priorità | Argomento | Impatto |
|----------|-----------|---------|
| 🔴 ALTA | Limite totale annuo | Logica di business |
| 🔴 ALTA | Limite per committente | Logica di business |
| 🔴 ALTA | Formato ricevuta obbligatorio | Template documenti |
| 🟡 MEDIA | Generazione F24/CU | Funzionalità documenti |
| 🟡 MEDIA | Committente privato | Flusso "tra privati" |
| 🟡 MEDIA | Rischio riqualificazione | Warning utenti |
| 🟢 BASSA | Prestazioni estero | Casi edge |
| 🟢 BASSA | Settore agricolo | Casi edge |

---

*Documento generato per il progetto Ricevuta.Studio*
*Per ogni punto contrassegnato come DA VERIFICARE, consultare @montron3 o fonti normative ufficiali*
