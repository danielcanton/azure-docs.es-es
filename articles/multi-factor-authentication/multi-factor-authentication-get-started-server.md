---
title: "Introducción a Servidor Azure Multi-Factor Authentication"
description: "En esta página de Azure Multi-Factor Authentication se describe cómo empezar a trabajar con Servidor Azure Multi-Factor Authentication."
services: multi-factor-authentication
keywords: "servidor de autenticación, página de activación de la aplicación de azure multi factor autenticación, descarga del servidor de autenticación"
documentationcenter: 
author: kgremban
manager: femila
editor: yossib
ms.assetid: e94120e4-ed77-44b8-84e4-1c5f7e186a6b
ms.service: multi-factor-authentication
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: get-started-article
ms.date: 11/29/2016
ms.author: kgremban
translationtype: Human Translation
ms.sourcegitcommit: 2e2d680a0f54830f6086a4d6ac98f4a550f4ee46
ms.openlocfilehash: 66726c39c09ed867beb999f9589dfef3f7cf65bb

---

# <a name="getting-started-with-the-azure-multi-factor-authentication-server"></a>Introducción a Servidor Azure Multi-Factor Authentication
<center>![MFA local](./media/multi-factor-authentication-get-started-server/server2.png)</center>

Ahora que hemos determinado que se usa una instancia local de Multi-Factor Authentication, vamos al paso siguiente. Esta página describe una nueva instalación del servidor y su configuración con una instancia loal de Active Directory. Si ya tiene instalado el servidor de Phonefactor y desea actualizarlo, consulte [Actualización de PhoneFactor Agent al Servidor Azure Multi-Factor Authentication](multi-factor-authentication-get-started-server-upgrade.md) o si busca información acerca de cómo instalar solo el servicio web, consulte [Implementación del servicio web de aplicación móvil del servidor Multi-Factor Authentication](multi-factor-authentication-get-started-server-webservice.md).

## <a name="download-the-azure-multi-factor-authentication-server"></a>Descarga de Servidor Azure Multi-Factor Authentication
Hay dos maneras diferentes de descargar Servidor Azure Multi-Factor Authentication. Ambas se pueden hacer a través de Azure Portal. La primera es administrando el proveedor de autenticación multifactor directamente. La segunda es mediante la configuración del servicio. La segunda opción requiere un Proveedor de Multi-Factor Authentication o una licencia de Azure MFA, Azure AD Premium o Enterprise Mobility Suite.

### <a name="to-download-the-azure-multi-factor-authentication-server-from-the-azure-classic-portal"></a>Para descargar el SDK de Servidor Azure Multi-Factor Authentication del Portal de Azure clásico

