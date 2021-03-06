---
title: "Información general sobre la arquitectura de red de los entornos del Servicio de aplicaciones"
description: "Introducción a la arquitectura de la topología de red de los entornos del Servicio de aplicaciones."
services: app-service
documentationcenter: 
author: stefsch
manager: wpickett
editor: 
ms.assetid: 13d03a37-1fe2-4e3e-9d57-46dfb330ba52
ms.service: app-service
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 10/04/2016
ms.author: stefsch
translationtype: Human Translation
ms.sourcegitcommit: 2ea002938d69ad34aff421fa0eb753e449724a8f
ms.openlocfilehash: 4a5fdbc73f5d30c8dacfb8f7039bf70a450ea251


---
# <a name="network-architecture-overview-of-app-service-environments"></a>Información general sobre la arquitectura de red de los entornos del Servicio de aplicaciones
## <a name="introduction"></a>Introducción
Las instancias de siempre se crean dentro de una subred de una [red virtual][virtualnetwork]; las aplicaciones que se ejecutan en App Service Environment pueden comunicarse con puntos de conexión privados ubicados que se encuentran de la misma topología de red virtual.  Puesto que los clientes pueden bloquear partes de su infraestructura de red virtual, es importante conocer los tipos de flujos de comunicación de red que se producen con un entorno del Servicio de aplicaciones.

## <a name="general-network-flow"></a>Flujo de red general
Cuando un entorno del Servicio de aplicaciones (ASE) utiliza una dirección IP virtual pública (VIP) para las aplicaciones, todo el tráfico entrante llega a esa VIP pública,  incluido el tráfico HTTP y HTTPS para las aplicaciones, así como otro tráfico de FTP, la funcionalidad de depuración remota y las operaciones de administración de Azure.  Para obtener una lista completa de los puertos específicos (obligatorios y opcionales) disponibles en la VIP pública, consulte el artículo sobre el [control del tráfico entrante][controllinginboundtraffic] en App Service Environment. 

Los entornos del Servicio de aplicaciones también admiten aplicaciones en ejecución enlazadas únicamente a una dirección de red virtual interna, que también se denomina "dirección del ILB" (equilibrador de carga interno).  En un ASE con un ILB, el tráfico HTTP y HTTPS de las aplicaciones, así como las llamadas de depuración remota, proceden de la dirección del ILB.  En las configuraciones de ASE con un ILB más habituales, el tráfico FTP y FTPS también llegan desde esa dirección.  Sin embargo, las operaciones de administración de Azure seguirán fluyendo a los puertos 454 y 455 en la VIP pública de un ASE con un ILB.

En el diagrama siguiente se muestra información general de los distintos flujos de red entrantes y salientes de un entorno del Servicio de aplicaciones, donde las aplicaciones se enlazan a una dirección IP virtual pública:

![Flujos de red generales][GeneralNetworkFlows]

Un entorno del Servicio de aplicaciones puede comunicarse con una variedad de extremos privados del cliente.  Por ejemplo, las aplicaciones que se ejecutan en el entorno del Servicio de aplicaciones pueden conectarse a servidores de base de datos que se ejecutan en máquinas virtuales de IaaS en la misma topología de red virtual.

> [!IMPORTANT]
> Si examinamos el diagrama de red, la implementación correspondiente a "Otros recursos de proceso" se efectúa en una subred diferente a la del entorno del Servicio de aplicaciones. Al implementar recursos en la misma subred que el entorno del Servicio de aplicaciones (ASE), se bloqueará la conectividad del ASE a esos recursos (excepto para el enrutamiento específico dentro del entorno del Servicio de aplicaciones). Implemente en su lugar en una subred diferente (en la misma red virtual). A continuación, el entorno del Servicio de aplicaciones podrá conectarse. No se necesita ninguna configuración adicional.
> 
> 

