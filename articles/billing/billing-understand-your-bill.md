---
title: "Descripción de la factura | Microsoft Azure"
description: "Aprenda a leer y entender el uso y la factura de la suscripción de Azure"
services: 
documentationcenter: 
author: genlin
manager: stevenpo
editor: 
tags: billing
ms.assetid: 32eea268-161c-4b93-8774-bc435d78a8c9
ms.service: billing
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2016
ms.author: erihur;genli
translationtype: Human Translation
ms.sourcegitcommit: 219dcbfdca145bedb570eb9ef747ee00cc0342eb
ms.openlocfilehash: 8768ccd5a1d04566c5f2e1f26ab328cea570cc61


---
# <a name="understand-your-bill-for-microsoft-azure"></a>Comprender la factura de Microsoft Azure
> [!NOTE]
> Si necesita más ayuda sobre cualquier aspecto de este artículo, [póngase en contacto con el soporte técnico](https://portal.azure.com/?#blade/Microsoft_Azure_Support/HelpAndSupportBlade) para resolver rápidamente el problema.
> 
> 

Los cargos de las suscripciones de Microsoft Azure varían según el plan de tarifas. Algunos planes de tarifas, como el de los suscriptores de Visual Studio Enterprise (MPN), incluyen créditos mensuales que puede usar en cualquier servicio de Azure según sus necesidades.

Tenga en cuenta que es posible que se le facturen hasta 24 horas de uso latente del período de facturación anterior dentro del período de facturación actual.

Para obtener más información acerca del consumo y los planes de tarifas, consulte la [página Opciones de compra de Microsoft Azure](https://azure.microsoft.com/pricing/purchase-options/).

<!-- The below links cover a complete list of all Microsoft Azure services.

<!-- - [Service Details list (csv1)](https://azurepricing.blob.core.windows.net/supplemental/MOSPServices_csv1.xlsx)
<!-- - [Service Details list (csv2)](https://azurepricing.blob.core.windows.net/supplemental/MOSPServices_csv2.xlsx)

<!-- *NOTE: The **csv1** link refers to the column header names for csv version 1 and **csv2** link refers to the new column header names for csv version 2.  These files are updated monthly.*-->

### <a name="view-or-download-a-bill-for-microsoft-azure"></a>Ver o descargar una factura de Microsoft Azure:
1. Inicie sesión en el [Centro de cuentas](https://account.windowsazure.com/subscriptions) con su cuenta Microsoft o con el identificador de la organización.
2. Haga clic en la suscripción para la que desea ver los detalles y el uso.
3. Haga clic en **Historial de facturación**
   
    ![Resumen: historial de facturación: 1](./media/billing-understand-your-bill/ContentViewaBillforMA1.png)
4. La sección **Historial de facturación** enumera los extractos de los anteriores períodos de facturación, además del período actual no facturado. El extracto del período actual es una estimación de los cargos en el momento en que se generó la estimación. Esta información solo se actualiza diariamente y es posible que no incluya todo el uso en el que se ha incurrido a la fecha. La factura mensual puede ser distinta a esta estimación.  
   
    ![Resumen: historial de facturación: 2](./media/billing-understand-your-bill/ContentViewaBillforMA2.png)
5. Haga clic en **Ver extracto actual** para ver una estimación de los cargos en el momento en que se generó la estimación. Esta información solo se actualiza diariamente y es posible que no incluya todo el uso en el que se ha incurrido a la fecha. La factura mensual puede ser distinta a esta estimación.
   
    ![Resumen: historial de facturación: 3](./media/billing-understand-your-bill/ContentViewaBillforMA3.png)
   
    ![Resumen: historial de facturación: 4](./media/billing-understand-your-bill/ContentViewaBillforMA4.png)
6. Haga clic en **Descargar factura** para ver una copia de la factura anterior.
   
    ![Resumen: historial de facturación: 5](./media/billing-understand-your-bill/ContentViewaBillforMA5.png)

> [!NOTE]
> Los cargos que se enumeran en los extractos de facturación de los clientes internacionales tienen únicamente carácter estimativo dadas las diferentes tasas de conversión de los bancos.
> 
> 

A continuación encontrará varios extractos de ejemplo de dos ofertas diferentes disponibles en Microsoft Azure.

| Tipo de oferta | Description | Descargar |
|:--- |:--- |:--- |
| Pay-As-You-Go |Pagar mensualmente con retraso |[Archivo de muestra](https://azurepricing.blob.core.windows.net/sampleinvoices/Microsoft_Azure_ccinvoice_Sample.pdf) |
| Oferta de compromiso |Gasto deducido de su compromiso de prepago |[Archivo de muestra](https://azurepricing.blob.core.windows.net/sampleinvoices/Microsoft_Azure_invoice_Sample.pdf) |

## <a name="account-information"></a>Información de cuenta
La sección de información de la cuenta identifica la información pertinente sobre el uso y el perfil.

![encabezado](./media/billing-understand-your-bill/Header.png)

| Término | Description |
| --- | --- |
| Número de factura |Identificador único de factura con fines de seguimiento |
| Ciclo de facturación |Período de tiempo en que se ha realizado el uso |
| Fecha de la factura |Fecha en que se ha generado la factura |
| Método de pago |Tipo de pago que se utiliza en la cuenta (factura o tarjeta de crédito). |
| Dirección de facturación |Dirección de pagos de Microsoft Azure. |
| Oferta de suscripción |Tipo de oferta de suscripción que se adquirió (pago por uso, BizSpark Plus, Pase para Azure, etc.) |
| Correo electrónico del propietario de cuenta |La dirección de correo electrónico de la cuenta con que está registrada la cuenta de Microsoft Azure. |

## <a name="understand-the-invoice-summary"></a>Comprender el resumen de factura
La sección **Resumen de factura** de la factura resume las transacciones desde la última factura y los cargos de uso actuales.

![Resumen de factura](./media/billing-understand-your-bill/InvoiceSummary.png)

Las secciones Saldo anterior, Pagos y Saldo pendiente de la factura resumen las transacciones desde la última factura.

| Término | Description |
| --- | --- |
| Saldo anterior |El importe total debido de la última factura |
| Pagos |Los pagos totales aplicados a la última factura |
| Saldo pendiente (desde el ciclo de facturación anterior) |Todos los ajustes de factura (créditos o saldos) aplicados a la cuenta desde la última factura |

## <a name="understand-the-current-charges"></a>Comprender los cargos actuales
La sección Cargos actuales de la factura contiene detalles acerca de los cargos mensuales. Los vínculos están organizados en las siguientes subsecciones.

| Término | Description |
| --- | --- |
| Cargos de uso |Los cargos de uso son los cargos mensuales totales de una suscripción. Se le facturará con un mes de retraso según el uso que haya realizado el mes anterior. |
| Descuentos |Los descuentos en los servicios aplicados a la factura actual se verían reflejados en este elemento de línea. |
| Ajustes |Los ajustes varios son cargos pendientes o créditos varios que se aplican a la factura actual. Por ejemplo, si tiene la oferta de Visual Studio Ultimate con MSDN, podría ver un crédito mensual en este elemento de línea. Si cancela la suscripción, verá los cargos por el uso mensual que excedan el crédito mensual incluido en la oferta desde el comienzo del período de facturación actual hasta la fecha de cancelación de la suscripción. |

## <a name="footer-information"></a>Información de pie de página
![pie de página](./media/billing-understand-your-bill/footerinformation.png)

## <a name="understand-the-additional-information"></a>Comprender la información adicional
La página de información adicional muestra referencias a otros recursos para poder comprender la factura, así como vínculos para ver tanto el uso como otra información importante relacionada con su factura.

![información adicional](./media/billing-understand-your-bill/AdditionalInformation.png)

### <a name="detailed-usage"></a>Uso detallado
Un vínculo en la descripción de **Uso detallado** le dirige al Centro de cuentas, donde puede consultar el detalle del uso realizado de esta suscripción.  Ahora hay dos versiones disponibles para descargar: **versión 1 de .csv** contiene la antigua convención de nomenclatura y campos de uso y **versión 2 de .csv** contiene los nombres descriptivos de cliente para cada una de las categorías además de campos adicionales que le ayudarán a entender qué servicios está utilizando en Microsoft Azure. Tenga en cuenta que en la versión 1 del .csv no existen detalles de Azure Resource Manager. Puede encontrar información de Azure Resource Manager en la versión 2 de .csv.

### <a name="additional-information-and-useful-resources"></a>Información adicional y recursos útiles
Esta sección cuenta con vínculos a preguntas sencillas relacionadas con los tamaños de las instancias de proceso, los cargos de Base de datos SQL y vínculos útiles para permitirle responder cualquier otra pregunta.

| Término | Description |
| --- | --- |
| Dirección de venta |Se rellena previamente con la dirección del perfil de la cuenta. |
| Instrucciones de pago |En esta sección se encuentran las instrucciones de pago de dónde enviar cheques, transferencias bancarias o cheques urgentes si el método de pago es la factura. |

## <a name="understand-detailed-usage-charges"></a>Comprender los cargos de uso detallados
Como parte de nuestro constante compromiso con los clientes para ayudarles a administrar fácilmente el uso de Azure, hemos mejorado el archivo de uso de descarga que informa sobre el uso de los servicios y los costos de Azure.  El vínculo de descarga contiene dos versiones del archivo de uso:

* **versión 1** utiliza el formato preexistente
* **versión 2** incluye información adicional y los nombres de columna actualizados en la sección Uso diario.  

Los cargos de uso son los cargos **mensuales** totales de una suscripción, menos cualquier crédito o descuento. Se le facturará con un mes de retraso según el uso que haya realizado el mes anterior.  La sección superior del archivo muestra los detalles de los servicios que se facturan durante el ciclo de facturación del mes anterior.  La tabla anterior enumera los nombres de columnas de cada uno de los archivos de la versión en .csv.

| versión 1 | versión 2 | Description |
|:--- |:--- | --- |
| Período de facturación |Período de facturación |El período de facturación en que se consumió el recurso. |
| Nombre |Categoría de medidor |Identifica el servicio de nivel superior al que pertenece este uso. |
| Tipo |Subcategoría de medidor |El servicio de Azure se puede definir por tipo en esta columna, lo que puede afectar la tarifa. |
| Recurso |Nombre de medidor |Identifica la unidad de medida del recurso que se está utilizando. |
| Region |Medidor de la región |Identifica la ubicación del centro de datos para ciertos servicios cuyos precios se establecen según la ubicación del centro de datos. |
| SKU |SKU |Identifica el identificador único de sistema de cada recurso de Azure. |
| Unidad |Unidad |Identifica la unidad en que se cobra el servicio. Por ejemplo, GB, horas, por 10.000. |
| Consumida |Cantidad consumida |Contiene la cantidad consumida del recurso durante el período de facturación. |
| Se incluye |Cantidad incluida |Contiene la cantidad del recurso incluida sin cargo en el período de facturación actual. |
| Facturable |Cantidad de superávit |Si la cantidad Consumida supera la cantidad incluida, esta columna muestra la diferencia. Se le facturará esta cantidad. En el caso de ofertas de pago por uso que no incluyen cantidad en la oferta, este total será igual a la cantidad Consumida. |
| Dentro del compromiso |Dentro del compromiso |Contiene los cargos de recurso que se restan del importe comprometido asociado a su oferta de 6 o 12 meses. Los cargos de recurso se restan del importe comprometido en orden cronológico. |
| Moneda |Moneda |Identifica la moneda reflejada en el período de facturación actual. |
| Superávit |Superávit |Contiene los cargos de recurso que superan el importe comprometido asociado a su oferta de 6 o 12 meses. |
| Tarifa de compromiso |Tarifa de compromiso |Contiene la tarifa de compromiso basada en el importe comprometido total asociado a su oferta de 6 o 12 meses. |
| Tarifa |Tarifa |Muestra la tarifa que se le cobra por unidad facturable. |
| Valor |Valor |Muestra el resultado de multiplicar la columna Facturable por la columna Tarifa. Si la cantidad Consumida no supera la cantidad incluida, no habrá cargo en esta columna. |

## <a name="analyze-daily-usage-data"></a>Analizar los datos de uso diario
Dependiendo del uso, puede haber miles de filas de datos de uso diario. Si desea analizar estos datos, haga clic en **Descargar uso** y elija una versión de archivo de variables separadas por comas (.csv) para ver los datos de uso diario del período de facturación adecuado.  Como referencia, puede descargar un archivo .csv de muestra para cada versión mostrada a continuación.

| Nombre | Descargar |
|:---:|:---:|
|   Uso detallado .csv Versión 1 |[Archivo de muestra](https://azurepricing.blob.core.windows.net/supplemental/MOSPServices_csv1.xlsx) |
|   Uso detallado .csv Versión 2 |[Archivo de muestra](https://azurepricing.blob.core.windows.net/supplemental/MOSPServices_csv2.xlsx) |

![csv2screenshot](./media/billing-understand-your-bill/csv2screenshot.png)

En el archivo .csv, los elementos se desglosan para mostrar una lista de la cantidad de cada recurso que se consumió dentro del período de facturación actual.

![instantánea de csv](./media/billing-understand-your-bill/csvsnapshotportal.png)

Las siguientes columnas muestran detalles que afectan las tarifas al comienzo del período de facturación:

| versión 1 | versión 2 | Description |
|:--- |:--- | --- |
| Fecha de uso |Fecha de uso |La fecha en que se emitió el recurso. |
| Nombre |Categoría de medidor |Identifica el servicio de nivel superior al que pertenece este uso. |
| GUID de recursos |Id. de medidor |El identificador del medidor facturado.  Esto se utiliza como identificador para el uso de facturación de precios. |
| Tipo |Subcategoría de medidor |El servicio de Azure se puede definir por tipo en esta columna, lo que puede afectar la tarifa. |
| Recurso |Nombre de medidor |Identifica la unidad de medida del recurso que se está utilizando. |
| Region |Medidor de la región |Identifica la ubicación del centro de datos para ciertos servicios cuyos precios se establecen según la ubicación del centro de datos. |
| Unidad |Unidad |Identifica la unidad en que se cobra el servicio. Por ejemplo, GB, horas, por 10.000. |
| Consumida |Cantidad consumida |Contiene la cantidad del recurso consumida durante ese día. |
| Subregión |Ubicación del recurso |Identifica el centro de datos donde se está ejecutando el recurso. |
| Servicio |Servicio consumido |Esta columna se utiliza para hacer un seguimiento del servicio individual de la plataforma Azure que puede no estar específicamente identificado en la columna Nombre. Esta columna Servicio indica el servicio específico al que pertenece el uso. |
| N/D |El grupos de recursos |***Nueva adición de columna.***  El grupo de recursos en el que se ejecuta el recurso implementado. Consulte [Información general de Azure Resource Manager](../azure-resource-manager/resource-group-overview.md) |
| Componente |Id. de instancia |El identificador para el recurso en ejecución. El identificador contiene el nombre especificado para el recurso cuando se creó |
| N/D |Etiquetas |***Nueva adición de columna.***  Los nuevos tipos de recursos de Azure le permiten etiquetar los recursos. Consulte [Organize your Azure resources with tags](http://azure.microsoft.com/updates/organize-your-azure-resources-with-tags/) |
| Información adicional |Información adicional |Metadatos adicionales relacionados con el servicio. |
| Información de servicio 1 |Información de servicio 1 |Esta columna proporciona el nombre del proyecto al que pertenece el servicio en la suscripción. |
| Información de servicio 2 |Información de servicio 2 |Se trata de un campo heredado que captura los metadatos específicos del servicio opcional. |

Además de algunos campos nuevos y cambios de nombres en la versión 2 de csv, habrá formatos estandarizados para los datos en los campos siguientes:

* **Id. de instancia**: este campo representa el identificador especificado por el usuario para el servicio de aprovisionamiento. Actualmente, existen dos formatos en los que está representado el id. de instancia: el nombre del recurso o el id. de recurso completo. Los servicios de Microsoft Azure están realizando la transición para representar el identificador de instancia en un formato de identificador de recurso completo estandarizado ***(/subscriptions/<subscription id>/resourcegroups/<resourcegroupname>/providers/<providername>/<resourcename>)***. Al realizar los servicios la transición al nuevo formato, verá el campo de datos de Id. de instancia cambiar desde el nombre del recurso al Id. de recurso. El identificador de recurso es el formato que usa la [API de Azure Resource Manager](https://msdn.microsoft.com/library/azure/dn790567.aspx) para identificar los recursos de una suscripción.

![InstanceId](./media/billing-understand-your-bill/instanceid.png)

* **Información adicional**: la columna Información adicional del .csv de uso especifica metadatos específicos del servicio. Por ejemplo, un tipo de imagen de una máquina virtual. Actualmente, un servicio emite metadatos específicos del servicio en varias columnas: campos Información adicional, Información de servicio 1 e Información de servicio 2. Los servicios de Microsoft Azure estandarizarán la emisión de metadatos específicos del servicio solo en la columna Información adicional.  Vea la siguiente instantánea del formato estandarizado:

![additionalinfo_csv2](./media/billing-understand-your-bill/AdditionaInfo_csv2.png)

* **Etiquetas**: esta columna contiene las etiquetas de recursos especificadas por el usuario. Las etiquetas se pueden utilizar para agrupar los registros de facturación. Por ejemplo, puede utilizar etiquetas para distribuir los costos por departamento mediante el servicio. Más información sobre el [uso de etiquetas para organizar los recursos de Azure](../resource-group-using-tags.md). Los servicios que admiten la emisión de etiquetas son:  
  
  * Máquinas virtuales
  * Almacenamiento y
  * servicios de redes aprovisionados con la [API de Administrador de recursos de Azure](https://msdn.microsoft.com/library/azure/dn790567.aspx)

![Etiquetas](./media/billing-understand-your-bill/tags.png)

## <a name="next-steps"></a>Pasos siguientes
* [Configurar alertas de facturación](../billing-set-up-alerts.md)
* [Administrar los métodos de pago](../billing-how-to-change-credit-card.md)
* [Descripción de los gastos de Azure Marketplace](../billing-understand-your-azure-marketplace-charges.md)
* [Preguntas más frecuentes sobre suscripciones y facturación de Azure ](../billing-subscription-faq.md)

> [!NOTE]
> Si tiene más preguntas, [póngase en contacto con el soporte técnico](https://portal.azure.com/?#blade/Microsoft_Azure_Support/HelpAndSupportBlade) para que resuelvan el problema rápidamente.
> 
> 

<!--
OLD MSDN Articles
- [What do I do if my Azure subscription become disabled?](https://msdn.microsoft.com/library/azure/dn736049.aspx)
- [Edit payment information for an existing credit card](https://msdn.microsoft.com/library/azure/dn736053.aspx)
- [Add a new credit card to use as a payment method](https://msdn.microsoft.com/library/azure/dn736057.aspx)
- [Change the credit card on your Microsoft Azure account](https://msdn.microsoft.com/library/azure/dn736050.aspx)
- [Manage your payment method](https://msdn.microsoft.com/library/azure/dn736054.aspx)
-->



<!--Image references-->



<!--HONumber=Nov16_HO3-->


