# ​​Contenido 

## Presentación  

## Power BI 

- Tarea 1: Crear un informe de forma automática
- Tarea 2: Ocultar tablas predeterminadas (métricas)
- Tarea 3: Configurar el fondo para un nuevo informe
- Tarea 4: Agregar un encabezado al informe
- Tarea 5: Agregar KPI al informe
- Tarea 6: Agregar un gráfico de líneas al informe
- Tarea 7: Configurar la columna Year en la tabla Date
- Tarea 8: Configurar la columna Short_Month_Name en la tabla Date
- Tarea 9: Aplicar formato al gráfico de líneas
- Tarea 10: Agregar nuevos datos para simular el modo Direct Lake

## Limpieza del entorno de laboratorio 

## Referencias 

## Presentación  

Absorbimos datos de diferentes orígenes de datos a un lakehouse, conocimos los lakehouse, creamos un modelo de datos y establecimos una programación de actualización para los orígenes de datos. Ahora vamos a crear un informe. 

Al final de este laboratorio, habrá aprendido:  

- Cómo crear un informe de forma automática
- Cómo crear un informe a partir de un lienzo en blanco
- Cómo usar el modo Direct Lake, que da como resultado una actualización automática de los datos

## Power BI 

### Tarea 1: Crear un informe de forma automática 

Comencemos con la opción de creación automática de informes. Y, más adelante en el laboratorio, volveremos a crear el informe que tenemos en Power BI. 

1. Volvamos **al área de trabajo de Fabric** que creó en el laboratorio anterior. 

2. Seguramente esté en la página principal de Data Factory. En la parte inferior del panel de navegación de la izquierda, seleccione el **icono de Data Factory**. 

3. Se abre el cuadro de diálogo de experiencia de Fabric. Seleccione **Power BI**. Se le llevará al **Inicio de Power BI**.

4. Seleccione **Nuevo informe** en el menú superior.

5. Se le dirigirá a la **pantalla de creación de su primer informe**. Habrá opciones para introducir datos manualmente y crear un informe o elegir un modelo semántico publicado. Hemos creado un modelo semántico en los laboratorios anteriores. Usemos ese. Seleccione la opción **Selección de un modelo semántico publicado**.

6. Se abre la página Elija un conjunto de datos para usar en su informe. Observe que tenemos cuatro opciones. **Seleccione lh_FAIAD**: 

    - **lh_FAIAD**: este es el lakehouse con el conjunto de datos que creamos y que queremos usar para el informe. 

    - **Units by Supplier**: este es el conjunto de datos que creamos con T-SQL. 

    - **DataflowsStagingWarehouse**: este es el almacén de almacenamiento provisional que se crea de forma predeterminada, ya que no lo utilizamos porque no preparamos datos. 

    - **DataflowsStagingLakehouse**: este es el lakehouse provisional que se crea de forma predeterminada, ya que no lo utilizamos porque no preparamos datos. 

7. Haga clic en la flecha **junto al botón Crear informe de forma automática**. Observe que hay dos opciones: Crear informe de forma automática y Crear un informe en blanco. Probemos la creación automática: seleccione **Crear informe de forma automática**.

8. Power BI comenzará a crear de forma automática el informe. Observe que hay una opción para seleccionar previamente los datos si así lo queremos. Una vez que el informe esté listo, aparecerá un cuadro de diálogo en la parte superior derecha de la pantalla. Seleccione **Ver informe ahora**.

   >**Punto de control**: tendrá un informe similar a la captura de pantalla siguiente. Hay algunos KPI y algunos objetos visuales de tendencias. Este es un buen comienzo si está analizando un nuevo modelo y necesita un impulso. 

   >**Nota**: Observe que en el menú superior tiene la opción de editar el informe o ver algunos de los datos como tablas. No dude en explorar estas opciones.

9. Una vez que esté listo, **contraiga** todas las tablas en la sección **Datos** de la derecha. Observe que tenemos cinco tablas nuevas que no forman parte del modelo que creamos. Son tablas predeterminadas agregadas para ayudar a analizar el rendimiento. Las eliminaremos de la vista del informe en breve. 

