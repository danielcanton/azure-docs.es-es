---
title: "Creación de un centro de IoT Hub con una plantilla de Azure Resource Manager y PowerShell | Microsoft Docs"
description: Siga este tutorial para empezar a usar las plantillas de Azure Resource Manager para crear un IoT Hub con PowerShell.
services: iot-hub
documentationcenter: .net
author: dominicbetts
manager: timlt
editor: 
ms.assetid: 7eade855-c289-4ffb-b5ef-02be8c5f670f
ms.service: iot-hub
ms.devlang: multiple
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/07/2016
ms.author: dobett
translationtype: Human Translation
ms.sourcegitcommit: 00746fa67292fa6858980e364c88921d60b29460
ms.openlocfilehash: cbd9c2a5d3e3f03fd9136feb35a82be0cd1ee420


---
# <a name="create-an-iot-hub-using-powershell"></a>Creación de un Centro de IoT con Powershell
[!INCLUDE [iot-hub-resource-manager-selector](../../includes/iot-hub-resource-manager-selector.md)]

## <a name="introduction"></a>Introducción
Puede usar el Administrador de recursos de Azure para crear y administrar los centros de IoT de Azure mediante programación. En este tutorial se muestra cómo usar una plantilla de Azure Resource Manager para crear un IoT Hub con PowerShell.

> [!NOTE]
> Azure tiene dos modelos de implementación diferentes para crear y trabajar con recursos: [Azure Resource Manager y clásico](../azure-resource-manager/resource-manager-deployment-model.md).  Este artículo trata sobre el uso del modelo de implementación de Azure Resource Manager.
> 
> 

Para completar este tutorial, necesitará lo siguiente:

* Una cuenta de Azure activa. <br/>Si no tiene ninguna, puede crear una [cuenta gratuita][lnk-free-trial] en tan solo unos minutos.
* [Microsoft Azure PowerShell 1.0][lnk-powershell-install] o versiones posteriores.

> [!TIP]
> El artículo [Using Azure PowerShell with Azure Resource Manager][lnk-powershell-arm] (Uso de Azure PowerShell con Azure Resource Manager) contiene más información sobre cómo utilizar scripts de PowerShell y plantillas de Azure Resource Manager para crear recursos de Azure. 
> 
> 

## <a name="connect-to-your-azure-subscription"></a>Conexión a su suscripción de Azure
En un símbolo del sistema de PowerShell, escriba el siguiente comando para iniciar sesión en su suscripción de Azure:

```
Login-AzureRmAccount
```

Puede usar los comandos siguientes para conocer donde puede implementar un Centro de IoT y las versiones de API admitidas actualmente:

```
((Get-AzureRmResourceProvider -ProviderNamespace Microsoft.Devices).ResourceTypes | Where-Object ResourceTypeName -eq IoTHubs).Locations
((Get-AzureRmResourceProvider -ProviderNamespace Microsoft.Devices).ResourceTypes | Where-Object ResourceTypeName -eq IoTHubs).ApiVersions
```

Cree un grupo de recursos para que contenga su Centro de IoT mediante el siguiente comando en una de las ubicaciones compatibles para el Centro de IoT. En este ejemplo se crea un grupo de recursos denominado **MyIoTRG1**:

```
New-AzureRmResourceGroup -Name MyIoTRG1 -Location "East US"
```

## <a name="submit-an-azure-resource-manager-template-to-create-an-iot-hub"></a>Enviar una plantilla de Azure Resource Manager para crear IoT Hub
Use una plantilla de JSON para crear un nuevo centro de IoT en el grupo de recursos. También puede usar una plantilla de Azure Resource Manager para realizar cambios en un IoT Hub existente.

