
![](Media/4.1.png)
# Sommario

- Introduzione
- Flusso di dati Gen2
    
    - Attività 1 - Copia di query di Snowflake nel flusso di dati
    
    - Attività 2 - Creazione della connessione a Snowflake
    
    - Attività 3 - Configurazione della destinazione dei dati per le query Supplier e PO
    
    - Attività 4 - Ridenominazione e pubblicazione del flusso di dati Snowflake
    
    - Attività 5 - Copia di query Dataverse nel flusso di dati
    
    - Attività 6 - Creazione della connessione a Dataverse
    
    - Attività 7 - Creazione della destinazione dati per la query Customer
    
    - Attività 8 - Pubblicazione e ridenominazione del flusso di dati Dataverse
    
    - Attività 9 - Copia di query SharePoint nel flusso di dati
    
    - Attività 10 - Creazione della connessione a SharePoint
    
    - Attività 11 - Configurazione della destinazione dei dati per la query People
    
    - Attività 12 - Pubblicazione e ridenominazione del flusso di dati SharePoint

- Riferimenti



# Introduzione 
Nel nostro scenario, i dati sui fornitori si trovano in Snowflake, i dati sui clienti si trovano in Dataverse e i dati sui dipendenti si trovano in SharePoint. Tutte queste origini dati vengono aggiornate in momenti diversi. Per ridurre al minimo il numero di aggiornamenti dei dati dei flussi di dati, creeremo flussi di dati individuali per ciascuna di queste origini dati.

**Nota:** è supportata la presenza di più origini dati in un unico flusso di dati.

In questo lab si imparerà a:  
- Connettersi a Snowflake mediante Flusso di dati Gen2 e inserire dati in lakehouse
- Connettersi a SharePoint mediante Flusso di dati Gen2 e inserire dati in lakehouse
- Connettersi a Dataverse mediante Flusso di dati Gen2 e inserire dati in lakehouse

# Flusso di dati Gen2
## Attività 1 - Copia di query di Snowflake nel flusso di dati

1. Torniamo all'area di lavoro di Fabric **FAIAD_<nome utente>** creata nel lab 2, attività 8.
2. Nel menu in alto selezionare **Nuovo -> Flusso di dati Gen2**.

    ![](Media/4.2.png)
  
Si apre la pagina **Flusso di dati**. Ora che abbiamo familiarità con Flusso di dati, procediamo con la copia delle query da Power BI Desktop a Flusso di dati.

3. Se non lo si è ancora aperto, aprire il file **FAIAD.pbix** contenuto nella cartella Report sul Desktop dell'ambiente lab.
4. Nella barra multifunzione selezionare **Home -> Trasforma dati**. Si apre la finestra Power Query. Come si è notato nel lab precedente, le query nel pannello di sinistra sono organizzate per origine dati.
5. Si apre la finestra Power Query. Nel pannello di sinistra selezionare le seguenti query nella cartella SnowflakeData tenendo premuto il tasto **CTRL o MAIUSC**:
    
    a.	SupplierCategories
    
    b.	Suppliers
    
    c.	Supplier
    
    d.	PO
    
    e.	PO Line Items

6. **Fare clic con il pulsante destro del mouse** e selezionare **Copia**.

    ![](Media/4.3.png)
 
