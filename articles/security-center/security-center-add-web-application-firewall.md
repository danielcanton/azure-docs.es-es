---
title: "Adición de un firewall de aplicaciones web en Azure Security Center | Microsoft Docs"
description: "En este documento se muestra cómo implementar las recomendaciones de agregar un firewall de aplicaciones web y de finalizar la protección de la aplicación de Azure Security Center."
services: security-center
documentationcenter: na
author: TerryLanfear
manager: MBaldwin
editor: 
ms.assetid: 8f56139a-4466-48ac-90fb-86d002cf8242
ms.service: security-center
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/01/2016
ms.author: terrylan
translationtype: Human Translation
ms.sourcegitcommit: 2ea002938d69ad34aff421fa0eb753e449724a8f
ms.openlocfilehash: 8d7034d296804ceeb0580eb80569b86fcf152db6


---
# <a name="add-a-web-application-firewall-in-azure-security-center"></a>Adición de un firewall de aplicaciones web en el Centro de seguridad de Azure
El Centro de seguridad de Azure puede recomendarle agregar Firewall de aplicaciones web (WAF) de un partner de Microsoft para proteger las aplicaciones web. Este documento le ofrece un ejemplo de cómo hacerlo:

> [!NOTE]
> En este documento se presenta el servicio mediante una implementación de ejemplo.  No se trata de una guía paso a paso.
> 
> 

## <a name="implement-the-recommendation"></a>Implementación de la recomendación
1. En la hoja **Recomendaciones**, seleccione **Secure web application using web application firewall** (Proteger la aplicación web con el firewall de aplicaciones web).
   ![Aplicación web segura][1]
2. En la hoja **Proteger la aplicación web con Firewall de aplicaciones web** , seleccione una aplicación web. Se abre la hoja **Add a Web Application Firewall** (Agregar un Firewall de aplicaciones web).
   ![Add a web application firewall][2]
3. Puede elegir usar un firewall de aplicaciones web existentes, si está disponible, o puede crear uno nuevo. En este ejemplo no hay ningún WAF existente, por lo que vamos a crear uno nuevo.
4. Para crear un nuevo WAF, seleccione una solución de la lista de partners integrados. En ese ejemplo, seleccionaremos **Firewall de aplicaciones web de Barracuda**.
5. Se abrirá la hoja **Firewall de aplicaciones web de Barracuda** , que le proporcionará información sobre la solución del partner. Seleccione **Crear** en la hoja de información.
   ![Hoja de información del firewall][3]
6. Se abrirá la hoja **Nuevo firewall de aplicaciones web** donde puede **configurar la máquina virtual** y proporcionar **información sobre WAF**. Seleccione **Configuración de VM**.
7. En la hoja **Configuración de VM** , se ingresa la información requerida para poner en marcha la máquina virtual que ejecutará el WAF.
   ![VM configuration][4]
8. Vuelva a la hoja **Nuevo firewall de aplicaciones web** y seleccione **Información del WAF**. En la hoja **Información de WAF** , configure el WAF. El paso 7 le permite configurar la máquina virtual en que se ejecutará el WAF y el paso 8 le permite aprovisionar el WAF.

## <a name="finalize-application-protection"></a>Finalización de la protección de la aplicación
1. Vuelva a la hoja **Recomendaciones** . Después de crear el WAF, se generó una entrada nueva, denominada **Finalize application protection**(Finalizar la protección de la aplicación). Dicha le permite saber qué se necesita para completar el proceso de conectar el WAF dentro de la Red virtual de Azure, con el fin de que pueda proteger la aplicación.
   ![Finalización de la protección de la aplicación][5]
2. Seleccione **Finalize application protection**(Finalizar la protección de la aplicación).. Se abre una nueva hoja. En ella puede ver que hay una aplicación web que necesita que su tráfico se vuelva a enrutar.
3. Seleccione la aplicación web. Se abre una hoja en la que encontrará los pasos necesarios para finalizar la configuración del Firewall de aplicaciones web. Complete los pasos y, a continuación, seleccione la opción de **restringir tráfico**. Después, el Security Center realizará las conexiones automáticamente.
   ![restringir tráfico][6]

> [!NOTE]
> Puede proteger varias aplicaciones web del Centro de seguridad si agrega estas aplicaciones a las implementaciones de WAF existentes. Los dispositivos WAF (creados mediante el modelo de implementación de Resource Manager) deben implementarse en una red virtual independiente. Los dispositivos WAF (creados mediante el modelo de implementación clásica) están limitados a usar un grupo de seguridad de red. Esta compatibilidad se extenderá a una implementación completamente personalizada de dispositivos WAF (clásica) en el futuro. Obtenga más información sobre los [modelos de implementación clásico y de Resource Manager](../azure-classic-rm.md) para los recursos de Azure.
> 
> 

Los registros de ese WAF ahora están totalmente integrados. El Centro de seguridad puede comenzar a recopilar y analizar automáticamente los registros, con el fin de poder exponer las alertas de seguridad importantes.

## <a name="see-also"></a>Consulte también
En este documento, mostramos cómo implementar la recomendación "Adición de una aplicación web" del Centro de seguridad. Para obtener más información sobre cómo configurar un firewall de aplicaciones web, vea lo siguiente:

* [Configuración de un firewall de aplicaciones web (WAF) para entornos del Servicio de aplicaciones](../app-service-web/app-service-app-service-environment-web-application-firewall.md)

Para más información sobre el Centro de seguridad, consulte los siguientes recursos:

* [Establecimiento de directivas de seguridad en Azure Security Center](security-center-policies.md) : aprenda a configurar directivas de seguridad para las suscripciones y los grupos de recursos de Azure.
* [Supervisión del estado de seguridad en Azure Security Center](security-center-monitoring.md) : obtenga información sobre cómo supervisar el mantenimiento de los recursos de Azure.
* [Administración y respuesta a las alertas de seguridad en Azure Security Center](security-center-managing-and-responding-alerts.md) : aprenda a administrar y responder a alertas de seguridad.
* [Administración de recomendaciones de seguridad en Azure Security Center](security-center-recommendations.md) : recomendaciones que le ayudan a proteger los recursos de Azure.
* [Preguntas más frecuentes sobre Azure Security Center](security-center-faq.md) : encuentre las preguntas más frecuentes sobre el uso del servicio.
* [Blog de seguridad de Azure](http://blogs.msdn.com/b/azuresecurity/) : encuentre publicaciones de blog sobre el cumplimiento y la seguridad de Azure.

<!--Image references-->
[1]: ./media/security-center-add-web-application-firewall/secure-web-application.png
[2]:./media/security-center-add-web-application-firewall/add-a-waf.png
[3]: ./media/security-center-add-web-application-firewall/info-blade.png
[4]: ./media/security-center-add-web-application-firewall/select-vm-config.png
[5]: ./media/security-center-add-web-application-firewall/finalize-waf.png
[6]: ./media/security-center-add-web-application-firewall/restrict-traffic.png



<!--HONumber=Nov16_HO3-->


