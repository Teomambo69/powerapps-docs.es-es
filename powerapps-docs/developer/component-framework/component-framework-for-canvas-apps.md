---
title: Componentes de código para aplicaciones de lienzo | Microsoft Docs
description: Crear componentes de código para aplicaciones de lienzo
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 11/26/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: e10a7c01e40e65e0a65f82713ba920500b8ee5bf
ms.sourcegitcommit: 13d4042c7bd73580cc8c595e137de7e7fec22875
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2020
ms.locfileid: "3170228"
---
# <a name="code-components-for-canvas-apps"></a>Componentes de código para aplicaciones de lienzo

Power Apps component framework permite a los fabricantes de aplicaciones crear componentes de código para usar en una aplicación o a través de aplicaciones. Más información: [Información general de Power Apps component framework](overview.md) 

En esta vista previa pública, Power Apps component framework permite a los creadores de aplicaciones crear componentes de código, depurarlos, importarlos y agregarlos a aplicaciones de lienzo utilizando útiles Power Apps CLI. Solo las API específicas son compatibles con esta vista previa pública. Recomendamos que verifique cada API para determinar si admite aplicaciones de lienzo. 

> [!WARNING]
> Los componentes de código contienen código que Microsoft puede no generar y puede acceder potencialmente a tokens de seguridad y datos. Cuando agrega componentes de código a una aplicación, asegúrese de que las soluciones de componentes de código son de una fuente de confianza.

## <a name="prerequisites"></a>Requisitos previos

1. Se necesita una licencia de Power Apps. Más información: [Licencia de Power Apps component framework](overview.md#licensing)
2. Se requieren privilegios de administrador del sistema para habilitar la característica de componente de Power Apps en el entorno.

## <a name="enable-power-apps-component-framework-feature"></a>Habilite la característica Power Apps component framework

Para agregar componentes de código a una aplicación, debe habilitar la característica Power Apps component framework en cada entorno donde desea usarla. Para permitir a un entorno que use componentes de código en sus aplicaciones:

1. Inicie sesión en [Power Apps](https://powerapps.microsoft.com/).

2. Seleccione el icono **Configuraciń** y, a continuación, seleccione **Centro de administración**.
    
    ![Configuración y Centro de administración](media/select-admin-center-from-settings.png "Configuración y Centro de administración") 

3. Seleccione la pestaña **Entornos** en el panel izquierdo y seleccione el entorno donde desea habilitar esta característica, seleccione los puntos suspensivos (**...**) y luego seleccione **Configuración**.

4. En pestaña **Productos**, seleccione **Características**.

   ![Habilitar Power Apps component framework](media/enable-pcf-feature.png "Habilitar Power Apps component framework")

5. De la lista de características disponibles, configure la opción a **Activada** bajo **Power Apps component framework para aplicaciones de lienzo** y haga clic en **Guardar**.

6. Ahora, abra la aplicación donde desea agregar el componente de código y navegue hasta **Archivo** > **Configuración** y seleccione **Configuración avanzada**.

   ![Habilitar componentes para Power Apps component framework](media/enable-components-for-pcf.png "Habilitar componentes para Power Apps component framework")
   
7. Active la opción **Componentes** como **Activada** en la sección **Características experimentales**.

## <a name="implementing-code-components"></a>Implementar componente de código

Después de habilitar la característica Power Apps component framework en el entorno, puede empezar a implementar la lógica para los componentes de código.

 El tema [Cree su primer componente de código](implementing-controls-using-typescript.md) demuestra el proceso paso a paso para crear componentes de código.

## <a name="add-components-to-a-canvas-app"></a>Agregar componentes a una aplicación de lienzo

Para agregar componentes de código a una aplicación de lienzo:

1. Navegar a Power Apps Studio.
2. Cree una nueva aplicación de lienzo o edite una aplicación existente a la que desee agregar el componente de código.

   > [!IMPORTANT]
   > Asegúrese de que el archivo zip de la solución ya está [importado](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) en Common Data Service antes de continuar con el siguiente paso.

3. Vaya a **Insertar** > **Personalizado** > **Importar componente**. 
 
    ![Insertar componentes](media/insert-components-import.png "Insertar componentes")

4. Seleccione la pestaña **Código**, agregue un componente de la lista y luego seleccione **Importar**. 

    ![Importar componente de ejemplo](media/import-component-add-sample-component.png "Importar componente de ejemplo")

5. Haga clic en el icono **+** en el panel izquierdo y expanda la pestaña de componentes de código para agregar el componente de muestra.

   ![Agregar componente de ejemplo](media/add-sample-component-from-list.png "Agregar componente de ejemplo")

## <a name="delete-a-code-component"></a>Eliminar un componente de código 

Para eliminar un componente de código de una aplicación de lienzo, seleccione el componente de código que desea eliminar y después seleccione el botón **Eliminar** en el menú. Cuando el componente de código se elimina de la aplicación, todos los elementos del componente de código se eliminan de la aplicación y del paquete de la aplicación.

## <a name="update-existing-code-components"></a>Actualizar componentes de código existentes

Cada vez que actualice los componentes de código y desee ver los cambios en tiempo de ejecución, tiene que saltar el atributo `version` en el archivo de manifiesto. Se recomienda saltar siempre la versión del componente cada vez que haga cambios.

> [!NOTE]
> Los componentes de código existentes solo se actualizan cuando la aplicación se cierra o vuelve a abrirse en Power Apps Studio. Cuando vuelva a abrir la aplicación, le pedirá que actualice los componentes de código. Si solo elimina los componentes de código o agrega el componente de código de nuevo a la aplicación no se actualizarán los componentes.

## <a name="see-also"></a>Vea también

[Información general sobre Power Apps component framework](overview.md)<br/>
[Crear el primer componente de código](implementing-controls-using-typescript.md)<br/>
[Más información sobre Power Apps component framework](https://docs.microsoft.com/learn/paths/use-power-apps-component-framework)
