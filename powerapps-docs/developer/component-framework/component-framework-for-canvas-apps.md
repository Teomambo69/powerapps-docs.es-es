---
title: PowerApps component framework para aplicaciones de lienzo  | Microsoft Docs
description: Crear componentes de código para aplicaciones de lienzo
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 08/31/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: e7671c01a9c21dda56579801b77e1480abab5e29
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753964"
---
# <a name="powerapps-component-framework-for-canvas-apps"></a>PowerApps component framework para aplicaciones de lienzo

> [!IMPORTANT]
> Esta característica sigue siendo piloto y está deshabilitada de forma predeterminada. Para obtener más información, consulte [Características en versión preliminar y piloto](../../maker/canvas-apps/working-with-experimental.md).

PowerApps component framework permite a los fabricantes de aplicaciones crear componentes de código para usar en una aplicación o a través de aplicaciones. Más información: [Información general de PowerApps component framework](overview.md) 

En esta vista previa piloto, PowerApps component framework permite a los fabricantes de aplicaciones crear componentes de código, depurar, importar, y agregarlos a aplicaciones de lienzo mediante útiles PowerApps CLI. Solo se admiten API específicas en esta vista previa piloto. Es recomendable que compruebe cada API para determinar si admite aplicaciones de lienzo. 

> [!WARNING]
> Los componentes de código contienen código que Microsoft puede no generar y puede acceder potencialmente a tokens de seguridad y datos. Cuando agrega componentes de código a una aplicación, asegúrese de que las soluciones de componentes de código son de una fuente de confianza.

## <a name="prerequisites"></a>Requisitos previos

Se requieren privilegios de administrador del sistema para habilitar la característica de componente de PowerApps en el entorno.

> [!IMPORTANT]
> De forma predeterminada PowerApps component framework está habilitado para las aplicaciones basadas en modelo.

## <a name="enable-powerapps-component-framework-feature"></a>Habilite la característica PowerApps component framework

Para agregar componentes de código a una aplicación, debe habilitar la característica PowerApps component framework en cada entorno donde desea usarla. Para permitir a un entorno que use componentes de código en sus aplicaciones:

1. Inicie sesión en [PowerApps](https://powerapps.microsoft.com/).

2. Seleccione el icono **Configuraciń** y, a continuación, seleccione **Centro de administración**.
    
    ![Configuración y Centro de administración](media/select-admin-center-from-settings.png "Configuración y Centro de administración") 

3. Seleccione el entorno donde desea habilitar esta característica, seleccione puntos suspensivos (**...**) y luego seleccione **Configuración**.

4. En pestaña **Productos**, seleccione **Características**.

   ![Habilitar PowerApps component framework](media/enable-pcf-feature.png "Habilitar PowerApps component framework")

5. En la lista de características disponibles, establezca la opción en **Activado** en **PowerApps component framework para aplicaciones de lienzo**.

6. Ahora, abra la aplicación donde desee agregar el componente de código y navegue a **Archivo** > **Configuración de la aplicación** y seleccione **Configuración avanzada**.

   ![Habilitar componentes para PowerApps component framework](media/enable-components-for-pcf.png "Habilitar componentes para PowerApps component framework")
   
7. Active la opción **Componentes** como **Activada** en la sección **Características experimentales**.

## <a name="implementing-code-components"></a>Implementar componente de código

Después de habilitar la característica PowerApps component framework en el entorno, puede empezar a implementar la lógica para los componentes de código. El tema [implementar componente de ejemplo](implementing-controls-using-typescript.md) demuestra el proceso paso a paso para crear componentes de código que implementan lógica personalizada y archivo de manifiesto, ejecutan el proceso de depuración, crean un archivo zip de solución e importan la solución a Common Data Service.

> [!NOTE]
> Implementar componentes de código es igual para las aplicaciones basadas en modelo y las aplicaciones de lienzo (vista previa experimental). La única diferencia es agregar los componentes de código. 

## <a name="add-components-to-a-canvas-app"></a>Agregar componentes a una aplicación de lienzo

> [!NOTE]
> Para agregar componentes de código a un campo o una entidad para las aplicaciones basadas en modelo, consulte [Agregar componentes de código a aplicaciones basadas en modelo](add-custom-controls-to-a-field-or-entity.md)

Para agregar componentes de código a una aplicación de lienzo:

1. Navegar a PowerApps Studio.
2. Cree una nueva aplicación de lienzo o edite una aplicación existente a la que desee agregar el componente de código.

   > [!IMPORTANT]
   > Asegúrese de que el archivo zip de la solución ya está [importado](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) en Common Data Service antes de continuar con el siguiente paso.

3. Vaya a **Insertar** > **Componentes** > **Componente de importación**. 
 
    ![Insertar componentes](media/insert-components-import.png "Insertar componentes")

4. Seleccione la pestaña **Código (experimental)**, agregue un componente de la lista y, a continuación seleccione **Importar**. Esto agrega el componente de ejemplo en el menú **Componentes**.

    ![Importar componente de ejemplo](media/import-component-add-sample-component.png "Importar componente de ejemplo")

5. Vaya a **Componentes** y seleccione el componente para agregarlo a la aplicación.

   ![Agregar componente de ejemplo](media/add-sample-component-from-list.png "Agregar componente de ejemplo")

## <a name="delete-a-code-component"></a>Eliminar un componente de código 

Para eliminar un componente de código de una aplicación de lienzo, seleccione el componente de código que desea eliminar y después seleccione el botón **Eliminar** en el menú. Cuando se elimina el componente de código de la aplicación, todos los elementos de componente de código se eliminan de la aplicación y del paquete de la aplicación. 

## <a name="update-existing-code-components"></a>Actualizar componentes de código existentes

Cuando actualiza los componentes del código, especificamos el atributo *versión* en el archivo de manifiesto, por lo que los últimos cambios se reflejan en tiempo de ejecución. Para aplicaciones de lienzo, cuando actualice los componentes de código existentes, no necesitará actualizar el atributo *versión*. Por diseño, las aplicaciones de lienzo recogen el último componente de código y lo muestran en tiempo de ejecución. Solo una sola versión del mismo componente puede existir en aplicaciones de lienzo.

> [!NOTE]
> Los componentes de código existentes solo se actualizan cuando la aplicación se cierra o vuelve a abrirse en PowerApps Studio. Cuando vuelva a abrir la aplicación, le pedirá que actualice los componentes de código. Si solo elimina los componentes de código o agrega el componente de código de nuevo a la aplicación no se actualizarán los componentes.

## <a name="see-also"></a>Vea también

[Información general sobre PowerApps component framework](overview.md)<br/>
[Implementar componente de ejemplo](implementing-controls-using-typescript.md)

