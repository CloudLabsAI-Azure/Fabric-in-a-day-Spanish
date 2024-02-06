
![](Media/0.1.png)

# Sommario
- Introduzione
- Credenziali lab
- Importazione del modello di flusso di dati
    - Importazione del modello di flusso di dati
- Requisiti demo
- Ambiente
    - Configurazione dell'ambiente lab
    - Creazione di un notebook per la previsione


# Introduzione 
Questo documento fornisce linee guida per le seguenti funzionalità:

- Credenziali lab
- Importazione del modello di flusso di dati
- Caricamento delle librerie Spark e configurare un ambiente
- Creazione di un notebook
- Uso il modello di data science per creare previsioni
- Salvataggio dell'output nel modello semantico

**Dichiarazione di non responsabilità:** tenere presente che alcuni screenshot potrebbero non essere aggiornati poiché il prodotto cambia ogni giorno. Lavoreremo per adeguarli nel prossimo aggiornamento.

# Credenziali lab
Se qualsiasi partecipante sceglie di completare i lab in un ambiente alternativo, potrebbe essere necessario condividere le seguenti credenziali.

I partecipanti avranno bisogno del nome utente e della password associati al proprio account Lab per connettersi a Dataverse e SharePoint

Nome utente Snowflake: **TE_SNOWFLAKE**

Password Snowflake: **8UpfRpExVDXv2AC**

Chiave dell'account ADLS Gen2: **Lpwn8hQASMpe5r4F+VFXAvpnzKF9x9Kjt5GMvMCFWB0xCFuM4fyVwOW6rF200bTop3LpKpsIno/T+AStx6cz6w==**
 
# Importazione del modello di flusso di dati
L'istruttore può scegliere di consentire ai partecipanti di impostare modelli di flusso di dati. Di seguito è riportata la procedura per importare un modello.

## Importazione del modello di flusso di dati
1. Andare all'**area di lavoro Fabric creata nel lab 2, attività 8 e denominata FAIAD_ <nomeutente>**. Alla nostra area di lavoro abbiamo assegnato il nome FAIAD_demouser
2. Andare alla **home page di Data Factory**.
3. Nel menu selezionare **Nuovo -> Flusso di dati Gen2**
 
4. Si apre la finestra Power Query. Nel riquadro centrale selezionare **Importa da un modello di Power Query**.
 
5. Andare alla cartella **Desktop -> Soluzioni** e selezionare il flusso di dati che si desidera importare. In questo caso stiamo importando **df_People_SharePoint.pqt**
6. Selezionare **Apri**.

Dopo l'importazione, verificare che la query e tutti i passaggi della query siano stati importati. È tuttavia ancora necessario configurare la connessione. Inoltre, è necessario impostare la destinazione dei dati. Attenersi alle istruzioni del lab per completare questi passaggi.
 

# Requisiti demo
All'istruttore è richiesto di completare i lab 1-6 e di immettere tutti i dati prima di procedere con i passaggi successivi.

# Ambiente
## Configurazione dell'ambiente lab
**Nota:** è consigliabile configurare l'ambiente lab prima della demo, poiché l'installazione della libreria richiede tempo. È possibile guidare i partecipanti in questi passaggi.

7. Andare all'**area di lavoro Fabric creata nel lab 2, attività 8 e denominata FAIAD_ <nomeutente>**
8. Nel menu in alto selezionare i **puntini di sospensione (…)**
9. Selezionare **Impostazioni area di lavoro**.
 
10. Si apre la finestra di dialogo Impostazioni area di lavoro. Nel menu a sinistra espandere **Ingegneria/Scienza dei dati**.
11. Selezionare **Impostazioni Spark**.
12. Nel menu Impostazioni Spark selezionare la scheda **Ambiente**.
13. Spostare il dispositivo di scorrimento **Impostazione dell'ambiente predefinito** su **Attivato**.
14. Selezionare il menu a discesa **Impostazione predefinita area di lavoro**.
15. Selezionare **Nuovo ambiente**.
 
16. Si apre la finestra di dialogo Nuovo ambiente. Immettere il nome **FAIAD_<nomeutente>_env**

**Nota:** il nome dell'area di lavoro deve essere univoco. In questo documento useremo FAIAD_demouser_env come nome dell'area di lavoro. Tuttavia, il nome dell'area di lavoro usato deve essere diverso. Assicurarsi che sotto il campo Nome sia presente un segno di spunta verde e che sia indicato "**Questo nome è disponibile**".

17. Selezionare **Crea**.
 
18. Si accederà a una schermata per aggiungere le librerie pubbliche e personalizzate. Vogliamo aggiungere prophet che è una libreria pubblica. Nel menu in alto selezionare **Librerie pubbliche -> Aggiungi da PyPI**
19. Nel riquadro centrale, nella casella di testo sotto Libreria, immettere **prophet**

