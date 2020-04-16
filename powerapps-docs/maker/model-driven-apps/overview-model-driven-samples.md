---
title: Aplicaciones controladas por modelos de ejemplo
description: Comprenda cómo obtener, personalizar y quitar aplicaciones controladas por modelos de ejemplo.
documentationcenter: na
author: mr-dang-msft
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/09/2020
ms.author: brdang
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 995fc58d72031a6108573ba48cebcb30f1aecd79
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136541"
---
# <a name="model-driven-sample-apps"></a>Aplicaciones controladas por modelos de ejemplo

En [powerapps.com](https://powerapps.com), use una aplicación de ejemplo para explorar posibilidades de diseño y para descubrir conceptos que puede aplicar cuando se desarrolla sus propias aplicaciones. Cada aplicación de ejemplo usa datos ficticios para mostrar un escenario del mundo real. 

Asegúrese de comprobar la documentación específica de cada aplicación de ejemplo para obtener más detalles. 

> [!div class="mx-imgBorder"] 
> ![Aplicación de ejemplo de recaudador de fondos](media/overview-model-driven-samples/fundraiser-app1.png "Aplicación de ejemplo de recaudador de fondos")


## <a name="get-sample-apps"></a>Obtener aplicaciones de ejemplo

Para ejecutar o editar aplicaciones controladas por modelos de ejemplo, primero se deben introducir las aplicaciones en una base de datos de Common Data Service. Primero cree un entorno y una base de datos de prueba y asegúrese de seleccionar la opción **Implementar aplicaciones y datos de ejemplo**.

> [!div class="mx-imgBorder"] 
> ![Crear base de datos](media/overview-model-driven-samples/create-database1.png "Crear una base de datos")

> [!IMPORTANT]
> Esta opción instala todas las aplicaciones de ejemplo disponibles en la base de datos. Las aplicaciones de ejemplo son para fines educativos y de demostración y no se recomienda instalarlas en bases de datos de producción. 

## <a name="customize-a-sample-app"></a>Personalizar una aplicación de ejemplo

1. Iniciar sesión en [powerApps.com](https://powerapps.com)  

2. Desde la página **Crear**, seleccione la aplicación de muestra y haga clic **Crear**.

> [!div class="mx-imgBorder"]
> <img src="media/overview-model-driven-samples/model-driven-create-page-sample.png" alt="Create a model-driven sample app" height="427" width="674">

3. El diseñador de aplicaciones se abrirá proporcionando varias opciones para personalizar la aplicación.

4. Para ver más opciones de personalización, haga clic en **Avanzadas** en la navegación izquierda del portal.

## <a name="remove-sample-apps-and-data"></a>Quitar aplicaciones y datos de ejemplo 
- Eliminar una aplicación de ejemplo requiere eliminar la correspondiente [solución administrada](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution). 
- Al eliminar la solución también se eliminan los datos de ejemplo específicos de las entidades personalizadas de la aplicación.
- Si se realizaron personalizaciones en la aplicación de ejemplo, puede haber [dependencias](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components), que se deberán quitar antes de eliminar la solución.

### <a name="steps"></a>Pasos
1. Inicie sesión en el [portal de administración de Power Apps](https://admin.powerapps.com).

2. Seleccione un entorno.

    > [!div class="mx-imgBorder"] 
    > ![Centro de administración de Dynamics 365](media/overview-model-driven-samples/admin-center.png "Seleccione un entorno")

3. Haga clic en **Centro de administración de Dynamics 365**.

4. Seleccione la base de datos de la lista y haga clic en **ABRIR**.

    > [!div class="mx-imgBorder"] 
    > ![Seleccionar la base de datos](media/overview-model-driven-samples/select-database.png "Seleccionar una base de datos")

5. Desplácese a **Configuración/Soluciones**.

6. Seleccione la solución para la aplicación que se va a eliminar y haga clic **Eliminar**.

    > [!div class="mx-imgBorder"] 
    > ![Eliminar solución](media/overview-model-driven-samples/delete-solution.png "Eliminar la solución")

*También puede acceder a la lista de soluciones haciendo clic en **Avanzadas** en el portal de creadores y eliminando todo lo que hay en la dirección URL después de .dynamics.com/*

> [!IMPORTANT]
> No elimine otras soluciones del sistema a menos que tenga en cuenta su repercusión.

## <a name="install-or-uninstall-sample-data"></a>Instalar o desinstalar datos de ejemplo
1. Siga los pasos 1-4 anteriores.
2. Acceda a **Configuración/Administración de datos/Datos de ejemplo**.
3. Si hay datos de ejemplo instalados, la opción de eliminar está disponible. En caso contrario, estará disponible la opción de instalar. 

    > [!div class="mx-imgBorder"] 
    > ![quitar datos de ejemplo](media/overview-model-driven-samples/remove-sample-data.png "Quitar datos de ejemplo")




