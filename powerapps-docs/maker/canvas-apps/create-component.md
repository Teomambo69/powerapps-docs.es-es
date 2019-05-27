---
title: Crear un componente para aplicaciones de lienzo | Microsoft Docs
description: Introducción a los componentes reutilizables para las aplicaciones de lienzo
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 12/12/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a20218d3670775f67b26c907ce5a3a54fa0af7b
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216665"
---
# <a name="create-a-component-for-canvas-apps"></a>Crear un componente para aplicaciones de lienzo

> [!IMPORTANT]
> Esta característica está todavía experimental y está deshabilitado de forma predeterminada. Para obtener más información, consulte [características experimentales y de vista previa](working-with-experimental.md).

Los componentes son bloques de creación reutilizables para las aplicaciones de lienzo para que los creadores de aplicaciones pueden crear controles personalizados para usarlos en una aplicación o entre aplicaciones. Características avanzadas, como las propiedades personalizadas, habilitar funciones complejas de componentes. Este artículo presentan los conceptos de componente y algunos ejemplos.

Los componentes son útiles en la creación de aplicaciones más grandes que tienen patrones de control similar. Si actualiza una definición de componente, todas las instancias de la aplicación reflejan los cambios. También puede mejorar el rendimiento mediante el uso de uno o más componentes ya no copiar y pegar controles, que duplica la sobrecarga. Los componentes también facilita el desarrollo en colaboración y normaliza la apariencia y funcionamiento de una organización.

## <a name="prerequisite"></a>Requisito previo

Abra el **configuración de la aplicación** pantalla, seleccione **configuración avanzada**y habilitar la característica, así como asegurarse de que **representación de aplicación mejorada** también está habilitada.

## <a name="component-canvas"></a>Lienzo de componente

Puede crear un componente de la **componentes** menú en el **insertar** pestaña o, como el siguiente gráfico se muestra, en la barra de navegación izquierdo. Esta lista muestra los componentes que se definen en la aplicación, ordenada por hora de creación.

![Vista de lista de componentes](./media/create-component/list-view.png)

Independientemente del enfoque que se adopte, aparecerá un lienzo vacío, donde puede agregar controles como parte de la definición del componente. Si edita un componente en el lienzo, deberá actualizar las instancias del mismo componente en otras pantallas de la aplicación y otras aplicaciones.

Si selecciona una pantalla, puede seleccionar un componente de la lista de componentes existentes en la barra de navegación izquierda o la **componentes** menú en el **insertar** ficha. Cuando se selecciona un componente, inserte una instancia de ese componente en la pantalla, como insertar un control.

## <a name="scope"></a>Ámbito

Piense en un componente como un cuadro negro encapsulado con propiedades como la interfaz. No se puede obtener acceso a los controles en el componente desde fuera del componente, y no puede hacer referencia a nada fuera el componente desde dentro del componente. Si lo intenta, se producirá un error. Restricciones de ámbito de mantener el contrato de datos de un componente simple y coherente y ayuda a habilitar las actualizaciones de definición de componente sin problemas, especialmente en las aplicaciones. Puede actualizar el contrato de datos del componente mediante la creación de una o varias propiedades personalizadas.

## <a name="variables"></a>Variables

Componentes no son compatibles con el **UpdateContext** funcionan, pero puede crear y actualizar las variables en un componente mediante el uso de la **establecer** función. El ámbito de estas variables se limita al componente, pero se pueden acceder a ellas desde fuera del componente mediante el aprovechamiento de las propiedades de salida personalizado.

## <a name="import-and-export"></a>Importación y exportación

Para importar uno o más componentes de una aplicación a otro, seleccione **importar componentes** en la lista desplegable de componentes. Un cuadro de diálogo enumera todas las aplicaciones que contienen los componentes que tienen permiso para editar. Seleccione una aplicación y, a continuación, seleccione **importar** para importar la versión publicada más reciente de todos los componentes en esa aplicación. Después de importar al menos un componente, puede editar su copia y eliminar cualquiera que no necesita.

> [!div class="mx-imgBorder"]
> ![Cuadro de diálogo Importar componentes](./media/create-component/import-components.png)