7. Tornare al **browser**.
8. Nel **riquadro Flusso di dati** selezionare il **riquadro centrale** e premere **CTRL+V** (l'opzione Incolla del menu del pulsante destro non è attualmente supportata).

## Attività 2 - Creazione della connessione a Snowflake
Notare che le cinque query vengono incollate e sulla sinistra è visualizzato il pannello Query. Poiché non abbiamo creato una connessione a Snowflake, compare un messaggio di avviso che chiede di configurare la connessione.
1. Selezionare **Configura connessione**.

    ![](Media/4.4.png)
 
2. Si apre la finestra di dialogo Connetti a origine dati. Assicurarsi che nel menu a discesa **Connessione** sia selezionato **Crea nuova connessione**.
3. Il **Tipo di autenticazione** dovrebbe essere impostato su **Snowflake**.
4. Immettere **nome utente e password di Snowflake** disponibili nella scheda Variabili di ambiente (accanto alla scheda Guida al lab).
5. Selezionare **Connetti**.

    ![](Media/4.5.png)
 
Viene stabilita la connessione ed è possibile visualizzare i dati nel pannello di anteprima. Esplorare i Passaggi applicati delle query. In genere, la query Suppliers contiene i dettagli sui fornitori e SupplierCategories contiene le categorie di fornitori. Queste due tabelle vengono unite per creare la dimensione Supplier, con le colonne necessarie. Analogamente, PO Line Items viene unita con PO per creare il fatto PO. Ora dobbiamo inserire i dati di Supplier e PO in Lakehouse.

6. Come indicato in precedenza, non effettuiamo lo staging di questi dati. Quindi **fare clic con il pulsante destro del mouse** sulla query **Supplier** nel riquadro Query e selezionare **Abilita staging** per rimuovere il segno di spunta.

    ![](Media/4.6.png)
 
7. Allo stesso modo, fare clic con il pulsante destro del mouse sulla query **PO.** Selezionare **Abilita staging** per rimuovere il segno di spunta.

**Nota:** non è necessario disabilitare lo staging per le altre tre query poiché l'opzione Abilita caricamento era disattivata in Power BI Desktop (da cui sono state copiate le query).

## Attività 3 - Configurazione della destinazione dei dati per le query Supplier e PO

1. Seleziona la query **Supplier**.
2. Nell'angolo inferiore destro selezionare "**+**" accanto a **Destinazione dati**.
3. Selezionare **Lakehouse** dalla finestra di dialogo.

    ![](Media/4.7.png)
 
4. Si apre la finestra di dialogo Connetti alla destinazione dati. Nel **menu a discesa Connessione selezionare Lakehouse (nessuno)**.
5. Selezionare **Avanti**.

    ![](Media/4.8.png)

6. Si apre la finestra di dialogo Scegliere il target di destinazione. Assicurarsi che il pulsante di opzione **Nuova tabella** sia **selezionato**, poiché si sta creando una nuova tabella.
7. Vogliamo creare la tabella nel Lakehouse creato in precedenza. Nel pannello di sinistra andare a **Lakehouse -> FAIAD_<nomeutente>**. 
8. Selezionare **lh_FAIAD**
9. Lasciare il nome della tabella **Supplier**
10. Selezionare **Avanti**.

    ![](Media/4.9.png)
 
11.	Si apre la finestra di dialogo Scegli le impostazioni di destinazione. Ogni volta che Flusso di dati Gen2 si aggiorna, occorre eseguire un caricamento completo. Assicurarsi che **Metodo di aggiornamento** sia impostato su **Sostituisci**.
12.	Notare che compare l'avviso: "Alcuni nomi di colonna contengono caratteri non supportati. È necessario correggerli automaticamente?" Lakehouse non supporta i nomi di colonna che contengono spazi. Selezionare **Correggere**, per rimuovere l'avviso.
13. È possibile usare il mapping delle colonne per mappare le colonne del flusso di dati alle colonne esistenti. Nel nostro caso, si tratta di una nuova tabella. Pertanto possiamo usare le impostazioni predefinite. Selezionare **Salva impostazioni**.

    ![](Media/4.10.png)
 
14. Si apre nuovamente la **finestra di Power Query**. Nell'angolo in basso a destra notare che la Destinazione dati è impostata su **Lakehouse**. Allo stesso modo, **impostare la Destinazione dati per la query PO**. Al termine, la **Destinazione dati** della query PO dovrebbe essere impostata su **Lakehouse** come illustrato nello screenshot.

    ![](Media/4.11.png)
 
## Attività 4 - Ridenominazione e pubblicazione del flusso di dati Snowflake
1. Nella parte superiore dello schermo selezionare la **freccia accanto a Flusso di dati 1** per rinominarlo.
2. Nella finestra di dialogo cambiarne il nome in **df_Supplier_Snowflake**
3. Premere **INVIO** per salvare la modifica del nome.

    ![](Media/4.12.png)
 
4. Nell'angolo inferiore destro selezionare **Pubblica**.

    ![](Media/4.13.png)
 
Si aprirà nuovamente la **schermata di Data Factory**. La pubblicazione del flusso di dati potrebbe richiedere alcuni istanti.

**Nota:** talvolta il nome del flusso di dati non viene aggiornato. In questo caso, attenersi alla procedura seguente. Se il flusso di dati viene rinominato, è possibile passare all'attività successiva.

5. Al termine della pubblicazione di Flusso di dati 1, rinominiamolo. Fare clic sui **puntini di sospensione (…)** accanto a Flusso di dati 1. Selezionare **Proprietà**.

    ![](Media/4.14.png)
 
6. Si apre la finestra di dialogo Proprietà flusso di dati. Cambiarne il nome in **df_Supplier_Snowflake**
7. Nella casella di testo Descrizione aggiungere **Flusso di dati per inserire i dati sui fornitori da Snowflake in Lakehouse**
8. Selezionare **Salva**.

    ![](Media/4.15.png)
 
Si aprirà nuovamente la **schermata di Data Factory**. Ora creiamo un flusso di dati per importare i dati da Dataverse.

## Attività 5 - Copia di query Dataverse nel flusso di dati

1. Nel menu in alto selezionare **Nuovo -> Flusso di dati Gen2**.

    ![](Media/4.16.png)
 
Si apre la pagina **Flusso di dati**. Ora che abbiamo familiarità con Flusso di dati, procediamo con la copia delle query da Power BI Desktop a Flusso di dati.

2. Se non lo si è ancora aperto, aprire il file **FAIAD.pbix** contenuto nella cartella **Report** sul **Desktop** dell'ambiente lab. 
3. Nella barra multifunzione selezionare **Home -> Trasforma dati**. Si apre la finestra Power Query. Come si è notato nel lab precedente, le query nel pannello di sinistra sono organizzate per origine dati.
4. Si apre la finestra Power Query. Dal pannello di sinistra, selezionare le seguenti query nella cartella DataverseData tenendo premuto il tasto **CTRL:**

    a.	BabyBoomer
    
    b.	GenX
    
    c.	GenY
    
    d.	GenZ
    
    e.	Customer

5. **Fare clic con il pulsante destro del mouse** e selezionare **Copia**.

    ![](Media/4.17.png)
 
6. Tornare alla pagina **Flusso di dati** nel browser.
7. Nel riquadro **Flusso di dati** premere **CTRL+V** (l'opzione Incolla del menu del pulsante destro non è attualmente supportata).

## Attività 6 - Creazione della connessione a Dataverse
Notare che le cinque query vengono incollate e sulla sinistra è visualizzato il pannello Query. Poiché non abbiamo creato una connessione a Dataverse, compare un messaggio di avviso che chiede di configurare la connessione.

1. Selezionare **Configura connessione**.

    ![](Media/4.18.png)
 
2. Si apre la finestra di dialogo Connetti a origine dati. Assicurarsi che nel **menu a discesa Connessione sia selezionato Crea nuova connessione**.
3. Il **Tipo di autenticazione** dovrebbe essere **Account aziendale**.
4. Selezionare **Connetti**.

    ![](Media/4.19.png)

## Attività 7 - Creazione della destinazione dati per la query Customer
Viene stabilita la connessione ed è possibile visualizzare i dati nel pannello di anteprima. Esplorare i Passaggi applicati delle query. I dati sui clienti sono disponibili per categoria: BabyBoomer, GenX, GenY e GenZ. Queste quattro query vengono aggiunte per creare la query Customer. Ora dobbiamo inserire i dati di Customer in Lakehouse.

1. Come indicato in precedenza, non effettuiamo lo staging di questi dati. Quindi **fare clic con il pulsante destro del mouse** sulla query **Customer** nel riquadro Query e selezionare **Abilita staging** per rimuovere il segno di spunta.

    ![](Media/4.20.png)
 
2. Selezionare la query **Customer**.
3. Nell'angolo inferiore destro selezionare "**+**" accanto a **Destinazione dati**.
4. Selezionare **Lakehouse** dalla finestra di dialogo.

    ![](Media/4.21.png)
 
5. Si apre la finestra di dialogo Connetti alla destinazione dati. Nel **menu a discesa Connessione** selezionare **Lakehouse (nessuno)**.
6. Selezionare **Avanti**.

    ![](Media/4.22.png)

7. Si apre la finestra di dialogo Scegliere il target di destinazione. Assicurarsi che il pulsante di opzione **Nuova tabella** sia selezionato, poiché si sta creando una nuova tabella.
8.	Vogliamo creare la tabella nel Lakehouse creato in precedenza. Nel pannello di sinistra andare a **Lakehouse -> FAIAD_<nomeutente>**
9. Selezionare **lh_FAIAD**
10.	Lasciare il nome della tabella **Customer**

11. Selezionare **Avanti**.

    ![](Media/4.23.png)
 
12.	Si apre la finestra di dialogo Scegli le impostazioni di destinazione. Ogni volta che Flusso di dati Gen2 si aggiorna, occorre eseguire un caricamento completo. Assicurarsi che **Metodo di aggiornamento** sia impostato su **Sostituisci**.
13.	Notare che compare l'avviso: "Alcuni nomi di colonna contengono caratteri non supportati. È necessario correggerli automaticamente?" Lakehouse non supporta i nomi di colonna che contengono spazi. Selezionare **Correggere**, per rimuovere l'avviso.

14. È possibile usare il mapping delle colonne per mappare le colonne del flusso di dati alle colonne esistenti. Nel nostro caso, si tratta di una nuova tabella. Pertanto possiamo usare le impostazioni predefinite. Selezionare **Salva impostazioni**.

    ![](Media/4.24.png)
 
## Attività 8 - Pubblicazione e ridenominazione del flusso di dati Dataverse
1. Si apre nuovamente la **finestra di Power Query**. Nell'**angolo in basso a destra** notare che la Destinazione dati è impostata su Lakehouse.
2. Nell'angolo inferiore destro selezionare **Pubblica**.

    ![](Media/4.25.png)
 
**Nota:** Si aprirà nuovamente la schermata di Data Factory. La pubblicazione del flusso di dati potrebbe richiedere alcuni istanti.

3. Stiamo lavorando in Flusso di dati 1. Rinominiamolo prima di continuare. Fare clic sui **puntini di sospensione (…)** accanto a Flusso di dati 1. Selezionare **Proprietà**.

    ![](Media/4.26.png)
 
4. Si apre la finestra di dialogo Proprietà flusso di dati. Cambiarne il **Nome** in **df_Customer_Dataverse**
5. Nella casella di testo **Descrizione** aggiungere **Flusso di dati per inserire i dati sui clienti da Dataverse in Lakehouse**.
6. Selezionare **Salva**.

    ![](Media/4.27.png)
 
Si aprirà nuovamente la **schermata di Data Factory**. Ora creiamo un flusso di dati per importare i dati da SharePoint.

## Attività 9 - Copia di query SharePoint nel flusso di dati
1. Nel menu in alto selezionare **Nuovo -> Flusso di dati Gen2**.

    ![](Media/4.28.png)
 
Si apre la pagina **Flusso di dati**. Ora che abbiamo familiarità con Flusso di dati, procediamo con la copia delle query da Power BI Desktop a Flusso di dati.

2. Se non lo si è ancora aperto, aprire il file **FAIAD.pbix** contenuto nella cartella **Report** sul **Desktop** dell'ambiente lab. 
3. Nella barra multifunzione selezionare **Home -> Trasforma dati**. Si apre la finestra Power Query. Come si è notato nel lab precedente, le query nel pannello di sinistra sono organizzate per origine dati.
4. Si apre la finestra Power Query. Dal pannello di sinistra **selezionare** la query **People** nella cartella SharepointData.
5. **Fare clic con il pulsante destro del mouse** e selezionare **Copia**.

    ![](Media/4.29.png)
  
6. Tornare alla schermata **Flusso di dati** nel browser.
7. Nel riquadro **Flusso di dati** premere **CTRL+V** (l'opzione Incolla del menu del pulsante destro non è attualmente supportata).

Notare che la query viene incollata ed è disponibile nel pannello di sinistra. Poiché non abbiamo creato una connessione a SharePoint, compare un messaggio di avviso che chiede di configurare la connessione.

## Attività 10 - Creazione della connessione a SharePoint
1. Selezionare **Configura connessione**.

    ![](Media/4.30.png)
 
2. Si apre la finestra di dialogo Connetti a origine dati. Assicurarsi che nel menu a discesa **Connessione** sia selezionato **Crea nuova connessione**.
3. Il **Tipo di autenticazione** dovrebbe essere **Account aziendale**.
4. Selezionare **Connetti**.

    ![](Media/4.31.png)
 
## Attività 11 - Configurazione della destinazione dei dati per la query People
Viene stabilita la connessione ed è possibile visualizzare i dati nel pannello di anteprima. Esplorare i Passaggi applicati delle query. Ora dobbiamo inserire i dati di People in Lakehouse.

1. Come indicato in precedenza, non effettuiamo lo staging di questi dati. Quindi **fare clic con il pulsante destro del mouse** sulla query **People** nel riquadro Query e selezionare **Abilita staging** per rimuovere il segno di spunta.

    ![](Media/4.32.png)
 
2. Selezionare la query **People**.
3. Nell'angolo inferiore destro selezionare "**+**" accanto a **Destinazione dati**.
4. Selezionare **Lakehouse** dalla finestra di dialogo.

    ![](Media/4.33.png)
 
5. Si apre la finestra di dialogo Connetti alla destinazione dati. Nel menu a discesa Connessione selezionare **Lakehouse (nessuno)**.
6. Selezionare **Avanti**.

    ![](Media/4.34.png)
 
7. Si apre la finestra di dialogo Scegliere il target di destinazione. Assicurarsi che il pulsante di opzione **Nuova tabella** sia selezionato, poiché si sta creando una nuova tabella.
8. Vogliamo creare la tabella nel Lakehouse creato in precedenza. Nel pannello di sinistra andare a **Lakehouse -> FAIAD_<nomeutente>**. 
9. Selezionare **lh_FAIAD**
10. Lasciare il nome della tabella **People**
11. Selezionare **Avanti**.

    ![](Media/4.35.png)
 
12. Si apre la finestra di dialogo le impostazioni di. Ogni volta che Flusso di dati Gen2 si aggiorna, occorre eseguire un caricamento completo. Assicurarsi che **Metodo di aggiornamento** sia impostato su **Sostituisci**.
13. Notare che compare l'avviso: "Alcuni nomi di colonna contengono caratteri non supportati. È necessario correggerli automaticamente?" Lakehouse non supporta i nomi di colonna che contengono spazi. Selezionare **Correggere**, per rimuovere l'avviso.

14. È possibile usare il mapping delle colonne per mappare le colonne del flusso di dati alle colonne esistenti. Nel nostro caso, si tratta di una nuova tabella. Pertanto possiamo usare le impostazioni predefinite. Selezionare **Salva impostazioni**.

    ![](Media/4.36.png)
 
## Attività 12 - Pubblicazione e ridenominazione del flusso di dati SharePoint
1. Si apre nuovamente la **finestra di Power Query**. Nell'**angolo in basso a destra** notare che la Destinazione dati è impostata su **Lakehouse**.
2. Nell'angolo inferiore destro selezionare **Pubblica**.

    ![](Media/4.37.png)
 
**Nota:** Si aprirà nuovamente la schermata di Data Factory. La pubblicazione del flusso di dati potrebbe richiedere alcuni istanti.

3. Stiamo lavorando in Flusso di dati 1. Rinominiamolo prima di continuare. Fare clic sui **puntini di sospensione (…)** accanto a Flusso di dati 1. Selezionare **Proprietà**.

    ![](Media/4.38.png)
 
4. Si apre la finestra di dialogo Proprietà flusso di dati. Cambiarne il **Nome** in **df_People_SharePoint**
5. Nella casella di testo **Descrizione** aggiungere **Flusso di dati per inserire i dati del personale da SharePoint in Lakehouse**.
6. Selezionare **Salva**.

    ![](Media/4.39.png)
 
Si aprirà nuovamente la **schermata di Data Factory**. Ora abbiamo inserito tutti i dati in Lakehouse. Nel prossimo lab pianificheremo l'aggiornamento del flusso di dati.

# Riferimenti
Fabric Analyst in a Day (FAIAD) presenta alcune delle funzionalità chiave disponibili in Microsoft Fabric. Nel menu di servizio, la sezione Guida (?) include collegamenti ad alcune risorse utili.

![](Media/4.40.png)
 
Di seguito sono riportate ulteriori risorse utili che consentiranno di progredire nell'uso di Microsoft Fabric.

- Vedere il post di blog per leggere l'[annuncio completo sulla disponibilità generale di Microsoft Fabric](https://aka.ms/Fabric-Hero-Blog-Ignite23)
- Esplorare Fabric attraverso la [Presentazione guidata](https://aka.ms/Fabric-GuidedTour)
- Iscriversi alla versione di [valutazione gratuita di Microsoft Fabric](https://aka.ms/try-fabric)
- Visitare il [sito Web di Microsoft Fabric](https://aka.ms/microsoft-fabric)
- Acquisire nuove competenze esplorando i [moduli di apprendimento su Fabric](https://aka.ms/learn-fabric)
- Consultare la [documentazione tecnica di Fabric](https://aka.ms/fabric-docs)
- Leggere l'[e-book gratuito introduttivo a Fabric](https://aka.ms/fabric-get-started-ebook)
- Unirsi alla [community di Fabric](https://aka.ms/fabric-community) per pubblicare domande, condividere feedback e imparare dagli altri

Leggere i blog di annunci più approfonditi sull'esperienza in Fabric:

- [Blog sull'esperienza Data Factory in Fabric](https://aka.ms/Fabric-Data-Factory-Blog) 
- [Blog sull'esperienza Synapse Data Engineering in Fabric](https://aka.ms/Fabric-DE-Blog) 
- [Blog sull'esperienza Synapse Data Science in Fabric ](https://aka.ms/Fabric-DS-Blog)
- [Blog sull'esperienza Synapse Data Warehousing in Fabric ](https://aka.ms/Fabric-DW-Blog)
- [Blog sull'esperienza Synapse Real-Time Analytics in Fabric](https://aka.ms/Fabric-RTA-Blog)
- [Blog di annunci di Power BI](https://aka.ms/Fabric-PBI-Blog)
- [Blog sull'esperienza Data Activator in Fabric ](https://aka.ms/Fabric-DA-Blog)
- [Blog su amministrazione e governance in Fabric](https://aka.ms/Fabric-Admin-Gov-Blog)
- [Blog su OneLake in Fabric](https://aka.ms/Fabric-OneLake-Blog)
- [Blog sull'integrazione di Dataverse e Microsoft Fabric](https://aka.ms/Dataverse-Fabric-Blog)

© 2023 Microsoft Corporation. Tutti i diritti sono riservati.

L'uso della demo/del lab implica l'accettazione delle seguenti condizioni:

La tecnologia/le funzionalità descritte nella demo/nel lab sono fornite da Microsoft Corporation allo scopo di ottenere feedback dall'utente e offrire un'esperienza di apprendimento. L'utilizzo della demo/del lab è consentito solo per la valutazione delle caratteristiche e delle funzionalità di tale tecnologia e per l'invio di feedback a Microsoft. L'utilizzo per qualsiasi altro scopo non è consentito. È vietato modificare, copiare, distribuire, trasmettere, visualizzare, eseguire, riprodurre, pubblicare, concedere in licenza, usare per la creazione di lavori derivati, trasferire o vendere questa demo/questo lab o parte di essi.

SONO ESPLICITAMENTE PROIBITE LA COPIA E LA RIPRODUZIONE DELLA DEMO/DEL LAB (O DI QUALSIASI PARTE DI ESSI) IN QUALSIASI ALTRO SERVER O IN QUALSIASI ALTRA POSIZIONE PER ULTERIORE RIPRODUZIONE O RIDISTRIBUZIONE.

QUESTA DEMO/QUESTO LAB RENDONO DISPONIBILI TECNOLOGIE SOFTWARE/FUNZIONALITÀ DI PRODOTTO SPECIFICHE, INCLUSI NUOVI CONCETTI E NUOVE FUNZIONALITÀ POTENZIALI, IN UN AMBIENTE SIMULATO, CON UN'INSTALLAZIONE E UNA CONFIGURAZIONE PRIVE DI COMPLESSITÀ, PER GLI SCOPI DESCRITTI IN PRECEDENZA. LA TECNOLOGIA/I CONCETTI RAPPRESENTATI IN QUESTA DEMO/IN QUESTO LAB POTREBBERO NON CONTENERE LE FUNZIONALITÀ COMPLETE E IL LORO FUNZIONAMENTO POTREBBE NON ESSERE LO STESSO DELLA VERSIONE FINALE. È ANCHE POSSIBILE CHE UNA VERSIONE FINALE DI TALI FUNZIONALITÀ O CONCETTI NON VENGA RILASCIATA. L'ESPERIENZA D'USO DI TALI CARATTERISTICHE E FUNZIONALITÀ PUÒ INOLTRE RISULTARE DIVERSA IN UN AMBIENTE FISICO.

**FEEDBACK.** L'invio a Microsoft di feedback sulle caratteristiche, sulle funzionalità e/o sui concetti della tecnologia descritti in questa demo/questo lab implica la concessione a Microsoft, a titolo gratuito, del diritto di utilizzare, condividere e commercializzare tale feedback in qualsiasi modo e per qualsiasi scopo. Implica anche la concessione a titolo gratuito a terze parti del diritto di utilizzo di eventuali brevetti necessari per i loro prodotti, le loro tecnologie e i loro servizi al fine di utilizzare o interfacciarsi ai componenti software o ai servizi Microsoft specifici che includono il feedback. L'utente si impegna a non inviare feedback la cui inclusione all'interno di software o documentazione Microsoft imponga a Microsoft di concedere in licenza a terze parti tale software o documentazione. Questi diritti sussisteranno anche dopo la scadenza del presente contratto.

CON LA PRESENTE MICROSOFT CORPORATION NON RICONOSCE ALCUNA GARANZIA O CONDIZIONE RELATIVAMENTE ALLA DEMO/AL LAB, INCLUSE TUTTE LE GARANZIE E CONDIZIONI DI COMMERCIABILITÀ, DI FATTO ESPRESSE, IMPLICITE O PRESCRITTE DALLA LEGGE, ADEGUATEZZA PER UNO SCOPO SPECIFICO, TITOLARITÀ E NON VIOLABILITÀ. MICROSOFT NON OFFRE GARANZIE O RAPPRESENTAZIONI IN RELAZIONE ALL'ACCURATEZZA DEI RISULTATI E DELL'OUTPUT DERIVANTI DALL'USO DELLA DEMO/DEL LAB O ALL'ADEGUATEZZA DELLE INFORMAZIONI CONTENUTE NELLA DEMO/NEL LAB PER QUALSIASI SCOPO.

**CLAUSOLA DI RESPONSABILITÀ**

Questa demo/questo lab contiene solo una parte delle nuove funzionalità e dei miglioramenti in Microsoft Power BI. Alcune funzionalità potrebbero cambiare nelle versioni future del prodotto. In questa demo/in questo lab si apprendono alcune delle nuove funzionalità, ma non tutte.