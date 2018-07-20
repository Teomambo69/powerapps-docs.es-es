---
title: Integración de PowerApps tanto en sitios web como en otros servicios | Microsoft Docs
description: Inserte aplicaciones en sitios web y en otros servicios.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/20/2017
ms.author: mblythe
ms.openlocfilehash: ed0863d8d7987e7e7f129a9804b35e00e76aad36
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39023813"
---
# <a name="integrate-powerapps-into-websites-and-other-services"></a>Integración de PowerApps tanto en sitios web como en otros servicios
Las aplicaciones que crea suelen ser más útiles cuando están disponibles allí donde las personas realizan su trabajo. PowerApps permite insertar aplicaciones en un iframe para poder integrarlas tanto en sitios web como en otros servicios, como Power BI o SharePoint.

En este tema se muestra cómo establecer los parámetros para la inserción de aplicaciones y, después, se instará la aplicación Asset Ordering en un sitio web.

![Panel de Power BI con aplicación insertada](./media/embed-apps-dev/embed-dashboard.png)

Tenga en mente las siguientes restricciones:

* Los únicos usuarios de PowerApps que pueden acceder a la aplicación insertada son los que se encuentran en el mismo inquilino.
* Para acceder a PowerApps mediante Internet Explorer 11, es preciso desactivar la vista de compatibilidad.

También puede integrar PowerApps en SharePoint Online (sin usar un iframe). Para más información, consulte [Creación de una aplicación desde SharePoint mediante PowerApps](../canvas-apps/generate-app-from-sharepoint-list-interface.md).

## <a name="set-uri-parameters-for-your-app"></a>Establecer los parámetros URI de la aplicación
Si tiene una aplicación que desea insertar, el primer paso es establecer los parámetros para el identificador uniforme de recursos (URI), para que el iframe sepa dónde se encuentra la aplicación. El identificador URI tiene la forma siguiente:

```
https://web.powerapps.com/webplayer/iframeapp?source=iframe
&appId=/providers/Microsoft.PowerApps/apps/[AppID]
```

> [!NOTE]
> Hemos agregado un salto de línea para que el identificador URI se muestre mejor en la página.

Lo único que tiene que hacer es sustituir el identificador de la aplicación por [AppID] en el identificador URI (incluido "[' & ']"). Le mostraremos cómo obtener ese valor en breve, pero primero aquí están todos los parámetros disponibles en el identificador URI:

* **[appID]**: tiene el formato `/providers/Microsoft.PowerApps/apps/[AppID]`. Proporciona el identificador de la aplicación que se va a ejecutar.
* **screenColor**: se usa para proporcionar a los usuarios una mejor experiencia de carga. Este parámetro tiene el formato [RGBA (rojo, verde, azul, alfa)](../canvas-apps/functions/function-colors.md) y controla el color de la pantalla mientras se carga la aplicación. Es mejor establecerlo en el mismo color que el icono de la aplicación.
* **source**: no afecta a la aplicación, pero se recomienda agregar un nombre descriptivo para hacer referencia al origen de la aplicación insertada.
* Por último, puede agregar los parámetros personalizados que desee con la [función Param()](../canvas-apps/functions/function-param.md) y esos valores pueden ser utilizados por la aplicación. Se agregan al final del identificador URI, como `[AppID]&amp;param1=value1`. Estos parámetros son de solo lectura durante el inicio de la aplicación; si necesita cambiarlos, debe volver a iniciar la aplicación.

### <a name="get-the-app-id"></a>Obtener el identificador de aplicación
El identificador de la aplicación está disponible en powerapps.com. Para la aplicación que desea insertar:

1. En [powerapps.com](https://powerapps.microsoft.com), en la pestaña **Aplicaciones**, pulse o haga clic en los puntos suspensivos (**...** ) y, a continuación, seleccione **Detalles**.
   
    ![Ir a los detalles de la aplicación](./media/embed-apps-dev/details.png)
2. Copie el **Id. de aplicación**.
   
    ![Copiar el identificador de la aplicación desde los detalles](./media/embed-apps-dev/app-id.png)
3. Sustituya el valor `[AppID]` en el identificador URI. Para la aplicación "Pedido de activos", el identificador URI tiene el siguiente aspecto:
   
    ```
    https://web.powerapps.com/webplayer/iframeapp?source=iframe&appId=/providers/Microsoft.PowerApps/apps/76897698-91a8-b2de-756e-fe2774f114f2
    ```

## <a name="embed-your-app-in-a-website"></a>Insertar la aplicación en un sitio web
Ahora es muy fácil incrustar aplicaciones, solo hay que agregar el iframe al código HTML del sitio (o a cualquier otro servicio que admita iframes, como Power BI o SharePoint):

```
<iframe width="[W]" height="[H]" src="https://web.powerapps.com/webplayer/iframeapp?source=website&screenColor=rgba(165,34,55,1)&appId=/providers/Microsoft.PowerApps/apps/[AppID]" allow="geolocation; microphone; camera"/>
```

Especifique los valores de ancho y alto del iframe y sustituya el identificador de la aplicación por `[AppID]`.

> [!NOTE]
> Incluya `allow="geolocation; microphone; camera"` en el código HTML de iframe para permitir que las aplicaciones usen estas funcionalidades en Google Chrome.

La siguiente imagen muestra la aplicación "Pedido de activos" insertada en un sitio web de ejemplo de Contoso.

![Sitio web de Contoso con la aplicación insertada](./media/embed-apps-dev/contoso-website.png)

Tenga en cuenta los puntos siguientes para autenticar a los usuarios de la aplicación:

* Si el sitio web usa autenticación basada en Azure Active Directory (AAD), no será necesario ningún inicio de sesión adicional.
* Si el sitio web utiliza cualquier otro mecanismo de inicio de sesión o no está autenticado, los usuarios verán un mensaje de inicio de sesión en el iframe. Después de iniciar sesión, podrán ejecutar la aplicación siempre y cuando el autor de la aplicación la haya compartido con ellos.

Como ve, insertar aplicaciones es fácil y eficaz. La inserción le permite llevar las aplicaciones a los lugares en los que usted y sus clientes trabajan (sitios web, paneles de Power BI y páginas de SharePoint, entre otros).