Si exporta un componente, cree un archivo local que se puede importar a otra aplicación. Si la aplicación contiene una versión modificada del mismo componente, se le pedirá que decida si desea reemplazar la versión modificada o cancelar la importación. 

## <a name="custom-properties"></a>Propiedades personalizadas

Un componente puede recibir valores de entrada y emitir los datos si crea una o varias propiedades personalizadas. Estos escenarios son avanzados y tendrá que comprender las fórmulas y contratos vinculantes.

Una propiedad de entrada es el modo en que un componente recibe los datos que se usará en el componente. Propiedades de entrada aparecen en la **propiedades** ficha del panel derecho, si se selecciona una instancia del componente. Puede configurar las propiedades de entrada con expresiones o fórmulas, tal como configurar las propiedades estándar en otros controles. Otros controles disponen de las propiedades de entrada, como el **predeterminado** propiedad de un **entrada de texto** control.

Propiedades de salida pueden emitir el estado de datos o un componente. Por ejemplo, el **seleccionados** propiedad en un **galería** control es una propiedad de salida. Cuando se crea una propiedad de salida, puede determinar qué otros controles pueden consultar el estado del componente.

Aún más en este tutorial explica estos conceptos.

## <a name="create-an-example-component"></a>Crear un componente de ejemplo

En este ejemplo, creará un componente de menú que se parece a este gráfico y en el que puede cambiar el texto y usar en varias pantallas, aplicaciones o ambas:

![Galería final](./media/create-component/menu-instance.png)

1. En PowerApps Studio, cree una aplicación en blanco.

1. En la barra de navegación izquierda, abra la lista de componentes y, a continuación, seleccione **nuevo componente**.

    ![Lista de componentes](./media/create-component/component-list.png)

1. Al mantener el mouse sobre el componente nuevo, seleccione el botón de puntos suspensivos (...), seleccione **cambiar el nombre de**y, a continuación, escriba o pegue **MenuComponent**.

1. En el panel derecho, establezca el ancho del componente **150** y su alto **250**y, a continuación, seleccione **nueva propiedad personalizada**.

    ![Nueva propiedad](./media/create-component/new-property.png)

1. En el **nombre para mostrar**, **nombre de la propiedad**, y **descripción** cuadros, escriba o pegue **elementos**.

    ![Nombre para mostrar, nombre de propiedad, los cuadros de descripción](./media/create-component/property-names.png)

    Cuando se especifica un nombre de propiedad, no incluya espacios porque hará referencia al componente con este nombre al escribir una fórmula (por ejemplo, **ComponentName.PropertyName**).

    El nombre para mostrar aparece en la **propiedades** ficha del panel derecho, si selecciona el componente. Un nombre para mostrar descriptivo le y otros fabricantes comprender el propósito de esta propiedad. El **descripción** aparece en una información sobre herramientas si sitúa sobre el nombre para mostrar de esta propiedad en el **propiedades** ficha.

1. En el **tipo de datos** lista, seleccione **tabla**y, a continuación, seleccione **crear**.

    ![Tipo de datos de la propiedad](./media/create-component/property-data-type.png)

    El **elementos** propiedad está establecida en un valor predeterminado según el tipo de datos que ha especificado, pero puede establecerlo en un valor que se adapte a sus necesidades. Si especifica un tipo de datos de **tabla** o **registro**, es posible que desee cambiar el valor de la **elementos** propiedad para que coincida con el esquema de datos que desea que el componente de entrada. En este caso, va a cambiar a una lista de cadenas.

    Puede establecer el valor de propiedad en la barra de fórmulas si selecciona el nombre de la propiedad en el **propiedades** ficha del panel derecho.

    ![Propiedad de entrada personalizada en la pestaña Propiedades](./media/create-component/properties-tab.png)

    Como el gráfico se muestra, también puede editar el valor de propiedad en el **avanzadas** ficha del panel derecho.

1. Establezca el componente **elementos** propiedad en esta fórmula:

    ```powerapps-dot
    Table({Item:"SampleText"})
    ```

    ![Fórmula](./media/create-component/set-component-items.png)

