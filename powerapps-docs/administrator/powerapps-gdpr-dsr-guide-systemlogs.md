---
title: Respuesta a solicitudes DSR sobre registros generados por el sistema en PowerApps, Microsoft Flow y Common Data Service (CDS) for Apps | Microsoft Docs
description: Tutorial sobre cómo responder solicitudes DSR sobre registros generados por el sistema en PowerApps, Microsoft Flow y Common Data Service (CDS) for Apps
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 2c06be34d46688e3a25ce531d0e791dc0b1aca62
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "34553022"
---
# <a name="responding-to-dsr-requests-for-system-generated-logs-in-powerapps-microsoft-flow-and-common-data-service-for-apps"></a>Respuesta a solicitudes DSR sobre registros generados por el sistema en PowerApps, Microsoft Flow y Common Data Service for Apps
Microsoft le ofrece la posibilidad de tener acceso, exportar y eliminar los registros generados por el sistema que se consideren personales en la amplia definición de *datos personales* del Reglamento general de protección de datos (RGDP) de la Unión Europea (UE). Ejemplos de registros generados por el sistema que se consideran personales en el RGPD:
* Datos de uso de productos y servicios tales como registros de actividad del usuario
* Solicitudes de búsqueda de usuario y datos de consulta
* Datos generados por los productos y servicios como consecuencia de la funcionalidad del sistema y la interacción entre usuarios u otros sistemas

Tenga en cuenta que no se admite la posibilidad de restringir ni rectificar datos de registros generados por el sistema. Los datos de registros generados por el sistema constituyen acciones objetivas realizadas en la nube de Microsoft y los datos de diagnóstico &mdash;que incluyen modificaciones a dichos datos&mdash; podrían poner en peligro el registro histórico de las acciones y aumentar los riesgos de seguridad y de fraude.

## <a name="prerequisites"></a>Requisitos previos
Este artículo se centra en responder a las solicitudes DSR para los registros generados por el sistema en los inquilinos administrados y no administrados. Para determinar si pertenece o no a un inquilino administrado o no administrado, vea la sección **Determinación del tipo de inquilino** más adelante.

## <a name="accessing-and-exporting-system-generated-logs-for-managed-tenants"></a>Acceso y exportación de los registros generados por el sistema para inquilinos administrados
Los administradores tienen acceso a los registros generados por el sistema asociados a la utilización que haga un usuario de PowerApps y Microsoft Flow, así como de servicios y aplicaciones de Common Data Service (CDS) for Apps.

Para tener acceso a registros generados por el sistema y exportarlos:

