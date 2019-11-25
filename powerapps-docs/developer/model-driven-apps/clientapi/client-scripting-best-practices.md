---
title: 'Prácticas recomendadas: ejemplo de script en aplicaciones basadas en modelos | MicrosoftDocs'
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 16271bd8-cfa8-4a7f-802a-60fbff7c3722
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0ef08d16ad91292c5757bb1d95c5ccadd15b5128
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749451"
---
# <a name="best-practices-client-scripting-in-model-driven-apps"></a>Prácticas recomendadas: ejemplo de script en aplicaciones basadas en modelos



A continuación se muestran algunas de las sugerencias de prácticas recomendadas que podría tener en cuenta mientras escribe código JavaScript para aplicaciones basadas en modelos.

## <a name="define-unique-javascript-function-names"></a>Defina nombres de funciones de JavaScript únicos

Al escribir las funciones que se usarán en las bibliotecas de JavaScript, las funciones se pueden cargar en un formulario con otras bibliotecas de JavaScript. Si otra biblioteca contiene una función que tenga el mismo nombre que una función que proporcione el usuario, la función que se cargue en último lugar será definida por la página. Para evitar que las funciones se sobrescriban con funciones de otra biblioteca, debe asegurarse de que las funciones tengan nombres únicos. Puede usar alguna de las siguientes estrategias:

- **Prefijo único de función**: Defina cada una de las funciones utilizando la sintaxis estándar con un nombre coherente que incluya una convención de nomenclatura única, como se muestra en el siguiente ejemplo.
    ```JavaScript
    function MyUniqueName_performMyAction()
    {
        // Code to perform your action.
    }
    ```
- **Nombres de biblioteca de con espacio de nombres**: Asocie cada una de las funciones con un objeto de JavaScript para crear un tipo de espacio de nombres que usar cuando se llame a las funciones, como se muestra en el siguiente ejemplo.
    ```JavaScript
    //If the MyUniqueName namespace object isn’t defined, create it.
    if (typeof (MyUniqueName) == "undefined")
       { MyUniqueName = {}; }
       // Create Namespace container for functions in this library;
       MyUniqueName.MyFunctions = {
         performMyAction: function(){
         // Code to perform your action.
         //Call another function in your library
         this.anotherAction();
       },
       anotherAction: function(){
         // Code in another function
      }
    };
    ```

    A continuación, cuando use la función, podrá especificar el nombre completo. El siguiente ejemplo muestra esto.

    ```JavaScript
    MyUniqueName.MyFunctions.performMyAction();
    ```

    Si llama a una función en otra función, puede usar esta palabra clave como acceso directo al objeto que contiene ambas funciones. No obstante, si la función se usa como controlador de eventos, esta palabra clave se referirá al objeto donde se produce el evento.

## <a name="avoid-using-unsupported-methods"></a>Evitar usar métodos incompatibles

En Internet, puede encontrar muchos ejemplos o sugerencias que describen el uso de métodos incompatibles. Pueden incluir el aprovechamiento de función interna no documentada para controles de página. Estos métodos pueden funcionar pero, al no estar admitidos, no puede esperar que continuarán funcionando en versiones futuras de aplicaciones basadas en modelos.

## <a name="avoid-using-jquery-for-form-scripts"></a>Evite utilizar jQuery para scripts de formularios

No se recomienda el uso de jQuery en scripts de formularios y comandos de cinta. La mayoría de las ventajas que proporciona jQuery es que permite la manipulación sencilla entre exploradores del DOM. Esto no se admite de manera explícita dentro de los scripts de formularios y comandos de la cinta de opciones. Restrinja los scripts para usar los objetos y métodos disponibles el [modelo de objetos Xrm](understand-clientapi-object-model.md). 

Si decide usar las funcionalidades restantes de jQuery que son útiles con aplicaciones basadas en modelos e incluir la capacidad de usar **$.ajax**, tenga en cuenta lo siguiente:

- Para el máximo rendimiento, no cargue jQuery en la página si no lo necesita.
- Se admite el uso de **$.ajax** para realizar solicitudes a los servicios web de aplicaciones basads en modelos, aunque hay alternativas. La alternativa al uso de **$.ajax** es usar el objeto **XMLHttpRequest** de los exploradores directamente. El método **$.ajax** de jQuery sólo es un contenedor para este objeto. Si usa el objeto **XMLHttpRequest** nativo directamente, no necesita cargar jQuery.
- Cada versión de jQuery que se carga en una página puede ser una versión diferente. Diferentes versiones de jQuery tienen distintos comportamientos y estos pueden causar problemas cuando se cargue varias versiones de jQuery en la misma página. Hay una técnica para mitigar esto, pero depende de editar la biblioteca jQuery y cualquier otra biblioteca que dependa de jQuery.


## <a name="write-your-code-for-multiple-browsers"></a>Escriba su código para varios exploradores

Las aplicaciones basadas en modelos admiten varios navegadores. Asegúrese de que los scripts que utilice funcionarán con todos los exploradores admitidos. La mayoría de las diferencias importantes entre Internet Explorer y otro explorador tienen que ver con la manipulación de DOM XML y HTML. Debido a que no se admite la manipulación de DOM HTML, si la lógica de script solo realiza acciones compatibles y usa el [modelo de objetos Xrm](understand-clientapi-object-model.md), los cambios necesarios para admitir otros exploradores podrían ser pequeños. 
