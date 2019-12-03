---
title: Crear un componente para las aplicaciones de Canvas | Microsoft Docs
description: Introducción a los componentes reutilizables para aplicaciones de Canvas
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 12/12/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 857ca2c78da5b3a7ced4d4d09dfb335fab02d47c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678704"
---
# <a name="create-a-component-for-canvas-apps"></a>Crear un componente para las aplicaciones de Canvas

> [!IMPORTANT]
> Esta característica sigue siendo experimental y está deshabilitada de forma predeterminada. Para obtener más información, vea [características experimentales y de vista previa](working-with-experimental.md).

Los componentes son bloques de creación reutilizables para aplicaciones de lienzo, de modo que los responsables de aplicaciones puedan crear controles personalizados para usarlos en una aplicación o en todas las aplicaciones. Las características avanzadas, como las propiedades personalizadas, permiten capacidades complejas en los componentes de. En este artículo se presentan conceptos de componentes y algunos ejemplos.

Los componentes son útiles para compilar aplicaciones de mayor tamaño que tengan patrones de control similares. Si actualiza una definición de componente, todas las instancias de la aplicación reflejarán los cambios. También puede mejorar el rendimiento mediante uno o varios componentes, ya que no copia y pega los controles, lo que duplica la sobrecarga. Los componentes también facilitan el desarrollo colaborativo y normaliza la apariencia y el funcionamiento de una organización.

## <a name="prerequisite"></a>Requisito previo

Abra la pantalla de configuración de la **aplicación** , seleccione **Configuración avanzada**y habilite la característica, además de asegurarse de que la **representación de aplicaciones mejorada** también está habilitada.

## <a name="component-canvas"></a>Lienzo de componentes

Puede crear un componente desde el menú **componentes** en la pestaña **Insertar** o, como se muestra en el siguiente gráfico, en la barra de navegación izquierda. Esta lista muestra los componentes que se definen en la aplicación, ordenados por hora de creación.

![Vista de lista de componentes](./media/create-component/list-view.png)

Independientemente del enfoque que tome, aparece un lienzo vacío, donde puede Agregar controles como parte de la definición del componente. Si edita un componente en el lienzo, actualizará las instancias del mismo componente en otras pantallas de aplicaciones y otras aplicaciones.

Si selecciona una pantalla, puede seleccionar un componente de la lista de componentes existentes en la barra de navegación izquierda o en el menú **componentes** de la pestaña **Insertar** . Al seleccionar un componente, se inserta una instancia de ese componente en la pantalla, de la misma forma que se inserta un control.

## <a name="scope"></a>Ámbito

Piense en un componente como un cuadro negro encapsulado con propiedades como interfaz. No se puede tener acceso a los controles del componente desde fuera del componente, y no se puede hacer referencia a nada fuera del componente desde dentro del componente. Si lo intenta, aparece un error. Las restricciones de ámbito mantienen el contrato de datos de un componente de forma sencilla y coherente, y ayudan a habilitar actualizaciones de definición de componentes sin problemas, especialmente en las aplicaciones. Puede actualizar el contrato de datos del componente creando una o varias propiedades personalizadas.

## <a name="variables"></a>Variable

Los componentes no admiten la función **UpdateContext** , pero puede crear y actualizar variables en un componente mediante la función **set** . El ámbito de estas variables se limita al componente, pero se puede tener acceso a ellas desde fuera del componente aprovechando las propiedades de salida personalizadas.

## <a name="import-and-export"></a>Importar y exportar

Para importar uno o más componentes de una aplicación a otra, seleccione **importar componentes** en la lista desplegable de componentes. En un cuadro de diálogo se muestran todas las aplicaciones que contienen los componentes para los que tiene permiso de edición. Seleccione una aplicación y, a continuación, seleccione **importar** para importar la versión publicada más reciente de todos los componentes de esa aplicación. Después de importar al menos un componente, puede editar la copia y eliminar los que no necesite.

> [!div class="mx-imgBorder"]
> ![cuadro de diálogo Importar componentes](./media/create-component/import-components.png)

