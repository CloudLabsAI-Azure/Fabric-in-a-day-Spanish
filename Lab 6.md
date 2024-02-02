# ​​Contenido 

## Presentación  

## Lakehouse 

- Tarea 1: Consultar datos con SQL 
- Tarea 2: visualizar el resultado de T-SQL 
- Tarea 3: Crear consulta de objetos visuales 
- Tarea 4: Visualizar los resultados de la consulta 
- Tarea 5: Crear relaciones 
- Tarea 6: Crear medidas 
- Tarea 7: Sección opcional: crear relaciones 
- Tarea 8: Sección opcional: crear medidas 

## Referencias 

## Presentación  

Tenemos datos de diferentes orígenes ingeridos en el lakehouse. En esta práctica de laboratorio, trabajará con el modelo de datos. Normalmente, hacemos actividades de modelado como crear relaciones, agregar medidas, etc. en Power BI Desktop. Aquí aprenderemos cómo hacer estas actividades de modelado en el servicio.  

Al final de este laboratorio, habrá aprendido:  
  - Cómo explorar un lakehouse 
  - Cómo explorar la vista de SQL del lakehouse 
  - Cómo explorar el modelado de datos en el lakehouse

## Lakehouse 

### Tarea 1: Consultar datos con SQL 

1. Volvamos al área de trabajo de Fabric, **FAIAD_<username>**, que creó en el Laboratorio 2, Tarea 8. 

2. Vuelva a la **pantalla de Data Factory**. 

3. Verá tres tipos de lh_FAIAD: modelo semántico, punto de conexión SQL y lakehouse. Exploramos la opción lakehouse en un laboratorio anterior. Seleccione la opción **Punto de conexión de análisis SQL lh_FAIAD** para explorar la opción SQL. Esto le llevará a la **vista de SQL** del explorador.

Si desea explorar los datos antes de crear un modelo de datos, puede utilizar SQL para hacerlo. Veamos dos opciones para usar SQL, la primera está orientada a desarrolladores y la segunda opción es para analistas. 
Supongamos que desea conocer rápidamente las unidades vendidas por el proveedor mediante SQL. Tenemos dos opciones: escribir una declaración SQL o usar un objeto visual para crear la declaración SQL. 

Observe que en el panel izquierdo puede ver las Tablas. Si expande las tablas, puede ver las columnas que componen la tabla. Además, hay opciones para crear vistas, funciones y procedimientos almacenados de SQL. Si tiene experiencia en SQL, no dude en explorar estas opciones. Intentemos escribir una consulta SQL simple. 

4. Desde el **menú superior**, seleccione **Nueva consulta SQL** o desde **la parte inferior izquierda panel**, seleccione **Consulta**. Esto le llevará a la vista de consultas de SQL.

5. Copie la **siguiente consulta de SQL** en la **ventana de consultas**. Esta consulta devolverá las unidades por nombre del proveedor. Para conseguirlo, se une la tabla Sales con las tablas Product y Supplier. 
 
      - SELECT su.Supplier_Name, SUM(Quantity) as Units 
      - FROM dbo.Sales s 
      - JOIN dbo.Product p on p.StockItemID = s.StockItemID 
      - JOIN dbo.Supplier su on su.SupplierID = p.SupplierID 
      - GROUP BY su.Supplier_Name 

6. Haga clic en **Run** para ver los resultados.

7. Observe que hay una opción para guardar esta consulta como Vista si selecciona **Guardar como vista**.

8. En el panel del **explorador izquierdo**, en la sección **Queries**, observe que esta consulta se guarda en **Mis consultas** como **SQL query 1**. Esto proporciona una opción para cambiar el nombre de la consulta y guardarla para uso futuro. También hay una opción para ver las consultas que se comparten con usted mediante la carpeta **Consultas compartidas**.

### Tarea 2: visualizar el resultado de T-SQL 

1. También podemos visualizar el resultado de esta consulta. **Resalte la consulta** en el panel de consulta y seleccione **el panel Resultados**; luego seleccione **Visualización de resultados**.

2. Se abre el cuadro de diálogo Visualización de resultados. Seleccione **Continuar**.

3. Se abre el conocido cuadro de diálogo de vista de informe. Desde el panel **Datos**, expanda **SQL query 1**.

4. Seleccione los **campos Supplier_Name y Units**. El objeto visual de tabla se crea de forma predeterminada. 

