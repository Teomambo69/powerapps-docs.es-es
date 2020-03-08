---
title: Descripción de las tarjetas de datos | Microsoft Docs
description: En Power Apps, use las tarjetas de formulario para recopilar y Mostrar información de un origen de datos.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4b159bbfe568e4f3a6501a0d98af83ac062b8c19
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404265"
---
# <a name="understand-data-cards-in-power-apps"></a>Descripción de las tarjetas de datos en Power apps

Los controles **[Tarjeta](controls/control-card.md)** son los componentes fundamentales de los controles **[Editar formulario](controls/control-form-detail.md)** y **[Mostrar formulario](controls/control-form-detail.md)** en aplicaciones de lienzo. El formulario representa todo el registro y cada tarjeta representa un único campo de ese registro.

Puede interactuar con las tarjetas más fácilmente en el panel derecho después de seleccionar un control de formulario en el área de trabajo de diseño. En este panel, puede elegir los campos que desea mostrar, cómo mostrarlos y en qué orden. En este ejemplo se muestra un control **Formulario de edición** en una aplicación que se crea a partir de una lista de SharePoint denominada **Assets**.

![Primera pantalla](./media/working-with-cards/first-screen.png)

Para empezar a trabajar con las tarjetas, consulte cómo [agregar un formulario](add-form.md) y cómo [entender los formularios de datos](working-with-forms.md). En el resto de este tema se explica con más detalle cómo funcionan las tarjetas y cómo puede personalizar o incluso crear las suyas propias.

## <a name="predefined-cards"></a>Tarjetas predefinidas

Power Apps ofrece un conjunto predefinido de tarjetas para cadenas, números y otros tipos de datos. En el panel derecho, puede ver las variaciones disponibles y cambiar la tarjeta usada para un campo:

![](./media/working-with-cards/selected-card.png)

En este ejemplo, se ha seleccionado una tarjeta con una sola línea de texto, pero el texto de la dirección URL ocupa más de lo que se puede mostrar en una única línea. Vamos a cambiarla a una tarjeta con múltiples líneas de texto para ofrecer a nuestros usuarios más espacio para editar:

![](./media/working-with-cards/multiline-edit.png)

Algunos de los campos de este origen de datos no se muestran, pero puede mostrar u ocultar un campo seleccionando su casilla. En este ejemplo se explica cómo mostrar el campo **SecurityCode**.

![](./media/working-with-cards/add-security-code.png)

## <a name="customize-a-card"></a>Personalizar una tarjeta
Las tarjetas constan de otros controles. En un control **Formulario de edición**, el usuario escribe datos en un control **[Entrada de texto](controls/control-text-input.md)** estándar que se agrega desde la pestaña **Insertar**.  

Analicemos un ejemplo de cambio de la apariencia de la tarjeta mediante la manipulación de los controles que aparecen en ella.

1. En primer lugar, vamos a volver a la tarjeta que insertamos más recientemente para el campo **SecurityCode**. Seleccione esta tarjeta pulsándola una vez o haciendo clic en ella:
   
    ![](./media/working-with-cards/select-security-code.png)
2. Seleccione el control **[Text Input](controls/control-text-input.md)** situado dentro de la tarjeta pulsando o haciendo clic en el propio control de entrada.
   
    ![](./media/working-with-cards/select-text-input.png)
3. Mueva este control dentro de la tarjeta arrastrando el cuadro de selección y cambie su tamaño arrastrando los controladores a lo largo del borde del cuadro de selección:
   
    ![](./media/working-with-cards/customize-text-input.png)  

Puede cambiar el tamaño de los controles de una tarjeta, moverlos y realizar otras modificaciones, pero no puede eliminarla sin desbloquearla primero.

## <a name="unlock-a-card"></a>Desbloquear una tarjeta
Además de contener controles, las tarjetas constituyen en sí mismas controles que tienen propiedades y fórmulas, al igual que cualquier otro control. Cuando decide mostrar un campo en un formulario, el panel derecho crea automáticamente la tarjeta y genera las fórmulas necesarias.  Podemos ver estas fórmulas en la pestaña **Avanzado** del panel derecho:

![](./media/working-with-cards/advanced-locked.png)

Inmediatamente vemos una de las propiedades más importantes de la tarjeta: **[DataField](controls/control-card.md)** . Esta propiedad indica qué campo del origen de datos puede ver y editar el usuario en esta tarjeta.  

En la pestaña **Avanzado**, el banner que aparece en la parte superior indica que las propiedades de esta tarjeta están bloqueadas. También aparece un icono de bloqueo junto a las propiedades **[DataField](controls/control-card.md)** , **[DisplayName](controls/control-card.md)** y **[Required](controls/control-card.md)** . El panel derecho fue el que creó estas fórmulas y el bloqueo impide que se realicen cambios accidentales en estas propiedades.