Los entornos del Servicio de aplicaciones también se comunican con la base de datos SQL y los recursos del Almacenamiento de Azure necesarios para administrar y operar un entorno del Servicio de aplicaciones.  Algunos recursos de almacenamiento y SQL con los que se comunica un entorno del Servicio de aplicaciones se encuentran en la misma región que el entorno del Servicio de aplicaciones, mientras que otros se encuentran en regiones de Azure remotas.  Como resultado, la conectividad saliente a Internet siempre es necesaria para que un entorno del Servicio de aplicaciones funcione correctamente. 

Puesto que un entorno del Servicio de aplicaciones se implementa en una subred, los grupos de seguridad de red pueden usarse para controlar el tráfico entrante a la subred.  Para obtener información acerca de cómo controlar el tráfico de entrada a App Service Environment, consulte el siguiente [artículo][controllinginboundtraffic].

Para obtener información detallada acerca de cómo permitir la conectividad de salida a Internet desde App Service Environment, consulte el artículo siguiente sobre cómo trabajar con [Express Route][ExpressRoute].  El mismo enfoque que se describe en este artículo se aplica al trabajar con conectividad de sitio a sitio y al usar la tunelización forzada.

## <a name="outbound-network-addresses"></a>Direcciones de red de salida
Cuando un entorno del Servicio de aplicaciones realiza las llamadas salientes, una dirección IP siempre se asocia con las llamadas salientes.  La dirección IP específica que se usa depende de si el extremo al que se llama se encuentra dentro de la topología de red virtual o fuera de ella.

Si el extremo al que se llama está **fuera** de la topología de red virtual, entonces la dirección saliente (también conocida como la dirección NAT saliente) que se utiliza es la VIP pública del entorno del Servicio de aplicaciones.  Esta dirección se encuentra en la interfaz de usuario del portal para el entorno de Servicio de aplicaciones en la hoja Propiedades.

![Dirección IP saliente][OutboundIPAddress]

Esta dirección también se puede determinar para los ASE que solo tienen una VIP pública creando una aplicación en el entorno de Servicio de aplicaciones y, después, realizando una operación *nslookup* en la dirección de la aplicación. La dirección IP resultante es tanto la VIP pública como la dirección NAT saliente del entorno del Servicio de aplicaciones.

Si el extremo al que se llama está **dentro** de la topología de red virtual, la dirección saliente de la aplicación de llamada será la dirección IP interna del recurso de proceso individual que ejecuta la aplicación.  Sin embargo, no hay una asignación persistente de direcciones IP internas de red virtual a las aplicaciones.  Las aplicaciones pueden moverse a través de recursos informáticos diferentes y el grupo de recursos informáticos disponibles en un entorno del Servicio de aplicaciones puede cambiar debido a las operaciones de ajuste de escala.

Sin embargo, puesto que un entorno del Servicio de aplicaciones siempre se encuentra dentro de una subred, se garantiza que la dirección IP interna de un recurso informático que ejecuta una aplicación siempre se queda dentro del intervalo CIDR de la subred.  Como resultado, cuando las ACL específicas o los grupos de seguridad de red se utilizan para proteger el acceso a otros extremos en la red virtual, el intervalo de subred que contiene el entorno del Servicio de aplicaciones necesita tener acceso.

En el diagrama siguiente se explican estos conceptos de manera detallada:

![Direcciones de red de salida][OutboundNetworkAddresses]

En el diagrama anterior:

* Dado que la VIP pública del entorno del Servicio de aplicaciones es 192.23.1.2, que es la dirección IP saliente que se utiliza cuando se realizan llamadas a los extremos de "Internet".
* El intervalo CIDR de la subred que contiene para el entorno del Servicio de aplicaciones es 10.0.1.0/26.  Otros extremos dentro de la misma infraestructura de red virtual verán las llamadas de aplicaciones como originadas en algún lugar dentro de este intervalo de direcciones.

