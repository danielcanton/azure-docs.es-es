---
title: "Información general de SQL Server en máquinas virtuales de Azure | Microsoft Docs"
description: "Obtenga información sobre cómo ejecutar las ediciones completas de SQL Server en máquinas virtuales de Azure. Obtenga vínculos directos a todas las imágenes de máquinas virtuales de SQL Server y al contenido relacionado."
services: virtual-machines-windows
documentationcenter: 
author: rothja
manager: jhubbard
editor: 
tags: azure-service-management
ms.assetid: c505089e-6bbf-4d14-af0e-dd39a1872767
ms.service: virtual-machines-windows
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: vm-windows-sql-server
ms.workload: infrastructure-services
ms.date: 12/01/2016
ms.author: jroth
translationtype: Human Translation
ms.sourcegitcommit: bef7de37e358b49c77a4774e3e90a5e1de273310
ms.openlocfilehash: 5c9cbe96b92546e802190879919602da8687542f


---
# <a name="overview-of-sql-server-on-azure-virtual-machines"></a>Información general de SQL Server en máquinas virtuales de Azure
Este tema describe las opciones para ejecutar SQL Server en máquinas virtuales de Azure (VM), junto con [vínculos a imágenes del portal](#option-1-create-a-sql-vm-with-per-minute-licensing) e información general sobre las [tareas comunes](#manage-your-sql-vm).

> [!NOTE]
> Si ya está familiarizado con SQL Server y solo desea ver cómo implementar una máquina virtual de SQL Server, consulte [Aprovisionamiento de una máquina virtual de SQL Server en Azure Portal](virtual-machines-windows-portal-sql-server-provision.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).
> 
> 

## <a name="overview"></a>Información general
Si es un administrador de base de datos o un desarrollador, las máquinas virtuales de Azure le proporcionan una manera de mover las cargas de trabajo y las aplicaciones de SQL Server local a la nube. El vídeo siguiente proporciona una introducción técnica a las máquinas virtuales de Azure de SQL Server.

> [!VIDEO https://channel9.msdn.com/Events/DataDriven/SQLServer2016/Azure-VM-is-the-best-platform-for-SQL-Server-2016/player]
> 
> 

El vídeo trata las áreas siguientes:

| Hora | Ámbito |
| --- | --- |
| 00:21 |¿Qué son las máquinas virtuales de Azure? |
| 01:45 |Seguridad |
| 02:50 |Conectividad |
| 03:30 |Rendimiento y confiabilidad del almacenamiento |
| 05:20 |Tamaños de VM |
| 05:54 |Alta disponibilidad y Acuerdo de Nivel de Servicio |
| 07:30 |Compatibilidad de configuración |
| 08:00 |Supervisión |
| 08:32 |Demostración: Creación de una máquina virtual de SQL Server 2016 |

> [!NOTE]
> El vídeo se centra en SQL Server 2016, pero Azure proporciona imágenes de máquinas virtuales para muchas versiones de SQL Server, incluidas la 2008, 2012, 2014 y 2016. 
> 
> 

## <a name="scenarios"></a>Escenarios
Hay muchas razones por las que puede decidir alojar los datos en Azure. Si la aplicación se traslada a Azure, mejorará el rendimiento si también mueve los datos. Pero hay otras ventajas. Tendrá acceso automático a varios centros de datos para una recuperación ante desastres y una presencia global. Datos muy protegidos y duraderos.

La ejecución de SQL Server en una máquina virtual de Azure es una opción para el almacenamiento de datos relacionales en Azure. Esta es una buena opción para varios escenarios. Por ejemplo, puede que desee configurar la máquina virtual de Azure de una forma lo más parecida posible a un equipo con SQL Server local. O puede que desee ejecutar aplicaciones y servicios adicionales en el mismo servidor de la base de datos. Hay dos recursos principales que pueden ayudarle a plantearse aún más escenarios y consideraciones:

* [SQL Server en Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/sql-server/) proporciona una visión general de los mejores escenarios para utilizar SQL Server en máquinas virtuales de Azure. 
* [Selección de una opción de SQL Server en la nube: Azure SQL (PaaS) Database o SQL Server en máquinas virtuales de Azure (IaaS)](../sql-database/sql-database-paas-vs-sql-server-iaas.md) proporciona una comparación detallada entre la ejecución de SQL Database y SQL Server en una máquina virtual.

## <a name="create-a-new-sql-vm"></a>Creación de una máquina virtual de SQL
Las secciones siguientes proporcionan vínculos directos a Azure Portal para las imágenes de la galería de máquinas virtuales de SQL Server. Dependiendo de la imagen que seleccione, podrá pagar los costos de licencias de SQL Server por minuto o aportar su propia licencia (BYOL).

Para obtener instrucciones detalladas sobre este proceso, consulte el tutorial [Aprovisionamiento de una máquina virtual de SQL Server en Azure Portal](virtual-machines-windows-portal-sql-server-provision.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json). Además, revise [Procedimientos recomendados de rendimiento para máquinas virtuales de SQL Server](virtual-machines-windows-sql-performance.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json), que explica cómo seleccionar el tamaño de máquina adecuado y otras características disponibles durante el aprovisionamiento.

## <a name="option-1-create-a-sql-vm-with-per-minute-licensing"></a>Opción 1: Crear una VM de SQL con licencias por minuto
En la tabla siguiente se ofrece una matriz de imágenes de SQL Server disponibles en la galería de máquinas virtuales. Haga clic en cualquier vínculo para empezar a crear una nueva máquina virtual de SQL con la versión, la edición y el sistema operativo que especifique.

| Versión | Sistema operativo | Edition |
| --- | --- | --- |
| **SQL 2016** |Windows Server 2012 R2 |[Enterprise](https://portal.azure.com/#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2), [Standard](https://portal.azure.com/#create/Microsoft.SQLServer2016RTMStandardWindowsServer2012R2), [Web](https://portal.azure.com/#create/Microsoft.SQLServer2016RTMWebWindowsServer2012R2), [Dev](https://portal.azure.com/#create/Microsoft.SQLServer2016RTMDeveloperWindowsServer2012R2), [Express](https://portal.azure.com/#create/Microsoft.SQLServer2016RTMExpressWindowsServer2012R2) |
| **SQL 2014 SP1** |Windows Server 2012 R2 |[Enterprise](https://portal.azure.com/#create/Microsoft.SQLServer2014SP1EnterpriseWindowsServer2012R2), [Standard](https://portal.azure.com/#create/Microsoft.SQLServer2014SP1StandardWindowsServer2012R2), [Web](https://portal.azure.com/#create/Microsoft.SQLServer2014SP1WebWindowsServer2012R2), [Express](https://portal.azure.com/#create/Microsoft.SQLServer2014SP1ExpressWindowsServer2012R2) |
| **SQL 2014** |Windows Server 2012 R2 |[Enterprise](https://portal.azure.com/#create/Microsoft.SQLServer2014EnterpriseWindowsServer2012R2), [Standard](https://portal.azure.com/#create/Microsoft.SQLServer2014StandardWindowsServer2012R2), [Web](https://portal.azure.com/#create/Microsoft.SQLServer2014WebWindowsServer2012R2) |
| **SQL 2012 SP3** |Windows Server 2012 R2 |[Enterprise](https://portal.azure.com/#create/Microsoft.SQLServer2012SP3EnterpriseWindowsServer2012R2), [Standard](https://portal.azure.com/#create/Microsoft.SQLServer2012SP3StandardWindowsServer2012R2), [Web](https://portal.azure.com/#create/Microsoft.SQLServer2012SP3WebWindowsServer2012R2), [Express](https://portal.azure.com/#create/Microsoft.SQLServer2012SP3ExpressWindowsServer2012R2) |
| **SQL 2012 SP2** |Windows Server 2012 R2 |[Enterprise](https://portal.azure.com/#create/Microsoft.SQLServer2012SP2EnterpriseWindowsServer2012R2), [Standard](https://portal.azure.com/#create/Microsoft.SQLServer2012SP2StandardWindowsServer2012R2), [Web](https://portal.azure.com/#create/Microsoft.SQLServer2012SP2WebWindowsServer2012R2) |
| **SQL 2012 SP2** |Windows Server 2012 |[Enterprise](https://portal.azure.com/#create/Microsoft.SQLServer2012SP2EnterpriseWindowsServer2012), [Standard](https://portal.azure.com/#create/Microsoft.SQLServer2012SP2StandardWindowsServer2012), [Web](https://portal.azure.com/#create/Microsoft.SQLServer2012SP2WebWindowsServer2012), [Express](https://portal.azure.com/#create/Microsoft.SQLServer2012SP2ExpressWindowsServer2012) |
| **SQL 2008 R2 SP3** |Windows Server 2008 R2 |[Enterprise](https://portal.azure.com/#create/Microsoft.SQLServer2008R2SP3EnterpriseWindowsServer2008R2), [Standard](https://portal.azure.com/#create/Microsoft.SQLServer2008R2SP3StandardWindowsServer2008R2), [Web](https://portal.azure.com/#create/Microsoft.SQLServer2008R2SP3WebWindowsServer2008R2) |
| **SQL 2008 R2 SP3** |Windows Server 2012 |[Express](https://portal.azure.com/#create/Microsoft.SQLServer2008R2SP3ExpressWindowsServer2012) |

## <a name="a-idbyola-option-2-create-a-sql-vm-with-an-existing-license"></a><a id="BYOL"></a> Opción 2: Crear una VM de SQL con una licencia ya existente
También puede traer su propia licencia (BYOL). En este escenario, solo paga por la máquina virtual sin ningún cargo adicional de licencia de SQL Server. Para utilizar su propia licencia, use la matriz de los sistemas operativos, ediciones y versiones de SQL Server que puede ver a continuación. En el portal, los nombres de las imágenes van precedidos de **{BYOL}**.

| Versión | Sistema operativos | Edition |
| --- | --- | --- |
| **SQL Server 2016** |Windows Server 2012 R2 |[Enterprise BYOL](https://portal.azure.com/#create/Microsoft.BYOLSQLServer2016RTMStandardWindowsServer2012R2), [Standard BYOL](https://portal.azure.com/#create/Microsoft.BYOLSQLServer2016RTMStandardWindowsServer2012R2) |
| **SQL Server 2014 SP1** |Windows Server 2012 R2 |[Enterprise BYOL](https://portal.azure.com/#create/Microsoft.BYOLSQLServer2014SP1EnterpriseWindowsServer2012R2), [Standard BYOL](https://portal.azure.com/#create/Microsoft.BYOLSQLServer2014SP1StandardWindowsServer2012R2) |
| **SQL Server 2012 SP2** |Windows Server 2012 R2 |[Enterprise BYOL](https://portal.azure.com/#create/Microsoft.BYOLSQLServer2012SP3EnterpriseWindowsServer2012R2), [Standard BYOL](https://portal.azure.com/#create/Microsoft.BYOLSQLServer2012SP3StandardWindowsServer2012R2) |

> [!IMPORTANT]
> Para poder utilizar imágenes de máquina virtual BYOL, tiene que tener un Contrato Enterprise con [Movilidad de Licencias a través de Software Assurance en Azure](https://azure.microsoft.com/pricing/license-mobility/). También necesita una licencia válida para la versión y edición de SQL Server que desea utilizar. Tiene que [proporcionar la información necesaria de BYOL a Microsoft](http://d36cz9buwru1tt.cloudfront.net/License_Mobility_Customer_Verification_Guide.pdf) dentro de un plazo de **10** días a partir del aprovisionamiento de la máquina virtual.
> 

> [!NOTE]
> No es posible cambiar el modelo de licencias de una máquina virtual con SQL Server de pago por minuto para usar su propia licencia. En este caso, debe crear una nueva máquina virtual BYOL y migrar las bases de datos a ella. 

## <a name="manage-your-sql-vm"></a>Administración de la máquina virtual de SQL
Después de aprovisionar la máquina virtual de SQL Server, hay varias tareas de administración opcionales. En muchos aspectos, SQL Server se configura y se administra exactamente igual que si se tratara de una instancia local. Sin embargo, algunas tareas son específicas de Azure. Las secciones siguientes resaltan algunas de estas áreas con vínculos a más información.

### <a name="connect-to-the-vm"></a>Conexión a la máquina virtual
Uno de los pasos más básicos de administración consiste en conectarse a la máquina virtual de SQL Server a través de herramientas, como SQL Server Management Studio (SSMS). Para obtener instrucciones sobre cómo conectarse a la nueva máquina virtual de SQL Server, consulte [Conexión a una máquina virtual de SQL Server en Azure](virtual-machines-windows-sql-connect.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).

### <a name="migrate-your-data"></a>Migración de los datos
Si tiene una base de datos existente, debe moverla a la máquina virtual de SQL recién aprovisionada. Para ver una lista de las opciones de migración e instrucciones, consulte [Migración de una Base de datos SQL Server a SQL Server en una máquina virtual de Azure](virtual-machines-windows-migrate-sql.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).

### <a name="configure-high-availability"></a>Configuración para alta disponibilidad
Si requiere alta disponibilidad, considere la posibilidad de configurar grupos de disponibilidad de SQL Server. Esto implica varias máquinas virtuales de Azure en una red virtual. El Portal de Azure dispone de una plantilla que define esta configuración. Para más información, consulte [Configuración de un grupo de disponibilidad AlwaysOn en máquinas virtuales de Azure Resource Manager](virtual-machines-windows-portal-sql-alwayson-availability-groups.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json). Si desea configurar manualmente el grupo de disponibilidad y el agente de escucha asociado, consulte [Configuración de un grupo de disponibilidad AlwaysOn en máquinas virtuales de Azure Resource Manager (GUI)](virtual-machines-windows-portal-sql-alwayson-availability-groups-manual.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).

Para otras consideraciones sobre alta disponibilidad, consulte [Alta disponibilidad y recuperación ante desastres para SQL Server en Máquinas virtuales de Azure](virtual-machines-windows-sql-high-availability-dr.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).

### <a name="back-up-your-data"></a>Realización de una copia de seguridad de los datos
Las máquinas virtuales de Azure pueden aprovechar la [Copia de seguridad automatizada](virtual-machines-windows-sql-automated-backup.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json), que crea de forma regular copias de seguridad de la base de datos en el almacenamiento de blobs. También puede utilizar esta técnica manualmente. Para más información, consulte [Uso de Almacenamiento de Azure para la copia de seguridad y la restauración de SQL Server](virtual-machines-windows-use-storage-sql-server-backup-restore.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json). Para obtener información general sobre las opciones de copia de seguridad y restauración, consulte [Copias de seguridad y restauración para SQL Server en máquinas virtuales de Azure](virtual-machines-windows-sql-backup-recovery.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).

### <a name="automate-updates"></a>Automatización de las actualizaciones
Las máquinas virtuales de Azure pueden usar las [revisiones automatizadas](virtual-machines-windows-sql-automated-patching.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json) para programar una ventana de mantenimiento para la instalación automática de actualizaciones de SQL Server y Windows.

### <a name="customer-experience-improvement-program-ceip"></a>Programa para la mejora de la experiencia del usuario (CEIP)
De manera predeterminada, el Programa para la mejora de la experiencia del cliente (CEIP) está habilitado. Esto permitirá enviar periódicamente informes a Microsoft para ayudar a mejorar SQL Server. No hay ninguna tarea de administración requerida relacionada con el CEIP, a menos que desee deshabilitarlo después del aprovisionamiento. Puede personalizar o deshabilitar el CEIP mediante la conexión a la máquina virtual a través del escritorio remoto. A continuación, ejecute la utilidad **Informes de uso y errores de SQL Server** . Siga las instrucciones para deshabilitar los informes. 

Para más información, consulte la sección CEIP del tema [Aceptar los términos de licencia](https://msdn.microsoft.com/library/ms143343.aspx). 

## <a name="next-steps"></a>Pasos siguientes
[Explore la ruta de aprendizaje](https://azure.microsoft.com/documentation/learning-paths/sql-azure-vm/) para SQL Server en máquinas virtuales de Azure.

¿Más preguntas? En primer lugar, consulte las [Preguntas más frecuentes sobre SQL Server en máquinas virtuales de Azure](virtual-machines-windows-sql-server-iaas-faq.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json). Pero también agregue sus preguntas o comentarios en la parte inferior de cualquiera de los temas de las máquinas virtuales de SQL para interactuar con Microsoft y la comunidad.




<!--HONumber=Dec16_HO1-->