1. Use un editor de texto para crear una plantilla de Azure Resource Manager llamada **template.json** , con la siguiente definición de recursos, para crear un nuevo IoT Hub estándar. Este ejemplo agrega el IoT Hub e la región **Este de EE. UU.**, crea dos grupos de consumidores (**cg1** and **cg2**) en el punto de conexión compatible con Centro de eventos y usa la versión de API **2016-02-03**. En esta plantilla se espera también que pase el nombre del centro de IoT como un parámetro denominado **hubName**. Para ver una lista actualizada de las ubicaciones admitidas en IoT Hub, consulte [Estado de Azure][lnk-status].
   
    ```
    {
      "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
      "contentVersion": "1.0.0.0",
      "parameters": {
        "hubName": {
          "type": "string"
        }
      },
      "resources": [
      {
        "apiVersion": "2016-02-03",
        "type": "Microsoft.Devices/IotHubs",
        "name": "[parameters('hubName')]",
        "location": "East US",
        "sku": {
          "name": "S1",
          "tier": "Standard",
          "capacity": 1
        },
        "properties": {
          "location": "East US"
        }
      },
      {
        "apiVersion": "2016-02-03",
        "type": "Microsoft.Devices/IotHubs/eventhubEndpoints/ConsumerGroups",
        "name": "[concat(parameters('hubName'), '/events/cg1')]",
        "dependsOn": [
          "[concat('Microsoft.Devices/Iothubs/', parameters('hubName'))]"
        ]
      },
      {
        "apiVersion": "2016-02-03",
        "type": "Microsoft.Devices/IotHubs/eventhubEndpoints/ConsumerGroups",
        "name": "[concat(parameters('hubName'), '/events/cg2')]",
        "dependsOn": [
          "[concat('Microsoft.Devices/Iothubs/', parameters('hubName'))]"
        ]
      }
      ],
      "outputs": {
        "hubKeys": {
          "value": "[listKeys(resourceId('Microsoft.Devices/IotHubs', parameters('hubName')), '2016-02-03')]",
          "type": "object"
        }
      }
    }
    ```
2. Guarde el archivo de plantilla de Azure Resource Manager. En este ejemplo, se da por supuesto que lo guarda en una carpeta llamada **c:\templates**.
3. Ejecute el comando siguiente para implementar el nuevo Centro de IoT, pasando el nombre de su Centro de IoT como un parámetro. En este ejemplo, el nombre del centro de IoT es **abcmyiothub** (tenga en cuenta que debe ser un nombre único global, por lo que debe incluir su nombre o sus iniciales):
   
    ```
    New-AzureRmResourceGroupDeployment -ResourceGroupName MyIoTRG1 -TemplateFile C:\templates\template.json -hubName abcmyiothub
    ```
4. El resultado muestra las claves para el Centro de IoT que ha creado.
5. Para comprobar que la aplicación ha agregado el nuevo centro de IoT Hub, visite [Azure Portal][lnk-azure-portal] y consulte la lista de recursos. También puede utilizar el cmdlet de PowerShell **Get-AzureRmResource**.

> [!NOTE]
> Esta aplicación de ejemplo agrega un Centro de IoT estándar S1 por el que se le cobrará. Cuando haya terminado, podrá eliminar el centro de IoT Hub a través de [Azure Portal][lnk-azure-portal] o mediante el cmdlet **Remove-AzureRmResource** de PowerShell.
> 
> 

## <a name="next-steps"></a>Pasos siguientes
Ahora que ha implementado un IoT Hub mediante una plantilla de Azure Resource Manager con PowerShell, quizá desee seguir explorando:

* Consulte las funcionalidades de la [API de REST del proveedor de recursos de IoT Hub][lnk-rest-api].
* Para más información sobre las funcionalidades de Azure Resource Manager, consulte [Información general de Azure Resource Manager][lnk-azure-rm-overview].

Para más información acerca del desarrollo para el Centro de IoT, consulte lo siguiente:

* [Introducción a C SDK][lnk-c-sdk]
* [SDK de IoT de Azure][lnk-sdks]

Para explorar aún más las funcionalidades de Centro de IoT, consulte:

* [Simulación de un dispositivo con el SDK de puerta de enlace de IoT][lnk-gateway]

<!-- Links -->
[lnk-free-trial]: https://azure.microsoft.com/pricing/free-trial/
[lnk-azure-portal]: https://portal.azure.com/
[lnk-status]: https://azure.microsoft.com/status/
[lnk-powershell-install]: ../powershell-install-configure.md
[lnk-rest-api]: https://msdn.microsoft.com/library/mt589014.aspx
[lnk-azure-rm-overview]: ../azure-resource-manager/resource-group-overview.md
[lnk-powershell-arm]: ../azure-resource-manager/powershell-azure-resource-manager.md

[lnk-c-sdk]: iot-hub-device-sdk-c-intro.md
[lnk-sdks]: iot-hub-devguide-sdks.md

[lnk-gateway]: iot-hub-linux-gateway-sdk-simulated-device.md



<!--HONumber=Nov16_HO5-->


