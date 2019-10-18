---
title: Marco de componentes de PowerApps para aplicaciones de Canvas | Microsoft Docs
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
ms.openlocfilehash: e1c6b4bad1280bdabf8c27e30396b368276ff10b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347231"
---
# <a name="powerapps-component-framework-for-canvas-apps"></a>Marco de componentes de PowerApps para aplicaciones de Canvas

> [!IMPORTANT]
> Esta característica sigue siendo experimental y está deshabilitada de forma predeterminada. Para obtener más información, vea [características experimentales y de vista previa](../../maker/canvas-apps/working-with-experimental.md).

El marco de componentes de PowerApps permite a los responsables de aplicaciones crear componentes de código para usarlos en una aplicación o en todas las aplicaciones. Más información: [información general sobre el marco de componentes de PowerApps](overview.md) 

En esta versión preliminar experimental, el marco de componentes de PowerApps permite a los responsables de aplicaciones crear componentes de código, depurar, importar y agregarlos a las aplicaciones de Canvas con las herramientas de la CLI de PowerApps. En esta versión preliminar experimental solo se admiten API específicas. Se recomienda que compruebe cada API para determinar si es compatible con las aplicaciones de canvas. 

> [!WARNING]
> Los componentes de código contienen código que no puede ser generado por Microsoft y que puede tener acceso a los tokens y datos de seguridad. Al agregar componentes de código a una aplicación, asegúrese de que las soluciones de componentes de código provienen de un origen de confianza.

## <a name="prerequisites"></a>Requisitos previos

Se requieren privilegios de administrador del sistema para habilitar la característica del componente PowerApps en el entorno.

> [!IMPORTANT]
> De forma predeterminada, el marco de componentes de PowerApps está habilitado para aplicaciones controladas por modelos.

## <a name="enable-powerapps-component-framework-feature"></a>Habilitar la característica de marco de componentes de PowerApps

Para agregar componentes de código a una aplicación, debe habilitar la característica de marco de componentes de PowerApps en cada entorno en el que desee usarlos. Para habilitar un entorno para que use componentes de código dentro de sus aplicaciones:

1. Inicie sesión en [PowerApps](https://powerapps.microsoft.com/en-us/).

2. Seleccione el icono de **configuración** y, a continuación, seleccione **centro de administración**.
    
    Configuración y centro de ![Administración](media/select-admin-center-from-settings.png "configuración y centro de administración") 

3. Seleccione el entorno en el que quiere habilitar esta característica, seleccione los puntos suspensivos ( **...** ) y, a continuación, seleccione **configuración**.

4. En la pestaña **productos** , seleccione **características**.

   ![Habilitar el marco de componentes de powerapps](media/enable-pcf-feature.png "Habilitar el marco") de componentes de powerapps

5. En la lista de características disponibles, establezca el conmutador en **activado** en el **marco de componentes de PowerApps para aplicaciones de canvas**.

6. Ahora, abra la aplicación en la que desea agregar el componente de código y vaya a **archivo**  >  configuración de la**aplicación** y seleccione **Configuración avanzada**.

   ![Habilitar componentes para el marco de componentes de powerapps](media/enable-components-for-pcf.png "Habilitar componentes para el marco de componentes de powerapps")
   
7. Active la opción activar los **componentes** en la sección **de** la **característica experimental** .

## <a name="implementing-code-components"></a>Implementar componentes de código

Después de habilitar la característica de marco de componentes de PowerApps en su entorno, puede empezar a implementar la lógica para los componentes de código. En el tema [implementar el componente de ejemplo](implementing-controls-using-typescript.md) se muestra el proceso paso a paso para crear componentes de código que implementan la lógica personalizada y el archivo de manifiesto, la ejecución del proceso de depuración, la creación de un archivo zip de la solución y la importación de la solución en común. Servicio de datos.

> [!NOTE]
> La implementación de componentes de código es la misma para aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental). La única diferencia es agregar los componentes de código. 

## <a name="add-components-to-a-canvas-app"></a>Agregar componentes a una aplicación de lienzo

> [!NOTE]
> Para agregar componentes de código a un campo o una entidad para aplicaciones controladas por modelos, vea [agregar componentes de código a aplicaciones controladas por modelos](add-custom-controls-to-a-field-or-entity.md) .

Para agregar componentes de código a una aplicación de lienzo:

1. Vaya a PowerApps Studio.
2. Cree una nueva aplicación de lienzo o edite una aplicación existente a la que desee agregar el componente de código.

   > [!IMPORTANT]
   > Asegúrese de que el archivo zip de la solución ya se haya [importado](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/import-update-export-solutions) en Common Data Service antes de continuar con el paso siguiente.

3. Vaya a **insertar**  > **componentes**  > **componente de importación**. 
 
    ![Insertar]componentes(media/insert-components-import.png "insertar componentes")

4. Seleccione la pestaña **código (experimental)** , agregue un componente de la lista y, a continuación, seleccione **importar**. Esto agrega el componente de ejemplo en el menú **componentes** .

    ![Importar]componente de ejemplo de(media/import-component-add-sample-component.png "importación") de componentes de ejemplo

5. Vaya a **componentes** y seleccione el componente para agregarlo a la aplicación.

   ![Agregar]componente de ejemplo Agregar componente de(media/add-sample-component-from-list.png "ejemplo")

## <a name="delete-a-code-component"></a>Eliminar un componente de código 

Para eliminar un componente de código de una aplicación de lienzo, seleccione el componente de código que desea eliminar y, a continuación, seleccione el botón **eliminar** en el menú. Cuando se elimina el componente de código de la aplicación, se eliminan todos los elementos de componente de código de la aplicación y el paquete de la aplicación. 

## <a name="update-existing-code-components"></a>Actualizar componentes de código existentes

Cuando se actualizan los componentes de código, se especifica el atributo de *versión* en el archivo de manifiesto, por lo que los cambios más recientes se reflejan en el tiempo de ejecución. En el caso de las aplicaciones de Canvas, al actualizar los componentes de código existentes, no es necesario actualizar el atributo *version* . Por diseño, las aplicaciones de canvas recogen el componente de código más reciente y lo muestran en tiempo de ejecución. En las aplicaciones de lienzo solo puede existir una versión única del mismo componente.

> [!NOTE]
> Los componentes de código existentes solo se actualizan cuando la aplicación se cierra o se vuelve a abrir en PowerApps Studio. Cuando vuelva a abrir la aplicación, le pedirá que actualice los componentes de código. La simple eliminación de los componentes de código o de volver a agregar el componente de código a la aplicación no actualiza los componentes.

## <a name="see-also"></a>Vea también

[Información general sobre el marco de componentes de PowerApps](overview.md)<br/>
[Implementar componente de ejemplo](implementing-controls-using-typescript.md)

