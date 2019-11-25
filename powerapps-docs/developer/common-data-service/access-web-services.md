---
title: Acceso a servicios web externos (Common Data Service) | MicrosoftDocs
description: Aprenda a obtener acceso a un servicio web desde un complemento o una actividad de flujo de trabajo.
ms.custom: ''
ms.date: 8/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b236ba63a4e82f5969c5496af58a5aa015b89a1b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749415"
---
# <a name="access-external-web-services"></a>Acceso a servicios web externos

Los complementos y las actividades personalizadas de flujo de trabajo pueden obtener acceso a la red con los protocolos HTTP y HTTPS. Esta funcionalidad proporciona soporte para obtener acceso a los servicios web populares como sitios sociales, fuentes de noticias, servicios web, etc. Las siguientes restricciones de acceso web se aplican a esta funcionalidad de espacios aislados.  
  
- Solo se admiten los protocolos HTTP y HTTPS.
- El acceso a localhost (bucle invertido) no está permitido.
- Las direcciones IP no se pueden usar. Debe usar una dirección web con nombre que requiera resolución de nombres DNS.
- La autenticación anónima es compatible y se recomienda. No existen ninguna disposición para preguntar los credenciales al usuario que inició la sesión o guardar dichos credenciales.

Otros métodos de acceso a los servicios web incluyen el uso de webhooks y [!INCLUDE [pn_azure_service_bus](../../includes/pn_azure_service_bus.md)]. Consulte los vínculos proporcionados más abajo para obtener más información sobre estos temas.

## <a name="how-to-access-external-web-services"></a>Cómo obtener acceso a servicios web externos

La mayoría de los usuarios están famliarizados con la [clase System.Net.Http.HttpClient](/dotnet/api/system.net.http.httpclient). `HttpClient` se introdujo con .NET 4.5 y ofrece funcionalidades significativas sobre la [clase System.Net.WebClient](/dotnet/api/system.net.webclient) que sigue estando disponible.

Para los nuevos complementos debe usar `HttpClient` porque [el equipo de .NET no recomienda WebClient para nuevos desarrollos](/dotnet/api/system.net.webclient?#remarks). No obstante, esto no significa que deba reemplazar los usos de códigos heredado de `WebClient` que encuentre. La mayoría de las ventajas proporcionadas en `HttpClient` no proporcionan ventajas necesariamente en un complemento. `HttpClient` está diseñada para ser reutilizado y es asincrónico de forma predeterminada. A menos que esté creando varias solicitudes de Http en el complemento, `WebClient` está diseñado para una sola solicitud. Puesto que `HttpClient` es asincrónico de forma predeterminada, debe olvidarse de los patrones de uso típicos y agregar código para forzar las operaciones que se deben realizar de forma sincrónica, normalmente quitando la palabra clave `await` y anexando `.Result` a cualquier llamada asincrónica.

`WebClient` proporciona métodos sincrónicos simples como [UploadData](/dotnet/api/system.net.webclient.uploaddata), [DownloadFile](/dotnet/api/system.net.webclient.downloadfile) que no exponen claramente el método Http subyacente usado, pero pueden ser establecidos con reemplazos específicos como [UploadString(String, String, String)](/dotnet/api/system.net.webclient.uploadstring#System_Net_WebClient_UploadString_System_String_System_String_System_String_) en caso de que desee usar `PATCH` en lugar de `POST`.

En la mayoría de los casos aparte de los complementos, le convendrá usar `HttpClient`. En complementos, también puede usar `WebClient` si lo prefiere.

## <a name="best-practices"></a>Prácticas recomendadas

Como se indica en los siguientes temas de procedimientos recomendados:

- [Establecer KeepAlive en false para interactuar con hosts externos en un complemento](best-practices/business-logic/set-keepalive-false-interacting-external-hosts-plugin.md)
- [Establecer tiempo de espera al realizar llamadas externas en un complemento](best-practices/business-logic/set-timeout-for-external-calls-from-plug-ins.md)

Debe asegurarse de establecer un período `Timeout` adecuado para sus llamadas externas y deshabilitar `KeepAlive`. Para obtener más información, consulte estos temas.


## <a name="see-also"></a>Vea también

[Complementos](plug-ins.md)<br />
[Extensiones de flujo de trabajo](workflow/workflow-extensions.md)<br />
[Integración de Azure](azure-integration.md)<br />
[Utilizar WebHooks](use-webhooks.md)<br />
[Ejemplo: acceso web desde un complemento de espacio aislado](org-service/samples/web-access-plugin.md)
