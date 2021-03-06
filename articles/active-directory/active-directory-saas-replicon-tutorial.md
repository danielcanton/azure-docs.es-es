---
title: "Tutorial: Integración de Azure Active Directory con Replicon | Microsoft Docs"
description: "Aprenda cómo usar Replicon con Azure Active Directory para habilitar el inicio de sesión único, el aprovisionamiento automatizado, etc."
services: active-directory
author: jeevansd
documentationcenter: na
manager: femila
ms.assetid: 02a62f15-917c-417c-8d80-fe685e3fd601
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 09/26/2016
ms.author: jeedes
translationtype: Human Translation
ms.sourcegitcommit: 219dcbfdca145bedb570eb9ef747ee00cc0342eb
ms.openlocfilehash: 1dfd8edcae7d54d4ba8456a424a3fbc40d45c777


---
# <a name="tutorial-azure-active-directory-integration-with-replicon"></a>Tutorial: Integración de Azure Active Directory con Replicon
El objetivo de este tutorial es mostrar la integración de Azure y Replicon. En la situación descrita en este tutorial se supone que ya cuenta con los elementos siguientes:

* Una suscripción de Azure válida
* Un inquilino de Replicon

Después de completar este tutorial, los usuarios de Azure AD que ha asignado a Replicon podrán realizar un inicio de sesión único en la aplicación en el sitio de la compañía Replicon (inicio de sesión iniciado por el proveedor de servicios) o con la [Introducción al Panel de acceso](active-directory-saas-access-panel-introduction.md).

La situación descrita en este tutorial consta de los siguientes bloques de creación:

1. Habilitación de la integración de aplicaciones para Replicon
2. Configuración del inicio de sesión único
3. Configuración del aprovisionamiento de usuario
4. Asignación de usuarios

![Escenario](./media/active-directory-saas-replicon-tutorial/IC777798.png "Scenario")

## <a name="enabling-the-application-integration-for-replicon"></a>Habilitación de la integración de aplicaciones para Replicon
El objetivo de esta sección es describir cómo habilitar la integración de aplicaciones para Replicon.

### <a name="to-enable-the-application-integration-for-replicon-perform-the-following-steps"></a>Siga estos pasos para habilitar la integración de aplicaciones para Replicon:
1. En el panel de navegación izquierdo del Portal de Azure clásico, haga clic en **Active Directory**.
   
   ![Active Directory](./media/active-directory-saas-replicon-tutorial/IC700993.png "Active Directory")
2. En la lista **Directory** , seleccione el directorio cuya integración desee habilitar.
3. Para abrir la vista de aplicaciones, haga clic en **Applications** , en el menú superior de la vista de directorios.
   
   ![Applications](./media/active-directory-saas-replicon-tutorial/IC700994.png "Applications")
4. Haga clic en **Agregar** en la parte inferior de la página.
   
   ![Agregar aplicación](./media/active-directory-saas-replicon-tutorial/IC749321.png "Add application")
5. En el cuadro de diálogo **¿Qué desea hacer?**, haga clic en **Agregar una aplicación de la galería**.
   
   ![Agregar una aplicación de la galería](./media/active-directory-saas-replicon-tutorial/IC749322.png "Add an application from gallerry")
6. En el **cuadro de búsqueda**, escriba **PolicyStat**.
   
   ![Galería de aplicaciones](./media/active-directory-saas-replicon-tutorial/IC777799.png "Application gallery")
7. En el panel de resultados, seleccione **Replicon** y haga clic en **Completar** para agregar la aplicación.
   
   ![Replicon](./media/active-directory-saas-replicon-tutorial/IC777800.png "Replicon")
   
   ## <a name="configuring-single-sign-on"></a>Configuración del inicio de sesión único

El objetivo de esta sección es describir cómo habilitar usuarios para que se autentiquen en Replicon con su cuenta de Azure AD a través de la federación basada en el protocolo SAML.

### <a name="to-configure-single-sign-on-perform-the-following-steps"></a>Siga estos pasos para configurar el inicio de sesión único:
1. En el Portal de Azure clásico, en la página de integración de aplicaciones de **Replicon**, haga clic en **Configurar inicio de sesión único** para abrir el cuadro de diálogo **Configurar inicio de sesión único**.
   
   ![Configurar inicio de sesión único](./media/active-directory-saas-replicon-tutorial/IC777801.png "Configure single sign-on")
2. En la página **¿Cómo desea que los usuarios inicien sesión en Replicon?**, seleccione **Inicio de sesión único de Microsoft Azure AD** y haga clic en **Siguiente**.
   
   ![Configurar inicio de sesión único](./media/active-directory-saas-replicon-tutorial/IC777802.png "Configure single sign-on")
