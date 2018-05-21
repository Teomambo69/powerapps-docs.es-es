---
title: Respuesta a solicitudes DSR sobre registros generados por el sistema en PowerApps, Microsoft Flow y Common Data Service (CDS) for Apps | Microsoft Docs
description: Tutorial sobre cómo responder solicitudes DSR sobre registros generados por el sistema en PowerApps, Microsoft Flow y Common Data Service (CDS) for Apps
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: 970cf64f9312e1d9f820671d313ee497f3e27b61
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2018
---
# <a name="responding-to-dsr-requests-for-system-generated-logs-in-powerapps-microsoft-flow-and-common-data-service-for-apps"></a>Respuesta a solicitudes DSR sobre registros generados por el sistema en PowerApps, Microsoft Flow y Common Data Service for Apps
Microsoft le ofrece la posibilidad de tener acceso, exportar y eliminar los registros generados por el sistema que se consideren personales en la amplia definición de *datos personales* del Reglamento general de protección de datos (RGDP) de la Unión Europea (UE). Ejemplos de registros generados por el sistema que se consideran personales en el RGPD:
* Datos de uso de productos y servicios tales como registros de actividad del usuario
* Solicitudes de búsqueda de usuario y datos de consulta
* Datos generados por los productos y servicios como consecuencia de la funcionalidad del sistema y la interacción entre usuarios u otros sistemas

Tenga en cuenta que no se admite la posibilidad de restringir ni rectificar datos de registros generados por el sistema. Los datos de registros generados por el sistema constituyen acciones objetivas realizadas en la nube de Microsoft y los datos de diagnóstico &mdash;que incluyen modificaciones a dichos datos&mdash; podrían poner en peligro el registro histórico de las acciones y aumentar los riesgos de seguridad y de fraude.

## <a name="accessing-and-exporting-system-generated-logs"></a>Acceso a registros generados por el sistema y exportación
Los administradores tienen acceso a los registros generados por el sistema asociados a la utilización que haga un usuario de PowerApps y Microsoft Flow, así como de servicios y aplicaciones de Common Data Service (CDS) for Apps.

Para tener acceso a registros generados por el sistema y exportarlos:

1. Vaya al [Portal de confianza de servicios Microsoft](https://servicetrust.microsoft.com/) e inicie sesión con las credenciales de administrador global de Office 365.

2. En la lista desplegable **Privacidad** de la parte superior de la página, seleccione **Data Subject Request** (Solicitud del interesado).

3. En la página **Data Subject Request** (Solicitud del interesado), en **System Generated Logs** (Registros generados por el sistema), seleccione **Exportación de registros de datos**. La herramienta Exportación de registros de datos se abre y muestra una lista de las solicitudes de datos de exportación enviadas por la organización.

4. Para crear una solicitud para un usuario, haga clic en **Create Export Data Request** (Crear solicitud de exportación de datos).

    Después de crear una solicitud, esta aparece en la página **Exportación de registros de datos**, donde se puede realizar el seguimiento de su estado. Una vez completada una solicitud, puede hacer clic en un vínculo para tener acceso a los registros generados por el sistema, que se exportarán a la ubicación de almacenamiento de Azure de la organización en los 30 días siguientes a la creación de la solicitud. Los datos se guardarán en formatos de archivo comunes y legibles por máquina, como XML, CSV o JSON. Si no dispone de una cuenta de Azure y una ubicación de almacenamiento de Azure, debe crear una cuenta de Azure o una ubicación de almacenamiento de Azure para su organización para que la herramienta Exportación de registros de datos pueda exportar los registros generados por el sistema. Para obtener más información, vea [Introducción a Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).

En la tabla siguiente se resume el acceso y la exportación de registros generados por el sistema:

| Pregunta | Respuesta |
| --- | --- |
| ¿Cuánto tiempo tarda la herramienta Exportación de registros de datos de Microsoft en completar una solicitud? |    Esto depende de varios factores. En la mayoría de los casos debe completarse en uno o dos días, pero puede tardar hasta 30 días.
| ¿En qué formato estará el resultado? | El resultado estará en forma de archivos estructurados y legibles por máquina, como XML, CSV o JSON.
| ¿Quién tiene acceso a la herramienta Exportación de registros de datos para enviar solicitudes de acceso para los registros generados por el sistema? | Los administradores globales de Office 365 tendrán acceso a la herramienta Administrador de registros del RGPD.
| ¿Qué datos devuelve la herramienta Exportación de registros de datos? | La herramienta Exportación de registros de datos devuelve los registros generados por el sistema que se almacenan en Microsoft. Los datos exportados abarcan varios servicios Microsoft tales como Office 365, Azure, Dynamics, PowerApps, Microsoft Flow y CDS for Apps.
| ¿Cómo se devuelven los datos al usuario? |   Los datos se exportarán a la ubicación de almacenamiento de Azure de la organización; serán los administradores de la organización quienes determinen cómo se muestran o devuelven los datos a los usuarios.
| ¿Qué aspecto tendrán los datos de los registros generados por el sistema? |  Ejemplo de una entrada de registros generados por el sistema en formato JSON: <br> [{ <br>"DateTime": "2017-04- 28T12:09:29-07:00",  <br> "AppName": "SharePoint", <br> "Action": "OpenFile", "IP": "154.192.13.131", <br> "DevicePlatform": "Windows 1.0.1607" <br>}]

> [!NOTE]
>  Con el fin de garantizar la seguridad y la auditoría, algunas características no le permiten exportar ni eliminar los registros generados por el sistema para poder mantener la integridad de la información personal.
>
>

## <a name="deleting-system-generated-logs"></a>Eliminación de registros generados por el sistema
Para eliminar los registros generados por el sistema recuperados a través de una solicitud de acceso, debe quitar el usuario del servicio y eliminar permanentemente su cuenta de Azure Active Directory. Para obtener instrucciones sobre cómo eliminar permanentemente un usuario, vea la sección correspondiente a la **eliminación de un usuario** de la *documentación de Azure sobre solicitudes del interesado del RGDP* que se encuentra en el [Portal de confianza de servicios de Office 365](https://servicetrust.microsoft.com/ViewPage/GDPRDSR). Es importante tener en cuenta que la eliminación permanente de una cuenta de usuario es irreversible una vez iniciada.

La eliminación permanente de una cuenta de usuario quita los datos del usuario de registros generados por el sistema para los servicios PowerApps, Microsoft Flow y CDS for Apps en los 30 días siguientes.