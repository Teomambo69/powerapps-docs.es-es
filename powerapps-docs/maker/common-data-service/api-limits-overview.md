---
title: Información general sobre límites de la API (Common Data Service) | MicrosoftDocs
description: Comprender los límites de las solicitudes de la API Common Data Service.
ms.custom: ''
ms.date: 11/23/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 786994fa531698919d1506dc90217f435e43fb8a
ms.sourcegitcommit: abeedb952afc5e09ae4c158611e4813b63cb49b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2019
ms.locfileid: "2854797"
---
# <a name="common-data-service-api-limits-overview"></a>Información general sobre límites de la API Common Data Service

Los límites API Common Data Service ayudan a garantizar los niveles de servicio, disponibilidad y calidad. Los límites API Common Data Service son parte de límites y asignaciones de solicitudes de Power Platform. Este tema introducirá límites específicamente para Common Data Service aplicables para aplicaciones basadas en modelo en Dynamics 365 (como Dynamics 365 Sales y Dynamics 365 Customer Service), Power Apps y Power Automate conectando a aplicaciones basadas en modelos/Common Data Service en Dynamics 365. 

Para obtener información sobre los límites de todas las áreas en Power Platform, vea [Límites y asignaciones de solicitudes de Power Platform](/power-platform/admin/api-request-limits-allocations).

Hay dos categorías de límites que se aplican para Common Data Service : límites de *Derechos* y de *Protección de servicio*.

## <a name="entitlement-limits"></a>Límites de derechos

Estos límites representan la cantidad de solicitudes que los usuarios tienen derecho a hacer cada día. El límite asignado depende del tipo de licencia asignada a cada usuario.

Si un usuario excede su derecho de solicitud, se notificará al administrador y podría asignar capacidad de solicitudes de Power Apps y Power Automate a ese usuario. Los usuarios no se bloquearán para el uso de aplicaciones para excedentes ocasionales y razonables en este momento.

Para Common Data Service, las solicitudes de API incluyen todas las operaciones de datos que interactúan con registros de entidad donde se crean, recuperan, actualizan o eliminan registros (CRUD). Operaciones especiales como *compartir* y *asignar* están incluidas porque se consideran actualizaciones. Estas solicitudes pueden ser de cualquier cliente o aplicación y usar cualquier extremo. Estas incluyen, entre otras, operaciones realizadas por complementos, flujos de trabajo asíncronos y controles personalizados. Hay un pequeño conjunto de operaciones internas del sistema que se excluyen, como operaciones de inicio de sesión, cierre de sesión y metadatos del sistema.

> [!IMPORTANT]
> Las asignaciones de solicitudes de API de Power Platform incluyen el uso de API de Power Automate, AI Builder y conector. Todas las solicitudes a través de un conector que resultan en una solicitud de Common Data Service representarán 1 solicitud de Power Platform.

Para obtener detalles sobre estos límites de derechos, consulte [Asignaciones de solicitudes de Microsoft Power Platform basadas en licencias](/power-platform/admin/api-request-limits-allocations#microsoft-power-platform-requests-allocations-based-on-licenses).

Para obtener información sobre cómo ver y asignar complementos de capacidad, vea [Complementos de capacidad](/power-platform/admin/capacity-add-on).

Para obtener información sobre la compra de complementos de capacidad individuales, consulte la [Guía de licencias de Power Apps y Power Automate](https://go.microsoft.com/fwlink/?linkid=2085130). 
<!-- There should be some help about purchasing these through the Portal -->


## <a name="service-protection-limits"></a>Límites de protección de servicio

Para garantizar una disponibilidad y un rendimiento consistentes para todos, aplicamos algunos límites sobre cómo se utilizan las API con Common Data Service. Los límites de API de protección de servicios ayudan a asegurarse de que los usuarios que ejecuten aplicaciones no puedan interferir unos con otros basándose en limitaciones de recursos. Los límites no afectarán a los usuarios normales de la plataforma. Solo podrán verse afectadas las aplicaciones que realicen un gran número de solicitudes de API. Los límites le proporcionan cierto grado de protección contra aumentos aleatorios e inesperados en los volúmenes de solicitudes que ponen en peligro las características de disponibilidad y rendimiento de la plataforma Common Data Service.

Limitamos el número de conexiones simultáneas por cuenta de usuario, el número de solicitudes de API por conexión y la cantidad de tiempo de ejecución que se puede usar para cada conexión. Estos se evalúan en una ventana deslizante de cinco minutos. Cuando se supere uno de estos límites, la plataforma generará una excepción.

> [!NOTE]
> Los límites de protección del servicio se aplican a todas las solicitudes, no solo a las operaciones CRUD en entidades que se contabilizan para límites de derechos.
> 
> Dado que los complementos y las actividades de flujo de trabajo personalizadas se ejecutan en el servidor independientemente de un usuario que ha iniciado sesión, los límites de protección de servicios no se cuentan para las llamadas de la API realizadas desde el código del complemento.

Dado que los límites de protección de servicios generalmente solo se encuentran en aplicaciones que realizan un gran volumen de operaciones de datos, recomendamos que los desarrolladores que crean esas aplicaciones apliquen patrones para volver a intentar las operaciones después de un período de tiempo cuando se devuelven estas excepciones. Esto permitirá que la aplicación responda a las excepciones que envía el servicio y reducirá el número total de solicitudes y logrará el mayor rendimiento posible.

Para obtener información sobre los errores específicos que se pueden devolver y cómo los desarrolladores pueden aplicar patrones para responder a estos errores, vea [Límites de API de protección de servicios](../../developer/common-data-service/api-limits.md).


### <a name="see-also"></a>Vea también

[Administrar Power Platform / Licencias y gestión de licencias / Límites de solicitudes y asignaciones](/power-platform/admin/api-request-limits-allocations)<br />
[Desarrollador / Trabajar con datos usando código / Límites de la API de protección de servicios](../../developer/common-data-service/api-limits.md)