5. En la sección **Visualizaciones**, cambie el tipo de objeto visual mediante la selección del **gráfico de Columna apilada**. 

6. **Cambie el tamaño** del objeto visual según sea necesario.  
 
     >**Nota:** Observe que todas las opciones disponibles para dar formato a un objeto visual en el informe de Power BI también están disponibles aquí. 
 
7. Seleccione **Guardar como informe** en la esquina inferior derecha. 

8. Se abre el cuadro de diálogo Guardar el informe. Escriba **Units by Supplier** en el cuadro de texto **Especifique un nombre para el informe**. 

9. Asegúrese de que el área de trabajo de destino es su área de trabajo de Fabric **FAIAD<username>**. 

10. Seleccione **Guardar**. 

### Tarea 3: Crear consulta de objetos visuales 

Se le dirigirá de vuelta a la vista del punto de conexión de análisis de SQL. Si no está familiarizado con SQL, puede ejecutar una consulta similar mediante consulta de objeto visual. 

1. En el menú superior, seleccione **Nueva consulta de objeto visual**. Se abre un panel de consulta de objeto visual. 

2. Desde el panel **Explorador**, arrastre las tablas **Sales, Product y Supplier** al panel de consulta de objeto visual. 

3. Con la tabla **Sales** seleccionada, en el menú del panel Consulta de objeto visual, seleccione **Combinar -> Combinar consultas**.

4. Se abrirá el cuadro de diálogo Combinar. Desde el **menú desplegable Tabla derecha para combinación**, seleccione **Product**. 

5. Seleccione **StockItemID** de las tablas **Sales y Product**. Esto se hace para combinar las tablas Sales y Product. 

6. En **Tipo de combinación**, seleccione **Externa**. 

7. Seleccione **Aceptar**.

8. En el panel **resultados**, haga clic en la **doble flecha** al lado de la columna **Product**. 

9. Seleccione **SupplierID** en el cuadro de diálogo que se abre. 

10. Seleccione **Aceptar**. Observe que los pasos **Consultas combinadas y Producto expandido** se crean en la tabla **Sales**.

11. De manera similar, combinemos la tabla Supplier. Dentro de la tabla **Sales**, seleccione **"+"** (ubicado después del Producto expandido) para agregar un nuevo paso. Se abre un cuadro de diálogo. 

12. Seleccione **Combinar -> Combinar consultas**.

13. Se abrirá el cuadro de diálogo Combinar. Desde el **menú desplegable Tabla derecha para combinación**, seleccione **Supplier**. 

14. Seleccione **SupplierID** de las tablas **Sales y Supplier**. Esto se hace para combinar las tablas Supplier y Sales. 

15. En **Tipo de combinación**, seleccione **Externa**. 

16. Seleccione **Aceptar**.

17. En el panel **resultados**, haga clic en la **doble flecha** al lado de la columna **Supplier**. 

18. Seleccione **Supplier_Name** en el cuadro de diálogo que se abre. 

19. Seleccione **Aceptar**. Observe que en la tabla Sales, se agregan C**onsultas combinadas** y se registran todos los **pasos**. 
 
>**Nota:** Consulte la primera captura de pantalla en la Tarea 4.

### Tarea 4: Visualizar los resultados de la consulta 

1. Ahora que tenemos la consulta lista, veamos el resultado. Seleccione **Visualización de resultados** en el panel de resultados.

2. Se abre el cuadro de diálogo Visualización de resultados. En el panel **Datos** de la derecha, seleccione los campos **Supplier_Name y Quantity**. 

3. Seleccione el **objeto visual de tabla** en el panel Objeto visual para ver los resultados como una tabla. Observe que el resultado es similar al resultado de la consulta SQL anterior. Si lo desea, puede guardar este informe. Como guardamos un informe similar anteriormente, seleccionaremos **Cancelar**.

### Tarea 5: Crear relaciones 

Bien, ahora estamos listos para crear el modelo, establecer relaciones entre tablas y crear medidas. 

1. En la parte **inferior del panel de la izquierda**, seleccione **Modelo**. Verá que el panel central se parece a la vista Modelo que vemos en Power BI Desktop. 

2. **Cambie el tamaño y mueva** las tablas según sea necesario. 