3. En la página **Configurar dirección URL de la aplicación** , realice los pasos siguientes:
   
   ![Configurar dirección URL de la aplicación](./media/active-directory-saas-replicon-tutorial/IC777803.png "Configure app URL")
   
   1. En el cuadro de texto **URL de inicio de sesión de Replicon**, escriba la dirección URL del inquilino de Replicon (p. ej.: *https://na2.replicon.com/company/saml2/sp-sso/post*).
   2. En el cuadro de texto **URL de inicio de sesión de Replicon**, escriba la dirección URL **AssertionConsumerService** de Replicon (p. ej.: *https://global.replicon.com/!/saml2/company/sso/post*).  
      
      > [!NOTE]
      > Puede obtener la dirección URL de los metadatos de Replicon en: **https://global.replicon.com/!/saml2/\<SuClaveCompañía\>**.
      > 
      > 
   3. Haga clic en **Siguiente**
4. En la página **Configurar inicio de sesión único en Replicon**, para descargar los metadatos, haga clic en **Descargar metadatos** y guarde los metadatos en el equipo.
   
   ![Configurar inicio de sesión único](./media/active-directory-saas-replicon-tutorial/IC777804.png "Configure single sign-on")
5. En otra ventana del explorador web, inicie sesión en como administrador en el sitio de Replicon de la compañía.
6. Lleve a cabo los siguientes pasos para configurar SAML 2.0:
   
   ![Habilitar autenticación SAML](./media/active-directory-saas-replicon-tutorial/IC777805.png "Enable SAML authentication")
   
   1. Para mostrar el cuadro de diálogo **EnableSAML Authentication2** (Habilitar SAML Authentication2), agregue lo siguiente a la URL después de la clave de su compañía:  
      **/services/SecurityService1.svc/help/test/EnableSAMLAuthentication2**  
      Lo siguiente muestra el esquema de la dirección URL completa:  
      **https://na2.replicon.com/\<SuClaveCompañía\>/services/SecurityService1.svc/help/test/EnableSAMLAuthentication2**
   2. Haga clic en **+** para expandir la sección **v20Configuration**.
   3. Haga clic en **+** para expandir la sección **metaDataConfiguration**.
   4. Haga clic en **Elegir archivo** para seleccionar el archivo XML de metadatos del proveedor de identidades y haga clic en **Enviar**.
7. En el Portal de Azure clásico, seleccione la confirmación de configuración de inicio de sesión único y haga clic en **Completar** para cerrar el cuadro de diálogo **Configurar inicio de sesión único**.
   
   ![Configurar inicio de sesión único](./media/active-directory-saas-replicon-tutorial/IC778418.png "Configure single sign-on")
   
   ## <a name="configuring-user-provisioning"></a>Configuración del aprovisionamiento de usuario

Para permitir que los usuarios de Azure AD inicien sesión en Replicon, deben aprovisionarse en Replicon.  
En el caso de Replicon, el aprovisionamiento es una tarea manual.

### <a name="to-configure-user-provisioning-perform-the-following-steps"></a>Siga estos pasos para configurar el aprovisionamiento de usuario:
1. En una ventana del explorador web, inicie sesión en como administrador en el sitio de Replicon de la compañía.
2. Vaya a **Administración \> Usuarios**.
   
   ![Usuarios](./media/active-directory-saas-replicon-tutorial/IC777806.png "Users")
3. Haga clic en **+Agregar usuario**.
   
   ![Agregar usuario](./media/active-directory-saas-replicon-tutorial/IC777807.png "Add User")
4. En la sección **Perfil de usuario** , lleve a cabo estos pasos:
   
   ![Perfil de usuario](./media/active-directory-saas-replicon-tutorial/IC777808.png "User profile")
   
   1. En el cuadro de texto **Nombre de inicio de sesión** , escriba la dirección de correo electrónico del usuario de Azure AD que quiera aprovisionar.
   2. En **Tipo de autenticación,** seleccione **SSO**.
   3. En el cuadro de texto **Departamento** , escriba el departamento del usuario.
   4. En **Tipo de empleado**, seleccione **Administrador**.
   5. Haga clic en **Guardar perfil de usuario**.

> [!NOTE]
> Puede usar cualquier otra API o herramienta de creación de cuentas de usuario de Replicon que proporcione Replicon para aprovisionar cuentas de usuario de AAD.
> 
> 

## <a name="assigning-users"></a>Asignación de usuarios
Para probar la configuración, debe conceder acceso a los usuarios de Azure AD a los que quiere permitir el uso de su aplicación.

### <a name="to-assign-users-to-replicon-perform-the-following-steps"></a>Para asignar usuarios a Replicon, lleve a cabo los siguientes pasos:
1. En el Portal de Azure clásico, cree una cuenta de prueba.
2. En la página de integración de aplicaciones de **Replicon**, haga clic en **Asignar usuarios**.
   
   ![Asignar usuarios](./media/active-directory-saas-replicon-tutorial/IC777809.png "Assign users")
3. Seleccione su usuario de prueba, haga clic en **Asignar** y en **Sí** para confirmar la asignación.
   
   ![Sí](./media/active-directory-saas-replicon-tutorial/IC767830.png "Yes")

Si desea probar la configuración de inicio de sesión único, abra el Panel de acceso. Para obtener más información sobre el Panel de acceso, vea [Introducción al Panel de acceso](active-directory-saas-access-panel-introduction.md).




<!--HONumber=Nov16_HO3-->