![](./media/working-with-cards/lock-icons.png)

Pulse o haga clic en la pancarta que aparece en la parte superior para desbloquear la tarjeta y poder modificar estas propiedades:

![](./media/working-with-cards/unlocked-card.png)

Vamos a modificar **[DisplayName](controls/control-card.md)** para agregar un espacio entre **Asset** e **ID**. Al realizar este cambio, estamos alterando lo que se ha generado automáticamente.  En el panel derecho, esta tarjeta tiene una etiqueta distinta:

![](./media/working-with-cards/change-display-name.png)

Ahora hemos tomado el control de esta tarjeta y podemos modificarla para que se ajuste a nuestras necesidades. Pero hemos perdido la capacidad que teníamos antes de cambiar la tarjeta de una representación a otra (por ejemplo, de texto de una sola línea a texto de múltiples líneas). Hemos transformado la tarjeta predefinida en una "tarjeta personalizada" sobre la que tenemos control.  

> [!IMPORTANT]
> Si ha desbloqueado una tarjeta, no podrá volver a bloquearla. Para volver al estado de bloqueo, quite la tarjeta y vuelva a insertarla en el panel derecho.

Puede cambiar la apariencia y el comportamiento de una tarjeta desbloqueada de varias formas como, por ejemplo, con la adición y eliminación de los controles dentro de ella. Por ejemplo, puede agregar una forma de estrella desde el menú **Iconos** de la pestaña **Insertar**.

![](./media/working-with-cards/add-star.png)

Ahora, la estrella forma parte de la tarjeta y se moverá con ella si, por ejemplo, reordena las tarjetas en el formulario.

Como otro ejemplo, desbloquee la tarjeta **ImageURL** y, a continuación, agregue un control **Image** en ella mediante la pestaña **Insertar**:

![](./media/working-with-cards/add-image.png)

En la barra de fórmulas, establezca la propiedad **Image** de este control en *TextBox*.**Text**, en la que *TextBox* es el nombre del control **Entrada de texto** que contiene la URL:

![](./media/working-with-cards/show-image.png)

Ahora ya podemos ver las imágenes y editar sus direcciones URL. Observe que podríamos haber usado **Parent.Default** como la propiedad **Image**, pero no se habría actualizado si el usuario hubiera cambiado la dirección URL.

Podemos hacer lo mismo en la segunda pantalla de esta aplicación, en la que usamos un control **Formulario de presentación** para mostrar los detalles de un registro. En este caso, es posible que queramos ocultar la etiqueta (establezca la propiedad **Visible** de la etiqueta, no la tarjeta, en **false**) porque el usuario no editará la dirección URL en esa pantalla:

![](./media/working-with-cards/show-image-display.png)

## <a name="interact-with-a-form"></a>Interactuar con un formulario
Después de desbloquear una tarjeta, puede cambiar la forma en que interactúa con el formulario que la contiene.

Más adelante se muestran algunas directrices sobre cómo deben funcionar los controles con su tarjeta y cómo deben funcionar las tarjetas con el formulario. Se trata únicamente de directrices. Como sucede con cualquier control en Power Apps, puede crear fórmulas que hagan referencia a cualquier otro control de Power apps y eso no es menos cierto para tarjetas y controles dentro de las tarjetas. Sea creativo: puede crear una aplicación de muchas maneras.  

### <a name="datafield-property"></a>Propiedad DataField
La propiedad más importante de la tarjeta es **[DataField](controls/control-card.md)** .  Esta propiedad controla la validación, qué campo se actualiza y otros aspectos de la tarjeta.

### <a name="information-flowing-in"></a>Información que entra
Como contenedor, el formulario pone **ThisItem** a disposición de todas las tarjetas que incluye. Este registro contiene todos los campos del registro actual de interés.  

La propiedad **[Default](controls/properties-core.md)** de todas las tarjetas debe establecerse como **ThisItem**.*FieldName*.  En determinadas circunstancias, es posible que le interese transformar este valor cuando lo especifique. Por ejemplo, es posible que desee dar formato a una cadena o traducir el valor de un idioma a otro.

Todos los controles de la tarjeta deben hacer referencia a **Parent.Default** para tener acceso al valor del campo. Esta estrategia proporciona un nivel de encapsulación para la tarjeta, de forma que la propiedad **[Default](controls/properties-core.md)** de esta pueda cambiar sin que lo hagan sus fórmulas internas.

De forma predeterminada, las propiedades **DefaultValue** y **[Required](controls/control-card.md)** se toman de los metadatos del origen de datos basándose en la propiedad **[DataField](controls/control-card.md)** . Puede reemplazar estas fórmulas con su propia lógica, integrando los metadatos del origen de datos mediante el uso de la función **[DataSourceInfo](functions/function-datasourceinfo.md)** .

