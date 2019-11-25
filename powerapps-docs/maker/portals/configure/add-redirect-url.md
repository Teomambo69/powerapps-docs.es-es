---
title: Redireccionar a una nueva dirección URL en un portal | MicrosoftDocs
description: Instrucciones para crear una dirección URL de redireccionamiento para redirigir a un usuario a otra página en un sitio.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761098"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>Agregar una URL de direccionamiento a una nueva dirección URL en un portal

Los clientes con frecuencia desean tener una dirección URL simple que redirija a una página más profunda del sitio o desean permitir que una dirección URL heredada se use con el sitio y automáticamente redirija a una nueva dirección URL del sitio. Los redireccionamientos de página permiten a un autor de contenido especificar una dirección URL que cuando se solicita redirigirá de forma continua o temporal a una página web o un archivo web específicos. Estas direcciones URL de redireccionameinto se administran por separado del contenido de la página, por lo que no tienen que ajustarse directamente a la jerarquía web.

## <a name="create-a-redirect"></a>Crear una redirección

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Página web** > **Redireccionamientos**.

3. seleccione **Nuevo**.

4. Especifique la información de redireccionamiento como se describe a continuación.

| Nombre        | Descripción                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre        | El nombre descriptivo del redireccionamiento. (Puede ser cualquier cosa. Hágalo fácil de identificar.)                                                              |
| Sitio web     | Sitio web al que está asociado el redireccionamiento. (El sitio desde el que se redirecciona al usuario.)                                                         |
| URL de entrada | La dirección URL parcial que debe ser redireccionada. (La página desde la que se redirecciona al usuario.)                                                            |
| Código de estado | Una de las siguientes:  **302 (Redireccionamientos activos)**: devuelve un estado de redireccionamiento temporal. Esta es la configuración predeterminada.                                               -   **301 (redireccionamiento permanente)**: devuelve un estado de redireccionamiento permanente que indica que el recurso se ha movido permanentemente.                          |
| URL         | Una dirección URL externa de destino a la que se realizará el redireccionamiento. (Use esta opción si al usuario se redirecciona a un vínculo exnterno al sitio web especificado arriba).                            |
| Página web    | Una página web interna de destino a la que se realizará el redireccionamiento. (Use esta opción si al usuario se redirecciona a una página interna al sitio web especificado arriba.) |
| Marcador de sitio | Un marcador de sitio interno de destino al que se realizará el redireccionamiento.                                                                                           |

4. Después de completar los campos obligatorios y especificar un valor para por lo menos uno de los campos Dirección URL, Página web o Marcador de sitio, seleccione **Guardar**.

    ![Redireccionar una encuesta a clientes](../media/redirect-customer-survey.png "Redireccionar una encuesta a clientes")  

## <a name="use-the-redirect"></a>Use el redireccionamiento

Cuando se solicite la dirección URL de entrada, el explorador se redirige a la dirección URL de la página web de destino para la entrada de redireccionamientos que coincidan.

Por ejemplo, para un valor de URL de entrada de cs-survey con una página web de destino establecida en la página Encuesta de soporte técnico a clientes, la siguiente solicitud:

https://customerportal.contoso.com/cs-survey

produce en el explorador la solicitud de la siguiente dirección URL:

https://customerportal.contoso.com/surveys/customer-service-survey/

