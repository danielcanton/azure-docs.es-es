---
title: Asistente para seguridad de Privileged Identity Management de Azure AD
description: "La primera vez que use la extensión de Privileged Identity Management de Azure Active Directory, aparecerá un asistente para seguridad. En este artículo se describen los pasos para usar al asistente."
services: active-directory
documentationcenter: 
author: kgremban
manager: femila
editor: 
ms.assetid: a53a3719-8cc7-4fc7-8164-aafca192871b
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 07/01/2016
ms.author: kgremban
translationtype: Human Translation
ms.sourcegitcommit: 2ea002938d69ad34aff421fa0eb753e449724a8f
ms.openlocfilehash: 03adc1873e8187a9104f42ba9b50df2ac0d015b5


---
# <a name="the-azure-ad-privileged-identity-management-security-wizard"></a>Asistente para seguridad de Privileged Identity Management de Azure AD
Si es la primera persona que ejecuta Privileged Identity Management (PIM) de Azure en su organización, se le presentará un asistente. El asistente le ayuda a comprender los riesgos de seguridad de las identidades con privilegios y a usar PIM para reducirlos. No tiene que realizar cambios en las asignaciones de roles existentes en el asistente; si lo prefiere, puede hacerlo más adelante.

## <a name="what-to-expect"></a>Qué esperar
Antes de que su organización comienza a usar PIM, todas las asignaciones de roles son permanentes: los usuarios siempre tienen estos roles aunque en el momento actual no necesiten sus privilegios.  El primer paso del asistente muestra una lista de roles con privilegios elevados y cuántos usuarios tienen actualmente esos roles. Puede explorar en profundidad un rol determinado para conocer mejor a los usuarios en caso de que alguno de ellos no le resulte familiar.

El segundo paso del asistente le ofrece la oportunidad de cambiar las asignaciones de roles del administrador.  

> [!WARNING]
> Es importante que tenga al menos un administrador global, y más de un administrador de roles con privilegios con una cuenta de organización (no una cuenta Microsoft). Si solo hay un administrador de roles con privilegios, la organización no podrá administrar PIM si esa cuenta se elimina.
> Además, mantenga las asignaciones de roles permanente si un usuario tiene una cuenta de Microsoft (una cuenta que usan para iniciar sesión en servicios de Microsoft como Skype y Outlook.com). Si tiene pensado exigir MFA para la activación de ese rol, ese usuario se bloqueará.
> 
> 

Una vez realizados los cambios, ya no se mostrará el asistente. La próxima vez que usted u otro administrador de roles con privilegios use PIM, verá el panel de PIM.  

* Si desea agregar o quitar usuarios a roles, o cambiar las asignaciones de permanentes a aptas, puede obtener más información en [Privileged Identity Management de Azure AD: Incorporación o eliminación de un rol de usuario](active-directory-privileged-identity-management-how-to-add-role-to-user.md).
* Si desea conceder acceso a más usuarios para administrar PIM, aprenda cómo hacerlo en [Concesión de acceso para administrar Privileged Identity Management de Azure AD](active-directory-privileged-identity-management-how-to-give-access-to-pim.md).

## <a name="next-steps"></a>Pasos siguientes
[!INCLUDE [active-directory-privileged-identity-management-toc](../../includes/active-directory-privileged-identity-management-toc.md)]




<!--HONumber=Nov16_HO3-->


