![](Media/2.1.png)
# Sommario	
- Introduzione

- Licenza di Fabric
    
    Attività 1 - Abilitazione di una licenza di valutazione per Microsoft Fabric

- Panoramica delle esperienze in Fabric
    
    Attività 2 - Esperienza Data Factory
    
    Attività 3 - Esperienza Data Activator
    
    Attività 4 - Esperienza Synapse Data Engineering
    
    Attività 5 - Esperienza Synapse Data Science
    
    Attività 6 - Esperienza Synapse Data Warehouse
    
    Attività 7 - Esperienza Real-Time Analytics

- Area di lavoro di Fabric
    
    Attività 8 - Creazione di un'area di lavoro di Fabric
    
    Attività 9 - Creazione di un lakehouse

- Riferimenti

# Introduzione 

Oggi si apprenderanno alcune funzionalità chiave di Microsoft Fabric. Questo è un workshop introduttivo che ha lo scopo di presentare le diverse esperienze di uso del prodotto e i vari elementi disponibili in Fabric. Al termine del workshop, si imparerà a usare le funzionalità Lakehouse, Flusso di dati Gen2, Pipeline di dati e DirectLake.

In questo lab si imparerà a:

- Creare un'area di lavoro Fabric
- Creare un lakehouse  

# Licenza di Fabric

## Attività 1 - Abilitazione di una licenza di valutazione per Microsoft Fabric

1. Aprire il **browser** e andare all'indirizzo https://app.powerbi.com/. Si aprirà la pagina di accesso.

**Nota:** se si ha un account Power BI esistente, può essere opportuno usare il browser in modalità privata o in incognito.

2. Immettere l'indirizzo **e-mail** fornito dall'istruttore e fare clic su **Invia**.

    ![](Media/2.2.png)
 
3. Si aprirà la schermata **Password**. Immettere la password condivisa dall'istruttore. 
4. Fare clic su **Accedi** e seguire le istruzioni per accedere a Fabric.

    ![](Media/2.3.png)

 
5. Si aprirà la **home page abituale del servizio Power BI**.
6. 	Si presuppone che si abbia familiarità con il layout del servizio Power BI. Per eventuali domande, rivolgersi all'istruttore.

A questo punto, ci si trova nell'**Area di lavoro personale**. Per lavorare con gli elementi di Fabric, è necessaria una licenza di valutazione e un'area di lavoro che disponga della licenza di Fabric. Procediamo per ottenere quanto necessario.

7. Nell'angolo in alto a destra della schermata selezionare l'**icona utente**.
8. Selezionare **Avvia versione di valutazione**.

    ![](Media/2.4.png)
 
9. Si apre la finestra di dialogo Esegui l'aggiornamento a una versione di valutazione gratuita di Microsoft Fabric. Selezionare **Avvia versione di valutazione**.

    ![](Media/2.5.png)
 

10. Si apre la finestra di dialogo Aggiornamento a una versione di valutazione gratuita di Microsoft Fabric riuscito. Selezionare **Fabric Home Page**.

    ![](Media/2.6.png)
 
11. Si aprirà la **home page** di **Microsoft Fabric**.

    ![](Media/2.7.png)
 

# Panoramica delle esperienze in Fabric

## Attività 2 - Esperienza Data Factory

1. Selezionare l'**icona di Microsoft Fabric** in basso a sinistra nella schermata. Si apre una finestra di dialogo che contiene l'elenco delle esperienze in Fabric. Notare che Power BI, Data Factory e Data Activator sono esperienze indipendenti. Data Engineering, Data Science, Data Warehouse e Real-Time Analytics sono esperienze di Synapse e si basano su Synapse. Procediamo a esaminarle.
2. Selezionare **Data Factory**.

    ![](Media/2.8.png)
 
3. Si apre la **home page** di **Data Factory**. La pagina contiene tre sezioni principali. 

    a. **Nuovo:** elenca gli elementi disponibili in Data Factory, ossia Flusso di dati Gen2 e Pipeline di dati.
    
    i. Flusso di dati Gen2 è la nuova generazione di Flusso di dati.
    
    ii.	Pipeline di dati si usa per l'orchestrazione dei dati.
    
    b. **Consigliato:** questa sezione fornisce accesso alla documentazione di apprendimento per l'avvio rapido.
    
    c. **Accesso rapido:** questa sezione elenca gli elementi preferiti o usati di recente.

    ![](Media/2.9.png)
 
## Attività 3 - Esperienza Data Activator
1. Selezionare **Data Factory** nella parte inferiore sinistra della schermata. Si apre la finestra di dialogo delle esperienze in Fabric.

    ![](Media/2.10.png)
 