10. Guardemos este informe. En el menú superior, seleccione **Guardar**. 

11. Se abre el cuadro de diálogo Guardar el informe. Nombre el informe como **rpt_Sales_Auto_Report**  

    >**Nota**: Estamos anteponiendo rpt al nombre del informe, que es la abreviatura de informe (en inglés). 

12. Asegúrese de que el informe esté guardado en **<your workspace name>**. 

13. Seleccione **Guardar**.

### Tarea 2: Ocultar tablas predeterminadas (métricas) 

Creemos un informe como el que tenemos en Power BI Desktop. Lo vamos a hacer desde un lienzo en blanco. Antes de comenzar a crear un informe, eliminemos las tablas predeterminadas (captura de pantalla anterior) de la vista del informe. Esto se hace en la sección de modelado del lakehouse. 

1. En la parte inferior del panel de navegación de la izquierda, seleccione **el icono de Power BI**. Se abre el cuadro de diálogo de Fabric. 

2. Seleccione **Data Engineering**. Se le dirigirá a la página principal de Data Engineering.

3. Desplácese hacia abajo hasta la sección **Acceso rápido**. 

4. Seleccione **lh_FAIAD -> Punto de conexión de análisis SQL**. Estaremos en la vista Datos del lakehouse. 

5. Desde la **parte inferior del panel izquierdo**, seleccione **Modelo** para navegar a la vista Modelo. 

Observe que en el lienzo de diseño encontrará las tablas predeterminadas. (Es posible que tenga que desplazarse hacia la derecha o hacia abajo para verlos).

6. Haga clic derecho en la tabla **long_running_queries** y seleccione **Ocultar en la vista de Informes**.

7. De manera similar, seleccione la opción **Ocultar en la vista de Informes** para las siguientes tablas: 

    - fabric_query_starting 
    - fabric_query_completed 
    - exec_requests_history 
    - frequently_run_queries

### Tarea 3: Configurar el fondo para un nuevo informe 

1. Podemos comenzar a crear un nuevo informe desde la vista del modelo. En el menú superior, seleccione **Inicio -> Nuevo informe**. Se le dirigirá al lienzo del informe de Power BI en una nueva ventana o pestaña en su explorador.

2. Si aún no lo ha abierto, abra **FAIAD.pbix**, que se encuentra en la carpeta **Report** en el **Escritorio** de su entorno de laboratorio.  

Vamos a utilizar este informe como referencia. Comenzaremos agregando el fondo del lienzo. Crearemos el encabezado del informe, agregaremos un par de KPI y crearemos el gráfico de líneas de Ventas a lo largo del tiempo. Por razones de tiempo y sabiendo que tiene experiencia en la creación de objetos visuales en Power BI Desktop, no crearemos todos los objetos visuales

3. Vuelva al **lienzo de Power BI** en su explorador. 

4. Seleccione el **icono** de **la página Formato** en el panel de Visualizaciones. 

5. Expanda la **sección Fondo del lienzo**. 

6. Seleccione la opción **Examinar** de la opción **Imagen**. Se abre el cuadro de diálogo Explorador de archivos. 

7. Navegue hasta la carpeta **Report** en el **Escritorio** de su entorno de laboratorio.  

8. Seleccione **Summary Background.png**. 

9. Establezca el menú desplegable **Ajuste de imagen** en **Ajustar**. 

10. Establezca la Transparencia en **0 %**.

### Tarea 4: Agregar un encabezado al informe

1. Agreguemos el encabezado en el margen superior. En el **menú**, seleccione **Cuadro de texto**. 

2. Introduzca **Fabrikam Company** como primera línea en el cuadro de texto. 

3. Introduzca **Sales Report** como segunda línea en el cuadro de texto. 

4. Resalte **Fabrikam Company** y establezca la **Fuente** en **Segoe UI** y el **tamaño de fuente** a **18**, **negrita**. 

5. Resalte **Informe de ventas** y establezca la **Fuente** en **Segoe UI** y el **tamaño de fuente** a **14**, **negrita**. 