Si exporta un componente, se crea un archivo local que se puede importar a otra aplicación. Si la aplicación contiene una versión modificada del mismo componente, se le pedirá que decida si desea reemplazar la versión modificada o cancelar la importación. 

## <a name="custom-properties"></a>Propiedades personalizadas

Un componente puede recibir valores de entrada y emitir datos si crea una o varias propiedades personalizadas. Estos escenarios son avanzados y requieren que entienda las fórmulas y los contratos de enlace.

Una propiedad de entrada es la forma en que un componente recibe los datos que se van a usar en el componente. Las propiedades de entrada aparecen en la pestaña **propiedades** del panel derecho si se selecciona una instancia del componente. Puede configurar las propiedades de entrada con expresiones o fórmulas, al igual que configura las propiedades estándar en otros controles. Otros controles tienen propiedades de entrada, como la propiedad **predeterminada** de un control **entrada de texto** .

Las propiedades de salida pueden emitir datos o el estado de los componentes. Por ejemplo, la propiedad **seleccionada** en un control de **Galería** es una propiedad de salida. Al crear una propiedad de salida, puede determinar qué otros controles pueden hacer referencia al estado del componente.

En este tutorial se explican aún más estos conceptos.

## <a name="create-an-example-component"></a>Crear un componente de ejemplo

En este ejemplo, creará un componente de menú que se parece a este gráfico y en el que puede cambiar el texto y usarlo en varias pantallas, aplicaciones o ambos:

![Galería final](./media/create-component/menu-instance.png)

1. En Power apps Studio, cree una aplicación vacía.

1. En la barra de navegación izquierda, abra la lista de componentes y, a continuación, seleccione **nuevo componente**.

    ![Lista de componentes](./media/create-component/component-list.png)

1. Mientras mantiene el mouse sobre el nuevo componente, seleccione los puntos suspensivos (...), seleccione **cambiar nombre**y, a continuación, escriba o pegue **MenuComponent**.

1. En el panel derecho, establezca el ancho del componente en **150** y su alto en **250**y, a continuación, seleccione **nueva propiedad personalizada**.

    ![Nueva propiedad](./media/create-component/new-property.png)

1. En los **cuadros nombre para mostrar**, nombre de **propiedad**y **Descripción** , escriba o pegue **los elementos**.

    ![Nombre para mostrar, nombre de propiedad, cuadros de Descripción](./media/create-component/property-names.png)

    Cuando se especifica un nombre de propiedad, no se incluyen espacios porque se hará referencia al componente con este nombre al escribir una fórmula (por ejemplo, **ComponentName. PropertyName**).

    El nombre para mostrar aparece en la pestaña **propiedades** del panel derecho si selecciona el componente. Un nombre descriptivo para mostrar ayuda a usted y a otros responsables a entender el propósito de esta propiedad. La **Descripción** aparece en una información sobre herramientas si mantiene el puntero sobre el nombre para mostrar de esta propiedad en la pestaña **propiedades** .

1. En la lista **tipo de datos** , seleccione **tabla**y, a continuación, seleccione **crear**.

    ![Tipo de datos de la propiedad](./media/create-component/property-data-type.png)

    La propiedad **Items** se establece en un valor predeterminado basado en el tipo de datos especificado, pero puede establecerlo en un valor que se ajuste a sus necesidades. Si especificó un tipo de datos de **tabla** o **registro**, puede que desee cambiar el valor de la propiedad **Items** para que coincida con el esquema de datos que desea introducir en el componente. En este caso, cambiará a una lista de cadenas.

    Puede establecer el valor de la propiedad en la barra de fórmulas si selecciona el nombre de la propiedad en la pestaña **propiedades** del panel derecho.

    ![Propiedad de entrada personalizada en la pestaña propiedades](./media/create-component/properties-tab.png)

    Como se muestra en el siguiente gráfico, también puede modificar el valor de la propiedad en la pestaña **avanzadas** del panel derecho.

1. Establezca la propiedad **elementos** del componente en esta fórmula:

    ```powerapps-dot
    Table({Item:"SampleText"})
    ```

    ![Fórmula](./media/create-component/set-component-items.png)

