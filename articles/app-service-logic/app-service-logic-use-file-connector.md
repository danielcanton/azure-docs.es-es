---
title: Uso del conector del sistema de archivos con la puerta de enlace de datos local en Logic Apps | Microsoft Docs
description: "Logic Apps le permite conectarse fácilmente al sistema de archivos local como parte del flujo de trabajo."
services: logic-apps
documentationcenter: dev-center-name
author: derek1ee
manager: erikre
ms.service: logic-apps
ms.devlang: wdl
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/15/2016
ms.author: deli
translationtype: Human Translation
ms.sourcegitcommit: 9b2ae8a06cfa0cf686b7cae50d3b6903e536ee73
ms.openlocfilehash: fc81b6ca60af48ddfd8862d5f6620db537646ae7


---
# <a name="use-file-system-connector-with-on-premises-data-gateway"></a>Uso del conector del sistema de archivos con la puerta de enlace de datos local en Logic Apps

La conectividad de nube híbrida es la esencia de Logic Apps. La puerta de enlace de datos local le permite administrar los datos y acceder de manera segura a los recursos locales de Logic Apps. En este artículo, mostraremos cómo conectarse a un sistema de archivos local con un escenario muy sencillo: copiar un archivo que se carga en Dropbox para un recurso compartido de archivos y, después, enviar un correo electrónico.

## <a name="prerequisites"></a>Requisitos previos
- Instale y configure la [puerta de enlace de datos local](https://www.microsoft.com/en-us/download/details.aspx?id=53127) más reciente.

 Instale la puerta de enlace de datos local más reciente, versión 1.15.6150.1 o superior, si no la tiene. Se puede encontrar instrucciones [en este artículo](http://aka.ms/logicapps-gateway). La puerta de enlace debe instalarse en una máquina local para poder continuar con el resto de los pasos.

## <a name="use-file-system-connector"></a>Uso del conector de sistema de archivos

1. Vamos a crear un desencadenador "Cuando se crea un archivo" de Dropbox y, después, tener una visión general de la acción del conector de archivos es tan sencillo como escribir "Sistema de archivos" en la búsqueda.

 ![Conector Buscar archivo](./media/app-service-logic-use-file-connector/search-file-connector.png)

2. Elija "Crear archivo" y crear una conexión para él.
 - Si no tiene una conexión existente, se le pedirá que cree una.
 - Seleccione la opción "Conectar a través de la puerta de enlace de datos local", verá que se muestran campos adicionales cuando se activa la casilla.
 - Especifique la carpeta raíz; puede ser una carpeta local en la máquina en la que está instalada la puerta de enlace de datos local o un recurso compartido de red al que tiene acceso la máquina.
 - Escriba el nombre de usuario y la contraseña en la puerta de enlace.
 - Seleccione la puerta de enlace que se ha instalado en el paso anterior.
    
 > [!NOTE]
 > La carpeta raíz es la carpeta primaria principal, que se usará para las rutas de acceso relativas para todas las acciones relacionadas con archivos.

 ![Configuración de la conexión](./media/app-service-logic-use-file-connector/create-file.png)

3. Una vez proporcionados todos los detalles, haga clic en "Crear". Logic Apps configurará y probará la conexión para asegurarse de que funciona correctamente. Si todo se extrae del repositorio, verá opciones para la tarjeta que seleccionó anteriormente y el conector de archivos ahora está listo para su uso.

4. Ponga el archivo cargado en Dropbox y cópielo en la carpeta raíz del recurso compartido de archivos local.

 ![Acción Crear archivo](./media/app-service-logic-use-file-connector/create-file-filled.png)

5. Una vez copiado el archivo, vamos a enviar un correo electrónico para que los usuarios correspondientes lo sepan. Al igual que otros conectores, la salida de acciones anteriores estará disponible en el selector de "contenido dinámico".
 - Especifique los destinatarios, el título y el cuerpo del correo electrónico. Utilice el selector de "contenido dinámico" para elegir la salida del conector de archivos para que el correo electrónico sea más completo.

 ![Acción Enviar correo electrónico](./media/app-service-logic-use-file-connector/send-email.png)

6. Guarde la aplicación lógica y pruébela al cargar archivos en Dropbox. Debe ver que el archivo se ha copiado en el recurso compartido de archivos local y que recibe una notificación por correo electrónico sobre la operación.
 > [!TIP]
 > Consulte cómo [supervisar las aplicaciones lógicas](app-service-logic-monitor-your-logic-apps.md).

7. Cuando todo haya acabado, tendrá una aplicación lógica en funcionamiento con el conector de sistema de archivos. Puede empezar a explorar las otras funcionalidades que ofrece:
    - Crear archivo
    - Enumerar archivos de la carpeta
    - Anexar archivo
    - Eliminar archivo
    - Obtener contenido de archivo
    - Obtener contenido de archivo mediante la ruta de acceso
    - Obtener metadatos de archivo
    - Obtener metadatos de archivo mediante la ruta de acceso
    - Enumerar archivos de la carpeta raíz
    - Actualizar archivo

## <a name="next-steps"></a>Pasos siguientes
- Información sobre [Enterprise Integration Pack](app-service-logic-enterprise-integration-overview.md). 
- Cree una [conexión local](app-service-logic-gateway-connection.md) a Logic Apps.



<!--HONumber=Nov16_HO3-->