3. Creemos una relación entre las tablas Sales and Reseller. Seleccione **ResellerID** de la tabla **Sales** y arrástrelo a **ResellerID** en la tabla **Reseller**.

4. Se abre el cuadro de diálogo Nueva relación. Asegúrese de que la **Table 1** sea Sales y que la **Columna** sea **ResellerID**. 

5. Asegúrese de que la **Table 2** sea **Reseller** y que la **Columna** sea **ResellerID**. 

6. Asegúrese de que la **Cardinality** sea **Varios a uno** (*:1). 

7. Asegúrese de que la **Dirección de filtro cruzado** sea **Único**. 

8. Seleccione **OK**.

9. De forma similar, creemos una relación entre las tablas Sales y Date. Seleccione **InvoiceDate** de la tabla **Sales** y arrástrelo a Date en la tabla **Date**. 

10. Se abre el cuadro de diálogo Nueva relación. Asegúrese de que la **Table 1** sea **Sales** y que la **Columna** sea **InvoiceDate**. 

11. Asegúrese de que la **Table 2** sea Date y que la **Columna** sea **Date**. 

12. Asegúrese de que la **Cardinality** sea **Varios a uno (*:1)**. 

13. Asegúrese de que la **Dirección de filtro cruzado sea Único**. 

14. Seleccione **Ok**. 

**Punto de control:** su modelo debe tener dos relaciones entre las tablas Sales y Reseller y las tablas Sales y Date como se muestra en la siguiente captura de pantalla: 

Por razones de tiempo, no crearemos todas las relaciones. Si el tiempo lo permite, puede completar la sección opcional al final de la práctica de laboratorio. La sección opcional recorre los pasos para crear las relaciones restantes. 

### Tarea 6: Crear medidas 

Agreguemos algunas medidas que necesitamos para crear el panel de Sales. 

1. Seleccione la **tabla Sales** desde la vista del modelo. Queremos agregar las medidas a la tabla Sales. 

2. En el menú superior, seleccione **Inicio -> Nueva medida**. Observe que se muestra la barra de fórmulas. 

3. Introduzca **Sales = SUM(Sales[Sales_Amount])** en la **barra de fórmulas**. 

4. Haga clic en la **marca de verificación** izquierda de la barra de fórmulas o haga clic en el botón **Enter**. 

5. En el panel Propiedades de la derecha, expanda la sección **Formato**. 

6. En el menú desplegable Formato, seleccione **Moneda**. 

7. Establezca **Posiciones decimales** en **0**.

8. Con la **tabla Sales** seleccionada en el menú superior, seleccione **Inicio -> Nueva medida**. Observe que se muestra la barra de fórmulas. 

9. Introduzca **Units = SUM(Sales[Quantity])** en la **barra de fórmulas**. 

10. Haga clic en la **marca de verificación** izquierda de la barra de fórmulas o haga clic en el botón **Enter**. 

11. En el panel Propiedades a la derecha, expanda la sección **Formato** (el panel Propiedades puede tardar unos momentos en cargarse). 

12. En el menú desplegable **Formato**, seleccione **Número entero**. 

13. Establezca el **Separador de miles** en **Sí**.

14. Con la **tabla Sales** seleccionada en el menú superior, seleccione **Inicio -> Nueva medida**. Observe que se muestra la barra de fórmulas. 

15. Introduzca **Orders = DISTINCTCOUNT(Sales[InvoiceID])** en la **barra de fórmulas**. 

16. Haga clic en la marca de verificación izquierda de la barra de fórmulas o haga clic en el botón **Enter**. 

17. En el panel Propiedades de la derecha, expanda la sección **Formato**. 

18. En el menú desplegable Formato, seleccione **Número entero**. 

19. Establezca el **Separador de miles** en **Sí**.

De nuevo, por razones de tiempo, no crearemos todas las medidas. Si el tiempo lo permite, puede completar la sección opcional al final de la práctica de laboratorio. La sección opcional recorre los pasos para crear las medidas restantes. 
Hemos creado un modelo de datos, el siguiente paso es crear un informe. Lo haremos en el siguiente laboratorio. 

### Tarea 7: Sección opcional: crear relaciones 

Agreguemos las relaciones restantes. 

1. Cree una relación **varios a uno** entre las tablas **Sales** y **Product**. Seleccione **StockItemID** en la tabla **Sales** y **StockItemID** en la tabla **Product**. 

