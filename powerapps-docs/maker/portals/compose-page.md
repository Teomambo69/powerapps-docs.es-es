---
title: Componer páginas web | Microsoft Docs
description: Instrucciones para componer páginas web en portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/10/2020
ms.author: tapanm
ms.reviewer: tapanm
ms.openlocfilehash: ec982dded0d67719effc0c2b0b4faecc19e656b8
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "3126033"
---
# <a name="compose-a-page"></a>Componer una página

Después de agregar las páginas web necesarias y administrar su jerarquía en el mapa del sitio, puede agregar diferentes componentes. El editor de WYSIWYG permite agregar y editar los componentes necesarios en el lienzo fácilmente. Puede agregar y editar los siguientes componentes en el lienzo:

- Secciones
    - Sección de una columna
    - Sección de dos columnas
    - Sección de tres columnas
- Componentes del portal
    - Text
    - Imagen
    - IFrame
    - Formulario
    - Enumerar
    - Ruta de navegación

> [!NOTE]
> Si personaliza el portal usando el diseñador de portales de Power Apps, los usuarios del sitio web observarían un impacto en el rendimiento. Se recomienda realizar los cambios en horas de poca actividad en un portal en directo. 

## <a name="use-the-wysiwyg-editor"></a>Usar el editor WYSIWYG

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione la página en la que desee agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

    > [!NOTE]
    > Los elementos editables están demarcados por un límite.

4.  Seleccione **Componentes** ![icono componentes](media/components-icon.png "Icono Componentes") del toolbelt en el lateral izquierdo de la pantalla.  

5.  Seleccione el componente que desea agregar.

    > [!div class=mx-imgBorder]
    > ![panel componentes](media/components-pane.png "Panel Componentes")  

    Se agrega el componente seleccionados al lienzo en el elemento editable.

6.  Para eliminar un componente, seleccione el componente en el lienzo y después seleccione **Eliminar** en la barra de comandos en la parte superior de la página.

    > [!div class=mx-imgBorder]
    > ![eliminar componente](media/delete-component.png "Eliminar componente")  

## <a name="add-sections"></a>Agregar secciones

Las secciones le permiten definir una estructura para la página y organizar los componentes del portal en consecuencia. Una vez que agregue secciones a la página, puede agregar componentes del portal dentro de las secciones según el requisito.

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.

2.  Seleccione la página en la que desea agregar una sección.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **Componentes** ![icono componentes](media/components-icon.png "Icono Componentes") del toolbelt en el lateral izquierdo de la pantalla.

5.  En **Diseño de sección**, seleccione el tipo de sección que se insertará.

6.  En el panel de propiedades de la derecha de la pantalla, escriba o seleccione la siguiente información:

    - **Alto mínimo**: Escriba la altura mínima de la sección. Si agrega un componente que ocupa más espacio que la altura especificada, la sección se expandirá para contener el componente. De forma predeterminada, el alto mínimo es 100 px. También puede introducir la altura en puntos (pt) y porcentaje (%).

        > [!div class=mx-imgBorder]
        > ![Alineación en la sección](media/section-props-height.png "Alineación en la sección")  

    - **Alineación**: Seleccione si el componente en la sección debe estar alineado a la izquierda, el centro o la derecha.

        > [!div class=mx-imgBorder]
        > ![Alineación en la sección](media/section-props-align.png "Alineación en la sección")  

    - **Fondo**: Seleccione si desea tener un color o una imagen como fondo de sección.

        - **Relleno**: Seleccione un color para el fondo.

            > [!div class=mx-imgBorder]
            > ![Color de relleno en la sección](media/section-props-fill.png "Color de relleno en la sección")  

        - **Imagen**: Seleccione una imagen de la lista. Si desea cargar una nueva imagen, seleccione **Cargar imagen**.

            > [!div class=mx-imgBorder]
            > ![Agregar imagen en la sección](media/section-props-image.png "Agregar imagen en la sección")  

7.  Agregue el componente del portal requerido a la sección.


## <a name="add-portal-components"></a>Agregar componentes del portal