2. Selezionare **Data Activator** nella finestra di dialogo. Si apre la **home page di Data Activator**. Data Activator è un'esperienza senza codice in Microsoft Fabric che consente di effettuare automaticamente azioni quando vengono rilevati schemi o condizioni nei dati che cambiano. Notare che le tre sezioni sono analoghe all'esperienza Data Factory. Nella sezione Nuovo osservare i seguenti elementi:

    a. **Reflex:** consente di monitorare set di dati, query e flussi di eventi per individuare schemi.

    b. **Esempio di Reflex:** soluzione di esempio.

    ![](Media/2.11.png)
 

## Attività 4 - Esperienza Synapse Data Engineering

1. Selezionare **Data Activator** nella parte inferiore sinistra della schermata. Si apre la finestra di dialogo delle esperienze in Fabric.
2. Selezionare **Data Engineering**. Si apre la **home page di Data Engineering**. Anche in questo caso, la pagina contiene tre sezioni principali. Nella sezione Nuovo osservare i seguenti elementi: 
    
    a. **Lakehouse:** consente di archiviare Big Data per operazioni di pulizia, query, reporting e condivisione.
    
    b. **Blocco appunti:** consente di eseguire query sui dati per produrre tabelle e oggetti visivi condivisibili.
    
    c. **Definizione processi Spark:** consente di definire, pianificare e gestire i processi Apache.
    
    d. **Pipeline di dati:** consente di orchestrare la soluzione di dati.
    
    e. **Importa blocco appunti:** consente di importare blocco appunti dal computer locale.
    
    f. **Usare un esempio:** consente di creare un esempio.

    ![](Media/2.12.png)
 

## Attività 5 - Esperienza Synapse Data Science
1. Selezionare **Data Engineering** nella parte inferiore sinistra della schermata. Si apre la finestra di dialogo delle esperienze in Fabric.
2. Selezionare **Data Science**. Si apre la home page di Data Science. Anche in questo caso sono presenti tre sezioni. Nella sezione Nuovo osservare i seguenti elementi:

    a. **Modello di Machine Learning:** consente di creare modelli di Machine Learning.
    
    b.	**Esperimento:** consente di creare, eseguire e monitorare lo sviluppo di più modelli.
    
    c.	**Blocco appunti:** consente di esplorare i dati e creare soluzioni di Machine Learning.
    
    d.	**Importa blocchi appunti:** consente di importare blocchi appunti dal computer locale.
    
    e.	**Esempio:** soluzione di esempio.

    ![](Media/2.13.png)
 

## Attività 6 - Esperienza Synapse Data Warehouse
1. Selezionare **Data Science** nella parte inferiore sinistra della schermata. Si apre la finestra di dialogo delle esperienze in Fabric.
2. Selezionare **Data Warehouse**. Si apre la **home page di Data Warehouse**. Anche in questo caso sono presenti tre sezioni. Nella sezione Nuovo osservare osservare gli elementi. Notare che Pipeline di dati e Flusso di dati Gen2 sono disponibili anche qui.

    a.	**Warehouse:** consente di fornire approfondimenti strategici da più fonti.
    
    b.	**Warehouse di esempio:** soluzione di warehouse di esempio.
    
    c.	**Pipeline di dati:** consente di orchestrare la soluzione di dati.

    ![](Media/2.14.png)

 

## Attività 7 - Esperienza Real-Time Analytics
1. Selezionare **Data Warehouse** nella parte inferiore sinistra della schermata. Si apre la finestra di dialogo delle esperienze in Fabric.
2. Selezionare **Real-Time Analytics**. Si apre la home page di Real-Time Analytics. Anche in questo caso sono presenti tre sezioni. Nella sezione Nuovo osservare i seguenti elementi: 
    
    a.	**Database KQL:** consente di caricare rapidamente dati strutturati, non strutturati e in streaming per l'esecuzione di query.
    
    b.	**Set di query KQL:** consente di eseguire query sui dati per produrre tabelle e oggetti visivi condivisibili.
    
    c.	**Eventstream:** consente di acquisire, trasformare e instradare il flusso di eventi in tempo reale.
    
    d.	**Usare un esempio:** consente di creare un esempio.

    ![](Media/2.15.png)
 

# Area di lavoro di Fabric

## Attività 8 - Creazione di un'area di lavoro di Fabric
1. Ora creeremo un'area di lavoro con la licenza di Fabric. Selezionare **Aree di lavoro** nella barra di spostamento a sinistra. Si apre una finestra di dialogo.
2. Selezionare **Nuova area di lavoro**.

    ![](Media/2.16.png)
 