**Nota:** assicurarsi che la **versione sia 1.1.5**

20. Nel riquadro in alto a destra selezionare **Pubblica**. 
 
21. Si apre la finestra di dialogo Modifiche in sospeso. Selezionare **Pubblica tutto**.
22. Si apre la finestra di dialogo Pubblicare tutte le modifiche?. Selezionate **Pubblica**. La pubblicazione dell'aggiornamento richiederà alcuni minuti.
 
23. Selezionare **Visualizza avanzamento** per verificare l'avanzamento. La pubblicazione dell'aggiornamento richiederà alcuni minuti.
 
24. Dopo l'installazione, verificare che lo **Stato** cambi in **Operazione riuscita**.
 
25.	Dopo aver configurato l'ambiente, dobbiamo salvarlo come ambiente predefinito per l'area di lavoro. Nel pannello a sinistra selezionare **FAIAD_<nomeutente>**.
26. Nel menu in alto selezionare **Impostazioni area di lavoro** (o puntini di sospensione -> Impostazioni area di lavoro).
 
27. Si apre la finestra di dialogo Impostazioni area di lavoro. Nel menu a sinistra espandere **Ingegneria/Scienza dei dati**.
28. Selezionare **Impostazioni Spark**.
29. Nel menu Impostazioni Spark selezionare la scheda **Ambiente**.
30. Spostare il dispositivo di scorrimento **Impostazione dell'ambiente predefinito** su **Attivato**.
31. Selezionare il menu a discesa **Impostazione predefinita area di lavoro**.
32. Selezionare l'ambiente appena creato dal menu a discesa: **FAIAD_<nomeutente>_env**
33. Selezionare **Salva**.
 

## Creazione di un notebook per la previsione
34. Andare alla pagina **Home** di **Synapse Data Engineering**.
35. Selezionare **Nuovo -> Blocco appunti**.
 
36. Fornire una **breve panoramica** del layout: notebook, lingua, ambiente, come creare una nuova cella e così via.
37. Creare una **nuova cella**.
38. Immettere il **codice** seguente:

        from pyspark.sql import SparkSession
        from pyspark.sql.functions import month, year, col
        from prophet import Prophet
        import pandas as pd

        # Initialize Spark session
        spark = SparkSession.builder.appName("Prophet Forecasting").getOrCreate()

        # Load data from your specific Spark table
        df = spark.sql("SELECT * FROM lh_FAIAD.Sales")

        # Aggregate data to monthly level
        monthly_df = df.withColumn("Month", month("InvoiceDate"))\
                    .withColumn("Year", year("InvoiceDate"))\
                    .groupBy("Year", "Month")\
                    .sum("Quantity")\
                    .orderBy("Year", "Month")

        # Convert to Pandas DataFrame and prepare for Prophet
        pandas_df = monthly_df.toPandas()
        pandas_df['ds'] = pd.to_datetime(pandas_df[['Year', 'Month']].assign(DAY=1))
        pandas_df['y'] = pandas_df['sum(Quantity)']

        # Fit the Prophet model
        model = Prophet(yearly_seasonality=True, weekly_seasonality=False,daily_seasonality=False)
        model.fit(pandas_df[['ds, 'y']])

        # Create a DataFrame for future predictions (e.g., next 12 months)
        future = model.make_future_dataframe(periods=12, freq='M')

        # Forecast
        forecast = model.predict(future)

        # Plotting the forecast
        model.plot(forecast)
        model.plot_components(forecast)

39. Spiegare ogni passaggio del **codice** (sono fornite righe di commenti).
40. Eseguire il codice selezionando il pulsante **Riproduci** accanto alla cella.
 
Illustrare ai partecipanti i tre grafici creati (vedere di seguito). Abbiamo dati effettivi fino ad aprile 2023 e previsioni per 12 mesi.

Notare che il **primo grafico** rimuove la stagionalità e le previsioni fino ad aprile 2024.

Il **secondo grafico** rimuove la tendenza e aggiunge la stagionalità alle previsioni fino ad aprile 2024.
 
Il **terzo grafico** effettua una previsione usando sia la tendenza che la stagionalità. Questo grafico fornisce anche il limite superiore e inferiore.
 
41. Creare una **nuova cella**. 
42. Aggiungere il **codice** seguente alla cella:

        display(forecast)
        #write forecast data to a table
        spark.createDataFrame(forecast).write.saveAsTable("Sales_Forecast", mode="overwrite")

43. Eseguire la cella selezionando il pulsante **Riproduci**.
 
44. Illustrare ai partecipanti i **dati visualizzati**.
45. Mostrare agli utenti che è stata creata una nuova tabella: **sales_forecast**
 
46. Effettuare una **query** sulla tabella e mostrare agli utenti il contenuto della tabella.