1. En el componente, inserte un valor en blanco vertical **galería** control.

1. Asegúrese de que se muestra la lista de propiedades el **elementos** propiedad (tal como se hace de forma predeterminada) y, a continuación, establezca el valor de esa propiedad en esta expresión:

    ```powerapps-dot
    MenuComponent.Items
    ```

    De este modo, el **elementos** propiedad de la **galería** control lee y depende de la **elementos** propiedad del componente de entrada.

1. Establecer el **galería** del control **BorderThickness** propiedad **1** y su **Tamañodeplantilla** propiedad **50**.

1. En la plantilla de la **galería** control, agregue un **etiqueta** control.

    ![Agregar etiqueta y establezca el borde de la Galería](./media/create-component/add-label.png)

A continuación, deberá agregar el componente a una pantalla y especificar una tabla de cadenas para el componente mostrar.

1. En la barra de navegación izquierdo, seleccione la lista de pantallas y, a continuación, seleccione la pantalla predeterminada.

    ![Pantalla predeterminada](./media/create-component/default-screen.png)

1. En el **insertar** pestaña, abra el **componentes** menú y, a continuación, seleccione **MenuComponent**.

    ![Insertar](./media/create-component/insert.png)

    El nuevo componente se denomina **MenuComponent_1** de forma predeterminada.

1. Establecer el **elementos** propiedad de **MenuComponent_1** en esta fórmula:

    ```powerapps-dot
    Table({Item:"Home"}, {Item:"Admin"}, {Item:"About"}, {Item:"Help"})
    ```

    Esta instancia es similar a este gráfico, pero puede personalizar el texto y otras propiedades de cada instancia.

    ![Galería final](./media/create-component/menu-instance.png)

Hasta ahora, ha creado un componente y agregarlo a una aplicación. A continuación, creará una propiedad de salida que refleja el elemento que el usuario selecciona en el menú.

1. Abra la lista de componentes y, a continuación, seleccione **MenuComponent**.

1. En el panel derecho, seleccione el **propiedades** pestaña y, a continuación, seleccione **nueva propiedad personalizada**.

1. En el **nombre para mostrar**, **nombre de la propiedad**, y **descripción** cuadros, escriba o pegue **seleccionados**.

1. En **tipo de propiedad**, seleccione **salida**y, a continuación, seleccione **crear**.

1. En el **avanzadas** pestaña, establezca el valor de la **seleccionados** propiedad en esta expresión, ajuste el número en el nombre de la Galería si es necesario:

    ```powerapps-dot
    Gallery1.Selected.Item
    ```

    ![Panel avanzado](./media/create-component/advance.png)

1. En la pantalla predeterminada de la aplicación, agregue una etiqueta y establezca su **texto** propiedad en esta expresión, ajuste el número en el nombre del componente si es necesario:

    ```powerapps-dot
    MenuComponent_1.Selected
    ```

    Tenga en cuenta que **MenuComponent_1** es el nombre predeterminado de una instancia, no el nombre de la definición del componente. Puede cambiar el nombre de cualquier instancia.

1. Mientras mantiene presionada la tecla Alt, seleccione cada elemento en el menú.

    El **etiqueta** control refleja el elemento de menú que ha seleccionado más recientemente.

## <a name="known-limitations"></a>Limitaciones conocidas

- Cuando se redactó este documento, los orígenes de datos no se guardan con los componentes, por lo que se deshabilitan los formularios y las tablas de datos.
- PowerApps no admite colecciones de componentes.
- No se puede insertar un componente en una galería, un formulario o una tarjeta de datos.
- Una instancia de un componente principal es un local maestro y ámbito de la aplicación. Si cambia una instancia de patrón, solo las copias del componente dentro de la aplicación reflejará el cambio. Copias en otras aplicaciones seguirá siendo el mismo, a menos que vuelva a importar la biblioteca de componentes. Todas las instancias maestras en esas aplicaciones se detectarán automáticamente y actualizadas.
- No se puede empaquetar archivos multimedia al importar un componente.
