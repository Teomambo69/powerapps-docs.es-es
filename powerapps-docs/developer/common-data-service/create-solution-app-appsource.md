---
title: 'Paso 2: Crear una solución administrada para la aplicación (Common Data Service) | Microsoft Docs'
description: Obtenga información sobre cómo crear una solución administrada para incluir todos los componentes de su aplicación. Esto es necesario para publicar una aplicación en Appsource.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d1c5407f408f11ce8bfed3443cc29be2b3f27675
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156328"
---
# <a name="step-2-create-a-managed-solution-for-your-app"></a>Paso 2: Crear una solución administrada para la aplicación

Cree una solución administrada para incluir todos los componentes de su aplicación. Estos temas pueden ser útiles cuando planee y cree una solución administrada para empaquetar los componentes de aplicaciones:
- [Introducción a soluciones](introduction-solutions.md)
- [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development) 
- [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)

## <a name="display-name-and-description-of-your-solution"></a>Nombre y descripción de la solución

Mientras crea una solución para los componentes de aplicaciones de paquete, asegúrese de que proporciona valores adecuados en los campos **nombre** y **descripción** de la solución nueva que quiere que se muestre a los clientes.

![Crear una solución](media/appsource-new-solution.png)

Los valores de **nombre** y **descripción** de una solución se muestran a los clientes en el portal **centro de administración de Dynamics 365**.

![Soluciones](media/appsource-solution-names.png)

## <a name="supporting-data-for-your-solution"></a>Compatibilidad con datos de la solución

Si la solución requiere datos de soporte o demostración:
1. Cree datos de soporte o prueba en su entorno de prueba.
2. Utilice la [herramienta Configuration Migration](/dynamics365/customer-engagement/admin/manage-configuration-data) para crear un esquema para incluir los datos de soporte o prueba. 
3. Guarde el archivo de esquema de forma que pueda volver a utilizarlo para actualizar los datos en caso de que los datos de prueba cambien.
4. Use el esquema para exportar los datos. Asegúrese de proporcionar un nombre significativo en el archivo de exportación. Los datos se exportan como un archivo .zip.

Para obtener información detallada sobre el uso de la herramienta Configuration Migration para crear un esquema y exportar los datos, consulte [crear un esquema para exportar datos de configuración](/dynamics365/customer-engagement/admin/create-schema-export-configuration-data)

## <a name="at-the-end-of-this-step"></a>Al final de este paso

Tendrá un archivo de solución (ejemplo: *SampleSolution.zip*) y opcionalmente un archivo de datos de demostración (ejemplo: *SampleData.zip*) para la aplicación.


> [!div class="nextstepaction"]
> [Paso 3: Crear un paquete de AppSource para la aplicación](create-package-app-appsource.md) 
  
