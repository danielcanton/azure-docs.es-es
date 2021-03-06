---
title: Informes de Azure Multi-Factor Authentication
description: "Aquí se describe cómo utilizar la característica de informes de Azure Multi-Factor Authentication."
services: multi-factor-authentication
documentationcenter: 
author: kgremban
manager: femila
editor: curtand
ms.assetid: 3f6b33c4-04c8-47d4-aecb-aa39a61c4189
ms.service: multi-factor-authentication
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 08/04/2016
ms.author: kgremban
translationtype: Human Translation
ms.sourcegitcommit: 2ea002938d69ad34aff421fa0eb753e449724a8f
ms.openlocfilehash: 738f9862ce8a8e4a0d63ec94583c4c868d914686


---
# <a name="reports-in-azure-multi-factor-authentication"></a>Informes en Azure Multi-Factor Authentication
Azure Multi-Factor Authentication proporciona varios tipos de informes que usted o su organización pueden usar. Estos informes son accesibles a través del Portal de administración de Multi-Factor Authentication, lo que requiere disponer de un proveedor de Azure Multi-Factor Authentication o una licencia de Azure Multi-Factor Authentication, Azure AD Premium o Enterprise Mobility Suite. La siguiente es una lista de los informes disponibles.

Acceda a los informes a través del Portal de administración de Azure

| Nombre | Description |
|:--- |:--- |
| Uso |Los informes de uso muestran información sobre el uso general, resúmenes y detalles de usuario. |
| Estado del servidor |Este informe muestra el estado de los Servidores Multi-Factor Authentication asociados a su cuenta. |
| Historial de usuarios bloqueados |Estos informes muestran el historial de solicitudes para bloquear o desbloquear a los usuarios. |
| Historial de usuarios omitidos |Muestra el historial de solicitudes para omitir Multi-Factor Authentication para el número de teléfono de un usuario. |
| Alerta de fraude |Muestra un historial de las alertas de fraude enviadas durante el intervalo de fechas especificado. |
| En cola |Enumera los informes en cola para su procesamiento y su estado. Cuando el informe se haya completado, se proporciona un vínculo para descargar o ver el informe. |

## <a name="to-view-reports"></a>Para ver los informes
1. Inicie sesión en http://azure.microsoft.com
2. En la parte izquierda, seleccione Active Directory.
3. Seleccione una de las siguientes opciones:
   * **Opción 1**: haga clic en la pestaña Proveedores de autenticación multifactor. Seleccione el proveedor de autenticación multifactor y haga clic en el botón Administrar de la parte inferior.
   * **Opción 2**: seleccione el directorio y haga clic en la pestaña Configurar. En la sección de autenticación multifactor, seleccione Administrar configuración del servicio. En la parte inferior de la página Configuración del servicio MFA, haga clic en el vínculo Ir al portal.
4. En el Portal de administración de Azure Multi-Factor Authentication, verá la vista de una sección del informe en el panel izquierdo. Desde aquí puede seleccionar los informes que se han descrito anteriormente.

<center>![Nube](./media/multi-factor-authentication-manage-reports/report.png)</center>


**Recursos adicionales**

* [Para los usuarios](end-user/multi-factor-authentication-end-user.md)
* [Azure Multi-Factor Authenticaton en MSDN](https://msdn.microsoft.com/library/azure/dn249471.aspx)




<!--HONumber=Nov16_HO3-->