6. Con el **cuadro de texto seleccionado**, en el panel Formato de la derecha, **expanda la sección Efectos**. 

7. Utilice el control deslizante **Fondo** para configurarlo en **Desactivado**. 

8. Cambie el tamaño del cuadro de texto **para que quepa en el margen superior**.

### Tarea 5: Agregar KPI al informe 

1. Agreguemos KPI de ventas. Seleccione el **espacio en blanco** en el lienzo para quitar el foco del cuadro de texto. 

2. En la **sección Visualizaciones**, seleccione el **objeto visual Tarjeta de varias filas**. 

3. En la sección Datos, expanda la **tabla Sales**. 

4. Seleccione **la medida Sales**.

5. Con **el objeto visual de tarjeta de varias filas seleccionado**, seleccione el **icono Dar formato a objeto visual** en la sección Visualizaciones. 

6. Expanda la sección **Etiquetas de categorías.** 

7. Aumente el **tamaño de fuente** a **14**. 

8. Seleccione el **menú desplegable Color**. Se abre el cuadro de diálogo Paleta de colores. 

9. Establezca el valor Hex en **#004753**.

10. Expanda la sección **Tarjetas**. 

11. Utilice el control deslizante **Barra de énfasis** para configurarlo en **Desactivado**.

12. Seleccione **General** en el panel de Visualizaciones. 

13. Expanda la **sección Efectos**. 

14. Utilice el control deslizante **Fondo** para configurarlo en **Desactivado**. 

15. Cambie el tamaño del **objeto visual** y muévalo al **cuadro izquierdo como se muestra en la captura de pantalla**.

16. Vamos a agregar otro KPI. Seleccione la **Tarjeta de varias filas de Sales** que acabamos de crear. **Copie** el objeto visual mediante la selección de **Ctrl+C** desde tu teclado. 

17. **Pegue** el objeto visual mediante la selección de **Ctrl+V** desde tu teclado. Observe que el objeto visual se pega en el lienzo. 

18. Con el **nuevo objeto visual resaltado**, en la sección **Visualizaciones -> Crear objeto visual -> Campos**, elimine la medida **Sales**. 

19. Desde la sección **Datos**, expanda la tabla **Sales** y seleccione la medida **Units**. 

20. Cambie el tamaño del **objeto visual** y **colóquelo en el cuadro debajo del objeto visual Sales**.

### Tarea 6: Agregar un gráfico de líneas al informe 

Creemos un gráfico de líneas para visualizar las ventas a lo largo del tiempo por empresa revendedora. 

1. Seleccione el **espacio en blanco** en el lienzo para quitar el foco del objeto visual de tarjeta de varias filas. 

2. En la **sección Visualizaciones**, seleccione **Gráfico de líneas**. 

3. En la **sección Datos**, expanda la tabla **Date**. 

4. Seleccione el campo **Year**. Tenga en cuenta que Year se suma de forma predeterminada y se agrega al eje Y. Rectifiquemos esto.

### Tarea 7: Configurar la columna Year en la tabla Date 

1. Navegue a la pestaña del explorador con la **vista del modelo del lakehouse**. 

2. En el panel izquierdo del explorador, expanda **lhFAIAD -> Schemas -> dbo -> Tables -> Date**. 

3. Seleccione la columna **Year**. 

4. En el panel **Propiedades** de la derecha, expanda la sección **Avanzado**. 

5. En el menú desplegable **Resumir por**, seleccione **Ninguno**.

6. Vuelva a la pestaña del explorador con el **lienzo de Power BI**. 

7. En el menú superior, seleccione **Actualizar**. Observe ahora que Year no es un campo de suma.  

8. Con el **objeto visual Gráfico de líneas seleccionado**, **elimine la Sum of Year** del eje Y. 

9. Seleccione el campo **Year** y se agregará al **eje X**. 

10. Expanda la tabla **Sales** y seleccione la **medida Sales**.

### Tarea 8: Configurar la columna Short_Month_Name en la tabla Date 