3.	Si apre la finestra di dialogo **Crea un'area di lavoro** sul lato destro del browser.
4. Nel campo **Nome** immettere **FAIAD_<nomeutente>**

**Nota:** il nome dell'area di lavoro deve essere univoco. In questo documento useremo FAIAD come nome dell'area di lavoro. Tuttavia, il nome dell'area di lavoro usato deve essere diverso. Assicurarsi che sotto il campo Nome sia presente un segno di spunta verde e che sia indicato "**Questo nome è disponibile**".

5. Se lo si desidera, è possibile immettere una **Descrizione** per l'area di lavoro. Questo campo è facoltativo.
6. Fare clic su **Avanzate** per espandere la sezione.

    ![](Media/2.17.png)
 
7. In **Modalità licenza** assicurarsi che si sia selezionato **Versione di prova** (deve essere selezionato per impostazione predefinita).
8. Selezionare **Applica** per creare una nuova area di lavoro.

    ![](Media/2.18.png)
 
Viene creata una nuova area di lavoro e si passa a tale area di lavoro. Importeremo dati da diverse origini dati in Lakehouse e li useremo da Lakehouse per creare il modello e il report relativi. Il primo passaggio consiste nel creare un lakehouse.

## Attività 9 - Creazione di un lakehouse
1. Selezionare **Real-Time Analytics** nella parte inferiore sinistra della schermata. Si apre la finestra di dialogo delle esperienze in Fabric.

2. Selezionare **Data Engineering** per andare alla home page di Data Engineering.

    ![](Media/2.19.png)
 
3. Selezionare **Lakehouse**.
  
    ![](Media/2.20.png)

4. Si apre la finestra di dialogo Nuovo lakehouse. Digitare **lh_FAIAD** nella casella di testo Nome.

**Nota:** lh indica Lakehouse. Aggiungiamo il prefisso lh per agevolarne l'identificazione e la ricerca.

5. Selezionare **Crea**.

    ![](Media/2.21.png)
 
Dopo qualche istante viene creato un lakehouse e si passerà all'interfaccia di Lakehouse.
Nel **pannello sinistro** notare che sotto all'area di lavoro è ancora presente l'icona di Lakehouse. È possibile passare agevolmente a Lakehouse facendo clic su questa icona in qualsiasi momento.

Nell'interfaccia di esplorazione di Lakehouse si noteranno **Tabelle** e **File**. Lakehouse può esporre file di Azure Data Lake Storage Gen2 nella sezione file oppure un flusso di dati può caricare dati nelle tabelle di Lakehouse. Sono disponibili varie opzioni. Mostreremo alcune di queste opzioni nei lab seguenti.

![](Media/2.22.png)
 
In questo lab abbiamo esplorato l'interfaccia di Fabric, creato uno spazio di lavoro di Fabric e un lakehouse. Nel prossimo lab si imparerà a usare Flusso di dati Gen2 per connettersi ad ADLS Gen2 per estrarre, trasformare e inserire dati nel lakehouse.

# Riferimenti
Fabric Analyst in a Day (FAIAD) presenta alcune delle funzionalità chiave disponibili in Microsoft Fabric. Nel menu di servizio, la sezione Guida (?) include collegamenti ad alcune risorse utili.

![](Media/2.23.png)
 

Di seguito sono riportate ulteriori risorse utili che consentiranno di progredire nell'uso di Microsoft Fabric.

- Vedere il post di blog per leggere l'[annuncio completo sulla disponibilità generale di Microsoft Fabric](https://aka.ms/Fabric-Hero-Blog-Ignite23)
- Esplorare Fabric attraverso la [Presentazione guidata](https://aka.ms/Fabric-GuidedTour)
- Iscriversi alla [versione di valutazione gratuita di Microsoft Fabric](https://aka.ms/try-fabric)
- Visitare il [sito Web di Microsoft Fabric](https://aka.ms/microsoft-fabric)
- Acquisire nuove competenze esplorando i [moduli di apprendimento su Fabric](https://aka.ms/learn-fabric)
- Consultare la [documentazione tecnica di Fabric](https://aka.ms/fabric-docs)
- Leggere l'[e-book gratuito introduttivo a Fabric](https://aka.ms/fabric-get-started-ebook)
- Unirsi alla [community di Fabric](https://aka.ms/fabric-community) per pubblicare domande, condividere feedback e imparare dagli altri

Leggere i blog di annunci più approfonditi sull'esperienza in Fabric:

- [Blog sull'esperienza Data Factory in Fabric](https://aka.ms/Fabric-Data-Factory-Blog) 
- [Blog sull'esperienza Synapse Data Engineering in Fabric ](https://aka.ms/Fabric-DE-Blog)
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