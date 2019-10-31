---
title: PowerApps component framework para aplicaciones de lienzo  | Microsoft Docs
description: Crear componentes de código para aplicaciones de lienzo
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 08/31/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
---

# <a name="powerapps-component-framework-for-canvas-apps"></a>PowerApps component framework para aplicaciones de lienzo

> [!IMPORTANT]
> Esta característica sigue siendo piloto y está deshabilitada de forma predeterminada. Para obtener más información, consulte [Características en versión preliminar y piloto](../../maker/canvas-apps/working-with-experimental.md).

PowerApps component framework permite a los fabricantes de aplicaciones crear componentes de código para usar en una aplicación o a través de aplicaciones. Más información: [Información general de PowerApps component framework](overview.md) 

En esta vista previa piloto, PowerApps component framework permite a los fabricantes de aplicaciones crear componentes de código, depurar, importar, y agregarlos a aplicaciones de lienzo mediante útiles PowerApps CLI. Solo se admiten API específicas en esta vista previa piloto. Se recomienda comprobar cada API si admite aplicaciones de lienzo o no. 

> [!WARNING]
> Los componentes de código contienen código que Microsoft puede no generar y puede acceder potencialmente a tokens de seguridad y datos. Cuando agrega componentes de código a una aplicación, asegúrese de que las soluciones de componentes de código son de una fuente de confianza.

## <a name="prerequisites"></a>Requisitos previos

1. Se requieren privilegios de administrador del sistema para habilitar la característica de componente de PowerApps en el entorno.

> [!IMPORTANT]
> De forma predeterminada PowerApps component framework está habilitado para las aplicaciones basadas en modelo.

## <a name="enable-powerapps-component-framework-feature"></a>Habilite la característica PowerApps component framework

Para agregar componentes de código a una aplicación, debe habilitar la característica PowerApps component framework en cada entorno donde desea usarla. Para permitir a un entorno que use componentes de código en sus aplicaciones:

1. Inicie sesión en [PowerApps](https://powerapps.microsoft.com/en-us/).

2. Haga clic en el icono **Configuración** y a continuación seleccione **Centro de administración**.
    
    ![Centro de administración de configuración](media/select-admin-center-from-settings.png "Centro de administración de configuración") 

3. Seleccione el entorno donde desea habilitar esta característica y haga clic en **...** y después seleccione **Configuración**.

4. En pestaña **Productos**, seleccione **Características**.

   ![Habilitar PCF](media/enable-pcf-feature.png "Habilitar PCF")

5. En la lista de características disponibles, active el conmutador bajo **PowerApps component framework para aplicaciones de lienzo**.

6. Ahora, abra la aplicación donde desee agregar el componente de código y navegue a **Archivo** > **Configuración de la aplicación** y seleccione **Configuración avanzada**.

   ![Habilitar componentes para pcf](media/enable-components-for-pcf.png "Habilitar componentes para pcf")
   
7. Active el conmutador **Componentes** en la sección **Característica piloto**.

## <a name="implementing-code-components"></a>Implementar componente de código

Después de habilitar la característica PowerApps component framework en el entorno, puede empezar a implementar la lógica para los componentes de código. El tema [implementar componente de ejemplo ](implementing-controls-using-typescript.md) demuestra el proceso paso a paso para crear componentes de código directamente desde la implementación de la lógica personalizada, archivo de manifiesto, proceso de depuración, creando un archivo zip de la solución y importando la solución a Common Data Service.

> [!NOTE]
> Implementar componentes de código es igual para aplicaciones basadas en modelo y aplicaciones de lienzo (vista previa piloto). La única diferencia es agregar los componentes de código. 

## <a name="add-components-to-a-canvas-app"></a>Agregar componentes a una aplicación de lienzo

Para agregar componentes de código a una aplicación de lienzo:

> [!NOTE]
> Para agregar componentes de código a un campo o una entidad para las aplicaciones basadas en modelo, consulte [Agregar componentes de código a aplicaciones basadas en modelo](add-custom-controls-to-a-field-or-entity.md)

1. Navegar a PowerApps Studio.
2. Cree una nueva aplicación de lienzo o edite una aplicación existente a la que desee agregar componente de código.

   > [!IMPORTANT]
   > Asegúrese de que el archivo zip de la solución ya está [importada](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/import-update-export-solutions) en Common Data Service antes de ir al paso siguiente.

3. Haga clic en **Insertar** > **Componentes** > .**Importar componente** 
 
    ![Insertar componentes](media/insert-components-import.png "Insertar componentes")

4. Seleccione la pestaña **Código (piloto)** y agregue un componente de la lista y haga clic en **Importar**. Esto agrega el componente de ejemplo en el menú **Componentes**.

    ![Importar componente de ejemplo](media/import-component-add-sample-component.png "Insertar componente de ejemplo")

5. Vaya a **Componentes** y seleccione el componente para agregarlo a la aplicación.

   ![Importar componente de ejemplo](media/add-sample-component-from-list.png "Importar componente de ejemplo")

## <a name="delete-a-code-component"></a>Eliminar un componente de código 

Para eliminar un componente de código de una aplicación de lienzo, seleccione el componente de código que desee eliminar y presione el botón **Eliminar** en el menú. Cuando el componente de código se elimina de la aplicación, todos los elementos de componente de código se eliminan de la aplicación y el paquete de la aplicación. 

## <a name="updating-existing-code-components"></a>Actualizar componentes de código existentes

Cuando actualice los componentes del código, especificamos el atributo *versión* en el archivo de manifiesto, de modo que los últimos cambios se reflejen en tiempo de ejecución. Para aplicaciones de lienzo, cuando actualice los componentes de código existentes, no necesitará actualizar el atributo *versión*. Por diseño, las aplicaciones de lienzo recogen el último componente de código y lo muestran en tiempo de ejecución. Solo una sola versión del mismo componente puede existir en aplicaciones de lienzo.

> [!NOTE]
> Los componentes de código existentes solo se actualizan cuando la aplicación se cierra o vuelve a abrir en PowerApps Studio. Cuando vuelva a abrir la aplicación, le pedirá que actualice los componentes de código. Si solo elimina los componentes de código o agrega el componente de código de nuevo a la aplicación no se actualizarán los componentes.

## <a name="see-also"></a>Vea también

[Información general sobre PowerApps component framework](overview.md)<br/>
[Implementar componente de ejemplo](implementing-controls-using-typescript.md)