1. Agreguemos Mes a este gráfico. Desde la tabla Date, arrastre el campo **Short_Month_Name** debajo de **Year** en el **eje X**. Observe que el objeto visual está ordenado por Sales. Ordenémoslo por Short_Month_Name. 

2. Haga clic en los **puntos suspensivos (…)** en la esquina superior derecha del objeto visual. 

3. Seleccione **Ordenar eje -> Year Short_Month_Name**. 

4. Haga clic en los **puntos suspensivos (…)** en la esquina superior derecha del objeto visual. 

5. Seleccione **Ordenar eje -> Orden ascendente**. 

   >**Nota:** Los meses están ordenados alfabéticamente. Vamos a arreglarlo. 

6. Navegue a la pestaña del explorador con la **vista del modelo del lakehouse**. 

7. En el panel izquierdo del explorador, expanda **lhFAIAD -> Schemes -> dbo -> Tables -> Date**. 

8. Seleccione la columna **Short_Month_Name**. 

9. En el panel **Propiedades** de la derecha, expanda la sección **Avanzado**. 

10. En el menú desplegable **Ordenar por columna** seleccione **Month**.

11. Vuelva a la pestaña del explorador con el **lienzo de Power BI**. 

12. En el menú superior, seleccione **Actualizar**. Observe que ahora los meses están ordenados correctamente.

### Tarea 9: Aplicar formato al gráfico de líneas 

Observe lo fácil que es actualizar el modelo semántico mientras se crean los informes. Esto proporciona una interacción fluida como Power BI Desktop. 

1. Con el **objeto visual Gráfico de líneas seleccionado**, en la **sección Datos**, expanda la tabla **Reseller**. 

2. Arrastre **Reseller -> Reseller Company** a la sección **Leyenda**.

3. Con el **objeto visual Gráfico de líneas seleccionado**, en la sección **Visualizaciones**, seleccione **icono Formato visual -> General**. 

4. Expanda la sección **Título**. 

5. Establezca el texto **Título** en **Ventas a lo largo del tiempo**. 

6. Expanda la sección **Efectos**. 

7. Utilice el control deslizante **Fondo** para configurarlo en **Desactivado**.

8. En la sección **Visualizaciones**, seleccione el **icono Formato de objeto visual -> Objeto visual**. 

9. Expanda la sección **Eje X**. 

10. Utilice el control deslizante Título para configurarlo en **Desactivado**. 

11. Expanda la sección **Líneas**. 

12. Expanda la sección **Colores**. 

13. Establezca el color de **Wingtip Toys** en **#004753**. 

14. Establezca el color de **Tailspin Toys** en **#F17925**. 

15. Cambie el tamaño del **objeto visual** y muévalo al **cuadro superior derecho como se muestra en la captura de pantalla**. 

16. Desplácese hacia la derecha en el objeto visual y **observe que tenemos datos hasta abril de 2023**.

17. Guardemos el informe: desde el menú, seleccione **Archivo -> Guardar**. 

18. Se abre el cuadro de diálogo Guardar el informe. Nombre el informe como **rpt_Sales_Report**  

    >**Nota**: Estamos anteponiendo rpt al nombre del informe, que es la abreviatura de informe (en inglés). 

19. Asegúrese de que el informe esté guardado en **<your workspace name>**. 

20. Seleccione **Guardar**.

Como se mencionó anteriormente, no crearemos todos los objetos visuales en esta práctica de laboratorio. Siéntase libre de crear más objetos visuales si lo desea.  

### Tarea 10: Agregar nuevos datos para simular el modo Direct Lake 

Normalmente, en el modo Import, una vez que se actualizan los datos en el origen, necesitamos actualizar el modelo de Power BI y después se actualizan los datos en el informe. Con el modo de Direct Query, una vez que los datos se actualizan en el origen, están disponibles en el informe de Power BI. Sin embargo, el modo de Direct Query suele ser lento. Para resolver este problema, Microsoft Fabric presenta el modo Direct Lake. Direct Lake es una ruta rápida para cargar los datos del lago directamente en el motor de Power BI listos para su análisis. Exploremos más. 

