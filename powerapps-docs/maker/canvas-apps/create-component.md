---
title: Crear un componente para las aplicaciones de Canvas | Microsoft Docs
description: Introducción a los componentes reutilizables para aplicaciones de Canvas
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3c2864a7953e115c650ff5cee879d2a1227acdb4
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "77911214"
---
# <a name="create-a-component-for-canvas-apps"></a>Crear un componente para las aplicaciones de Canvas

> [!IMPORTANT]
> Esta característica todavía está en versión preliminar pública. Para obtener más información, vea [Características en versión preliminar y experimentales](working-with-experimental.md).

Los componentes son bloques de creación reutilizables para aplicaciones de lienzo, de modo que los responsables de aplicaciones puedan crear controles personalizados para usarlos dentro de una aplicación o entre aplicaciones mediante la [biblioteca de componentes](component-library.md). Los componentes pueden usar características avanzadas, como propiedades personalizadas y habilitar funcionalidades complejas. En este artículo se presentan conceptos de componentes y algunos ejemplos.

Los componentes son útiles para compilar aplicaciones de mayor tamaño que tengan patrones de control similares. Si actualiza una definición de componente dentro de la aplicación, todas las instancias de la aplicación reflejarán los cambios. Los componentes también reducen la duplicación de esfuerzos, ya que eliminan la necesidad de copiar y pegar controles y mejorar el rendimiento. Los componentes también ayudan a crear un desarrollo colaborativo y normalizan la apariencia y el funcionamiento de una organización cuando se usa una [biblioteca de componentes](component-library.md).

## <a name="components-in-canvas-app"></a>Componentes de la aplicación Canvas

Puede crear un componente desde una aplicación, tal como se explica en este artículo, o mediante la creación de un nuevo componente dentro de una [biblioteca de componentes](component-library.md). Se debe usar una biblioteca de componentes para los requisitos de uso de componentes en varias pantallas de la aplicación. También puede copiar los componentes existentes en una biblioteca de componentes existente o en una nueva.

Para crear un componente dentro de una aplicación, vaya a la **vista de árbol**, seleccione la pestaña **componentes** y, después, seleccione **nuevo componente**:

![Crear nuevo componente personalizado con la vista de árbol](./media/create-component/insert-new-component-treeview.png)

Al seleccionar **nuevo componente** , se abre un lienzo vacío. Puede Agregar controles como parte de la definición del componente en el lienzo. Si edita un componente en el lienzo, actualizará las instancias del mismo componente en otras pantallas de la aplicación. Las aplicaciones que reutilizan un componente ya creado también pueden recibir actualizaciones de componentes después de publicar cambios en los componentes.

Puede seleccionar un componente de la lista de componentes existentes en el panel de navegación izquierdo después de seleccionar una pantalla. Al seleccionar un componente, se inserta una instancia de ese componente en la pantalla; del mismo modo que inserta un control.

Los componentes disponibles dentro de la aplicación se muestran en categoría **personalizada** en lista de componentes dentro de la vista de árbol. Los componentes de las bibliotecas de componentes importados aparecen en la categoría **componentes de biblioteca** :

![Inserción de componentes en la aplicación](./media/create-component/insert-components.png)

