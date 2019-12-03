---
title: Comprender los formularios de aplicaciones de lienzo | Microsoft Docs
description: En Power Apps, agregue un formulario a una aplicación de lienzo para que pueda recopilar y Mostrar información de un origen de datos.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/27/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 462830806165b4eb52eebb17436e11798dbdb267
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674453"
---
# <a name="understand-canvas-app-forms-in-microsoft-powerapps"></a>Comprender los formularios de aplicaciones de lienzo en Microsoft PowerApps

Agregue tres tipos de controles a una aplicación de lienzo para que el usuario pueda buscar un registro, mostrar los detalles sobre ese registro y editar o crear un registro:

| Actividad | Control | Descripción |
| --- | --- | --- |
| **Buscar un registro** |Control **[Galería](controls/control-gallery.md)** |Filtra, ordena, busca y se desplaza por los registros de un origen de datos, además de seleccionar un registro específico. Muestra solo algunos campos de cada registro para ver varios registros a la vez, incluso en una pantalla pequeña. |
| **Mostrar los detalles de un registro** |Control **[Mostrar formulario](controls/control-form-detail.md)** |Muestra varios o todos los campos de un solo registro. |
| **Editar o crear un registro** |Control **[Editar formulario](controls/control-form-detail.md)** |Actualiza uno o varios campos de un solo registro (o cree un registro a partir de los valores predeterminados) y guarde esos cambios en el origen de datos subyacente. |

Ubique cada control en una pantalla distinta para que sea más fácil distinguirlos:

![Búsqueda, visualización y edición de registros en tres pantallas](./media/working-with-forms/three-screens.png)

Tal como se describe en este tema, combine estos controles con fórmulas para crear la experiencia global del usuario.

## <a name="prerequisites"></a>Requisitos previos

