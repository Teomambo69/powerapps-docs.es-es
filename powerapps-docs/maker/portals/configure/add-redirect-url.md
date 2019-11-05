---
title: Redirigir a una nueva dirección URL en un portal | MicrosoftDocs
description: Instrucciones para crear una dirección URL de redireccionamiento para redirigir a un usuario a otra página de un sitio.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 63cec47042cee4c29e225f33f1678261da3a01ca
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553426"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>Agregar una dirección URL de redireccionamiento a una nueva dirección URL en un portal

A menudo, los clientes quieren tener una dirección URL simple que redirija a una página más profunda en el sitio, o que desee permitir el uso de una dirección URL heredada con el sitio y redirigir automáticamente a una nueva dirección URL en el sitio. Las redirecciones de páginas permiten que un autor de contenido especifique una dirección URL que, cuando se solicite, se redirigirá de manera permanente o temporal a una página web o un archivo Web específicos. Estas direcciones URL de redireccionamiento se administran de forma independiente del contenido de la página para que no tengan que ajustarse directamente a la jerarquía Web.

## <a name="create-a-redirect"></a>Creación de una redirección

1. Abra la [aplicación administración del portal](configure-portal.md).

2. Vaya al **portal** de > **sitios web** > **redirecciones**.

3. Seleccione **nuevo**.

4. Escriba la información de redirección tal y como se describe a continuación.

| Nombre        | Descripción                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre        | Nombre descriptivo de la redirección. (Puede ser cualquier cosa. Facilita la identificación).                                                              |
| Bsitio     | Sitio web al que está asociada la redirección. (El sitio desde el que se redirige al usuario).                                                         |
| Dirección URL de entrada | Dirección URL parcial que se va a redirigir. (La página desde la que se redirige al usuario).                                                            |
| Código de estado | Uno de los siguientes: **302 (redirección temporal)** : devuelve un estado de redirección temporal. Este es el valor predeterminado.                                               -   **301 (redirección permanente)** : devuelve un estado de redirección permanente, que indica que el recurso se ha despasado de forma permanente.                          |
| Dirección         | Dirección URL externa de destino a la que se va a redirigir. (Úselo si el usuario se redirige a un vínculo externo al sitio Web especificado anteriormente).                            |
| Página Web    | Página Web interna de destino a la que se va a redirigir. (Úselo si el usuario se redirige a una página interna del sitio Web especificado anteriormente). |
| Marcador de sitio | Marcador de sitio interno de destino al que se va a redirigir.                                                                                           |

4. Después de escribir los campos obligatorios y especificar un valor para al menos uno de los campos dirección URL, página web o marcador de sitio, seleccione **Guardar**.

    ![Redirigir una encuesta de cliente](../media/redirect-customer-survey.png "Redirigir una encuesta de cliente")  

## <a name="use-the-redirect"></a>Usar el redireccionamiento

Cuando se solicita la URL de entrada, el explorador se redirige a la dirección URL de la Página Web de destino para la entrada de redireccionamientos coincidentes.

Por ejemplo, para un valor de dirección URL de entrada de CS-Survey con una página web de destino establecida en la página encuesta de soporte al cliente, la siguiente solicitud:

https://customerportal.contoso.com/cs-survey

da como resultado el explorador que solicita la siguiente dirección URL:

https://customerportal.contoso.com/surveys/customer-service-survey/