1. Inicie sesión como administrador en el [Portal de Azure clásico](https://manage.windowsazure.com).
2. En la parte izquierda, seleccione **Active Directory**.
3. En la parte superior de la página Active Directory, haga clic en **Proveedores de autenticación multifactor**
    ![Proveedores de autenticación multifactor](./media/multi-factor-authentication-get-started-server/authproviders.png)
4. En la parte inferior, haga clic en **Administrar**. Se abrirá una nueva página.
5. Haga clic en **Descargas**.
6. Haga clic en el vínculo **Descargar** encima de **Generar credenciales de activación**.
   ![Descargar](./media/multi-factor-authentication-get-started-server/download4.png)
7. Guarde el archivo descargado.

### <a name="to-download-the-azure-multi-factor-authentication-server-from-the-service-settings"></a>Para descargar Servidor Azure Multi-Factor Authentication mediante la configuración del servicio
1. Inicie sesión como administrador en el [Portal de Azure clásico](https://manage.windowsazure.com).
2. En la parte izquierda, seleccione **Active Directory**.
3. Haga doble clic en la instancia de Azure AD.
4. En la parte superior, haga clic en **Configurar**
5. Vaya a la sección **autenticación multifactor** y seleccione **Administrar configuración del servicio**.
6. En la parte inferior de la página de configuración de servicios, haga clic en **Ir al portal**. Se abrirá una nueva página.
   ![Descargar](./media/multi-factor-authentication-get-started-server/servicesettings.png)
7. Haga clic en **Descargas**
8. Haga clic en el vínculo **Descargar** encima de **Generar credenciales de activación**.
    ![Descargar](./media/multi-factor-authentication-get-started-server/download4.png)
9. Guarde el archivo descargado.

## <a name="install-and-configure-the-azure-multi-factor-authentication-server"></a>Instalación y configuración del Servidor Azure Multi-Factor Authentication
Una vez descargado el servidor, ya se puede instalar y configurar.  Asegúrese de que el servidor que va a instalar cumple los requisitos siguientes:

| Requisitos del Servidor Azure Multi-Factor Authentication | Description |
|:--- |:--- |
| Hardware |<li>200 MB de espacio de disco duro</li><li>Procesador compatible con x32 o x64</li><li>1 GB o más de RAM</li> |
| Software |<li>Windows Server 2008 o superior si el host es un sistema operativo de servidor</li><li>Windows 7 o superior si el host es un sistema operativo cliente</li><li>Microsoft .NET 4.0 Framework</li><li>IIS 7.0 o superior si está instalado el SDK de servicio web o el portal de usuario</li> |

### <a name="azure-multi-factor-authentication-server-firewall-requirements"></a>Requisitos de firewall del Servidor Azure Multi-Factor Authentication
- - -
Cada servidor MFA debe ser capaz de comunicarse en el puerto 443 de salida a las siguientes direcciones:

* https://pfd.phonefactor.net
* https://pfd2.phonefactor.net
* https://css.phonefactor.net

Si los firewalls de salida están restringidos en el puerto 443, deberán abrirse los siguientes intervalos de direcciones IP:

| Subred IP | Máscara de red | Rango de direcciones IP |
|:--- |:--- |:--- |
| 134.170.116.0/25 |255.255.255.128 |134.170.116.1 – 134.170.116.126 |
| 134.170.165.0/25 |255.255.255.128 |134.170.165.1 – 134.170.165.126 |
| 70.37.154.128/25 |255.255.255.128 |70.37.154.129 – 70.37.154.254 |

Si no está usando la característica de confirmación de eventos y los usuarios no usan aplicaciones móviles para comprobar desde dispositivos de la red corporativa, las direcciones IP se pueden reducir a los siguientes intervalos:

| Subred IP | Máscara de red | Rango de direcciones IP |
|:--- |:--- |:--- |
| 134.170.116.72/29 |255.255.255.248 |134.170.116.72 – 134.170.116.79 |
| 134.170.165.72/29 |255.255.255.248 |134.170.165.72 – 134.170.165.79 |
| 70.37.154.200/29 |255.255.255.248 |70.37.154.201 – 70.37.154.206 |

### <a name="to-install-and-configure-the-azure-multi-factor-authentication-server"></a>Para instalar y configurar el Servidor Azure Multi-Factor Authentication

1. Haga doble clic en el archivo ejecutable. Se inicia la instalación.
2. En la pantalla Seleccionar carpeta de instalación, asegúrese de que la carpeta sea correcta y haga clic en **Siguiente**.
3. Una vez completada la instalación, haga clic en **Finalizar**.  Se inicia el asistente para configuración.
4. En la pantalla de bienvenida del asistente para configuración, active **Omitir el uso del Asistente para configuración de autenticación** y haga clic en **Siguiente**.  El asistente se cierra y el servidor se inicia.
    ![Nube](./media/multi-factor-authentication-get-started-server/skip2.png)
5. De vuelta en la página desde la que hemos descargado el servidor, haga clic en el botón **Generar credenciales de activación** . Copie esta información en Servidor Azure Multi-Factor Authentication en los cuadros correspondientes y haga clic en **Activar**.

Los pasos anteriores muestran una instalación rápida con el Asistente para configuración.  Para volver a ejecutar el asistente para autenticación, puede seleccionarlo en el menú Herramientas del servidor.

## <a name="import-users-from-active-directory"></a>Importación de usuarios desde Active Directory
Ahora que está instalado y configurado el servidor, puede importar rápidamente los usuarios en Servidor Azure Multi-Factor Authentication.

1. En Servidor Azure Multi-Factor Authentication, a la izquierda, seleccione **Usuarios**.
2. En la parte inferior, seleccione **Importar desde Active Directory**.
3. Ahora puede buscar usuarios individuales o buscar en el directorio de AD las unidades organizativas con usuarios en ellas.  En este caso, se especifican las unidades organizativas de los usuarios.
4. Resalte todos los usuarios de la derecha y haga clic en **Importar**.  Debe aparecer una ventana emergente que le indica que la operación se realizó correctamente.  Cierre la ventana de importación.

![Nube](./media/multi-factor-authentication-get-started-server/import2.png)

## <a name="send-users-an-email"></a>Enviar un correo electrónico a los usuarios
Ahora que ha importado los usuarios al servidor MFA, se recomienda enviar un correo electrónico para informarles de que se les ha inscrito en la verificación en dos pasos.

El correo electrónico que envíe estará determinado por cómo haya configurado la verificación en dos pasos para los usuarios. Por ejemplo, si puede importar el número de teléfono de los usuarios desde el directorio de la empresa, el mensaje de correo electrónico deberá incluir los números de teléfono predeterminados para que los usuarios sepan qué pueden esperar. De forma similar, si no se han importado los números de teléfono de los usuarios o los usuarios están configurados para usar la aplicación móvil, envíeles un mensaje de correo electrónico que los dirija a completar la inscripción de su cuenta mediante un hipervínculo al portal de usuarios de Azure Multi-Factor Authentication.

El contenido del correo electrónico variará según el método de autenticación que se haya establecido para el usuario (llamada de teléfono, SMS o aplicación móvil).  Por ejemplo, si el usuario debe usar un PIN para autenticarse, el correo electrónico le indica el PIN inicial que se ha establecido.  Los usuarios deben cambiar su código PIN durante su primera autenticación.


### <a name="configure-email-and-email-templates"></a>Configuración del correo electrónico y las plantillas de correo electrónico
Haga clic en el icono de correo electrónico situado a la izquierda para configurar las opciones de envío de estos correos electrónicos. Aquí puede especificar la información de SMTP del servidor de correo electrónico y seleccionar la casilla **Enviar correos electrónicos a los usuarios** para enviar correo electrónico.

![Configuración de correo electrónico](./media/multi-factor-authentication-get-started-server/email1.png)

En la pestaña Contenido del mensaje de correo electrónico, verá las plantillas de correo electrónico que hay disponibles. Elija la plantilla más adecuada según cómo haya configurado la verificación en dos pasos para los usuarios.

![Email templates](./media/multi-factor-authentication-get-started-server/email2.png)

## <a name="how-the-azure-multi-factor-authentication-server-handles-user-data"></a>¿Cómo controla el Servidor Azure Multi-Factor Authentication los datos de usuario?
Cuando se usa Servidor Azure Multi-Factor Authentication (MFA) local, los datos de un usuario se almacenan en los servidores locales. Los datos de usuario persistentes no se almacenan en la nube. Cuando el usuario realiza una verificación en dos pasos, Servidor MFA envía los datos al servicio en la nube Azure MFA para realizar la verificación. Cuando estas solicitudes de autenticación se envían al servicio en la nube, en la solicitud y los registros se incluyen los siguientes campos para que estén disponibles en los informes de uso/autenticación del cliente. Algunos de los campos son opcionales y se pueden habilitar o deshabilitar en Servidor Multi-Factor Authentication. La comunicación desde Servidor MFA al servicio en la nube MFA usa SSL/TLS en el puerto 443 de salida. Estos campos son:

* Id. exclusivo: nombre de usuario o Id. interno de Servidor MFA
* Nombre y apellidos (opcional)
* Dirección de correo electrónico (opcional)
* Número de teléfono: al realizar una llamada de voz o autenticación por SMS
* Token de dispositivo: al realizar la autenticación de una aplicación móvil
* Modo de autenticación
* Resultado de autenticación
* Nombre de Servidor MFA
* IP de Servidor MFA
* IP de cliente: si está disponible

Además de los campos anteriores, el resultado (éxito o denegación) de la verificación y el motivo de las denegaciones también se almacenan con los datos de autenticación y están disponibles en informes de uso y autenticación.

## <a name="advanced-azure-multi-factor-authentication-server-configurations"></a>Configuraciones de servidor de Azure Multi-Factor Authentication avanzadas
Para más información sobre las opciones de configuración e instalación avanzadas, consulte la tabla siguiente:

| Método | Description |
|:--- |:--- |
| [Portal de usuario](multi-factor-authentication-get-started-portal.md) |Información sobre la instalación y configuración del portal de usuario, incluida la implementación y el autoservicio del usuario. |
| [Servicio de federación de Active Directory](multi-factor-authentication-get-started-adfs.md) |Información sobre cómo configurar la Azure Multi-Factor Authentication con AD FS. |
| [Autenticación RADIUS](multi-factor-authentication-get-started-server-radius.md) |Información sobre la instalación y configuración del servidor de MFA de Azure con RADIUS. El uso de RADIUS permite integrar varios sistemas de terceros con Servidor Azure MFA. |
| [Autenticación de IIS](multi-factor-authentication-get-started-server-iis.md) |Información sobre la instalación y configuración del servidor de MFA de Azure con IIS. El uso de IIS permite integrar varios sistemas de terceros con Servidor Azure MFA. |
| [Autenticación de Windows](multi-factor-authentication-get-started-server-windows.md) |Información sobre la instalación y configuración del servidor de MFA de Azure con la autenticación de Windows. |
| [Autenticación LDAP](multi-factor-authentication-get-started-server-ldap.md) |Información sobre la instalación y configuración del servidor de MFA de Azure con la autenticación LDAP. El uso de LDAP permite integrar varios sistemas de terceros con Servidor Azure MFA. |
| [Puerta de enlace de Escritorio remoto y Servidor Azure Multi-Factor Authentication con RADIUS](multi-factor-authentication-get-started-server-rdg.md) |Información sobre la instalación y configuración del servidor de MFA de Azure con la puerta de enlace de escritorio remoto mediante RADIUS. |
| [Sincronización con Windows Server Active Directory](multi-factor-authentication-get-started-server-dirint.md) |Información sobre la instalación y configuración de la sincronización entre Active Directory y el servidor de MFA de Azure. |
| [Implementación del servicio web móvil de la aplicación móvil del servidor de Azure Multi-Factor Authentication](multi-factor-authentication-get-started-server-webservice.md) |Información sobre la instalación y configuración del servicio web del servidor de Azure MFA. |
| [Escenarios avanzados con Azure Multi-Factor Authentication y VPN de terceros](multi-factor-authentication-advanced-vpn-configurations.md) | Guías paso a paso para la configuración de dispositivos VPN de Cisco, Citrix y Juniper. |



<!--HONumber=Dec16_HO1-->