* [Regístrese](../signup-for-powerapps.md) en Power apps y, a continuación, [inicie sesión](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para suscribirse.
* Aprenda a [configurar un control](add-configure-controls.md) en PowerApps.

## <a name="explore-a-generated-app"></a>Exploración de una aplicación generada
Power apps puede generar automáticamente una aplicación basada en un origen de datos que especifique. Cada aplicación contiene tres pantallas con los controles anteriormente descritos, además de fórmulas que las conectan. Ejecute estas aplicaciones "de uso inmediato", personalícelas para lograr objetivos específicos o examine cómo funcionan para que pueda aprender conceptos útiles para usarlos con sus propias aplicaciones. En las secciones siguientes, revise las pantallas, los controles y las fórmulas que crean una aplicación generada.  

### <a name="browse-screen"></a>Pantalla de exploración
![Controles de la pantalla de exploración](./media/working-with-forms/afd-browse-screen-basic.png)

Esta pantalla incluye las siguientes fórmulas clave:

| Control | Comportamiento admitido | Fórmula |
| --- | --- | --- |
| **BrowseGallery1** |Muestra los registros del origen de datos **Assets**. |La propiedad **[Items](controls/properties-core.md)** de la galería está establecida en una fórmula basada en el origen de datos **Assets**. |
| **ImageNewItem1** |Muestra la pantalla **Editar y crear** con cada campo establecido en un valor predeterminado para que el usuario pueda crear fácilmente un registro. |La propiedad **[OnSelect](controls/properties-core.md)** de la imagen está establecida en esta fórmula:<br> **NewForm( EditForm1 );<br>Navigate( EditScreen1, None )** |
| **NextArrow1** (en la galería) |Muestra la pantalla **Detalles** para ver varios o todos los campos del registro actualmente seleccionado. |La propiedad **[OnSelect](controls/properties-core.md)** de la flecha está establecida en esta fórmula:<br>**Navigate( DetailScreen1, None )** |

El control principal de esta pantalla, **BrowseGallery1**, abarca la mayor parte de la pantalla. El usuario puede desplazarse en la galería para encontrar un registro específico a fin de mostrar más campos o hacer una actualización.

Establezca la propiedad **[Items](controls/properties-core.md)** de una galería para que muestre los registros provenientes de un origen de datos. Por ejemplo, establezca la propiedad en **Assets** para mostrar los registros de un origen de datos con ese nombre.

> [!NOTE]
> En una aplicación generada, la propiedad **[Elementos](controls/properties-core.md)** se establece, de manera predeterminada, en una fórmula mucho más complicada para que el usuario pueda ordenar y buscar registros. Más adelante en este tema obtendrá información sobre cómo crear esta fórmula; por ahora basta con la versión más sencilla.

En lugar de buscar un registro para mostrarlo o editarlo, el usuario puede crear un registro si selecciona el símbolo "+" que se encuentra arriba de la galería. Para crear este efecto, agregue un control **[Image](controls/control-image.md)** , colóquele un símbolo "+" y establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:
<br>**NewForm( EditForm1 ); Navigate( EditScreen1, None )**

Esta fórmula abre la pantalla **Editar y crear**, que incluye un control **[Editar formulario](controls/control-form-detail.md)** llamado **EditForm1**. La fórmula también convierte ese formulario al modo **New**, en el cual el formulario muestra los valores predeterminados del origen de datos para que el usuario pueda crear fácilmente un registro desde cero.

Para examinar cualquier control que aparezca en **BrowseGallery1**, selecciónelo en la primera sección de la galería, lo que sirve como plantilla para todas las demás secciones. Por ejemplo, seleccione el control **[Etiqueta](controls/control-text-box.md)** central que se encuentra en el borde de la izquierda:

![Controles de la pantalla de exploración](./media/working-with-forms/afd-browse-gallery-controls.png)

En este ejemplo, la propiedad **[Text](controls/properties-core.md)** del control está establecida en **ThisItem.AssignedTo**, que es un campo que se encuentra en el origen de datos **Assets**. La propiedad **[Texto](controls/properties-core.md)** de los otros tres controles **[Etiqueta](controls/control-text-box.md)** en la galería está establecida en fórmulas similares y cada control muestra un campo distinto en el origen de datos.  

Seleccione el control **[Forma](controls/control-shapes-icons.md)** (la flecha) y confirme que la propiedad **[OnSelect](controls/properties-core.md)** está establecida en esta fórmula:
<br>**Navigate( DetailScreen1, None )**

Si el usuario encuentra un registro en **BrowseGallery1**, puede seleccionar la flecha correspondiente a ese registro para mostrar más información sobre él en **DetailScreen1**. Cuando selecciona una flecha, el usuario cambia el valor de la propiedad **Selected** de **BrowseGallery1**. En esta aplicación, esa propiedad determina el registro que aparece no solo en la pantalla **DetailScreen1**, sino que también en **Edit and Create**, si el usuario decide actualizar el registro.

### <a name="detail-screen"></a>Pantalla de detalle
![Controles de la pantalla de detalle](./media/working-with-forms/afd-detail-screen-basic.png)

Esta pantalla incluye las siguientes fórmulas clave:

| Control | Comportamiento admitido | Fórmula |
| --- | --- | --- |
| **DetailForm1** |Muestra un registro en el origen de datos **Assets**. |Establezca la propiedad **[DataSource](controls/control-form-detail.md)** en **Assets**. |
| **DetailForm1** |Determina el registro que se mostrará. En una aplicación generada, muestra el registro que el usuario seleccionó en la galería. |Establezca la propiedad **[Item](controls/control-form-detail.md)** de este control en este valor:<br>**BrowseGallery1.Selected** |
| Controles **[Tarjeta](controls/control-card.md)** |En un control **[Mostrar formulario](controls/control-form-detail.md)** , muestra un solo campo de un registro. |Establezca la propiedad **[DataField](controls/control-card.md)** en el nombre de un campo entre comillas dobles (por ejemplo, **"Nombre"** ). |
| **ImageBackArrow1** |Cuando el usuario selecciona este control, se abre **BrowseScreen1**. |Establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br>**Back()** |
| **ImageDelete1** |Cuando el usuario selecciona este control, se elimina un registro. |Establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br>**Remove( Assets, BrowseGallery1.Selected )** |
| **ImageEdit1** |Cuando el usuario selecciona este control, la pantalla **Editar y crear** se abre en el registro actual. |Establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br>**Navigate( EditScreen1, None )** |

En la parte superior de la pantalla, aparecen tres imágenes fuera de **DetailForm1** que actúan como botones y se organizan entre las tres pantallas de la aplicación.

**DetailForm1** domina esta pantalla y muestra el registro que el usuario seleccionó en la galería (porque la propiedad **[Item](controls/control-form-detail.md)** del formulario está establecida en **BrowseGallery1.Selected**). La propiedad **[DataSource](controls/control-form-detail.md)** del formulario también proporciona metadatos sobre el origen de datos, como un nombre descriptivo para mostrar para cada campo.

**DetailForm1** contiene varios controles **[Tarjeta](controls/control-card.md)** . Puede seleccionar el control **[Tarjeta](controls/control-card.md)** mismo o el control que contiene para encontrar información adicional.

![Tarjeta de detalle y controles de tarjeta seleccionados en la experiencia de creación](./media/working-with-forms/afd-detail-card-controls.png)

La propiedad **[DataField](controls/control-card.md)** de un control **[Tarjeta](controls/control-card.md)** determina el campo que se muestra. En este caso, esa propiedad está establecida en **AssetID**. La tarjeta contiene un control **[Etiqueta](controls/control-text-box.md)** para el que la propiedad **[Texto](controls/properties-core.md)** está establecida en **Parent.Default**. Este control muestra el valor **Default** de la tarjeta, que se establece a través de la propiedad **[DataField](controls/control-card.md)** .

En una aplicación generada, los controles **[Tarjeta](controls/control-card.md)** están bloqueados de manera predeterminada. Cuando una tarjeta está bloqueada, no se pueden modificar algunas propiedades, como **[DataField](controls/control-card.md)** , y la barra de fórmulas no está disponible para esas propiedades. Esta restricción permite garantizar que las personalizaciones no interrumpan la funcionalidad básica de la aplicación generada. Sin embargo, puede modificar algunas de las propiedades de una tarjeta y sus controles en el panel de la derecha:

![Pantalla de detalle con el panel de opciones abierto](./media/working-with-forms/detail-screen-new.png)

En el panel de la derecha, puede seleccionar los campos que se van a mostrar y el tipo de control que mostrará cada uno.

### <a name="editcreate-screen"></a>Pantalla de edición o creación
![Controles de la pantalla de edición](./media/working-with-forms/afd-edit-screen-basic.png)

Esta pantalla incluye las siguientes fórmulas clave:

| Control | Comportamiento admitido | Fórmula |
| --- | --- | --- |
| **EditForm1** |Muestra un registro en el origen de datos **Assets**. |Establezca la propiedad **[DataSource](controls/control-form-detail.md)** en **Assets**. |
| **EditForm1** |Determina el registro que se mostrará. En una aplicación generada, muestra el registro que el usuario seleccionó en **BrowseScreen1**. |Establezca la propiedad **[Item](controls/control-form-detail.md)** en este valor:<br>**BrowseGallery1.Selected** |
| Controles **[Tarjeta](controls/control-card.md)** |En un control **[Editar formulario](controls/control-form-detail.md)** , proporciona controles para que el usuario pueda editar uno o varios campos de un registro. |Establezca la propiedad **[DataField](controls/control-card.md)** en el nombre de un campo entre comillas dobles (por ejemplo, **"Nombre"** ). |
| **ImageCancel1** |Cuando el usuario selecciona este control, se descartan los cambios en curso y se abre la pantalla **Detalles**. |Establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br>**ResetForm( EditForm1 ); Back()** |
| **ImageAccept1** |Cuando el usuario selecciona este control, los cambios se envían al origen de datos. |Establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br>**SubmitForm( EditForm1 )** |
| **EditForm1** |Si se aceptan los cambios, se vuelve a la pantalla anterior. |Establezca la propiedad **[OnSuccess](controls/control-form-detail.md)** en esta fórmula:<br>**Back()** |
| **EditForm1** |Si no se aceptan los cambios, el usuario continúa en la pantalla actual para poder corregir cualquier problema e intente volver a enviar. |Deje en blanco la propiedad **[OnFailure](controls/control-form-detail.md)** . |
| **LblFormError1** |Si no se aceptan los cambios, se muestra un mensaje de error. |Establezca la propiedad **[Text](controls/properties-core.md)** en este valor:<br>**EditForm1.Error** |

Tal como ocurre en la pantalla **Detalles**, un control de formulario, llamado **EditForm1**, domina la pantalla **Editar y crear**. Además, la propiedad **[Item](controls/control-form-detail.md)** de **EditForm1** está establecida en **BrowseGallery1.Selected**, por lo que el formulario muestra el registro que el usuario seleccionó en **BrowseScreen1**. Si bien la pantalla **Detalles** muestra cada campo como un campo de solo lectura, el usuario puede actualizar el valor de uno o más campos con los controles en **EditForm1**. También usa la propiedad **[DataSource](controls/control-form-detail.md)** para tener acceso a metadatos sobre este origen de datos, como el nombre descriptivo para mostrar de cada campo y la ubicación en la que se deben guardar los cambios.

Si el usuario selecciona el icono "X" para cancelar una actualización, la función **[ResetForm](functions/function-form.md)** descarta los cambios que no se hayan guardado y la función **[Back](functions/function-navigate.md)** abre la pantalla **Detalles**. Tanto la pantalla **Detalles** como la pantalla **Editar y crear** muestran el mismo registro hasta que el usuario selecciona otro en **BrowseScreen1**. Los campos de ese registro siguen establecidos en los valores que se guardaron más recientemente, no en ningún cambio que el usuario haya hecho para luego abandonar.

Si el usuario cambia uno o más valores del formulario y luego selecciona el icono "marca de verificación", la función **[SubmitForm](functions/function-form.md)** envía los cambios del usuario al origen de datos.

* Si los cambios se guardaron correctamente, se ejecuta la fórmula **[OnSuccess](controls/control-form-detail.md)** del formulario y la función **Back()** abre la pantalla de detalle para mostrar el registro actualizado.
* Si los cambios no se guardaron correctamente, se ejecuta la fórmula **[OnFailure](controls/control-form-detail.md)** del formulario, pero no cambia nada porque está *en blanco*. La pantalla **Editar y crear** sigue abierta, por lo que el usuario puede cancelar los cambios o corregir el error. **LblFormError1** muestra un mensaje de error descriptivo en el que está establecida la propiedad **Error** del formulario.

Al igual que con un control **[Mostrar formulario](controls/control-form-detail.md)** , un control **[Editar formulario](controls/control-form-detail.md)** contiene controles **[Tarjeta](controls/control-card.md)** los que, a su vez, contienen otros controles que muestran otros campos de un registro:

![Tarjeta de edición y controles de tarjeta seleccionados en la experiencia de creación](./media/working-with-forms/afd-edit-card-controls.png)

En la imagen anterior, la tarjeta seleccionada muestra el campo **AssetID** y contiene un control **[Entrada de texto](controls/control-text-input.md)** para que el usuario pueda editar el valor de ese campo. (En cambio, la pantalla de detalle muestra el mismo campo en un control de **[etiqueta](controls/control-text-box.md)** , que es de solo lectura). El control **[entrada de texto](controls/control-text-input.md)** tiene una propiedad **[predeterminada](controls/properties-core.md)** , que se establece en **Parent. default**. Si el usuario estuviera creando un registro en lugar de editándolo, ese control mostraría un valor inicial que el usuario podría cambiar para el registro nuevo.

En el panel de la derecha, puede mostrar u ocultar cada una de las tarjetas, reorganizarlas o configurarlas para mostrar campos en los distintos tipos de controles.

![Pantalla de edición con el panel de opciones abierto](./media/working-with-forms/edit-screen.png)

## <a name="build-an-app-from-scratch"></a>Crear una aplicación desde cero
Al comprender cómo Power apps genera una aplicación, puede compilar una que use los mismos bloques de creación y las mismas fórmulas que se han descrito anteriormente en este tema.

## <a name="identify-test-data"></a>Identificación de los datos de prueba
Para aprovechar al máximo este tema, comience con un origen de datos con el que pueda experimentar. Debe contener datos de prueba que pueda leer y actualizar sin tener que preocuparse.

> [!NOTE]
> Si usa una lista de SharePoint o una tabla de Excel que contenga nombres de columna con espacios como origen de datos, Power apps reemplazará los espacios por **"\_x0020\_"** . Por ejemplo, **"nombre de columna"** en SharePoint o Excel aparecerá como **"Column_x0020_Name"** en Power apps cuando se muestre en el diseño de datos o se use en una fórmula.

Para seguir el resto de este tema al pie de la letra, cree una lista de SharePoint llamada "Helado" con los siguientes datos:

![Lista Helado de SharePoint](./media/working-with-forms/sharepointlist-icecream.png)

* Cree una aplicación desde cero, para teléfonos, y [conéctela al origen de datos](add-data-connection.md).
  
    > [!NOTE]
  > Las aplicaciones de tableta son muy similares, pero es posible que desee un [diseño de pantalla](#screen-design) distinto para aprovechar al máximo el espacio adicional de la pantalla.
  
    Los ejemplos que aparecen en el resto del tema se basan en un origen de datos llamado **Helado**.

## <a name="browse-records"></a>Búsqueda de registros
Obtenga un fragmento de información de un registro; para ello, búsquelo en una galería en una pantalla de exploración.

1. Agregue una galería **Vertical** y cambie el diseño a solo **Título**.
   
    ![Galería conectada al origen de datos Helado](./media/working-with-forms/new-gallery.png)
2. Establezca la propiedad **[Elementos](controls/properties-core.md)** de la galería en **Helado**.
3. Establezca la propiedad **[Texto](controls/properties-core.md)** de la primera etiqueta en la galería en **ThisItem.Title** si está establecida en algo diferente.
   
    Ahora la etiqueta muestra el valor del campo **Título** para cada registro.
   
    ![Galería conectada al origen de datos Helado](./media/working-with-forms/new-gallery-2.png)
4. Cambie el tamaño de la galería para que llene la pantalla y establezca su propiedad **[TamañoDePlantilla](controls/control-gallery.md)** en **60**.
   
    La pantalla es similar a este ejemplo, el que muestra todos los registros del origen de datos:
   
    ![Galería conectada al origen de datos Helado](./media/working-with-forms/new-gallery-icecream.png)

## <a name="view-details"></a>Ver detalles
Si la galería no muestra la información que desea, seleccione la flecha de un registro para abrir la pantalla de detalles. Un control **[Mostrar formulario](controls/control-form-detail.md)** de esa pantalla muestra más campos, posiblemente todos, del registro que seleccionó.

El control **[Mostrar formulario](controls/control-form-detail.md)** usa dos propiedades para mostrar el registro:

* Propiedad **[DataSource](controls/control-form-detail.md)** .  El nombre del origen de datos que contiene el registro. Esta propiedad rellena el panel de la derecha con campos y determina el nombre para mostrar y el tipo de datos (cadena, número, fecha, etc.) de cada campo.  
* Propiedad **[Item](controls/control-form-detail.md)** .  El registro que se mostrará.  A menudo, esta propiedad está conectada con la propiedad **Selected** del control **[Galería](controls/control-gallery.md)** , por lo que el usuario puede seleccionar un registro en el control **[Galería](controls/control-gallery.md)** y luego profundizar en ese registro.

Cuando se establece la propiedad **[DataSource](controls/control-form-detail.md)** , puede agregar y quitar campos en el panel de la derecha y cambiar la forma en que se muestran.

En esta pantalla, los usuarios no pueden cambiar ningunos de los valores del registro, ya sea intencional o accidentalmente. El control **[Mostrar formulario](controls/control-form-detail.md)** es un control de solo lectura, por lo que no modificará el registro.

Para agregar un control **[Mostrar formulario](controls/control-form-detail.md)** :

1. Agregue una pantalla y, luego, agréguele un control **[Mostrar formulario](controls/control-form-detail.md)** .
2. Establezca la propiedad **[DataSource](controls/control-form-detail.md)** del control de formulario en **"Helado"** .

En el panel de la derecha, puede seleccionar los campos que se van a mostrar en la pantalla y el tipo de tarjeta que se mostrará para cada campo. Cuando hace cambios en el panel de la derecha, la propiedad **[DataField](controls/control-card.md)** de cada control **[Tarjeta](controls/control-card.md)** se establece en el campo con el que interactuará el usuario. La pantalla debe ser similar al ejemplo:

![Mostrar formulario para el origen de datos Helado](./media/working-with-forms/ice-cream-new.png)

Por último, es necesario conectar el control **[Mostrar formulario](controls/control-form-detail.md)** con el control **[Galería](controls/control-gallery.md)** para poder ver los detalles de un registro específico.  Tan pronto como se termine de establecer la propiedad **[Item](controls/control-form-detail.md)** , el primer registro de la galería aparecerá en el formulario.

* Establezca la propiedad **[Item](controls/control-form-detail.md)** del control **[Mostrar formulario](controls/control-form-detail.md)** en **Gallery1.Selected**.
   
    Los detalles del elemento seleccionado aparecen en el formulario.
   
    ![Mostrar formulario para el origen de datos Helado conectado al control Galería](./media/working-with-forms/view-form-select-coconut.png)

Excelente.  Ahora analizaremos la navegación: cómo un usuario abre la pantalla de detalles desde la pantalla de galería y viceversa.

* Agregue un control **[Botón](controls/control-button.md)** a la pantalla, establezca su propiedad **[Text](controls/properties-core.md)** para mostrar **[Back](functions/function-navigate.md)** , y establezca su propiedad **[OnSelect](controls/properties-core.md)** en **Back()** .
   
    Esta fórmula devuelve al usuario a la galería cuando termina de ver los detalles.

    ![Mostrar formulario para el origen de datos Helado con botón para volver](./media/working-with-forms/viewform-icecream-back.png)

Volvamos al control **[Galería](controls/control-gallery.md)** y agreguemos navegación a la pantalla de detalle.

1. Vaya a la primera pantalla, que hospeda el control **[Galería](controls/control-gallery.md)** , y seleccione la flecha del primer elemento de la galería.

2. Establezca la propiedad **[OnSelect](controls/properties-core.md)** de la forma en esta fórmula:
   <br>**Navigate( Screen2, None )**
   
    ![Mostrar formulario para el origen de datos Helado con botón para volver](./media/working-with-forms/gallery-icecream-nav-new.png)

3. Presione F5 y seleccione una flecha en la galería para mostrar los detalles de un elemento.

4. Seleccione el botón **[Atrás](functions/function-navigate.md)** para volver a la galería de productos y, luego, presione Esc.

## <a name="editing-details"></a>Edición de detalles
Finalmente, la última actividad central es cambiar el contenido de un registro, algo que los usuarios pueden hacer en un control **[Editar formulario](controls/control-form-detail.md)** .

El control **[Editar formulario](controls/control-form-detail.md)** usa dos propiedades para mostrar y editar el registro:

* Propiedad **[DataSource](controls/control-form-detail.md)** .  El nombre del origen de datos que contiene el registro.  Del mismo modo que con el control **[Mostrar formulario](controls/control-form-detail.md)** , esta propiedad rellena el panel de la derecha con campos y determina el nombre para mostrar y el tipo de datos (cadena, número, fecha, etc.) de cada campo. Esta propiedad también determina si el valor de cada campo es válido antes de enviarlo al origen de datos subyacente.
* Propiedad **[Item](controls/control-form-detail.md)** .  El registro que se editará, que a menudo está conectado a la propiedad **Selected** del control **[Galería](controls/control-gallery.md)** . Así, puede seleccionar un registro en el control **[Galería](controls/control-gallery.md)** , mostrarlo en la pantalla de detalles y editarlo en la pantalla **Editar y crear**.

Para agregar un control **[Editar formulario](controls/control-form-detail.md)** :

1. Agregue una pantalla y un control **[Editar formulario](controls/control-form-detail.md)** y, luego, establezca la propiedad **[DataSource](controls/control-form-detail.md)** del formulario en **"Helado"** .
2. Establezca la propiedad **[Item](controls/control-form-detail.md)** en **Gallery1.Selected**.

Ahora puede seleccionar los campos que se mostrarán en la pantalla. También puede seleccionar el tipo de tarjeta que se mostrará para cada campo. Cuando hace cambios en el panel de la derecha, la propiedad **[DataField](controls/control-card.md)** de cada control **[Tarjeta](controls/control-card.md)** se establece en el campo con el que interactuará el usuario.  La pantalla debe ser similar al ejemplo:

![Mostrar formulario para el origen de datos Helado](./media/working-with-forms/icecream-edit.png)

Estas dos propiedades son las mismas propiedades del control **[Mostrar formulario](controls/control-form-detail.md)** .  Con ellas se pueden mostrar los detalles de un registro.  

El control **[Editar formulario](controls/control-form-detail.md)** va más allá y ofrece la función **[SubmitForm](functions/function-form.md)** para reescribir los cambios en el origen de datos. Puede usarla con un control de botón o imagen para guardar los cambios de un usuario.

* Agregue un control **[Botón](controls/control-button.md)** , establezca la propiedad **[Text](controls/properties-core.md)** para mostrar **Guardar** y establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br>
  **SubmitForm( Form1 )**

![Editar formulario para el origen de datos Helado](./media/working-with-forms/edit-icecream-save.png)

Para agregar navegación desde esta pantalla y hacia ella:

1. Agregue otro control **[Botón](controls/control-button.md)** , establezca la propiedad **[Text](controls/properties-core.md)** para mostrar **Cancelar** y establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula: <br>**ResetForm( Form1 ); Back()**
   
    Esta fórmula descarta las ediciones no guardadas y abre la pantalla anterior.
   
    ![Mostrar formulario para el origen de datos Helado](./media/working-with-forms/edit-icecream-cancel.png)
2. Establezca la propiedad **[OnSuccess](controls/control-form-detail.md)** del formulario en **Back()** .
   
    Si las actualizaciones se guardan correctamente, la pantalla anterior (en este caso, la pantalla de detalles) se abre automáticamente.
   
    ![Editar formulario con la regla "OnSuccess" agregada](./media/working-with-forms/edit-icecream-onsuccess.png)
3. En la pantalla **Mostrar**, agregue un botón, establezca su propiedad **[Text](controls/properties-core.md)** para mostrar **Editar** y establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br> **Navigate( Screen3, None )**
   
    ![Mostrar formulario con el botón "Editar" agregado](./media/working-with-forms/viewform-icecream-edit.png)

Ha compilado una aplicación básica con tres pantallas para ver y escribir datos.  Para probarla, muestre la pantalla de galería y, luego, presione F5 (o seleccione el botón "Vista previa" de la flecha hacia adelante junto a la esquina superior izquierda de la pantalla). El punto rosa indica donde el usuario toca o hace clic en la pantalla en cada paso.

![Prueba de la aplicación Helado](./media/working-with-forms/try-icecream.png)

## <a name="create-a-record"></a>Creación de un registro
El usuario interactúa con el mismo formulario **Editar** para actualizar y crear registros. Cuando el usuario desea crear un registro, la función **[NewForm](functions/function-form.md)** cambia el formulario al modo **New**.

Si el formulario está en modo **New**, el valor de cada campo se establece en los valores predeterminados del origen de datos. Se omite el registro que se proporcionó en la propiedad **[Item](controls/control-form-detail.md)** del formulario.  

Cuando el usuario está listo para guardar el registro nuevo, se ejecuta **[SubmitForm](functions/function-form.md)** . Una vez que el formulario se envía correctamente, vuelve al modo **EditMode**.  

En la primera pantalla, agregará un botón **Nuevo**:

1. En la pantalla con la galería, agregue un control **[Botón](controls/control-button.md)** .
2. Establezca la propiedad **[Text](controls/properties-core.md)** en **New** y su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br>
   **NewForm( Form1 ); Navigate( Screen3, None )**
   
    Esta fórmula cambia el control **[Editar formulario](controls/control-form-detail.md)** en **Screen3** al modo **New** y se abre esa pantalla para que el usuario pueda rellenarla.

![Mostrar formulario con el botón "Editar" agregado](./media/working-with-forms/gallery-icecream-new.png)

Cuando se abre la pantalla Editar y crear, el formulario está vacío y listo para que el usuario agregue un elemento. Cuando el usuario selecciona el botón **Guardar**, la función **[SubmitForm](functions/function-form.md)** garantiza que se cree un registro, en lugar de actualizarlo. Si el usuario selecciona el botón **Cancelar**, la función **[ResetForm](functions/function-form.md)** vuelve a cambiar el formulario al modo **Edit** y la función **[Back](functions/function-navigate.md)** abre la pantalla para explorar la galería.

## <a name="delete-a-record"></a>Eliminación de un registro
1. En la pantalla **Mostrar**, agregue un botón y establezca su propiedad **[Text](controls/properties-core.md)** para que muestre **Eliminar**.
2. Establezca la propiedad **[OnSelect](controls/properties-core.md)** del botón en esta fórmula:
   <br>**Remove( 'Ice Cream', Gallery1.Selected ); Back()**
   
    ![Mostrar formulario con el botón "Editar" agregado](./media/working-with-forms/viewform-icecream-remove.png)

## <a name="handling-errors"></a>Control de errores
En esta aplicación, se produce un error si el valor de un campo no es válido, si un campo obligatorio está en blanco, si se le desconecta de la red o si emerge cualquier otro número de problemas.  

Si **[SubmitForm](functions/function-form.md)** presenta un error por cualquier motivo, la propiedad **Error** del control **[Editar formulario](controls/control-form-detail.md)** contiene un mensaje de error que se le mostrará al usuario. Con esta información, el usuario debe poder corregir el problema y reenviar el cambio, o bien puede cancelar la actualización.

1. En la pantalla Editar y crear, agregue un control **[Etiqueta](controls/control-text-box.md)** y póngalo justo debajo del botón **Guardar**. Será sencillo detectar cualquier error una vez que el usuario seleccione este control para guardar los cambios.

2. Establezca la propiedad **[Texto](controls/properties-core.md)** del control **[Etiqueta](controls/control-text-box.md)** para mostrar **Form1.Error**.

    ![Mostrar formulario con el botón "Editar" agregado](./media/working-with-forms/edit-icecream-error.png)

En una aplicación que Power apps genera a partir de datos, la propiedad **[autoheight](controls/control-text-box.md)** de este control está establecida en *true* para que no se consuma espacio si no se produce ningún error. Las propiedades **[Height](controls/properties-size-location.md)** e **[Y](controls/properties-size-location.md)** del control **[Editar formulario](controls/control-form-detail.md)** también se ajustan de forma dinámica para contemplar el crecimiento de este control cuando se produce un error. Para más detalles, genere una aplicación a partir de los datos existentes y revise estas propiedades. El control de cuadro de texto para los errores es muy breve cuando no se ha producido ningún error; es posible que tenga que abrir la vista **Avanzada** (disponible en la pestaña **Ver**) para seleccionar este control.

![Editar formulario de aplicación desde datos con el control de texto de error seleccionado](./media/working-with-forms/edit-assets-error1.png)

![Editar formulario de aplicación desde datos con el control de formulario seleccionado](./media/working-with-forms/edit-assets-error2.png)

## <a name="refresh-data"></a>Actualización de datos
El origen de datos se actualiza cada vez que el usuario abre la aplicación, pero es posible que el usuario quiera actualizar los registros en la galería sin cerrar la aplicación. Agregue un botón **Actualizar**, de modo que el usuario pueda seleccionarlo para actualizar manualmente los datos:

1. En la pantalla con el control **[Galería](controls/control-gallery.md)** , agregue un control **[Botón](controls/control-button.md)** y establezca su propiedad **[Text](controls/properties-core.md)** para que muestre **Actualizar**.

2. Establezca la propiedad **[OnSelect](controls/properties-core.md)** de este control en esta fórmula:<br> **Refresh( 'Ice Cream' )**

    ![Actualización del origen de datos](./media/working-with-forms/browse-icecream-refresh.png)

## <a name="search-and-sort-the-gallery"></a>Búsqueda y ordenación de la galería
En la aplicación que Power apps generó a partir de los datos, no se analizan dos controles en la parte superior de la pantalla de exploración. Con estos controles, el usuario puede buscar uno o varios registros, ordenar la lista de registros en orden ascendente o descendente, o ambas acciones.

![Controles de ordenación y búsqueda en la pantalla de exploración](./media/working-with-forms/afd-browse-search-sort.png)

Cuando el usuario selecciona el botón de ordenación, se invierte el criterio de ordenación de la galería. Para crear este comportamiento, usamos una *variable de contexto* para hacer seguimiento de la dirección en que se ordena la galería. Cuando el usuario selecciona el botón, se actualiza la variable y se invierte la dirección. La propiedad **[OnSelect](controls/properties-core.md)** del botón de ordenación se establece en esta fórmula: **UpdateContext( {SortDescending1: !SortDescending1} )**

La función **[UpdateContext](functions/function-updatecontext.md)** crea la variable de contexto **SortDescending1** si todavía no existe. La función leerá el valor de la variable y lo establecerá en la lógica opuesta con el operador **!** . Si el valor es *true*, se convierte en *false*. Si el valor es *false*, se convierte en *true*.

La fórmula de la propiedad **[Items](controls/properties-core.md)** del control **[Galería](controls/control-gallery.md)** usa esta variable de contexto junto con el texto del control **TextSearchBox1**:

```powerapps-dot
Sort( 
    If( IsBlank(TextSearchBox1.Text),
        Assets,
        Filter( Assets, TextSearchBox1.Text in Text(ApproverEmail) ) 
    ),
    ApproverEmail,
    If(SortDescending1, Descending, Ascending) 
)
```

Desglosemos esto:

* Por fuera, tenemos la función **[Sort](functions/function-sort.md)** , que toma tres argumentos: una tabla, un campo según el cual ordenar y la dirección de ordenación.  
  
  * La dirección de ordenación se toma de la variable de contexto que alterna cuando el usuario selecciona el control **ImageSortUpDown1**. El valor *true*/*false* se traduce a las constantes **Descending** y **Ascending**.
  * El campo de ordenación se fija en **ApproverEmail**. Si cambia los campos que aparecen en la galería, también deberá cambiar este argumento.
* Por dentro, tenemos la función **[Filter](functions/function-filter-lookup.md)** , que toma una tabla como argumento y una expresión para evaluar para cada registro.
  
  * La tabla es el origen de datos **Assets** sin procesar, que es el punto de partida antes de filtrar u ordenar.
  * La expresión busca una instancia de la cadena en **TextSearchBox1** dentro del campo **ApproverEmail**.  Le recordamos que si cambia los campos que aparecen en la galería, también deberá actualizar este argumento.
  * Si el valor **TextSearchBox1** está vacío, el usuario desea mostrar todos los registros y se omite la función **[Filter](functions/function-filter-lookup.md)** .

Este es solo un ejemplo, porque puede crear su propia fórmula para la propiedad **[Items](controls/properties-core.md)** , en función de las necesidades de la aplicación, si junta las funciones **[Filter](functions/function-filter-lookup.md)** , **[Sort](functions/function-sort.md)** y otras.    

## <a name="screen-design"></a>Diseño de pantalla
Hasta ahora, no hemos analizado otras formas para distribuir los controles entre las pantallas. Esto se debe a que tiene muchas opciones y la mejor selección depende de las necesidades específicas de la aplicación.

Como el espacio real en las pantallas de los teléfonos es tan limitado, es probable que desee buscar, mostrar y editar o crear formularios en distintas pantallas. En este tema, las funciones **[Navigate](functions/function-navigate.md)** y **[Back](functions/function-navigate.md)** abren cada pantalla.  

En una tableta, puede buscar, mostrar y editar o crear formularios en dos pantallas, o incluso en una. En el último caso, no se requerirá la función **[Navigate](functions/function-navigate.md)** ni la función **[Back](functions/function-navigate.md)** .

Si el usuario trabaja en la misma pantalla, se debe tener cuidado de que el usuario no pueda cambiar la selección de la **[Galería](controls/control-gallery.md)** porque podría perder las modificaciones hechas en el control **[Editar formulario](controls/control-form-detail.md)** .  Para evitar que el usuario seleccione un registro distinto cuando todavía no se guardan los cambios en otro registro, establezca la propiedad **[Disabled](controls/properties-core.md)** de la galería en esta fórmula:<br>
**EditForm.Unsaved**

