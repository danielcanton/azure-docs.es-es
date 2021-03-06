---
title: 'Uso de Analytics: la herramienta de búsqueda eficaz de Application Insights | Microsoft Docs'
description: 'Uso de Analytics, la eficaz herramienta de búsqueda de Application Insights. '
services: application-insights
documentationcenter: ''
author: danhadari
manager: douge

ms.service: application-insights
ms.workload: tbd
ms.tgt_pltfrm: ibiza
ms.devlang: na
ms.topic: article
ms.date: 10/03/2016
ms.author: danha

---
# <a name="using-analytics-in-application-insights"></a>Uso de Analytics en Application Insights
[Analytics](app-insights-analytics.md) es la eficaz característica de búsqueda de [Application Insights](app-insights-overview.md). En estas páginas se describe el lenguaje de consulta de Analytics.

* **[Vea el vídeo de introducción](https://applicationanalytics-media.azureedge.net/home_page_video.mp4)**.
* **[Use una versión de prueba de Analytics en nuestros datos simulados](https://analytics.applicationinsights.io/demo)** si su aplicación aún no envía datos a Application Insights.

## <a name="open-analytics"></a>Apertura de Analytics
En el recurso de inicio de la aplicación de Application Insights, haga clic en Analytics.

![Abra portal.azure.com, abra su recurso de Application Insights y haga clic en Análisis.](./media/app-insights-analytics-using/001.png)

El tutorial en línea le proporciona algunas ideas sobre lo que puede hacer.

Puede encontrar un [paseo más amplio aquí](app-insights-analytics-tour.md).

## <a name="query-your-telemetry"></a>Consulta de la telemetría
### <a name="write-a-query"></a>Escriba una consulta.
![Pantalla del esquema](./media/app-insights-analytics-using/150.png)

Comience con los nombres de cualquiera de las tablas que aparecen a la izquierda (o los operadores [range](app-insights-analytics-reference.md#range-operator) o [union](app-insights-analytics-reference.md#union-operator)). Use `|` para crear una canalización de [operadores](app-insights-analytics-reference.md#queries-and-operators). IntelliSense le indicará los operadores y algunos de los elementos de la expresión que se puede utilizar.

Consulte [Un paseo por Analytics de Application Insights](app-insights-analytics-tour.md) y [Referencia para Analytics](app-insights-analytics-reference.md).

### <a name="run-a-query"></a>Ejecución de una consulta
![Ejecución de una consulta](./media/app-insights-analytics-using/130.png)

1. Puede utilizar saltos de línea sencillos en las consultas.
2. Coloque el cursor dentro o al final de la consulta que desea ejecutar.
3. Haga clic en Ir para ejecutar la consulta.
4. No ponga líneas en blanco en la consulta. Puede mantener varias consultas separadas en una pestaña de consulta; para ello, sepárelas con líneas en blanco. Solo se ejecutará la que tiene el cursor.

### <a name="save-a-query"></a>Almacenamiento de una consulta
![Almacenamiento de una consulta](./media/app-insights-analytics-using/140.png)

1. Guarde el archivo de consulta actual.
2. Abra un archivo de consulta guardado.
3. Cree un archivo de consulta.

## <a name="see-the-details"></a>Visualización de los detalles
Expanda cualquier fila de los resultados para ver la lista completa de sus propiedades. Puede expandir más cualquier propiedad que tenga un valor estructurado: por ejemplo, las dimensiones personalizadas o la pila indicada en una excepción.

![Expansión de una fila](./media/app-insights-analytics-using/070.png)

## <a name="arrange-the-results"></a>Disposición de los resultados
Puede ordenar, filtrar, paginar y agrupar los resultados devueltos desde la consulta.

> [!NOTE]
> Ordenar, agrupar y filtrar en el explorador no vuelve a ejecutar la consulta. Solo vuelve a ordenar los resultados devueltos por la última consulta. 
> 
> Para realizar estas tareas en el servidor antes de que se devuelvan los resultados, escriba la consulta con los operadores [sort](app-insights-analytics-reference.md#sort-operator), [summarize](app-insights-analytics-reference.md#summarize-operator) y [where](app-insights-analytics-reference.md#where-operator).
> 
> 

Elija las columnas que desea ver, arrastre los encabezados de columna para reorganizarlos y cambie el tamaño de las columnas arrastrando sus bordes.

![Organización de columnas](./media/app-insights-analytics-using/030.png)

### <a name="sort-and-filter-items"></a>Ordenación y filtrado de elementos
Haga clic en el encabezado de una columna para ordenar los resultados. Vuelva a hacer clic para ordenar de otra manera, y haga clic una tercera vez para volver a la ordenación original devuelta por la consulta.

Utilice el icono de filtro para restringir la búsqueda.

![Ordenación y filtrado de columnas](./media/app-insights-analytics-using/040.png)

### <a name="group-items"></a>Agrupación de elementos
Para ordenar por más de una columna, use la agrupación. Primero, habilítela y, después, arrastre los encabezados de columna en el espacio por encima de la tabla.

![Grupo](./media/app-insights-analytics-using/060.png)

### <a name="missing-some-results?"></a>¿Faltan algunos resultados?
Hay un límite de 10 000 filas en los resultados devueltos desde el portal. Se muestra una advertencia si se sobrepasa el límite. Si esto sucede, al ordenar los resultados de la tabla no siempre mostrará todos los resultados primeros o últimos reales. 

Es recomendable evitar llegar al límite. Utilice operadores como:

* [where timestamp > ago(3d)](app-insights-analytics-reference.md#where-operator)
* [top 100 by timestamp](app-insights-analytics-reference.md#top-operator) 
* [take 100](app-insights-analytics-reference.md#take-operator)
* [summarize ](app-insights-analytics-reference.md#summarize-operator) 

## <a name="diagrams"></a>Diagramas
Seleccione el tipo de diagrama que desea:

![Seleccione un tipo de diagrama](./media/app-insights-analytics-using/230.png)

Si tiene varias columnas de los tipos correctos, puede elegir los ejes X e Y, así como una columna de dimensiones para dividir los resultados.

De manera predeterminada, los resultados se muestran en un principio en forma de tabla y el diagrama se selecciona manualmente. Sin embargo, para seleccionar un diagrama se puede usar la [directiva render](app-insights-analytics-reference.md#render-directive) al final de una consulta.

## <a name="pin-to-dashboard"></a>Anclar al panel
Puede anclar un diagrama o una tabla a uno de sus [paneles compartidos](app-insights-dashboards.md) ; simplemente haga clic en la chincheta. (Es posible que necesite [actualizar el paquete de precios de la aplicación](app-insights-pricing.md) para activar esta característica). 

![Haga clic en la chincheta](./media/app-insights-analytics-using/pin-01.png)

Esto significa que, cuando elabora un panel que le ayude a supervisar el rendimiento o el uso de los servicios web, puede incluir un análisis bastante complejo junto con las demás métricas. 

Puede anclar una tabla al panel, si tiene cuatro o menos columnas. Se muestran solo las siete filas superiores.

#### <a name="dashboard-refresh"></a>Actualización del panel
El gráfico anclado en el panel se actualiza automáticamente al volver a ejecutar la consulta aproximadamente cada media hora.

#### <a name="automatic-simplifications"></a>Simplificaciones automáticas
En algunos casos, determinadas simplificaciones se aplican a un gráfico cuando se fija a un panel.

Al anclar un gráfico que muestra muchos intervalos discretos (normalmente un gráfico de barras), los intervalos rellenados automáticamente se agrupan en un solo intervalo "otros". Por ejemplo, esta consulta:

    requests | summarize count_search = count() by client_CountryOrRegion

tiene esta apariencia en Analytics:

![Gráfico con cola larga](./media/app-insights-analytics-using/pin-07.png)

pero cuando se ancla a un panel, la siguiente apariencia:

![Gráfico con intervalos limitados](./media/app-insights-analytics-using/pin-08.png)

## <a name="export-to-excel"></a>Exportación a Excel
Una vez que haya ejecutado una consulta, puede descargar un archivo .csv. Haga clic en **Exportar, Excel**.

## <a name="export-to-power-bi"></a>Exportación a Power BI
1. Coloque el cursor en una consulta y elija **Exportar, Power BI**.
   
    ![](./media/app-insights-analytics-using/240.png)
   
    Esta operación descarga un archivo de script de M.
2. Copie el script del lenguaje M en el editor de consultas avanzadas de Power BI Desktop.
   
   * Abra el archivo exportado.
   * En Power BI Desktop seleccione **Obtener datos, Consulta en blanco, Editor avanzado** y pegue el script de lenguaje M.
     
     ![](./media/app-insights-analytics-using/250.png)
3. Edite las credenciales, en caso de que sea necesario, y podrá generar el informe.
   
    ![](./media/app-insights-analytics-using/260.png)

[!INCLUDE [app-insights-analytics-footer](../../includes/app-insights-analytics-footer.md)]

<!--HONumber=Oct16_HO2-->