## <a name="calls-between-app-service-environments"></a>Llamadas entre entornos del Servicio de aplicaciones
El escenario puede resultar más complejo si implementa varios entornos del Servicio de aplicaciones en la misma red virtual y realiza llamadas salientes desde un entorno del Servicio de aplicaciones a otro.  Estos tipos de llamadas cruzadas entre entornos del Servicio de aplicaciones también se tratarán como llamadas de "Internet".

En el siguiente diagrama, se muestra un ejemplo de arquitectura en capas con aplicaciones en un entorno de Servicio de aplicaciones (p. ej., aplicaciones web de "entrada principal") que llaman a aplicaciones en un segundo entorno de Servicio de aplicaciones (por ejemplo, aplicaciones de API de back-end internas que no se crearon para que sean accesibles desde Internet). 

![Llamadas entre entornos del Servicio de aplicaciones][CallsBetweenAppServiceEnvironments] 

En el ejemplo anterior, el entorno de Servicio de aplicaciones "ASE One" tiene la dirección IP saliente 192.23.1.2.  Si una aplicación que se ejecuta en este entorno de Servicio de aplicaciones hace una llamada saliente a una aplicación que se ejecuta en un segundo entorno de Servicio de aplicaciones ("ASE Two") ubicado en la misma red virtual, la llamada saliente se tratará como una llamada de "Internet".  Como resultado, el tráfico de red que llega al segundo entorno de Servicio de aplicaciones se mostrará como originado en 192.23.1.2 (es decir, no el intervalo de direcciones de subred del primer entorno de Servicio de aplicaciones).

Aunque las llamadas entre diferentes entornos de Servicio de aplicaciones se tratan como llamadas de "Internet", cuando ambos entornos de Servicio de aplicaciones se encuentran en la misma región de Azure, el tráfico de red permanecerá en la red regional de Azure y no pasará físicamente a través de la Internet pública.  Como resultado, puede usar un grupo de seguridad de red en la subred del segundo entorno de Servicio de aplicaciones para permitir solo las llamadas entrantes desde el primer entorno de Servicio de aplicaciones (cuya dirección IP saliente es 192.23.1.2), lo que garantiza una comunicación segura entre los entornos de Servicio de aplicaciones.

## <a name="additional-links-and-information"></a>Información y vínculos adicionales
Todos los artículos y procedimientos para los entornos del Servicio de aplicaciones están disponibles en el archivo [Léame para entornos del Servicio de aplicaciones](../app-service/app-service-app-service-environments-readme.md).

[Aquí][controllinginboundtraffic] se puede obtener más información acerca de los puertos de entrada que usan las instancias de App Service Environment y del uso de grupos de seguridad de red para controlar el tráfico de entrada.

En este [artículo][ExpressRoute] encontrará información detallada acerca del uso de rutas definidas por el usuario para conceder acceso de salida a Internet a las instancias de App Service Environment. 

<!-- LINKS -->
[virtualnetwork]: http://azure.microsoft.com/services/virtual-network/
[controllinginboundtraffic]:  http://azure.microsoft.com/documentation/articles/app-service-app-service-environment-control-inbound-traffic/
[ExpressRoute]:  http://azure.microsoft.com/documentation/articles/app-service-app-service-environment-network-configuration-expressroute/

<!-- IMAGES -->
[GeneralNetworkFlows]: ./media/app-service-app-service-environment-network-architecture-overview/NetworkOverview-1.png
[OutboundIPAddress]: ./media/app-service-app-service-environment-network-architecture-overview/OutboundIPAddress-1.png
[OutboundNetworkAddresses]: ./media/app-service-app-service-environment-network-architecture-overview/OutboundNetworkAddresses-1.png
[CallsBetweenAppServiceEnvironments]: ./media/app-service-app-service-environment-network-architecture-overview/CallsBetweenEnvironments-1.png




<!--HONumber=Nov16_HO3-->