1. En el componente, inserte un control **Galería** vertical en blanco.

1. Asegúrese de que la lista de propiedades muestra la propiedad **Items** (como hace de forma predeterminada) y, a continuación, establezca el valor de esa propiedad en esta expresión:

    ```powerapps-dot
    MenuComponent.Items
    ```

    De este modo, la propiedad **elementos** del control **Galería** Lee y depende de la propiedad **elementos** entrada del componente.

1. Establezca la propiedad **BorderThickness** del control de **Galería** en **1** y su propiedad **Template** en **50**.

1. En la plantilla del control **Galería** , agregue un control **etiqueta** .

    ![Agregar etiqueta y establecer borde de la galería](./media/create-component/add-label.png)

A continuación, agregará el componente a una pantalla y especificará una tabla de cadenas para el componente que se va a mostrar.

1. En la barra de navegación izquierda, seleccione la lista de pantallas y, a continuación, seleccione la pantalla predeterminada.

    ![Pantalla predeterminada](./media/create-component/default-screen.png)

1. En la pestaña **Insertar** , abra el menú **componentes** y, a continuación, seleccione **MenuComponent**.

    ![Introducir](./media/create-component/insert.png)

    El nuevo componente se denomina **MenuComponent_1** de forma predeterminada.

1. Establezca la propiedad **Items** de **MenuComponent_1** en esta fórmula:

    ```powerapps-dot
    Table({Item:"Home"}, {Item:"Admin"}, {Item:"About"}, {Item:"Help"})
    ```

    Esta instancia se parece a este gráfico, pero puede personalizar el texto y otras propiedades de cada instancia.

    ![Galería final](./media/create-component/menu-instance.png)

Hasta ahora, ha creado un componente y lo ha agregado a una aplicación. A continuación, creará una propiedad de salida que refleje el elemento que el usuario selecciona en el menú.

1. Abra la lista de componentes y, a continuación, seleccione **MenuComponent**.

1. En el panel derecho, seleccione la pestaña **propiedades** y, a continuación, seleccione **nueva propiedad personalizada**.

1. En los cuadros **nombre para mostrar**, nombre de **propiedad**y **Descripción** , escriba o pegue **seleccionado**.

1. En **tipo de propiedad**, seleccione **salida**y, a continuación, seleccione **crear**.

1. En la pestaña **Opciones avanzadas** , establezca el valor de la propiedad **seleccionada** en esta expresión, ajustando el número en el nombre de la Galería si es necesario:

    ```powerapps-dot
    Gallery1.Selected.Item
    ```

    ![Panel avanzado](./media/create-component/advance.png)

1. En la pantalla predeterminada de la aplicación, agregue una etiqueta y establezca su propiedad **texto** en esta expresión, ajustando el número en el nombre del componente si es necesario:

    ```powerapps-dot
    MenuComponent_1.Selected
    ```

    Tenga en cuenta que **MenuComponent_1** es el nombre predeterminado de una instancia, no el nombre de la definición del componente. Puede cambiar el nombre de cualquier instancia de.

1. Mientras mantiene presionada la tecla Alt, seleccione cada elemento en el menú.

    El control **etiqueta** refleja el elemento de menú que seleccionó más recientemente.

## <a name="known-limitations"></a>Limitaciones conocidas

- En el que se redactó este documento, los orígenes de datos no se guardan con componentes, por lo que los formularios y las tablas de datos están deshabilitados.
- Power apps no admite recopilaciones en componentes.
- No se puede insertar un componente en una galería, un formulario o una tarjeta de datos.
- Una instancia maestra de un componente es un maestro local y se centra en la aplicación. Si cambia una instancia maestra, solo se reflejará el cambio en las copias del componente dentro de la aplicación. Las copias en otras aplicaciones seguirán siendo las mismas, a menos que vuelva a importar la biblioteca de componentes. Todas las instancias maestras de esas aplicaciones se detectarán y actualizarán automáticamente.
- No se pueden empaquetar archivos multimedia al importar un componente.