2. Igualmente, cree una relación **varios a uno** entre las tablas **Sales** y **People**. Seleccione **SalespersonPersonID** de **Sales** y **PersonID** de **People**. 

     **>Punto de control:** su modelo debe parecerse al de la siguiente captura de pantalla.

3. Ahora creemos una relación entre las tablas Product y Supplier. Seleccione **SupplierID** de la tabla **Product** y arrástrelo a **SupplierID** en la tabla **Supplier**. 

4. Se abre el cuadro de diálogo Nueva relación. Asegúrese de que la **Table 1** sea Product y que la **Columna** sea **SupplierID**. 

5. Asegúrese de que la **Table 2** sea **Supplier** y que la **Columna** sea **SupplierID**. 

6. Asegúrese de que la **Cardinality** sea **Varios a uno** (*:1). 

7. Asegúrese de que la **Dirección de filtro cruzado** sea **Ambas**. 

8. Seleccione **OK**.

9. De manera similar, cree una relación **varios a uno** con **Dirección de filtro cruzado** como **Ambas** entre **Product_Details** y **Product**. Seleccione **StockItemID** de **Product_Details** y **StockItemID** de **Product**. 

10. Ahora creemos una relación entre las tablas Reseller y Geo. Seleccione **PostalCityID** de la tabla **Reseller** y arrástrela sobre **CityID** en la tabla **Geo**. 

11. Se abre el cuadro de diálogo Nueva relación. Asegúrese de que la **Table 1** sea **Reseller** y que la **Columna** sea **PostalCityID**. 

12. Asegúrese de que la **Table 2** sea **Geo** y que la **Columna** sea **CityID**. 

13. Asegúrese de que la **Cardinality** sea **Varios a uno (*:1)**. 

14. Asegúrese de que la **Dirección de filtro cruzado** sea **Ambas**. 

15. Seleccione **OK**.

16. Ahora creemos una relación entre las tablas Customer y Reseller. Seleccione **ResellerID** de la tabla **Customer** y arrástrelo a **ResellerID** en la tabla **Reseller**. 

17. Se abre el cuadro de diálogo Nueva relación. Asegúrese de que la **Table 1** sea Customer y que la **Columna** sea **ResellerID**. 

18. Asegúrese de que la **Table 2** sea **Reseller** y que la Columna sea **ResellerID**. 

19. Asegúrese de que la **Cardinality** sea **Varios a uno (*:1)**. 

20. Asegúrese de que la **Dirección de filtro cruzado sea Único**. 

21. Seleccione **OK**.

      >**Punto de control:** su modelo debe parecerse al de la siguiente captura de pantalla.

22. Ahora creemos una relación entre las tablas PO y Date. Seleccione **Order_Date** de la tabla PO y arrástrela sobre **Date** en la tabla **Date**. 

23. Se abre el cuadro de diálogo Nueva relación. Asegúrese de que la **Table 1** sea **PO** y que la **Columna** sea **Order_Date**. 

24. Asegúrese de que la **Table 2** sea **Date** y que la **Columna** sea **Date**. 

25. Asegúrese de que la **Cardinality** sea **Varios a uno (*:1)**. 

26. Asegúrese de que la **Dirección de filtro cruzado** sea **Único**. 

27. Seleccione **OK**.

28. Igualmente, cree una relación varios a uno entre las tablas **PO** y **Product**. Seleccione **StockItemID** de **PO** y **StockItemID** de **Product**. 

29. Igualmente, cree una relación **varios a uno** entre las tablas **PO** y **People**. Seleccione **ContactPersonID** de **PO** y **PersonID** de **People**.  
Hemos terminado de crear todas las relaciones.  

>**Punto de control:** su modelo debe parecerse al de la siguiente captura de pantalla.

### Tarea 8: Sección opcional: crear medidas 

Agreguemos las medidas restantes. 

1. Introduzca **Avg Order = DIVIDE([Sales], [Orders])** en la barra de fórmulas. 

2. Haga clic en la **marca de verificación** en la barra de fórmulas o haga clic en el botón Enter. 

3. Una vez guardada la medida, observe la opción Herramientas de medición en el menú superior. Haga clic en **Herramientas de medición**. 

4. En el menú desplegable Formato, haga clic en **Moneda**.

