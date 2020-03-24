---
title: Funciones SaveData y LoadData | Microsoft Docs
description: Información de referencia, incluida la sintaxis, para las funciones SaveData y LoadData en Power apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c90f0be8d1f8f62afd3fdec1701b98b434f74387
ms.sourcegitcommit: 1b29cd1fa1492037ef04188dd857a911edeb4985
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80122839"
ms.PowerAppsDecimalTransform: true
---
# <a name="savedata-and-loaddata-functions-in-power-apps"></a>Funciones SaveData y LoadData en Power apps
Guarda y recarga una [colección](../working-with-data-sources.md#collections) desde un dispositivo local.

## <a name="description"></a>Descripción
La función **SaveData** almacena una colección para su uso posterior con un nombre.  

La función **LoadData** recarga una colección por el nombre que se guardó anteriormente con **savedata**. No se puede utilizar esta función para cargar una colección de otro origen.  

Use estas funciones para mejorar el rendimiento de inicio de la aplicación:

- Almacenar en caché los datos de la fórmula **[app. OnStart](../controls/control-screen.md#additional-properties)** en una primera ejecución.
- Volver a cargar la memoria caché local en las siguientes ejecuciones.

También puede usar estas funciones para agregar [funcionalidades sin conexión sencillas](../offline-apps.md) a la aplicación.

No puede usar estas funciones dentro de un explorador cuando:

- Crear la aplicación en Power apps Studio.
- Ejecutar la aplicación en el reproductor Web. 

Para probar la aplicación, ejecútela en Power apps Mobile en un dispositivo iPhone o Android.

Estas funciones están limitadas por la cantidad de memoria de la aplicación disponible mientras operan en una colección en memoria. La memoria disponible puede variar dependiendo de factores como: 

- El dispositivo y el sistema operativo.
- La memoria que usa el reproductor de Power apps.
- Complejidad de la aplicación con pantallas y controles. 

Pruebe la aplicación con los escenarios esperados en el tipo de dispositivos que espera que la aplicación se ejecute al almacenar datos de gran tamaño. En general, se espera tener entre 30 MB y 70 MB de memoria disponible.

Estas funciones dependen de la colección que se define implícitamente con **[Collect](function-clear-collect-clearcollect.md)** o **[ClearCollect](function-clear-collect-clearcollect.md)** . No es necesario llamar a **Collect** o **ClearCollect** para cargar datos en la colección para definirlos. Es un caso común cuando se usa **LoadData** después de un **savedata**anterior.  Lo único que se necesita es la presencia de estas funciones en una fórmula para definir implícitamente la estructura de la colección.  Para obtener más información, vea [crear y quitar variables](../working-with-variables.md#create-and-remove-variables).

Los datos cargados se anexarán a la colección. Utilice la función **[Clear](function-clear-collect-clearcollect.md)** antes de llamar a **LoadData** si desea empezar con una colección vacía.

Las funciones de espacio aislado de la aplicación integradas del dispositivo se usan para aislar los datos guardados de otras aplicaciones. 

El dispositivo también puede cifrar los datos. también puede usar una herramienta de administración de dispositivos móviles como [Microsoft Intune](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune).

## <a name="syntax"></a>Sintaxis
**SaveData**( *Colección*; *Nombre* )<br>**LoadData**( *Collection*; *Name* [; *IgnoreNonexistentFile* ])

* *Colección*: requerido.  Colección para almacenar o cargar.
* *Nombre*: requerido.  Nombre del almacenamiento. El nombre debe ser el mismo para guardar y cargar el mismo conjunto de datos. El espacio de nombres no se comparte con otros usuarios o aplicaciones.
* *IgnoreNonexistentFile*: opcional. Valor booleano que indica qué hacer si el archivo todavía no existe.  Use *false* (valor predeterminado) para devolver un error y *true* para suprimir el error.   

## <a name="examples"></a>Ejemplos:

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **SaveData (LocalCache, "My cache")** | Guarde la colección **LocalCache** en el dispositivo del usuario con el nombre "My cache", adecuado para que **LoadData** recupere más adelante. | Los datos se guardan en el dispositivo local. |
| **LoadData (LocalCache, "caché")** | Carga la colección **LocalCache** desde el dispositivo del usuario con el nombre "My cache", previamente almacenado con una llamada a **savedata**.  | Los datos se cargan desde el dispositivo local. |   

### <a name="simple-offline-example"></a>Ejemplo sin conexión sencillo

En el siguiente ejemplo simple se capturan y almacenan los nombres y las imágenes de los elementos cotidianos sin conexión.  Almacena la información en el almacenamiento local del dispositivo para su uso posterior. Esto permite que la aplicación se cierre o que el dispositivo se reinicie sin perder datos.  

Debe tener un dispositivo para trabajar en este ejemplo, ya que usa las funciones **LoadData** y **savedata** que no funcionan en un explorador Web.

1. Cree una aplicación de lienzo en blanco con un diseño de Tablet PC.  Para más información, lea [creación de una aplicación a partir de una plantilla](../get-started-test-drive.md) y seleccione **diseño de Tablet PC** en **aplicación en blanco**.  

1. Agregue un control [**entrada de texto**](../controls/control-text-input.md) y un control [**cámara**](../controls/control-camera.md) y organícelos aproximadamente como se muestra a continuación:
    > [!div class="mx-imgBorder"]  
    > ![un control de entrada de texto y de cámara agregado a una pantalla en blanco](media/function-savedata-loaddata/simple-text-camera.png)

1. Agregue un control de [**botón**](../controls/control-button.md) .

2. Haga doble clic en el control de botón para cambiar el texto del botón a **Agregar elemento** (o modificar la propiedad **Text** ).

3. Establezca la propiedad **alseleccionar** del control botón en esta fórmula que agregará un elemento a nuestra colección:
    ```powerapps-comma
    Collect( MyItems; { Item: TextInput1.Text; Picture: Camera1.Photo } )
    ```
    > [!div class="mx-imgBorder"] 
    > ![un control de botón agregado con el texto "Agregar elemento" y el conjunto de propiedades alseleccionar](media/function-savedata-loaddata/simple-additem.png)

1. Agregue otro control de **botón** .

2. Haga doble clic en el control de botón para cambiar el texto del botón para **guardar los datos** (o modificar la propiedad **Text** ).

3. Establezca la propiedad **alseleccionar** del control botón en esta fórmula para guardar la colección en el dispositivo local:
    ```powerapps-comma
    SaveData( MyItems; "LocalSavedItems" )
    ```
    > [!div class="mx-imgBorder"] 
    > ![un control de botón agregado con el texto "guardar datos" y el conjunto de propiedades alseleccionar](media/function-savedata-loaddata/simple-savedata.png)

    Es tentador probar el botón porque no afecta a nada. Pero solo verá un error mientras crea en un explorador Web. Guarde la aplicación primero y abra en un dispositivo antes de seguir los pasos siguientes para probar esta fórmula:

1. Agregue un tercer control de **botón** .

2. Haga doble clic en el control de botón para cambiar el texto del botón a **cargar datos** (o modificar la propiedad **Text** ).

3. Establezca la propiedad **alseleccionar** del control botón en esta fórmula para cargar la colección desde el dispositivo local:
    ```powerapps-comma
    LoadData( MyItems; "LocalSavedItems" )
    ``` 
    > [!div class="mx-imgBorder"] 
    > ![un control de botón agregado con el texto "cargar datos" y el conjunto de propiedades alseleccionar](media/function-savedata-loaddata/simple-loaddata.png)

1. Agregue un control [**Galería**](../controls/control-gallery.md) con un diseño vertical que incluya una imagen y áreas de texto: 
    > [!div class="mx-imgBorder"] 
    > selección de variedad de la galería de ![, "vertical" seleccionado con áreas de imagen y texto](media/function-savedata-loaddata/simple-gallery-add.png)

1. Cuando se le solicite, seleccione la colección de mis **elementos** como origen de datos para esta galería.  Esto establecerá la propiedad **elementos** del control **Galería** : 
    > [!div class="mx-imgBorder"] 
    > ![selección de la galería de orígenes de datos](media/function-savedata-loaddata/simple-gallery-collection.png) el control de imagen de la plantilla de la Galería debería tener como valor predeterminado su propiedad de **imagen** en **ThisItem. Picture** y los controles de etiqueta deberían tener ambas propiedades de **texto** como **ThisItem. Item**como valor predeterminado.  Compruebe estas fórmulas si después de agregar elementos en los pasos siguientes no ve nada en la galería. 

1. Coloque el control a la derecha de los otros controles: 
    > [!div class="mx-imgBorder"] 
    > ![Galería cambia de posición a la derecha de la pantalla](media/function-savedata-loaddata/simple-gallery-placed.png)

1. Guarde la aplicación.  Si es la primera vez que se ha guardado, no es necesario publicarla. Si no es la primera vez, publique la aplicación después de guardarla.

1. Abra la aplicación en un dispositivo como un teléfono o una tableta.  **Savedata** y **LoadData** no se pueden usar en Studio o en un explorador Web.  Actualice la lista de aplicaciones si no ve la aplicación inmediatamente, la aplicación puede tardar unos segundos en aparecer en el dispositivo.  Cerrar sesión y volver a la cuenta también puede ser útil.
    > [!div class="mx-imgBorder"] 
    > ![aplicación que se ejecuta sin elementos agregados](media/function-savedata-loaddata/simple-mobile.png) una vez que se haya descargado la aplicación, puede desconectarse de la red y ejecutar la aplicación sin conexión.

1. Escriba el nombre y tome una imagen de un elemento.

2. Seleccione el botón **Agregar elemento** .  Repita la adición de los elementos un par de veces para cargar la colección.
    > [!div class="mx-imgBorder"] 
    > ![aplicación que se ejecuta con tres elementos agregados](media/function-savedata-loaddata/simple-mobile-with3.png) 

1. Seleccione el botón **guardar datos** .  Esto guardará los datos de la colección en el dispositivo local.

1. Cierre la aplicación.  La colección en memoria se perderá, incluidos todos los nombres de elementos e imágenes, pero seguirán allí en el almacenamiento del dispositivo.

1. Vuelva a iniciar la aplicación.  La colección en memoria volverá a aparecer como vacía en la galería.
    > [!div class="mx-imgBorder"] 
    > ![aplicación de nuevo en ejecución sin elementos agregados](media/function-savedata-loaddata/simple-mobile.png) 

1. Seleccione el botón **cargar datos** .  La recopilación se volverá a rellenar a partir de los datos almacenados en el dispositivo y los elementos volverán a la galería.  La colección estaba vacía antes de que este botón llame a la función **LoadData** ; no era necesario llamar a **Collect** o **ClearCollect** antes de cargar los datos desde el almacenamiento.
    > [!div class="mx-imgBorder"] 
    > ![aplicación que se ejecuta con tres elementos restaurados después de llamar a la función LoadData](media/function-savedata-loaddata/simple-mobile-load1.png) 

1. Vuelva a seleccionar el botón **cargar datos** .  Los datos almacenados se anexarán al final de la colección y aparecerá una barra de desplazamiento en la galería.  Si desea reemplazar en lugar de append, utilice primero la función **Clear** para borrar la colección antes de llamar a la función **LoadData** .
    > [!div class="mx-imgBorder"] 
    > ![aplicación que se ejecuta con seis elementos restaurados después de llamar a la función LoadData dos veces](media/function-savedata-loaddata/simple-mobile-load2.png) 
 
### <a name="more-advanced-offline-example"></a>Ejemplo sin conexión más avanzado

Para obtener un ejemplo detallado, consulte el artículo sobre las [funcionalidades sin conexión simples](../offline-apps.md).