En un escenario real, los datos se actualizan en el origen. Como estamos en un entorno de entrenamiento, lo simularemos mediante la conexión a un archivo Parquet con datos de mayo de 2023.  

1. Navegue a la pestaña del explorador con la **vista del modelo del lakehouse**. 

2. Seleccione **<your workspace name>** en el panel izquierdo. 

3. Seleccione **df_Sales_ADFS** para que podamos editar el flujo de datos al agregar el nuevo archivo Parquet.

4. Si aún no lo ha abierto, abra **FAIAD.pbix**, que se encuentra en la carpeta **Report** en el **Escritorio** de su entorno de laboratorio.  

5. En la cinta de opciones, seleccione **Inicio -> Transformar datos**. Se abre la ventana de Power Query. 

6. En el panel izquierdo, en la carpeta **DirectLake**, seleccione la consulta **MayInvoice**. 

7. **Haga clic derecho** y seleccione **Copiar**.

8. Vuelva a la **pantalla del flujo de datos** en el explorador. 

9. En el panel del flujo de datos, introduzca **Ctrl+V** (actualmente, hacer clic con el botón derecho en Pegar no es compatible). 

Ahora eliminemos la referencia a ADLS Base Folder (2) y usemos ADLS Base Folder. 

10. Seleccione consulta **MayInvoice**. 

11. Desde el panel derecho, en **Pasos aplicados**, seleccione **Source**. 

12. En la barra de fórmulas, cambie de **#"ADLS Base Folder (2)"** a **#"ADLS Base Folder"**. 

13. Seleccione la **marca de verificación** al lado de la barra de fórmulas o pulse Enter.

14. En el panel izquierdo, en la sección Consultas, **haga clic con el botón derecho en la consulta ADLS Base Folder (2)** y seleccione **Eliminar**. 

15. Aparece el cuadro de diálogo Eliminar consulta. Seleccione **Eliminar** para confirmar.

16. Ahora, agreguemos los datos de la factura de mayo a la tabla Invoice. Seleccione la consulta **Invoice** desde la sección Consultas. 

17. En la cinta de opciones, seleccione **Inicio - Anexar** consultas. 

18. Aparece el cuadro de diálogo Anexar consulta. Desde el menú desplegable **Tabla para anexar**, seleccione **MayInvoice**. 

19. Seleccione **Aceptar**.

20. Seleccione **Publicar** en la esquina inferior derecha para guardar y publicar las actualizaciones.

    >**Nota**: Una vez publicado, el flujo de datos se actualizará. Esto puede tardar varios minutos. 

21. Vuelva a la pestaña del explorador con el **lienzo de Power BI**. 

22. En el menú superior, seleccione **Actualizar**. Observe ahora que en el gráfico de líneas hay datos para mayo de 2023. Además, observe que el dólar de ventas ha aumentado.

A medida que cada flujo de datos que hemos creado en laboratorios anteriores se actualiza según lo programado, los datos se incorporan al lakehouse. El modelo de datos en el lakehouse y los informes se actualizan. No tenemos que actualizar el modelo de datos ni informar cuando se actualice cada uno de los flujos de datos. Esta es la ventaja de Direct Lake. 

Revisemos los desafíos que se enumeran en el planteamiento del problema: 

- **Debe actualizar su conjunto de datos al menos tres veces al día para adaptarse a los diferentes tiempos de actualización para los diferentes orígenes de datos**. 
Resolvimos esto con Direct Lake. Cada flujo de datos individual se actualiza según su programación. No es necesario actualizar el conjunto de datos y el informe. 

- **Sus actualizaciones tardan mucho tiempo, ya que necesita hacer una actualización completa cada vez para capturar cualquier actualización que haya ocurrido en los sistemas de origen.** 
De nuevo, resolvimos esto con Direct Lake. Cada flujo de datos individual se actualiza según su programación. No es necesario actualizar el conjunto de datos y el informe, por lo que no tenemos que preocuparnos por la actualización completa.  

