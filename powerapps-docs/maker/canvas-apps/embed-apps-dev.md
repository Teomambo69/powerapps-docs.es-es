---
title: Integración de aplicaciones de lienzo en sitios web y en otros servicios | Microsoft Docs
description: Inserte aplicaciones de lienzo en sitios web y otros servicios.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/28/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 99594d99aa0ab1ae4971f3ec2eb1987bb7dcfbcc
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73539023"
---
# <a name="integrate-canvas-apps-into-websites-and-other-services"></a>Integración de aplicaciones de lienzo en sitios web y otros servicios
Las aplicaciones que cree suelen ser más útiles cuando están disponibles en el momento en que los usuarios realizan su trabajo. Al incrustar aplicaciones de lienzo en un iframe, puede integrar esas aplicaciones en sitios web y otros servicios, como Power BI o SharePoint.

En este tema se muestra cómo establecer los parámetros para la inserción de aplicaciones y, después, se instará la aplicación Asset Ordering en un sitio web.

![Panel de Power BI con aplicación insertada](./media/embed-apps-dev/embed-dashboard.png)

Tenga en mente las siguientes restricciones:

- Los únicos usuarios de PowerApps que pueden acceder a la aplicación insertada son los que se encuentran en el mismo inquilino.
- Para acceder a PowerApps mediante Internet Explorer 11, es preciso desactivar la vista de compatibilidad.

También puede integrar las aplicaciones de canvas en SharePoint Online sin usar un iframe. Más información: [use el elemento Web de PowerApps](https://support.office.com/article/use-the-powerapps-web-part-6285f05e-e441-408a-99d7-aa688195cd1c).

## <a name="set-uri-parameters-for-your-app"></a>Establecer los parámetros URI de la aplicación
Si tiene una aplicación que desea insertar, el primer paso es establecer los parámetros para el identificador uniforme de recursos (URI), para que el iframe sepa dónde se encuentra la aplicación. El identificador URI tiene la forma siguiente:

```
https://apps.powerapps.com/play/[AppID]?source=iframe
```

> [!IMPORTANT]
> A partir del 2019 de agosto, el formato del URI ha cambiado de https://make.powerapps.com/webplayer a https://apps.powerapps.com/play. Actualice cualquier iframe incrustado para que use el nuevo formato de URI. Las referencias al formato anterior se redirigirán al nuevo URI para garantizar la compatibilidad.
>
> Formato anterior:
> 
> https\://make.powerapps.com/WebPlayer/iframeapp? Source = iframe & appId =/providers/Microsoft.PowerApps/apps/[AppID]

Lo único que tiene que hacer es sustituir el identificador de la aplicación por [AppID] en el identificador URI (incluido "[' & ']"). Le mostraremos cómo obtener ese valor en breve, pero primero aquí están todos los parámetros disponibles en el identificador URI:

* **[appID]** : proporciona el identificador de la aplicación que se va a ejecutar.
* **tenantid** : es un parámetro opcional para admitir el acceso de invitado y determina en qué inquilino se debe abrir la aplicación. 
* **screenColor**: se usa para proporcionar a los usuarios una mejor experiencia de carga. Este parámetro tiene el formato [RGBA (rojo, verde, azul, alfa)](../canvas-apps/functions/function-colors.md) y controla el color de la pantalla mientras se carga la aplicación. Es mejor establecerlo en el mismo color que el icono de la aplicación.
* **source**: no afecta a la aplicación, pero se recomienda agregar un nombre descriptivo para hacer referencia al origen de la aplicación insertada.
* Por último, puede agregar los parámetros personalizados que desee con la [función Param()](../canvas-apps/functions/function-param.md) y esos valores pueden ser utilizados por la aplicación. Se agregan al final del identificador URI, como `[AppID]&amp;param1=value1`. Estos parámetros son de solo lectura durante el inicio de la aplicación. Si tiene que cambiarlos, debe volver a iniciar la aplicación. Tenga en cuenta que solo el primer elemento después de [AppID] debe tener un "?"; después, use el "&" como se muestra aquí. 

### <a name="get-the-app-id"></a>Obtener el identificador de aplicación
El identificador de la aplicación está disponible en powerapps.com. Para la aplicación que desea insertar:

1. En [powerapps.com](https://powerapps.microsoft.com), en la pestaña **Aplicaciones**, pulse o haga clic en los puntos suspensivos ( **...** ) y, a continuación, seleccione **Detalles**.
   
    ![Ir a los detalles de la aplicación](./media/embed-apps-dev/details.png)
1. Copie el **Id. de aplicación**.
   
    ![Copiar el identificador de la aplicación desde los detalles](./media/embed-apps-dev/app-id.png)
1. Sustituya el valor `[AppID]` en el identificador URI. Para la aplicación "Pedido de activos", el identificador URI tiene el siguiente aspecto:
   
    ```
    https://apps.powerapps.com/play/76897698-91a8-b2de-756e-fe2774f114f2?source=iframe
    ```

## <a name="embed-your-app-in-a-website"></a>Insertar la aplicación en un sitio web
Ahora es muy fácil incrustar aplicaciones, solo hay que agregar el iframe al código HTML del sitio (o a cualquier otro servicio que admita iframes, como Power BI o SharePoint):

```html
<iframe width="[W]" height="[H]" src="https://apps.powerapps.com/play/[AppID]?source=website&screenColor=rgba(165,34,55,1)" allow="geolocation; microphone; camera"/>
```

Especifique los valores de ancho y alto del iframe y sustituya el identificador de la aplicación por `[AppID]`.

> [!NOTE]
> Incluya `allow="geolocation; microphone; camera"` en el código HTML de iframe para permitir que las aplicaciones usen estas funcionalidades en Google Chrome.

La siguiente imagen muestra la aplicación "Pedido de activos" insertada en un sitio web de ejemplo de Contoso.

![Sitio web de Contoso con la aplicación insertada](./media/embed-apps-dev/contoso-website.png)

Tenga en cuenta los puntos siguientes para autenticar a los usuarios de la aplicación:

- Si el sitio web usa autenticación basada en Azure Active Directory (AAD), no será necesario ningún inicio de sesión adicional.
- Si el sitio web utiliza cualquier otro mecanismo de inicio de sesión o no está autenticado, los usuarios verán un mensaje de inicio de sesión en el iframe. Después de iniciar sesión, podrán ejecutar la aplicación siempre y cuando el autor de la aplicación la haya compartido con ellos.

Como ve, insertar aplicaciones es fácil y eficaz. La inserción le permite llevar las aplicaciones a los lugares en los que usted y sus clientes trabajan (sitios web, paneles de Power BI y páginas de SharePoint, entre otros).
