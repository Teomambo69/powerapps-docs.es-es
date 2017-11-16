---
title: "Solución de problemas: no se puede crear o recuperar un mashup para esta base de datos | Microsoft Docs"
description: "Resuelva problemas mediante la creación de una entidad personalizada con CDS y Power Query mediante los cambios del administrador a las restricciones de AAD."
services: 
suite: powerapps
documentationcenter: na
author: mllopis
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/18/2017
ms.author: millopis
ms.openlocfilehash: 230ad9f61185caff93fb3a5f56c62176b4f78c16
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting---unable-to-create-or-retrieve-a-mashup-for-this-database"></a>Solución de problemas: no se puede crear o recuperar un mashup para esta base de datos
Al usar la característica **Nuevas entidades de datos (Technical Preview)**, puede encontrarse un error similar al siguiente:

    *Unable to create or retrieve a mashup for the current database*

Esto puede ocurrir cuando se utiliza la característica para crear *entidades personalizadas* en **Common Data Service (CD)** con datos procedentes de orígenes de datos externos mediante **Power Query**. El error se desencadena cuando **Power Query** no puede acceder a los datos que hay de la organización en **PowerApps o CDS**. Hay dos escenarios en los que esto puede ocurrir:

* Un administrador de inquilinos de **Azure Active Directory** (AAD) ha deshabilitado la capacidad de los usuarios para consentir que las aplicaciones accedan a los datos de la compañía en su nombre.
* Uso de un inquilino de Active Directory no administrado. Un inquilino no administrado es un directorio sin un administrador global creado para completar una oferta de suscripción de autoservicio. Para corregir esta situación, *en primer lugar* los usuarios deben convertirse en un inquilino administrado y, después, seguir una de las dos soluciones a este problema que se describen en la sección siguiente.

## <a name="how-to-fix-the-issue"></a>Solución del problema
Hay dos formas de solucionar el problema que se ha descrito anteriormente:

* Que el administrador de AAD siga los pasos necesarios para que los usuarios den su consentimiento para que las aplicaciones accedan a los datos de la compañía
* Que el administrador de AAD permita a **Power Query** acceder a los datos

A continuación se describen todos los pasos necesarios para estas soluciones.

### <a name="allowing-users-to-give-apps-consent-to-access-company-data"></a>Concesión del permiso para que los usuarios den su consentimiento para que las aplicaciones accedan a los datos de la empresa
Puede ponerse en contacto con el administrador de inquilinos de AAD para que este realice los pasos siguientes, lo que permite que los usuarios den su consentimiento para que todas las aplicaciones accedan a los datos de la compañía:

1. Visite [https://portal.azure.com](https://portal.azure.com)
2. Abra la hoja **Azure Active Directory**.
3. Seleccione **Configuración de usuario**.
4. Seleccione **Sí** en **Los usuarios pueden permitir que las aplicaciones accedan a los datos de la compañía en su nombre**  y, después, seleccione **Guardar**.
5. Una vez que haya completado ese proceso, se resolverá el problema.

Es posible que este enfoque sea el más sencillo, pero permite para permisos menos restrictivos que la opción siguiente.

### <a name="allowing-power-query-to-access-company-data"></a>Concesión del permiso para que Power Query acceda a los datos de la empresa
Otra solución es que el administrador de inquilinos dé su consentimiento a **Power Query** sin modificar los permisos de todos los inquilinos. El administrador de inquilinos debe dar los siguientes pasos lograrlo:

1. Instale [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps).
2. Ejecute los siguientes comandos de PowerShell:
   * Login-AzureRmAccount (e inicie sesión como administrador de inquilinos).
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128.

La ventaja de este enfoque (frente a la solución anterior) es que esta solución es muy directa. Solo aprovisiona la entidad de servicio de **Power Query**, pero no se realizan otros cambios de permisos en el inquilino.

