---
title: Crear páginas web | Microsoft Docs
description: Instrucciones para crear páginas web en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cec2b106ba35f73a34128e9e89233c18d2d70dd1
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975711"
---
# <a name="compose-a-page"></a>Creación de una página

Después de agregar las páginas web necesarias y administrar su jerarquía en el mapa del sitio, puede agregar varios componentes. El editor WYSIWYG permite agregar y editar fácilmente los componentes necesarios en el lienzo. Puede Agregar y editar los siguientes componentes en el lienzo:

- Secciones
    - Sección de una columna
    - Sección dos columnas
    - Sección de tres columnas
- Componentes del portal
    - Text
    - Imagen
    - IFrame
    - Formulario
    - Lista
    - Situada

> [!NOTE]
> Si personaliza el portal con PowerApps portales Studio, los usuarios del sitio web observarán un impacto en el rendimiento. Le recomendamos que realice los cambios durante las horas de poca actividad en un portal activo. 

## <a name="use-the-wysiwyg-editor"></a>Usar el editor WYSIWYG

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  Seleccione la página en la que desea agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

    > [!NOTE]
    > Los elementos modificables se delimitan mediante un límite.

4.  Seleccione **componentes** ![icono]componentes icono(media/components-icon.png "en el") toolbelt en el lado izquierdo de la pantalla.  

5.  Seleccione el componente que se va a agregar.

    > [!div class=mx-imgBorder]
    > panel ![componentes panel](media/components-pane.png "componentes")  

    El componente seleccionado se agrega al lienzo dentro del elemento editable.

6.  Para eliminar un componente, seleccione el componente en el lienzo y, a continuación, seleccione **eliminar** en la barra de comandos de la parte superior de la página.

    > [!div class=mx-imgBorder]
    > ![eliminar](media/delete-component.png "componente de eliminación") de componente  

## <a name="add-sections"></a>Agregar secciones

Las secciones permiten definir una estructura para la página y organizar los componentes del portal en consecuencia. Una vez agregadas las secciones a la página, puede agregar componentes del portal dentro de las secciones según el requisito.

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.

2.  Seleccione la página en la que desea agregar una sección.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **componentes** ![icono]componentes icono(media/components-icon.png "en el") toolbelt en el lado izquierdo de la pantalla.

5.  En **diseño de sección**, seleccione el tipo de sección que se va a insertar.

6.  En el panel Propiedades, en el lado derecho de la pantalla, escriba o seleccione la siguiente información:

    - **Altura**mínima: especifique el alto mínimo de la sección. Si agrega un componente que ocupa más espacio que el alto especificado, la sección se expande para dar cabida al componente. De forma predeterminada, el alto mínimo es 100 píxeles. También puede especificar el alto en puntos (PT) y el porcentaje (%).

        > [!div class=mx-imgBorder]
        > ![Alineación en la sección](media/section-props-height.png "alineación de la sección")  

    - **Alignment**: Seleccione si el componente de la sección debe estar alineado a la izquierda, en el centro o a la derecha.

        > [!div class=mx-imgBorder]
        > ![Alineación en la sección](media/section-props-align.png "alineación de la sección")  

    - **Background**: Seleccione si desea tener color o una imagen como fondo de la sección.

        - **Fill**: Seleccione un color para el fondo.

            > [!div class=mx-imgBorder]
            > ![Color de relleno en la sección](media/section-props-fill.png "color de relleno de la sección")  

        - **Imagen**: Seleccione una imagen de la lista. Si desea cargar una nueva imagen, seleccione **cargar imagen**.

            > [!div class=mx-imgBorder]
            > ![Agregar imagen en la sección](media/section-props-image.png "Agregar imagen en la sección")  

7.  Agregue el componente de portal necesario en la sección.


## <a name="add-portal-components"></a>Agregar componentes del portal

Puede Agregar los siguientes componentes en una página web:

