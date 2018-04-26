---
title: Aplicaciones de ejemplo controladas por modelos
description: Obtenga información sobre cómo obtener, personalizar y quitar aplicaciones de ejemplo controladas por modelos.
documentationcenter: na
author: caburk
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/08/2018
ms.author: caburk
ms.openlocfilehash: c9525827c7e8e48c0f5e68e3608c9b6b9f630121
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="model-driven-sample-apps"></a>Aplicaciones de ejemplo controladas por modelos

En [powerapps.com](https://powerapps.com), utilice una aplicación de ejemplo para explorar posibilidades de diseño y descubrir conceptos que puede aplicar al desarrollar sus propias aplicaciones. Cada aplicación de ejemplo usa datos ficticios para presentar un escenario real. 

No olvide consultar la documentación específica de cada aplicación de ejemplo para obtener más información. 

![Aplicación de ejemplo Fundraiser](media/overview-model-driven-samples/fundraiser-app1.png)


## <a name="get-sample-apps"></a>Obtener aplicaciones de ejemplo

Para reproducir o modificar las aplicaciones de ejemplo controladas por modelos, primero se deben aprovisionar en una base de datos de Common Data Service. En primer lugar, cree un entorno y una base de datos de prueba y no olvide activar **Include sample apps and data** (Incluir aplicaciones y datos de ejemplo).

![Crear una base de datos](media/overview-model-driven-samples/create-database1.png)


> [!IMPORTANT]
> Esta opción instala todas las aplicaciones de ejemplo disponibles en la base de datos. Las aplicaciones de ejemplo son para fines educativos y de demostración, y no se recomienda su instalación en bases de datos de producción. 

## <a name="customize-a-sample-app"></a>Personalizar una aplicación de ejemplo

1. Inicie sesión en [powerapps.com](https://powerapps.com) y elija **Basado en modelos** para el modo de diseño. 

    ![Elección del modo de diseño](media/overview-model-driven-samples/choose-design-mode.png)

2. En la página de inicio, mantenga el puntero sobre la aplicación de ejemplo y haga clic en **Personalizar**.
3. Se abrirá el Diseñador de aplicaciones con varias opciones para personalizar la aplicación. 
4. Para ver opciones de personalización adicionales, haga clic en **Opciones avanzadas** en la barra de navegación de la izquierda en el portal.

## <a name="remove-sample-apps-and-data"></a>Quitar datos y aplicaciones de ejemplo 
- Para eliminar una aplicación de ejemplo es necesario eliminar la [solución administrada](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution) correspondiente. 
- Al eliminar la solución también se eliminan los datos de ejemplo específicos de las entidades personalizadas para la aplicación.
- Si se realizaron personalizaciones en la aplicación de ejemplo, puede haber [dependencias](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components), que deben quitarse antes de eliminar la solución.

### <a name="steps"></a>Pasos
1. Inicie sesión en el [Centro de administración de PowerApps](https://admin.powerapps.com).

2. Seleccione un entorno.

3. Haga clic en **Centro de administración de Dynamics 365** 

    ![Centro de administración de Dynamics 365](media/overview-model-driven-samples/admin-center.png)

4. Seleccione la base de datos de la lista y haga clic en **ABRIR**.

    ![Seleccionar la base de datos](media/overview-model-driven-samples/select-database.png)

5. Vaya a **Configuración/soluciones**.

6. Seleccione la solución para la aplicación que se va a eliminar y haga clic en **Eliminar**.

    ![Eliminar la solución](media/overview-model-driven-samples/delete-solution.png)

*Como alternativa, vaya a la lista de soluciones haciendo clic en **Opciones avanzadas** en el portal de creador y elimine todo el contenido de la dirección URL después de .dynamics.com/*

> [!IMPORTANT]
> No elimine otras soluciones del sistema a menos que sea consciente del impacto.

## <a name="install-or-uninstall-sample-data"></a>Instalar o desinstalar datos de ejemplo
1. Siga los pasos 1 a 4 anteriores.
2. Vaya a **Configuración/Administración de datos/Datos de ejemplo**.
3. Si hay datos de ejemplo instalados, la opción para quitarlos está disponible. En caso contrario, estará disponible la opción para instalar. 

    ![Quitar datos de ejemplo](media/overview-model-driven-samples/remove-sample-data.png)