Puede agregar los componentes siguientes en una página web.

- [Texto](#add-text-box)
- [Imagen](#add-image)
- [IFrame](#add-iframe)
- [Formulario](#add-form)
- [Lista](#add-list)
- [Ruta de navegación](#add-breadcrumb)


### <a name="add-text-box"></a>Agregar cuadro de texto

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione la página en la que desee agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **Componentes** ![icono componentes](media/components-icon.png "Icono Componentes") del toolbelt en el lateral izquierdo de la pantalla.  

5.  En **Componentes del portal**, seleccione **Texto**.

6.  Especifique el texto requerido en el cuadro de texto.

7.  Para dar formato al texto, seleccione el texto para mostrar las opciones de formato. Modifique el tamaño de fuente y el estilo según corresponda.

    > [!div class=mx-imgBorder]
    > ![componente de texto](media/text-component.png "Componente de texto")  

8. En el panel de propiedades de la derecha de la pantalla, seleccione la siguiente información:

    - **Alineación**: Seleccione si el texto debe estar alineado a la izquierda, el centro o la derecha.

    - **Color de fuente**: Seleccione un color para el texto.

        > [!div class=mx-imgBorder]
        > ![Seleccionar alineación y color del texto](media/text-props.png "Seleccionar alineación y color del texto")  
 

### <a name="add-image"></a>Agregar imagen

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione la página en la que desee agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **Componentes** ![icono componentes](media/components-icon.png "Icono Componentes") del toolbelt en el lateral izquierdo de la pantalla.  

5.  En **Componentes del portal**, seleccione **Imagen**. El marcador de imagen se agrega al lienzo.

6.  En el panel de propiedades de la derecha de la pantalla, introduzca la siguiente información:

    - **Imagen**: Seleccione esta opción si desea seleccionar una imagen existente o cargar una nueva. Si desea seleccionar una imagen cargada anteriormente, elija una imagen de la lista **Seleccionar imagen**. Para cargar una nueva imagen, seleccione **Cargar imagen**. Todas las imágenes cargadas se incluyen en la biblioteca de imágenes, que se puede seleccionar otra vez a través de la lista **Seleccionar imagen**.

        > [!div class=mx-imgBorder]
        > ![propiedades de la imagen](media/image-props.png "Propiedades de la imagen")  

        > [!NOTE]
        > - Puede cargar solo las imágenes de tipo png, svg, jpg, y jpeg con el tamaño máximo de 5 MB.
        > - No puede cargar una imagen con el mismo nombre. Debe modificar el nombre de la imagen para cargarla de nuevo.

    - **Dirección URL externa**: Seleccione esta opción si desea cargar una imagen de una dirección URL externa. Escriba la dirección URL en el campo **Dirección URL externa**. Solo se aceptan enlaces seguros, es decir, https:// es obligatorio. Si tiene imágenes almacenadas en la red de entrega de contenido, puede proporcionar el vínculo en este campo.

        > [!div class=mx-imgBorder]
        > ![dirección URL externa de imagen](media/image-ext-url.png "Dirección URL externa de imagen")  

    -   **Opciones de formato**

        - **Ancho**: Escriba el ancho de la imagen.

        - **Alto**: Escriba el alto de la imagen.

    > [!NOTE]
    > También puede seleccionar la imagen en el lienzo y arrastrar los mangos para cambiar su tamaño.

### <a name="add-iframe"></a>Agregar un IFrame

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione la página en la que desee agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **Componentes** ![icono componentes](media/components-icon.png "Icono Componentes") del toolbelt en el lateral izquierdo de la pantalla.  

5.  En **Componentes del portal**, seleccione **IFrame**. El marcador de IFrame se agrega al lienzo.

6.  En el panel de propiedades de la derecha de la pantalla, introduzca la siguiente información:

    - **Ancho**: Especifique el ancho del IFrame.

    - **Alto**: Especifique el alto del IFrame.

        > [!NOTE]
        > También puede seleccionar el IFrame en el lienzo y arrastrar los mangos para cambiar su tamaño.

    - **Vínculo**: Escriba la dirección URL del sitio web que se mostrará en el IFrame. Solo se aceptan enlaces seguros, es decir, https:// es obligatorio. El valor predeterminado es <https://www.bing.com>.
    
        > [!div class=mx-imgBorder]
        > ![propiedades de iframe](media/iframe-props.png "Propiedades de IFrame")  

> [!NOTE]
> También puede agregar el bot [Power Virtual Agent](https://docs.microsoft.com/power-virtual-agents/fundamentals-what-is-power-virtual-agents) al IFrame, de manera similar, usando los pasos descritos en [Agregar un bot al sitio web](https://docs.microsoft.com/power-virtual-agents/publication-connect-bot-to-web-channels#custom-website).

### <a name="add-form"></a>Agregar un formulario

Un formulario es una configuración basada en datos que se utiliza para agregar un formulario para obtener datos del portal sin necesidad de que un programador emerja el formulario en el portal. [Los formularios se crean en Common Data Service](https://docs.microsoft.com/powerapps/maker/model-driven-apps/form-designer-overview) y pueden utilizarse en páginas web en el portal o junto con listas para crear aplicaciones web completas.  

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione la página en la que desee agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **Componentes** ![icono componentes](media/components-icon.png "Icono Componentes") del toolbelt en el lateral izquierdo de la pantalla.  

5.  En **Componentes del portal**, seleccione **Formulario**.

6.  En el panel de propiedades de la derecha de la pantalla, seleccione una de las siguientes opciones:

    - **Crear nuevo**: Crear un formulario nuevo.
    - **Usar existente**: Usar un formulario existente.

7. Especifique la información o realice la selección para lo siguiente:

    - **Nombre**: Nombre del formulario.

    - **Entidad**: El nombre de la entidad desde la que se cargará el formulario.

    - **Diseño de formulario**: El nombre del formulario de la entidad de destino en Common Data Service que se va a representar.

    - **Modo**: Seleccione una de las siguientes opciones:

        - **Insertar**: indica que el formulario debe insertar un nuevo registro tras el envío.

        - **Editar**: indica que el formulario deben modificar un registro existente.

        - **Solo lectura**: Indica que el formulario debe mostrar el formulario no editable de un registro existente.

        > [!NOTE]
        > La opción predeterminada para los modos **Editar** y **Solo lectura** se establece como Nombre de parámetro de cadena de consulta que pasa como identificador en dirección URL. Para modificar esos valores, necesita abrir la aplicación Administración del portal y actualice las propiedades de formulario.

    - **En caso de éxito**: Seleccione una de las siguientes opciones:

        - **Mostrar mensaje correcto**: Requiere un mensaje que se mostrará al usuario si envía correctamente el formulario. También puede seleccionar **Ocultar formulario en caso de éxito** para ocultar el formulario si el envío es correcto.

        - **Redirigir a página web**: Redirige al usuario a la página web seleccionada en el portal. Debe seleccionar una página web de la lista **Redirigir a página web**.

        - **Redirigir a dirección URL**: Redirige al usuario a la dirección URL especificada. Debe escribir una dirección URL en el campo **Redirigir a dirección URL**.

    - **Mostrar captcha para usuarios anónimos**: Muestra captcha a usuarios anónimos.

    - **Mostrar captcha para usuarios autenticados**: Muestra captcha a usuarios autenticados.

    - **Habilitar permisos de entidad**: Permisos de entidad que se pueden emplear para el formulario. De forma predeterminada no está seleccionado. Si se seleccionan, se requieren permisos explícitos para que cualquier usuario obtenga acceso al formulario. Más información: [Permiso de entidad](configure/assign-entity-permissions.md)

        > [!div class=mx-imgBorder]
        > ![propiedades del formulario](media/form-props.png "Propiedades del formulario")

### <a name="add-list"></a>Agregar lista

Una lista es una configuración basada en datos que usa para agregar una página web que representará una lista de registros sin necesidad de que un programador muestre la cuadrícula en el portal. Las listas usan [Vistas de Common Data Service](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-and-edit-views) para mostrar registros en el portal.  

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione la página en la que desee agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **Componentes** ![icono componentes](media/components-icon.png "Icono Componentes") del toolbelt en el lateral izquierdo de la pantalla.  

5.  En **Componentes del portal**, seleccione **Lista**.

6.  En el panel de propiedades de la derecha de la pantalla, seleccione una de las siguientes opciones:

    - **Crear nuevo**: Crear una lista nueva.
    - **Usar existente**: Usar una lista existente.

7.  Especifique la información o realice la selección para lo siguiente:

    - **Nombre**: Nombre de la lista.

    - **Entidad**: El nombre de la entidad desde la que se cargarán las vistas.

    - **Vistas**: La lista de vistas de la entidad de destino que se va a representar. Puede seleccionar varias vistas para mostrar registros en la lista. La vista seleccionada primero será la vista predeterminada.

    - **Crear registro nuevo**: Permite a un usuario crear un registro. Seleccione una página web que contenga un formulario para crear un nuevo registro.

    - **Ver detalles**: Permitir que un usuario vea los detalles. Seleccione una página web que contenga un formulario para mostrar los detalles.

    - **Editar registro**: Permite a un usuario editar un registro. Seleccione una página web que contenga un formulario para editar el registro.

    - **Eliminar registro**: Permite a un usuario eliminar un registro.

    - **Mensaje de lista vacío**: Mensaje que se mostrará cuando no haya ningún registro que mostrar.

    - **Número de registros por página**: Un valor entero para especificar el número de los registros que se mostrarán en una página.

    - **Habilitar búsqueda en lista de entidades**: Permite a un usuario buscar registros en la lista.

    - **Habilitar permisos de entidad**: Permisos de entidad que se pueden emplear para la lista. De forma predeterminada no está seleccionado. Si se seleccionan, se requieren permisos explícitos para que cualquier usuario obtenga acceso al formulario. Más información: [Permiso de entidad](configure/assign-entity-permissions.md)  

    > [!div class=mx-imgBorder]
    > ![propiedades de lista](media/list-props.png "Propiedades de lista")

### <a name="add-breadcrumb"></a>Agregar ruta de navegación

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione la página en la que desee agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **Componentes** ![icono componentes](media/components-icon.png "Icono Componentes") del toolbelt en el lateral izquierdo de la pantalla.  

5.  En **Componentes del portal**, seleccione **Ruta de navegación**.

## <a name="add-a-custom-menu"></a>Agregar un menú personalizado

De forma predeterminada, el menú en el sitio web se crea automáticamente basándose en la jerarquía de las páginas web. Se llama menú **predeterminado**. Para crear un menú personalizado, debe crear el conjunto de vínculos web en la aplicación Administración del portal. Más información: [Administrar vínculos web](configure/manage-web-links.md).

Tras crear el conjunto de vínculos web:

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.

2.  Seleccione el componente del encabezado. 

3.  En las propiedades a la derecha de la pantalla, seleccione el nombre del conjunto de vínculos web de la lista **Menú de navegación**.

    > [!div class=mx-imgBorder]
    > ![Menú de navegación](media/navigation-menu.png "Menú de navegación")

## <a name="use-code-editor"></a>Usar editor de código

Para ver el origen de un componente en el lienzo, seleccione el componente y, a continuación, seleccione el icono del editor de código de origen **&lt;/&gt;** en el pie de página.

> [!div class=mx-imgBorder]
> ![icono editor de código](media/code-editor-icon.png "Icono editor de código")  

El código fuente se muestra en el panel **Editor de código** en la parte inferior de la pantalla. Los cambios que haya realizado se actualizan en el código fuente. Para realizar cambios, actualice el origen de código y seleccione **Guardar**. Los cambios se reflejan en el lienzo.

> [!div class=mx-imgBorder]
> ![editor de código](media/code-editor.png "Editor de código") 

> [!NOTE]
> También puede agregar etiquetas de Liquid en el editor de código de origen para configuración avanzada. Más información: [Trabajar con plantillas de Liquid](liquid/liquid-overview.md)


