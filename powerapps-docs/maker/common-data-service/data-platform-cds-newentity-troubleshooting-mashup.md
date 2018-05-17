---
title: Solución de problemas de Power Query | Microsoft Docs
description: Resuelva problemas con Power Query para crear una entidad personalizada en Common Data Service (CDS) for Apps.
author: mllopis
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 08/18/2017
ms.author: millopis
ms.openlocfilehash: d71349c90748b1820cd3430613e0925498ce9793
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2018
---
# <a name="troubleshooting-power-query"></a>Solución de problemas de Power Query
Cuando usa Power Query para crear una entidad personalizada que contiene datos de orígenes externos, puede aparecer este error:

`Your Azure Active Directory administrator has set a policy that prevents you from using this feature. Please contact your administrator, who can grant permissions for this feature on your behalf.`

El error aparece si Power Query no tiene acceso a los datos de la organización en PowerApps o en Common Data Service (CDS) for Apps. Esta situación se da en dos conjuntos de circunstancias:

* Un administrador de inquilinos de Azure Active Directory (AAD) ha deshabilitado la capacidad de los usuarios de dar su consentimiento para que las aplicaciones tengan acceso a los datos de la compañía en su nombre.
* Uso de un inquilino de Active Directory no administrado. Un inquilino no administrado es un directorio sin un administrador global creado para completar una oferta de suscripción de autoservicio. Para corregir esta situación, los usuarios han de convertirse primero en un inquilino administrado y luego seguir una de las dos soluciones a este problema que se describen en la sección siguiente.

Para resolver este problema, el administrador de Azure Active Directory debe seguir los pasos descritos en cualquiera de los procedimientos indicados más adelante en este tema.

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>Permita que los usuarios den su consentimiento en aplicaciones con acceso a datos de la compañía
Puede que este enfoque sea el más sencillo, pero concede permisos menos restrictivos.

1. En [https://portal.azure.com](https://portal.azure.com), abra la hoja **Azure Active Directory** y seleccione **Configuración de usuario**.
2. Seleccione **Sí** en **Los usuarios pueden permitir que las aplicaciones accedan a los datos de la compañía en su nombre**  y, después, seleccione **Guardar**.

## <a name="allow-power-query-to-access-company-data"></a>Permita que Power Query tenga acceso a los datos de la compañía
Como alternativa, el administrador de inquilinos puede dar su consentimiento a Power Query sin modificar los permisos de todo el inquilino.

1. Instale [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps).
2. Ejecute los siguientes comandos de PowerShell:
   * Login-AzureRmAccount (e inicie sesión como administrador de inquilinos).
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128.

La ventaja de este enfoque (frente a la solución anterior) es que esta solución es muy directa. Solo aprovisiona la entidad de servicio de **Power Query**, pero no se realizan otros cambios de permisos en el inquilino.