- [Texto](#add-text-box)
- [Imagen](#add-image)
- [IFrame](#add-iframe)
- [Formulario](#add-form)
- [Lista](#add-list)
- [Situada](#add-breadcrumb)


### <a name="add-text-box"></a>Agregar cuadro de texto

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  Seleccione la página en la que desea agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **componentes** ![icono]componentes icono(media/components-icon.png "en el") toolbelt en el lado izquierdo de la pantalla.  

5.  En **componentes del portal**, seleccione **texto**.

6.  Escriba el texto necesario en el cuadro de texto.

7.  Para dar formato al texto, seleccione el texto para mostrar las opciones de formato. Modifique el tamaño y el estilo de la fuente según sea necesario.

    > [!div class=mx-imgBorder]
    > ![](media/text-component.png "componente de texto") de componente de texto  

8. En el panel Propiedades, en el lado derecho de la pantalla, seleccione la siguiente información:

    - **Alineación**: Seleccione si el texto debe estar a la izquierda, en el centro o alineado a la derecha.

    - **Color de fuente**: Seleccione un color para el texto.

        > [!div class=mx-imgBorder]
        > ![Seleccionar alineación del texto y color](media/text-props.png "seleccionar alineación del texto y color")  
 

### <a name="add-image"></a>Agregar imagen

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  Seleccione la página en la que desea agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **componentes** ![icono]componentes icono(media/components-icon.png "en el") toolbelt en el lado izquierdo de la pantalla.  

5.  En **componentes del portal**, seleccione **imagen**. El marcador de posición de la imagen se agrega al lienzo.

6.  En el panel Propiedades, en el lado derecho de la pantalla, escriba la siguiente información:

    - **Imagen**: Seleccione esta opción si desea seleccionar una imagen existente o cargar una nueva. Si desea seleccionar una imagen cargada previamente, elija una imagen en la lista **seleccionar imagen** . Para cargar una nueva imagen, seleccione **cargar imagen**. Todas las imágenes cargadas se incluyen en la biblioteca de imágenes, que se pueden seleccionar de nuevo a través de la lista **seleccionar imagen** .

        > [!div class=mx-imgBorder]
        > Propiedades de ![la imagen propiedades]de(media/image-props.png "la imagen")  

        > [!NOTE]
        > - Solo puede cargar las imágenes de tipo PNG, SVG, jpg y JPEG con el tamaño máximo de 5 MB.
        > - No se puede cargar una imagen con el mismo nombre. Debe modificar el nombre de la imagen para volver a cargarla.

    - **Dirección URL externa**: Seleccione esta opción si desea cargar una imagen de una dirección URL externa. Escriba la dirección URL en el campo **dirección URL externa** . Solo se aceptan vínculos seguros, es decir, https://es obligatorio. Si tiene imágenes almacenadas en Content Delivery Network, puede proporcionar el vínculo en este campo.

        > [!div class=mx-imgBorder]
        > URL externa de(media/image-ext-url.png "imagen dirección") ![URL]externa  

    -   **Opciones de formato**

        - **Ancho**: escriba el ancho de la imagen.

        - **Alto**: escriba el alto de la imagen.

    > [!NOTE]
    > También puede seleccionar la imagen en el lienzo y arrastrar los controladores para cambiar su tamaño.

### <a name="add-iframe"></a>Agregar IFrame

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  Seleccione la página en la que desea agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **componentes** ![icono]componentes icono(media/components-icon.png "en el") toolbelt en el lado izquierdo de la pantalla.  

5.  En **componentes del portal**, seleccione **iframe**. El marcador de posición IFrame se agrega al lienzo.

6.  En el panel Propiedades, en el lado derecho de la pantalla, escriba la siguiente información:

    - **Ancho**: escriba el ancho del iframe.

    - **Height**: escriba el alto del iframe.

    - **Vínculo**: escriba la dirección URL del sitio web que se va a mostrar en el iframe. Solo se aceptan vínculos seguros, es decir, https://es obligatorio. De forma predeterminada, <https://www.bing.com> está disponible como valor.

        > [!div class=mx-imgBorder]
        > propiedades ![de iframe propiedades]de(media/iframe-props.png "iframe")  

    > [!NOTE]
    > También puede seleccionar el IFrame en el lienzo y arrastrar los controladores para cambiar su tamaño.

### <a name="add-form"></a>Agregar formulario

Form es una configuración controlada por datos que se usa para agregar un formulario para recopilar datos en el portal sin necesidad de que un desarrollador muestre el formulario en el portal. Los [formularios se crean en Common Data Service](https://docs.microsoft.com/powerapps/maker/model-driven-apps/form-designer-overview) y se pueden usar en páginas web en el portal o junto con listas para crear aplicaciones web completas.  

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  Seleccione la página en la que desea agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **componentes** ![icono]componentes icono(media/components-icon.png "en el") toolbelt en el lado izquierdo de la pantalla.  

5.  En **componentes del portal**, seleccione **formulario**.

6.  En el panel Propiedades, en el lado derecho de la pantalla, seleccione una de las siguientes opciones:

    - **Crear nuevo**: cree un nuevo formulario.
    - **Usar existente**: usar un formulario existente.

7. Escriba información o haga una selección para lo siguiente:

    - **Name**: nombre del formulario.

    - **Entidad**: nombre de la entidad desde la que se cargará el formulario.

    - **Diseño del formulario**: el nombre del formulario en la entidad de destino en Common Data Service que se va a representar.

    - **Modo**: Seleccione una de las siguientes opciones:

        - **Insert**: indica que el formulario debe insertar un nuevo registro tras su envío.

        - **Editar**: indica que el formulario debe editar un registro existente.

        - **Solo lectura**: indica que el formulario debe mostrar un formulario no editable de un registro existente.

        > [!NOTE]
        > La opción predeterminada para los modos de **edición** y de **solo lectura** se establece como nombre de parámetro de cadena de consulta pasado como identificador en la dirección URL. Para cambiar estos valores, debe abrir la aplicación administración del portal y actualizar las propiedades del formulario.

    - **En caso de éxito**: Seleccione una de las siguientes opciones:

        - **Mostrar mensaje de operación correcta**: requiere que se muestre un mensaje al usuario en el envío correcto del formulario. También puede seleccionar **ocultar formulario en caso de éxito** para ocultar el formulario cuando el envío se realiza correctamente.

        - **Redirigir a la página web**: redirige al usuario a la Página Web seleccionada en el portal. Debe seleccionar una página web de la lista **redirigir a la página web** .

        - **Redirigir a la dirección URL**: redirige al usuario a la dirección URL especificada. Debe escribir una dirección URL en el campo **redirigir a dirección URL** .

    - **Mostrar CAPTCHA para usuarios anónimos**: muestra CAPTCHA a usuarios anónimos.

    - **Mostrar CAPTCHA para los usuarios autenticados**: muestra CAPTCHA a los usuarios autenticados.

    - **Habilitar permisos de entidad**: permisos de entidad que se deben tener en cuenta para el formulario. De forma predeterminada, no está seleccionada. Si se selecciona, se requieren permisos explícitos para que cualquier usuario tenga acceso al formulario. Más información: [permisos de entidad](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions)

        > [!div class=mx-imgBorder]
        > ![](media/form-props.png "propiedades del") formulario propiedades del formulario

### <a name="add-list"></a>Agregar lista

List es una configuración controlada por datos que se usa para agregar una página web que representará una lista de registros sin necesidad de que un desarrollador muestre la cuadrícula en el portal. Las listas usan [Common Data Service vistas](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-and-edit-views) para mostrar registros en el portal.  

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  Seleccione la página en la que desea agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **componentes** ![icono]componentes icono(media/components-icon.png "en el") toolbelt en el lado izquierdo de la pantalla.  

5.  En **componentes del portal**, seleccione **lista**.

6.  En el panel Propiedades, en el lado derecho de la pantalla, seleccione una de las siguientes opciones:

    - **Crear nuevo**: crea una nueva lista.
    - **Usar existente**: usar una lista existente.

7.  Escriba información o haga una selección para lo siguiente:

    - **Nombre**: nombre de la lista.

    - **Entidad**: nombre de la entidad desde la que se cargarán las vistas.

    - **Vistas**: lista de vistas de la entidad de destino que se va a representar. Puede seleccionar varias vistas para mostrar los registros de la lista. La vista seleccionada en primer lugar será la vista predeterminada.

    - **Crear nuevo registro**: permite a un usuario crear un registro. Seleccione una página web que contenga un formulario para crear un nuevo registro.

    - **Ver detalles**: permite que un usuario vea los detalles. Seleccione una página web que contenga un formulario para mostrar los detalles.

    - **Editar Registro**: permite que un usuario edite un registro. Seleccione una página web que contenga un formulario para editar el registro.

    - **Eliminar registro**: permite que un usuario elimine un registro.

    - **Mensaje de lista vacío**: mensaje que se mostrará cuando no haya ningún registro para mostrar.

    - **Número de registros por página**: un valor entero para especificar el número de registros que se van a mostrar en una página.

    - **Habilitar la búsqueda en la lista de entidades**: permite que un usuario Busque registros en la lista.

    - **Habilitar permisos de entidad**: permisos de entidad que se deben tener en cuenta para la lista. De forma predeterminada, no está seleccionada. Si se selecciona, se requieren permisos explícitos para que cualquier usuario tenga acceso al formulario. Más información: [permisos de entidad](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions)  

    > [!div class=mx-imgBorder]
    > ![](media/list-props.png "propiedades") de lista de propiedades de lista

### <a name="add-breadcrumb"></a>Agregar ruta de navegación

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  Seleccione la página en la que desea agregar el componente.

3.  Seleccione un elemento editable en el lienzo.

4.  Seleccione **componentes** ![icono]componentes icono(media/components-icon.png "en el") toolbelt en el lado izquierdo de la pantalla.  

5.  En **componentes del portal**, seleccione **ruta de navegación**.

## <a name="add-a-custom-menu"></a>Agregar un menú personalizado

De forma predeterminada, el menú del sitio web se crea automáticamente en función de la jerarquía de las páginas Web. Se denomina menú **predeterminado** . Para crear un menú personalizado, debe crear el conjunto de vínculos Web en la aplicación de administración del portal. Más información: [administrar vínculos Web](https://docs.microsoft.com/dynamics365/customer-engagement/portals/manage-web-links)

Después de crear el conjunto de vínculos Web:

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.

2.  Seleccione el componente de encabezado. 

3.  En las propiedades del lado derecho de la pantalla, seleccione el nombre del conjunto de vínculos Web en la lista de **menús de navegación** .

    > [!div class=mx-imgBorder]
    > ![](media/navigation-menu.png "Menú") de navegación menú de navegación

## <a name="use-code-editor"></a>Usar el editor de código

Para ver el origen de un componente en el lienzo, seleccione el componente y, a continuación, seleccione el icono editor de código fuente **&lt;/&gt;** en el pie de página.

> [!div class=mx-imgBorder]
> icono del editor de ![código]icono del(media/code-editor-icon.png "Editor de código")  

El código fuente se muestra en el panel del **Editor de código** en la parte inferior de la pantalla. Los cambios realizados anteriormente se actualizan en el código fuente. Para realizar cambios, actualice el código fuente y seleccione **Guardar**. Los cambios se reflejan en el lienzo.

> [!div class=mx-imgBorder]
> ![](media/code-editor.png "Editor de código") del editor de código 

> [!NOTE]
> También puede agregar etiquetas líquidas en el editor de código fuente para la configuración avanzada. Más información: [trabajar con plantillas líquidas](https://docs.microsoft.com/dynamics365/customer-engagement/portals/custom-templates-dynamic-content)