- **Cualquier error en cualquiera de los orígenes de datos de los que extrae provocará que se interrumpa la actualización del conjunto de datos. Muchas veces, el archivo del empleado no se carga a tiempo, lo que provoca que se interrumpa la actualización del conjunto de datos**. 
La canalización de datos ayuda a resolver este problema al brindar la capacidad de volver a intentar la actualización en caso de error y en diferentes intervalos. 

- **Se necesita mucho tiempo para hacer cambios en su modelo de datos, ya que Power Query tarda mucho en actualizar sus versiones preliminares, dado el gran tamaño de los datos y las transformaciones complejas**.  
Vimos que los flujos de datos son eficientes y es fácil hacer cambios en ellos. Normalmente, la versión preliminar en flujos de datos no tarda mucho en cargarse. 

- **Necesita que un PO con Windows use Power BI Desktop aunque el estándar corporativo es Mac**. 
Microsoft Fabric es una oferta SaaS. Lo único que necesitamos es un explorador para acceder al servicio. No tenemos que instalar ningún software en nuestros escritorios. 

## Limpieza del entorno de laboratorio 

Una vez que esté todo listo para limpiar el entorno del laboratorio, siga los pasos a continuación. 

1. Vuelva a la pestaña del explorador con el **lienzo de Power BI. Cierre esta pestaña**. 

2. Navegue a la pestaña con la **vista del modelo del lakehouse**. 

3. Seleccione **<your workspace name>** en el panel izquierdo para navegar a la página de inicio.

4. En el menú superior, seleccione **puntos suspensivos (…)** al lado de Administrar acceso y seleccione **Configuración del área de trabajo**.

5. Se abre el cuadro de diálogo de Configuración del área de trabajo. Seleccione **Otros** en el menú izquierdo. 

6. Seleccione **Quitar esta área de trabajo**. 

7. Se abrirá el cuadro de diálogo de eliminar área de trabajo. Seleccione **Eliminar**. 

Esto eliminará el área de trabajo y todos los elementos que contenía. 

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

**COMENTARIOS**. Si envía comentarios a Microsoft sobre las características, funcionalidades o conceptos de tecnología descritos en esta demostración/laboratorio práctico, acepta otorgar a Microsoft, sin cargo alguno, el derecho a usar, compartir y comercializar sus comentarios de cualquier modo y para cualquier fin. También concederá a terceros, sin cargo alguno, los derechos de patente necesarios para que sus productos, tecnologías y servicios usen o interactúen con cualquier parte específica de un software o servicio de Microsoft que incluya los comentarios. No enviará comentarios que estén sujetos a una licencia que obligue a Microsoft a conceder su software o documentación bajo licencia a terceras partes porque incluyamos sus comentarios en ellos. Estos derechos seguirán vigentes después del vencimiento de este acuerdo. 

MICROSOFT CORPORATION RENUNCIA POR LA PRESENTE A TODAS LAS GARANTÍAS Y CONDICIONES RELATIVAS A LA DEMOSTRACIÓN/LABORATORIO PRÁCTICO, INCLUIDA CUALQUIER GARANTÍA Y CONDICIÓN DE COMERCIABILIDAD (YA SEA EXPRESA, IMPLÍCITA O ESTATUTARIA), DE IDONEIDAD PARA UN FIN DETERMINADO, DE TITULARIDAD Y DE AUSENCIA DE INFRACCIÓN. MICROSOFT NO DECLARA NI GARANTIZA LA EXACTITUD DE LOS RESULTADOS, EL RESULTADO DERIVADO DE LA REALIZACIÓN DE LA DEMOSTRACIÓN/LABORATORIO PRÁCTICO NI LA IDONEIDAD DE LA INFORMACIÓN CONTENIDA EN ELLA CON NINGÚN PROPÓSITO. 

## DECLINACIÓN DE RESPONSABILIDADES 

Esta demostración/laboratorio práctico contiene solo una parte de las nuevas características y mejoras realizadas en Microsoft Power BI. Puede que algunas de las características cambien en versiones futuras del producto. En esta demostración/laboratorio práctico, conocerá algunas de estas nuevas características, pero no todas.