### <a name="information-flowing-out"></a>Información que sale
Después de que el usuario modifique un registro usando los controles de las tarjetas, la función **[SubmitForm](functions/function-form.md)** guarda esos cambios en el origen de datos. Cuando se ejecuta esa función, el control de formulario lee los valores de la propiedad **[DataField](controls/control-card.md)** de cada tarjeta para saber qué campo debe cambiar.  

El control de formulario también lee el valor de la propiedad **[Update](controls/control-card.md)** de cada tarjeta. Este valor se almacenará en el origen de datos para este campo. Este es el lugar para aplicar otra transformación, quizás para revertir la transformación que se ha aplicado en la fórmula **[Default](controls/properties-core.md)** de la tarjeta.

La propiedad **Valid** se toma de los metadatos del origen de datos, basándose en la propiedad **[DataField](controls/control-card.md)** . También depende de la propiedad **[Required](controls/control-card.md)** y de si la propiedad **[Update](controls/control-card.md)** contiene un valor. Si el valor de la propiedad **[Update](controls/control-card.md)** no es válido, la propiedad **Error** proporciona un mensaje de error descriptivo.

Si la propiedad **[DataField](controls/control-card.md)** de una tarjeta está *en blanco*, la tarjeta sencillamente es un contenedor de controles. Sus propiedades **Valid** y **[Update](controls/control-card.md)** no participan cuando se envía el formulario.

## <a name="dissecting-an-example"></a>Examinar un ejemplo
Echemos un vistazo a los controles que componen una tarjeta de entrada de datos básica. Se ha aumentado el espacio entre controles para mostrar cada uno de ellos de forma más clara:

![](./media/working-with-cards/dissect-card1.png)

En este gráfico, los controles de la tarjeta de datos tienen la etiqueta:

![](./media/working-with-cards/dissect-card2.png)

Cuatro controles hacen que esta tarjeta funcione:

| Name | Tipo | Descripción |
| --- | --- | --- |
| **TextRequiredStar** |Control **[Etiqueta](controls/control-text-box.md)** |Muestra una estrella, que se utiliza habitualmente en los formularios de entrada de datos para indicar que un campo es obligatorio. |
| **TextFieldDisplayName** |Control **[Etiqueta](controls/control-text-box.md)** |Muestra el nombre descriptivo de este campo. Este nombre puede diferir de lo que aparece en el esquema del origen de datos. |
| **InputText** |Control **Input text** |Muestra el valor inicial del campo y permite al usuario cambiar dicho valor. |
| **TextErrorMessage** |Control **[Etiqueta](controls/control-text-box.md)** |Muestra un mensaje de error descriptivo al usuario si se produce un problema con la validación. También garantiza que el campo tiene un valor si es necesario. |

Para rellenar estos controles con datos, se pueden tomar sus propiedades de las propiedades de la tarjeta a través de estas fórmulas claves. Tenga en cuenta que ninguna de estas fórmulas hace referencia a un campo específico. En su lugar, toda la información procede de la tarjeta.

| Propiedad de control | Fórmula | Descripción |
| --- | --- | --- |
| **TextRequiredStar.Visible** |**Parent.Required** |La estrella solo aparece si el campo es obligatorio. "Required" es una fórmula controlada por usted o los metadatos del origen de datos. |
| **TextFieldDisplayName.Text** |**Parent.DisplayName** |El control de cuadro de texto muestra el nombre descriptivo, proporcionado por usted o los metadatos del origen de datos, y que se establece en la propiedad **[DisplayName](controls/control-card.md)** de la tarjeta. |
| **InputText.Default** |**Parent.Default** |Inicialmente, el control de entrada de texto muestra el valor del campo del origen de datos, según lo proporcionado por el valor predeterminado de la tarjeta. |
| **TextErrorMessage.Text** |**Parent.Error** |Si se produce un problema de validación, la propiedad **Error** de la tarjeta proporciona el correspondiente mensaje de error. |

> [!NOTE]
> La propiedad **Parent. error** es una propiedad de solo salida que no se puede establecer mediante una fórmula. Por lo tanto, esta propiedad no aparecerá en la lista de propiedades cerca de la esquina superior izquierda o en las pestañas **propiedades** o **avanzadas** cerca del borde derecho. La barra de fórmulas sugiere esta propiedad si está escribiendo una fórmula que podría hacer referencia a la propiedad.

Para extraer información de estos controles y volver a insertarla en el origen de datos, tenemos las siguientes fórmulas clave:

| Nombre del control | Fórmula | Descripción |
| --- | --- | --- |
| **DataCard.DataField** |**"ApproverEmail"** |El nombre del campo que el usuario puede mostrar y editar en esta tarjeta. |
| **DataCard.Update** |**InputText.Text** |El valor que se valida y se vuelve a insertar en el origen de datos cuando se ejecuta **[SubmitForm](functions/function-form.md)** . |