> [!NOTE]
> Los componentes descritos en este artículo son diferentes del marco de trabajo de componentes de Power apps que permite a los desarrolladores y a los desarrolladores crear componentes de código para aplicaciones basadas en modelos y Canvas. Para obtener más información, lea [información general sobre el marco de trabajo de componentes de Power apps](https://docs.microsoft.com/powerapps/developer/component-framework/overview).

## <a name="scope"></a>Ámbito

Piense en un componente como un cuadro negro encapsulado con propiedades como interfaz. No se puede tener acceso a los controles del componente desde fuera del componente. Y no puede hacer referencia a nada fuera del componente desde dentro del componente. La excepción son los orígenes de datos compartidos entre la aplicación y sus componentes. Las restricciones de ámbito mantienen el contrato de datos de un componente de forma sencilla y coherente, y ayudan a habilitar las actualizaciones de definición de componentes, especialmente en las aplicaciones con bibliotecas de componentes. Puede actualizar el contrato de datos del componente creando una o varias propiedades personalizadas.

> [!NOTE]
> Puede insertar instancias de componentes en una pantalla de una biblioteca de componentes y obtener una vista previa de la pantalla con fines de prueba. Además, tenga en cuenta que la biblioteca de componentes no se muestra cuando se usa [Power apps Mobile](https://powerapps.microsoft.com/downloads/).

## <a name="custom-properties"></a>Propiedades personalizadas

Un componente puede recibir valores de entrada y emitir datos si crea una o varias propiedades personalizadas. Estos escenarios son avanzados y requieren que entienda las [fórmulas](formula-reference.md) y los contratos de enlace.

La **propiedad de entrada** es la forma en que un componente recibe los datos que se van a usar en el componente. Las propiedades de entrada aparecen en la pestaña **propiedades** del panel derecho si se selecciona una instancia del componente. Puede configurar las propiedades de entrada con expresiones o fórmulas, al igual que configura las propiedades estándar en otros controles. Otros controles tienen propiedades de entrada, como la propiedad **predeterminada** de un control **entrada de texto** .

La **propiedad Output** se usa para emitir datos o el estado de los componentes. Por ejemplo, la propiedad **seleccionada** en un control de **Galería** es una propiedad de salida. Al crear una propiedad de salida, puede determinar qué otros controles pueden hacer referencia al estado del componente.

En el siguiente tutorial se explican estos conceptos.

## <a name="create-an-example-component"></a>Crear un componente de ejemplo

En este ejemplo, creará un componente de menú similar al siguiente gráfico. Además, puede cambiar el texto posteriormente para usarlo en varias pantallas, aplicaciones o en ambas:

![Galería final](./media/create-component/menu-instance-new.png)

> [!NOTE]
> Se recomienda usar la [biblioteca de componentes](component-library.md) al crear componentes para reutilizarlos. La actualización de componentes dentro de una aplicación solo hace que las actualizaciones de componentes estén disponibles dentro de la aplicación. Al importar componentes de una aplicación a otra, las nuevas actualizaciones de los componentes de la aplicación original no se propagan a la aplicación que importó anteriormente esos componentes. Al usar la biblioteca de componentes, se le pedirá que actualice los componentes si los componentes de una biblioteca se actualizan y publican.

### <a name="create-a-new-component"></a>Crear un nuevo componente

1. Inicie sesión en [make.powerapps.com](https://make.powerapps.com).

1. Seleccione **aplicaciones** y seleccione la **aplicación de lienzo en blanco**. 

1. Proporcione un nombre de aplicación, seleccione cualquier diseño y, a continuación, seleccione **crear**.

1. En la **vista de árbol**, seleccione **componentes** y, a continuación, seleccione **nuevo componente** para crear un componente nuevo.

    ![Crear nuevo componente personalizado con la vista de árbol](./media/create-component/insert-new-component-treeview.png)

1. Seleccione el nuevo componente en el panel de navegación izquierdo, seleccione los puntos suspensivos (...) y seleccione **cambiar nombre**. Escriba o pegue el nombre como **MenuComponent**.

1. En el panel derecho, establezca el ancho del componente en **150** y su alto en **250**y, a continuación, seleccione **nueva propiedad personalizada**. También puede establecer el alto & ancho en cualquier otro valor según corresponda.

    ![Nueva propiedad](./media/create-component/new-property.png)

1. En los cuadros **nombre para mostrar**, nombre de **propiedad**y **Descripción** , escriba o pegue texto como *elementos*.

    ![Nombre para mostrar, nombre de propiedad, cuadros de Descripción](./media/create-component/property-names.png)

    No incluya espacios en el nombre de propiedad, ya que hará referencia al componente con este nombre al escribir una fórmula. Por ejemplo, **ComponentName. PropertyName**.

    El nombre para mostrar aparece en la pestaña **propiedades** del panel derecho si selecciona el componente. Un nombre descriptivo para mostrar ayuda a usted y a otros responsables a entender el propósito de esta propiedad. La **Descripción** aparece en una información sobre herramientas si mantiene el puntero sobre el nombre para mostrar de esta propiedad en la pestaña **propiedades** .

1. En la lista **tipo de datos** , seleccione **tabla**y, a continuación, seleccione **crear**.

    ![Tipo de datos de la propiedad](./media/create-component/property-data-type.png)

    La propiedad **Items** se establece en un valor predeterminado basado en el tipo de datos especificado. Puede establecerlo en un valor que se ajuste a sus necesidades. Si especificó un tipo de datos de **tabla** o **registro**, puede que desee cambiar el valor de la propiedad **Items** para que coincida con el esquema de datos que desea introducir en el componente. En este caso, cambiará a una lista de cadenas.

    Puede establecer el valor de la propiedad en la barra de fórmulas si selecciona el nombre de la propiedad en la pestaña **propiedades** del panel derecho.

    ![Propiedad de entrada personalizada en la pestaña propiedades](./media/create-component/properties-tab.png)

    Como se muestra en el siguiente gráfico, también puede modificar el valor de la propiedad en la pestaña **avanzadas** del panel derecho.

1. Establezca la propiedad **elementos** del componente en esta fórmula:

    ```powerapps-dot
    Table({Item:"SampleText"})
    ```

    ![Fórmula](./media/create-component/set-component-items.png)

1. En el componente, inserte un control **Galería** vertical en blanco y seleccione **diseño** en el panel propiedad como **título**.

1. Asegúrese de que la lista de propiedades muestra la propiedad **Items** (como hace de forma predeterminada). Y, a continuación, establezca el valor de esa propiedad en esta expresión:

    ```powerapps-dot
    MenuComponent.Items
    ```

    De este modo, la propiedad **elementos** del control **Galería** Lee y depende de la propiedad **elementos** entrada del componente.

1. Opcional: establezca la propiedad **BorderThickness** del control de **Galería** en **1** y su propiedad **Template** en **50**. También puede actualizar los valores del grosor del borde y del tamaño de la plantilla a cualquier otro valor según corresponda.

### <a name="add-component-to-a-screen"></a>Agregar componente a una pantalla

A continuación, agregará el componente a una pantalla y especificará una tabla de cadenas para el componente que se va a mostrar.

1. En la barra de navegación izquierda, seleccione la lista de pantallas y, a continuación, seleccione la pantalla predeterminada.

    ![Pantalla predeterminada](./media/create-component/default-screen.png)

1. En la pestaña **Insertar** , abra el menú **componentes** y, a continuación, seleccione **MenuComponent**.

    ![Insertar](./media/create-component/insert.png)

    El nuevo componente se denomina **MenuComponent_1** de forma predeterminada.

1. Establezca la propiedad **Items** de **MenuComponent_1** en esta fórmula:

    ```powerapps-dot
    Table({Item:"Home"}, {Item:"Admin"}, {Item:"About"}, {Item:"Help"})
    ```

    Esta instancia se parece a este gráfico, pero puede personalizar el texto y otras propiedades de cada instancia.

    ![Galería final](./media/create-component/menu-instance-new.png)

### <a name="create-and-use-output-property"></a>Crear y usar la propiedad de salida

Hasta ahora, ha creado un componente y lo ha agregado a una aplicación. A continuación, creará una propiedad de salida que refleje el elemento que el usuario selecciona en el menú.

1. Abra la lista de componentes y, a continuación, seleccione **MenuComponent**.

1. En el panel derecho, seleccione la pestaña **propiedades** y, a continuación, seleccione **nueva propiedad personalizada**.

1. En los cuadros **nombre para mostrar**, nombre de **propiedad**y **Descripción** , escriba o pegue **seleccionado**.

1. En **tipo de propiedad**, seleccione **salida**y, a continuación, seleccione **crear**.

    ![Tipo de propiedad como Output](./media/create-component/output-property-type.png)

1. En la pestaña **Opciones avanzadas** , establezca el valor de la propiedad **seleccionada** en esta expresión, ajustando el número en el nombre de la Galería si es necesario:

    ```powerapps-dot
    Gallery1.Selected.Item
    ```

    ![Panel avanzado](./media/create-component/advance.png)

1. En la pantalla predeterminada de la aplicación, agregue una etiqueta y establezca su propiedad **texto** en esta expresión, ajustando el número en el nombre del componente si es necesario:

    ```powerapps-dot
    MenuComponent_1.Selected
    ```

    **MenuComponent_1** es el nombre predeterminado de una instancia de, no el nombre de la definición del componente. Puede cambiar el nombre de cualquier instancia de.

1. Mientras mantiene presionada la tecla Alt, seleccione cada elemento en el menú.

    El control **etiqueta** refleja el elemento de menú que seleccionó más recientemente.

## <a name="import-and-export-components"></a>Importar y exportar componentes

> [!NOTE]
> Esta característica estará en desuso. Las [bibliotecas de componentes](component-library.md) son la manera recomendada de reutilizar los componentes en las aplicaciones. Cuando se usa la biblioteca de componentes, una aplicación mantiene las dependencias de los componentes que usa. El creador de la aplicación recibirá una alerta cuando las actualizaciones de los componentes dependientes estén disponibles. Por lo tanto, todos los componentes reutilizables nuevos deben crearse dentro de las bibliotecas de componentes.

### <a name="import-components-from-another-app"></a>Importar componentes desde otra aplicación

Para importar uno o más componentes de una aplicación a otra, seleccione **importar componentes** en el menú **Insertar** y, a continuación, use el menú desplegable **personalizado** . O mediante **componentes** en la vista de árbol en el panel de navegación izquierdo.

En un cuadro de diálogo se muestran todas las aplicaciones que contienen los componentes para los que tiene permiso de edición. Seleccione una aplicación y, a continuación, seleccione **importar** para importar la versión publicada más reciente de todos los componentes de esa aplicación. Después de importar al menos un componente, puede editar la copia y eliminar los que no necesite.

![Importar componentes (cuadro de diálogo)](./media/create-component/import-component-screen.png)

Puede guardar una aplicación con componentes existentes en un archivo localmente y, a continuación, volver a usar el archivo importándola. Puede usar el archivo para importar componentes a otra aplicación.

Si la aplicación contiene una versión modificada del mismo componente, se le pedirá que decida si desea reemplazar la versión modificada o cancelar la importación. 

Después de crear los componentes en una aplicación, otras aplicaciones pueden usar los componentes de esta aplicación importándolos.

### <a name="export-components-from-your-app"></a>Exportación de componentes desde la aplicación

Puede exportar componentes a un archivo y descargarlos para importarlos a otra aplicación.

Seleccione la opción **exportar componentes** en la sección **componentes** de la vista de árbol de navegación izquierda:

![Vista de árbol de componentes de exportación](./media/create-component/export-components-treeview.png)

También puede usar el menú **Insertar** y, a continuación, seleccionar la lista desplegable **personalizada** en su lugar.

![Menú de inserción de componentes de exportación](./media/create-component/export-components-insert-menu.png)

Al seleccionar **exportar componentes** se descargan los componentes en un archivo:

![Descargar componente](./media/create-component/download-component.png)

El archivo de componentes descargado utiliza la extensión de nombre de archivo *. msapp* . 

### <a name="import-components-from-exported-components-file"></a>Importar componentes del archivo de componentes exportados

Para importar componentes desde un archivo de componentes exportado, seleccione **importar componentes** en el menú **Insertar** . Y, a continuación, use el menú desplegable **personalizado** o **los componentes** de la vista de árbol en el panel de navegación izquierdo. En el cuadro de diálogo componentes, seleccione **Importar archivo** en lugar de seleccionar otros componentes o aplicaciones:

![Importar archivo de componente](./media/create-component/import-component-file.png)

En el cuadro de diálogo **abrir** , vaya a la ubicación del archivo de componente y seleccione **abrir** para importar los componentes dentro de la aplicación.

### <a name="import-components-from-exported-app"></a>Importar componentes desde la aplicación exportada

Puede guardar una aplicación localmente con la opción **archivo** -> **Guardar como** :

![Guardar aplicación](./media/create-component/save-app-locally.png)

Una vez guardada la aplicación, puede volver a usar los componentes de esta aplicación con el mismo método de importación de componentes desde el archivo. Siga los pasos que se explican en la sección anterior sobre la importación de componentes desde el archivo de componentes exportados.

## <a name="known-limitations"></a>Limitaciones conocidas

- No se pueden guardar orígenes de datos, formularios y tablas de datos con componentes de.
- No se admiten colecciones de componentes.
- No se puede insertar un componente en una galería o un formulario.
- Una instancia maestra de un componente es un maestro local y se centra en la aplicación. Si cambia una instancia maestra, solo se reflejará el cambio en las copias del componente dentro de la aplicación. Las copias en otras aplicaciones seguirán siendo las mismas, a menos que vuelva a importar la biblioteca de componentes. Todas las instancias maestras de esas aplicaciones se detectarán y actualizarán automáticamente.
- No se pueden empaquetar archivos multimedia al importar un componente.
- Los componentes no admiten la función [**UpdateContext**](./functions/function-updatecontext.md) , pero puede crear y actualizar variables en un componente mediante la función [**set**](functions/function-set.md) . El ámbito de estas variables se limita al componente, pero se puede tener acceso a ellas desde fuera del componente a través de las propiedades de salida personalizadas.

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre la [biblioteca de componentes](component-library.md) para crear un repositorio de componentes reutilizables.