---
title: 'Control Cámara: referencia | Microsoft Docs'
description: Información sobre el control Cámara, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/07/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 59c0f85dd71c9dc512e348d6d8ee9686d6945fa1
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80871129"
---
# <a name="camera-control-in-power-apps"></a>Control Cámara en Power Apps

Un control que permite a los usuarios tomar fotografías con la cámara en un dispositivo.

## <a name="description"></a>Descripción

Use el control **cámara** para capturar imágenes con la cámara de un dispositivo.  El dispositivo debe tener una cámara y el usuario debe autorizar a la aplicación para que use la cámara. El control de cámara se admite cuando se ejecuta en un explorador Web.

La imagen capturada más recientemente está disponible a través de la propiedad **Photo** . Con esta propiedad, las imágenes pueden ser:

- **Se ve con el control de imagen.** Use el control [imagen](control-image.md) para ver la imagen capturada. Para obtener más información, vea los [ejemplos](#examples).  
- **Se coloca temporalmente en una variable o una colección.**  Use las funciones [set](../functions/function-set.md) o [Collect](../functions/function-clear-collect-clearcollect.md) para almacenar imágenes en una variable o una colección.  Tenga cuidado al usar varias imágenes en una colección al mismo tiempo que consume memoria limitada del dispositivo. Use las funciones [savedata](../functions/function-savedata-loaddata.md) y [LoadData](../functions/function-savedata-loaddata.md) para trasladar imágenes al almacenamiento local en el dispositivo y para [escenarios sin conexión](../offline-apps.md).
- **Almacenado en una base de datos.**  Utilice la función [patch](../functions/function-patch.md) para almacenar imágenes en una base de datos.
- **Se transmite como una cadena de texto codificada en Base64.**  Use la función [JSON](../functions/function-json.md) para codificar imágenes en Base64.

Use las propiedades **Stream**, **Tasasecuencia**y **ALStream** para capturar imágenes automáticamente en un temporizador, por ejemplo, ajustar una imagen cada minuto para crear una secuencia Time-lapse.

Un URI de cadena de texto hace referencia a los medios capturados. Para obtener más información, lea la [documentación del tipo de datos](../functions/data-types.md#uris-for-images-and-other-media).

Las imágenes generadas por el control de cámara no suelen estar en la resolución completa de la cámara. Si necesita imágenes de resolución completa, use el control [Agregar imagen](control-add-picture.md) .

## <a name="key-properties"></a>Propiedades principales

**AvailableDevices** : tabla de las cámaras disponibles en el dispositivo.

La tabla contiene dos columnas: 
- Número de *identificación* que se va a usar con la propiedad **Camera** 
- *Nombre* proporcionado por el dispositivo para identificar la cámara. Algunas plataformas pueden incluir *Front* o *back* para ayudar a encontrar la cámara.

*Nota*: no todos los dispositivos de la tabla pueden usarse en la aplicación.  Algunos pueden ser controladores especializados o aplicaciones destinadas a fines específicos.  

**Cámara** : el identificador numérico de la cámara que se va a usar.  Resulta útil en dispositivos con más de una cámara.  

**EnSecuencia**: indica cómo responde la aplicación cuando la propiedad **Stream** está actualizada.

**Foto** : la imagen que se captura cuando el usuario toma una fotografía. 

**Stream**: la imagen se actualiza automáticamente en la propiedad **TasaSecuencia**.

**TasaSecuencia**: la frecuencia de actualización de la imagen en la propiedad **Stream**, en milisegundos. Este valor puede oscilar entre 100 (1/10 centésimas de segundo) y 3 600 000 (1 hora).

## <a name="additional-properties"></a>Propiedades adicionales

[AccessibleLabel](properties-accessibility.md): etiqueta para lectores de pantalla. Debe describir la finalidad de realizar una foto.

[BorderColor](properties-color-border.md): el color de un borde del control.

[BorderStyle](properties-color-border.md) : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

[BorderThickness](properties-color-border.md): el grosor de un borde del control.

**Brillo**: indica la claridad que el usuario percibirá probablemente en una imagen.

**Contraste**: indica cómo el usuario puede distinguir fácilmente colores similares en una imagen.

[DisplayMode](properties-core.md) : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**deshabilitado**).

[FocusedBorderColor](properties-color-border.md) : el color del borde de un control cuando el control tiene el foco.

[FocusedBorderThickness](properties-color-border.md) : el grosor del borde de un control cuando el control tiene el foco.

[Height](properties-size-location.md): la distancia entre los bordes superior e inferior de un control.

[OnSelect](properties-core.md): indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

[TabIndex](properties-accessibility.md) : orden de navegación por el teclado comparado con otros controles.

[Tooltip](properties-core.md): texto explicativo que aparece cuando el usuario mantiene el mouse sobre un control.

[Visible](properties-core.md): indica si un control aparece o está oculto.

[Width](properties-size-location.md): la distancia entre los bordes derecho e izquierdo de un control.

[X](properties-size-location.md) : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor o pantalla primaria.

[Y](properties-size-location.md) : la distancia entre el borde superior de un control y el borde superior del contenedor o la pantalla primarios.

## <a name="examples"></a>Ejemplos

En estos ejemplos, necesitará un dispositivo con una cámara. Para probar la aplicación, use una cámara web accesible desde el explorador. O bien, guarde la aplicación y cargarla en un dispositivo iOS o Android con una cámara.

### <a name="simple-display-of-a-captured-picture"></a>Visualización simple de una imagen capturada

1. [Agregue](../add-configure-controls.md) un control de **cámara** .

1. Autorice a la aplicación a usar la cámara del dispositivo si se le solicita.

1. Agregue un control [**imagen**](../controls/control-image.md) .

1. Establezca la propiedad **Image** del control **imagen** en la fórmula siguiente:

    ```powerapps-dot
    Camera1.Photo
    ```

    > [!NOTE]
    > Reemplace el nombre del control de cámara *Camera1* según corresponda.

1. Presione F5 para obtener una vista previa de la aplicación.

1. Tome una imagen seleccionando o pulsando el control cámara. Debería ver el resultado en el control de imagen.

### <a name="add-pictures-to-an-image-gallery-control"></a>Agregar imágenes a un control Galería de imágenes

1. Agregue un control **cámara** , asígnele el nombre de **la cámara y**establezca su propiedad [alseleccionar](properties-core.md) en esta fórmula:

    ```powerapps-dot
    Collect( MyPix, MyCamera.Photo )
    ```

    Para obtener más información:

    - [¿Cómo agregar, nombrar y configurar un control?](../add-configure-controls.md)
    - Obtenga más información sobre la función [Collect](../functions/function-clear-collect-clearcollect.md) u [otras funciones](../formula-reference.md).

1. Presione F5 y, a continuación, tome una imagen seleccionando o tocando la **cámara**.

1. Agregue un control [Galería vertical](control-gallery.md) . Y, a continuación, cambie el tamaño del control de [imagen](control-image.md) , su plantilla y el propio control **Galería de imágenes** para que quepa en la pantalla.

1. Establezca la propiedad [elementos](properties-core.md) del control **Galería de imágenes** en esta fórmula:
 
    ```powerapps-dot
    MyPix
    ```

1. Establezca la propiedad [imagen](properties-visual.md) del control **imagen** de la galería en esta fórmula:

    ```powerapps-dot   
    ThisItem.Url
    ```

    La imagen que tomó aparece en el control **Galería de imágenes** .

1. Tome tantas imágenes como desee y, a continuación, vuelva al área de trabajo predeterminada presionando ESC.

1. opta Establezca la propiedad **alseleccionar** del control **imagen** en el control **Galería de imágenes** en la fórmula:

    ```powerapps-dot
    Remove( MyPix, ThisItem )
    ```

1. Presione F5 y, a continuación, seleccione una imagen para quitarla.

Utilice la función [savedata](../functions/function-savedata-loaddata.md) para guardar las imágenes localmente o la función [patch](../functions/function-patch.md) para actualizar un origen de datos.

### <a name="change-the-active-camera-from-a-drop-down"></a>Cambiar la cámara activa de un menú desplegable

1. [Agregue](../add-configure-controls.md) un control de **cámara** .

1. Autorice a la aplicación a usar la cámara del dispositivo si se le solicita.
    
1. [Agregue](../add-configure-controls.md) un control [lista](control-drop-down.md) desplegable.

1. Establezca el prroperty de **elementos** de la lista desplegable en:

    ```powerapps-dot
    Camera1.AvailableDevices
    ```

    > [!NOTE]
      > Reemplace el nombre del control de cámara *Camera1* según corresponda.
    
1. Establezca la propiedad **Camera** de la cámara en: 

    ```powerapps-dot
    Dropdown1.Selected.Id
    ```

    > [!NOTE]
      > Reemplace el nombre del control DropDown *Dropdown1* según corresponda.

1. Presione F5 y, a continuación, seleccione un elemento de la lista desplegable para cambiar la cámara.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

El control cámara muestra la fuente de cámara y también funciona como un botón que toma una fotografía. Por lo tanto, existen consideraciones de accesibilidad similares a las de los botones.

### <a name="video-alternatives"></a>Alternativas de vídeo

Considere la posibilidad de agregar una forma alternativa de entrada para los usuarios con discapacidades visuales. Por ejemplo, [agregue una imagen](control-add-picture.md) para permitir que los usuarios carguen una imagen desde su dispositivo.

### <a name="color-contrast"></a>Contraste de color

Debe haber un contraste de color adecuado entre [FocusedBorderColor](properties-color-border.md) y el color exterior.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla

[Propiedad accessiblelabel](properties-accessibility.md) debe estar presente.

### <a name="keyboard-support"></a>Compatibilidad con el teclado

- [TabIndex](properties-accessibility.md) debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.

- Los indicadores de foco deben ser claramente visibles. Use [FocusedBorderColor](properties-color-border.md) y [FocusedBorderThickness](properties-color-border.md) para actualizar la visibilidad de los indicadores de foco.