5. Siga pasos similares para agregar las siguientes medidas: 

      - **GM = SUM(Sales[Line_Profit])** con formato **Moneda, posición decimal 2** 

      - **GM% = DIVIDE([GM], [Sales])** con formato **Porcentaje, posición decimal 2** 

      - **No of Customers** = **COUNTROWS(Customer)** con formato **Número entero** 

## Referencias 

Fabric Analyst in a Day (FAIAD) le presenta algunas funciones clave disponibles en Microsoft Fabric. En el menú del servicio, la sección Ayuda (?) tiene vínculos a algunos recursos excelentes. 

Estos son algunos recursos más que podrán ayudarle a seguir avanzando con Microsoft Fabric. 

- Vea la publicación del blog para leer el [anuncio de disponibilidad general de Microsoft Fabric](https://www.microsoft.com/en-us/microsoft-fabric/blog/2023/11/15/prepare-your-data-for-ai-innovation-with-microsoft-fabric-now-generally-available/) completo. 

- Explore Fabric a través de la [Visita guiada](https://guidedtour.microsoft.com/en-us/guidedtour/microsoft-fabric/microsoft-fabric/1/1) 

- Regístrese en la [prueba gratuita de Microsoft Fabric](https://app.powerbi.com/home?experience=power-bi)

- Visite el [sitio web de Microsoft Fabric](https://www.microsoft.com/en-in/microsoft-fabric)

- Adquiera nuevas capacidades mediante la exploración de los [módulos de aprendizaje de Fabric](https://learn.microsoft.com/en-us/training/browse/?products=fabric&resource_type=module) 

- Explore la [documentación técnica de Fabric](https://learn.microsoft.com/en-us/fabric/) 

- Lea el [libro electrónico gratuito sobre cómo empezar a usar Fabric](https://info.microsoft.com/ww-landing-unlocking-transformative-data-value-with-microsoft-fabric.html)

- Únase a la [comunidad de Fabric](https://community.fabric.microsoft.com/) para publicar sus preguntas, compartir sus comentarios y aprender de otros.

Obtenga más información en los blogs de anuncios de la experiencia Fabric: 

- [Experiencia de Data Factory en el blog de Fabric](https://blog.fabric.microsoft.com/en-us/blog/introducing-data-factory-in-microsoft-fabric/) 

- [Experiencia de Synapse Data Engineering en el blog de Fabric](https://blog.fabric.microsoft.com/en-us/blog/introducing-synapse-data-engineering-in-microsoft-fabric/)  

- [Experiencia de Synapse Data Science en el blog de Fabric](https://blog.fabric.microsoft.com/en-us/blog/introducing-synapse-data-science-in-microsoft-fabric/) 

- [Experiencia de Synapse Data Warehousing en el blog de Fabric](https://blog.fabric.microsoft.com/en-us/blog/introducing-synapse-data-warehouse-in-microsoft-fabric/)  

- [Experiencia de Synapse Real-Time Analytics en el blog de Fabric](https://blog.fabric.microsoft.com/en-us/blog/sense-analyze-and-generate-insights-with-synapse-real-time-analytics-in-microsoft-fabric/)

- [Blog de anuncios de Power BI](https://powerbi.microsoft.com/en-us/blog/empower-power-bi-users-with-microsoft-fabric-and-copilot/)

- [Experiencia de Data Activator en el blog de Fabric](https://blog.fabric.microsoft.com/en-us/blog/driving-actions-from-your-data-with-data-activator/)  

- [Administración y gobernanza en el blog de Fabric](https://blog.fabric.microsoft.com/en-us/blog/administration-security-and-governance-in-microsoft-fabric/) 

- [OneLake en el blog de Fabric](https://blog.fabric.microsoft.com/en-us/blog/microsoft-onelake-in-fabric-the-onedrive-for-data/) 

- [Blog de integración de Dataverse y Microsoft Fabric](https://cloudblogs.microsoft.com/dynamics365/it/2023/05/24/new-dataverse-enhancements-and-ai-powered-productivity-with-microsoft-365-copilot/) 

© 2023 Microsoft Corporation. Todos los derechos reservados. 

Al participar en esta demostración o laboratorio práctico, acepta las siguientes condiciones: 

Microsoft Corporation pone a su disposición la tecnología o funcionalidad descrita en esta demostración/laboratorio práctico con el fin de obtener comentarios por su parte y de facilitarle una experiencia de aprendizaje. Esta demostración/laboratorio práctico solo se puede usar para evaluar las características de tal tecnología o funcionalidad y para proporcionar comentarios a Microsoft. No se puede usar para ningún otro propósito. Ninguna parte de esta demostración/laboratorio práctico se puede modificar, copiar, distribuir, transmitir, mostrar, realizar, reproducir, publicar, licenciar, transferir ni vender, ni tampoco crear trabajos derivados de ella. 

LA COPIA O REPRODUCCIÓN DE ESTA DEMOSTRACIÓN/LABORATORIO PRÁCTICO (O PARTE DE ELLA) EN CUALQUIER OTRO SERVIDOR O UBICACIÓN PARA SU REPRODUCCIÓN O DISTRIBUCIÓN POSTERIOR QUEDA EXPRESAMENTE PROHIBIDA. 

ESTA DEMOSTRACIÓN/LABORATORIO PRÁCTICO PROPORCIONA CIERTAS FUNCIONES Y CARACTERÍSTICAS DE PRODUCTOS O TECNOLOGÍAS DE SOFTWARE (INCLUIDOS POSIBLES NUEVOS CONCEPTOS Y CARACTERÍSTICAS) EN UN ENTORNO SIMULADO SIN INSTALACIÓN O CONFIGURACIÓN COMPLEJA PARA EL PROPÓSITO ARRIBA DESCRITO. LA TECNOLOGÍA/CONCEPTOS DESCRITOS EN ESTA DEMOSTRACIÓN/LABORATORIO PRÁCTICO NO REPRESENTAN LA FUNCIONALIDAD COMPLETA DE LAS CARACTERÍSTICAS Y, EN ESTE SENTIDO, ES POSIBLE QUE NO FUNCIONEN DEL MODO EN QUE LO HARÁN EN UNA VERSIÓN FINAL. ASIMISMO, PUEDE QUE NO SE PUBLIQUE UNA VERSIÓN FINAL DE TALES CARACTERÍSTICAS O CONCEPTOS. DE IGUAL MODO, SU EXPERIENCIA CON EL USO DE ESTAS CARACTERÍSTICAS Y FUNCIONALIDADES EN UN ENTORNO FÍSICO PUEDE SER DIFERENTE. 

**COMENTARIOS**. Si envía comentarios a Microsoft sobre las características, funcionalidades o conceptos de tecnología descritos en esta demostración/laboratorio práctico, acepta otorgar a Microsoft, sin cargo alguno, el derecho a usar, compartir y comercializar sus comentarios de cualquier modo y para cualquier fin. También concederá a terceros, sin cargo alguno, los derechos de patente necesarios para que sus productos, tecnologías y servicios usen o interactúen con cualquier parte específica de un software o servicio de Microsoft que incluya los comentarios. No enviará comentarios que estén sujetos a una licencia que obligue a Microsoft a conceder su software o documentación bajo licencia a terceras partes porque incluyamos sus comentarios en ellos. Estos derechos seguirán vigentes después del vencimiento de este acuerdo. 

MICROSOFT CORPORATION RENUNCIA POR LA PRESENTE A TODAS LAS GARANTÍAS Y CONDICIONES RELATIVAS A LA DEMOSTRACIÓN/LABORATORIO PRÁCTICO, INCLUIDA CUALQUIER GARANTÍA Y CONDICIÓN DE COMERCIABILIDAD (YA SEA EXPRESA, IMPLÍCITA O ESTATUTARIA), DE IDONEIDAD PARA UN FIN DETERMINADO, DE TITULARIDAD Y DE AUSENCIA DE INFRACCIÓN. MICROSOFT NO DECLARA NI GARANTIZA LA EXACTITUD DE LOS RESULTADOS, EL RESULTADO DERIVADO DE LA REALIZACIÓN DE LA DEMOSTRACIÓN/LABORATORIO PRÁCTICO NI LA IDONEIDAD DE LA INFORMACIÓN CONTENIDA EN ELLA CON NINGÚN PROPÓSITO. 

## DECLINACIÓN DE RESPONSABILIDADES 

Esta demostración/laboratorio práctico contiene solo una parte de las nuevas características y mejoras realizadas en Microsoft Power BI. Puede que algunas de las características cambien en versiones futuras del producto. En esta demostración/laboratorio práctico, conocerá algunas de estas nuevas características, pero no todas. 