1. Vaya al [Portal de confianza de servicios Microsoft](https://servicetrust.microsoft.com/) e inicie sesión con las credenciales de administrador global de Office 365.

2. En la lista desplegable **Privacidad** de la parte superior de la página, seleccione **Data Subject Request** (Solicitud del interesado).

3. En la página **Data Subject Request** (Solicitud del interesado), en **System Generated Logs** (Registros generados por el sistema), seleccione **Exportación de registros de datos**. La herramienta Exportación de registros de datos se abre y muestra una lista de las solicitudes de datos de exportación enviadas por la organización.

4. Para crear una solicitud para un usuario, haga clic en **Create Export Data Request** (Crear solicitud de exportación de datos).

    Después de crear una solicitud, esta aparece en la página **Exportación de registros de datos**, donde se puede realizar el seguimiento de su estado. Una vez completada una solicitud, puede hacer clic en un vínculo para tener acceso a los registros generados por el sistema, que se exportarán a la ubicación de almacenamiento de Azure de la organización en los 30 días siguientes a la creación de la solicitud. Los datos se guardarán en formatos de archivo comunes y legibles por máquina, como XML, CSV o JSON. Si no dispone de una cuenta de Azure y una ubicación de almacenamiento de Azure, debe crear una cuenta de Azure o una ubicación de almacenamiento de Azure para su organización para que la herramienta Exportación de registros de datos pueda exportar los registros generados por el sistema. Para obtener más información, vea [Introducción a Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).

En la tabla siguiente se resume el acceso y la exportación de los registros generados por el sistema para inquilinos administrados:

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

## <a name="deleting-system-generated-logs-for-managed-tenants"></a>Eliminación de los registros generados por el sistema para inquilinos administrados
Para eliminar los registros generados por el sistema recuperados a través de una solicitud de acceso, debe quitar el usuario del servicio y eliminar permanentemente su cuenta de Azure Active Directory. Para obtener instrucciones sobre cómo eliminar permanentemente un usuario, vea la sección correspondiente a la **eliminación de un usuario** de la *documentación de Azure sobre solicitudes del interesado del RGDP* que se encuentra en el [Portal de confianza de servicios de Office 365](https://servicetrust.microsoft.com/ViewPage/GDPRDSR). Es importante tener en cuenta que la eliminación permanente de una cuenta de usuario es irreversible una vez iniciada.

La eliminación permanente de una cuenta de usuario quita los datos del usuario de registros generados por el sistema para los servicios PowerApps, Microsoft Flow y CDS for Apps en los 30 días siguientes.


## <a name="accessing-and-exporting-system-generated-logs-for-unmanaged-tenants"></a>Acceso y exportación de los registros generados por el sistema para inquilinos no administrados

Los usuarios pueden tener acceso a los registros generados por el sistema asociados al uso que hagan de PowerApps y Microsoft Flow, así como de servicios y aplicaciones de Common Data Service (CDS) for Apps.

Para tener acceso a registros generados por el sistema y exportarlos:
1. Vaya al [portal de privacidad profesional y educativa](https://go.microsoft.com/fwlink/?linkid=873123).
1. En la página **Mis solicitudes de datos**, un usuario puede solicitar una exportación de datos si hace clic en el botón **Nueva solicitud de exportación**.
1. Al hacer clic en este botón, se le pedirá que confirme la solicitud. Haga clic en **Sí** para continuar.
1. Las solicitudes de exportación nuevas pueden tardar hasta un mes en completarse. Durante este tiempo, verá un estado de **En ejecución**.
1. Cuando haya terminado, se rellenará la columna **Fecha de finalización** y se proporcionará un vínculo a los registros **generados por el sistema**.
1. Haga clic en este vínculo para descargar los datos. Puede usar un editor de texto para ver estos datos.
1. Tenga en cuenta también que la **Fecha de expiración** para este contenido se rellena dentro de la columna Fecha de expiración. Tendrá hasta esa fecha para recuperar los registros generados por el sistema.

En la tabla siguiente se resume el acceso y la exportación de los registros generados por el sistema para inquilinos no administrados:

| Pregunta | Respuesta |
| --- | --- |
| ¿Cuánto tiempo tarda la herramienta Exportación de registros de datos de Microsoft en completar una solicitud? |    Esto depende de varios factores. En la mayoría de los casos debe completarse en uno o dos días, pero puede tardar hasta 30 días.
| ¿En qué formato estará el resultado? | El resultado estará en forma de archivos estructurados y legibles por máquina, como XML, CSV o JSON.
| ¿Quién tiene acceso a la herramienta Exportación de registros de datos para enviar solicitudes de acceso para los registros generados por el sistema? | Los usuarios que son miembros de un inquilino no administrado tienen acceso para enviar solicitudes.
| ¿Qué datos devuelve la herramienta Exportación de datos? | La herramienta Exportación de datos devuelve los registros generados por el sistema que se almacenan en Microsoft. Los datos exportados abarcan varios servicios Microsoft tales como Office 365, Azure, Dynamics, PowerApps, Microsoft Flow y CDS for Apps.
| ¿Cómo se devuelven los datos al usuario? |   Los datos se exportarán a un sitio web de Microsoft donde se proporcionará un vínculo de forma segura al usuario que realizó la solicitud DSR.
| ¿Qué aspecto tendrán los datos de los registros generados por el sistema? |  Ejemplo de una entrada de registros generados por el sistema en formato JSON: <br> [{ <br>"DateTime": "2017-04- 28T12:09:29-07:00",  <br> "AppName": "SharePoint", <br> "Action": "OpenFile", "IP": "154.192.13.131", <br> "DevicePlatform": "Windows 1.0.1607" <br>}]

> [!NOTE]
>  Con el fin de garantizar la seguridad y la auditoría, algunas características no le permiten exportar ni eliminar los registros generados por el sistema para poder mantener la integridad de la información personal.
>
>

## <a name="deleting-system-generated-logs-for-unmanaged-tenants"></a>Eliminación de los registros generados por el sistema para inquilinos no administrados
Para eliminar los registros generados por el sistema recuperados a través de una solicitud de acceso, debe cerrar la cuenta, lo que eliminará los registros generados por el sistema y quitará los datos de PowerApps, Microsoft Flow y los servicios de CDS for Apps en un plazo de 30 días.

Para eliminar los registros generados por el sistema, siga estos pasos:
1. Vaya al [portal de privacidad profesional y educativa](https://go.microsoft.com/fwlink/?linkid=873123).
1. En la página **Mis solicitudes de datos**, un usuario puede solicitar la eliminación de sus datos si hace clic en el botón **Cerrar cuenta**.
1. Al hacer clic en este botón, se le pedirá que confirme la solicitud. Haga clic en **Sí** para continuar.
1. Una vez que se haya cerrado la cuenta, no tendrá acceso a PowerApps, Microsoft Flow ni CDS.

## <a name="determining-tenant-type"></a>Determinación del tipo de inquilino
Para determinar si es o no un usuario de un inquilino administrado o no administrado, realice las acciones siguientes:
1. Abra la dirección URL siguiente en un explorador y asegúrese de reemplazar la dirección de correo electrónico en la dirección URL:[ https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1](https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1).

2. Si es miembro de un **inquilino no administrado**, verá `"IsViral": true` en la respuesta.
  ```
      {
      ...
      "Login": "foobar@unmanagedcontoso.com",
      "DomainName": "unmanagedcontoso.com",
      "IsViral": **true**,
      ...
      }
  ```

3. En caso contrario, pertenece a un inquilino administrado.
