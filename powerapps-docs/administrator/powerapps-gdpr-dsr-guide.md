---
title: Guía de DSR de PowerApps sobre datos creados por el cliente | Microsoft Docs
description: Guía de DSR de PowerApps sobre datos creados por el cliente
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms-topic: article
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/17/2018
ms.author: jamesol
ms.openlocfilehash: 823c14d0677ef96c48a26e2488bac1c91bbea225
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-powerapps-customer-data"></a>Respuesta a solicitudes de derechos del interesado (DSR) sobre datos de cliente de PowerApps

## <a name="introduction-to-dsr-requests"></a>Introducción a las solicitudes de DSR
Como parte de nuestro compromiso de asociarnos con usted en su viaje al RGPD, hemos desarrollado esta documentación para ayudarle a prepararse. La documentación no sólo describe lo que hacemos para prepararnos para el RGPD, sino que también comparte ejemplos de pasos que puede seguir hoy en día con Microsoft como apoyo al cumplimiento del RGPD al usar PowerApps, Microsoft Flow y Common Data Service for Apps.

El Reglamento general de protección de datos (RGPD) de la UE otorga derechos a las personas (denominadas "interesados" en el reglamento) para administrar los datos personales recopilados por un empresario u otro tipo de agencia u organización (denominado "poseedor de los datos" o simplemente "poseedor"). Los datos personales se definen de manera muy amplia en RGPD como cualquier dato que se refiera a una persona física identificada o identificable. El RGPD ofrece a los interesados derechos específicos sobre sus datos personales; entre estos derechos se incluye el de obtener copias de los datos personales, solicitar correcciones en ellos, restringir su procesamiento, eliminarlos o recibirlos en formato electrónico para poder trasladarlos a otro poseedor de los datos. Una solicitud formal realizada por un interesado al poseedor de los datos para que tome medidas en sus datos personales se denomina solicitud de derechos del interesado (DSR, por sus siglas en inglés).

La guía describe cómo utilizar los productos, los servicios y las herramientas administrativas de Microsoft para ayudar a nuestros clientes poseedores de los datos a buscar datos personales y actuar en ellos para responder a las solicitudes de DSR. Específicamente, esto incluye cómo encontrar, acceder y actuar sobre los datos personales que residen en la nube de Microsoft. Este es un breve resumen de los procesos descritos en esta guía:

1. **Descubrir**: usar herramientas de búsqueda y detección para encontrar más fácilmente los datos de cliente que pueden ser objeto de una solicitud DSR. Cuando se recopilan documentos potencialmente sensibles, se puede realizar una o varias de las acciones de DSR descritas en los pasos siguientes para responder a la solicitud. También puede determinar que la solicitud no cumple con las directrices de la organización para responder a las solicitudes DSR.

1. **Acceso**: recuperar datos personales que residen en la nube de Microsoft y, si se solicita, hacer una copia de los mismos que pueda estar disponible para el interesado.

1. **Rectificar**: realizar cambios o implementar otras acciones solicitadas sobre los datos personales, cuando corresponda.

1. **Restringir**: restringir el procesamiento de datos personales, ya sea mediante la eliminación de licencias para varios servicios en línea o mediante la desactivación de los servicios deseados cuando sea posible. También puede quitar datos de la nube de Microsoft y conservarlos de manera local o en otra ubicación.

5. **Eliminar**: quitar permanentemente los datos personales que residían en la nube de Microsoft.

6. **Exportar**: proporcionar una copia electrónica (en formato legible por máquina) de los datos personales al interesado.

Cada sección de esta guía describe los procedimientos técnicos que puede llevar a cabo una organización poseedora de los datos para responder a una solicitud DSR sobre datos personales en la nube de Microsoft.

## <a name="discover"></a>Descubra
El primer paso para responder a una solicitud DSR consiste en encontrar los datos personales objeto de la solicitud. El primer paso, encontrar los datos personales en cuestión y revisarlos, le ayudará a determinar si una solicitud DSR cumple los requisitos de su organización para aceptar o rechazar una solicitud DSR. Por ejemplo, después de encontrar y revisar los datos personales en cuestión, puede determinar que la solicitud no cumple los requisitos de su organización porque al hacerlo puede que afecte negativamente a los derechos y las libertades de terceros.

### <a name="step-1-find-personal-data-for-the-user-in-powerapps"></a>Paso 1: Búsqueda de datos personales del usuario en PowerApps
Seguidamente se muestra un resumen de los tipos de recursos de PowerApps que contienen datos personales de un usuario concreto.

Recursos que contienen datos personales |    Propósito
--- | ---
Entorno |   Un entorno es un espacio para almacenar, administrar y compartir los datos empresariales, las aplicaciones y los flujos de la organización. [Más información](https://go.microsoft.com/fwlink/?linkid=872239)
Permisos de entorno | A los usuarios se les asignan roles de entornos que les conceden privilegios de administrador y de creador en un entorno. [Más información](https://go.microsoft.com/fwlink/?linkid=872240)
Aplicaciones de lienzo  | Aplicaciones empresariales multiplataforma que pueden generarse a partir de un lienzo en blanco y conectarse a más de 200 orígenes de datos. [Más información](https://go.microsoft.com/fwlink/?linkid=872241)
Permisos de aplicaciones de lienzo  | Las aplicaciones de lienzo se pueden compartir entre usuarios de una organización. [Más información](https://go.microsoft.com/fwlink/?linkid=872242)
Conexión  | La usan los conectores y permite establecer conectividad con las API, los sistemas, las bases de datos, etcétera. [Más información](https://go.microsoft.com/fwlink/?linkid=872243)
Permisos de conexión  | Ciertos tipos de conexiones se pueden compartir entre usuarios de una organización. [Más información](https://go.microsoft.com/fwlink/?linkid=872244)
Conector personalizado    | Conectores personalizados que ha creado un usuario para proporcionar acceso a un origen de datos que no se ofrece a través de uno de los conectores estándar de PowerApps. [Más información](https://go.microsoft.com/fwlink/?linkid=872245)
Permisos de conector personalizado    | Los conectores personalizados se pueden compartir entre usuarios de una organización. [Más información](https://go.microsoft.com/fwlink/?linkid=872246)
Configuración de usuarios y aplicaciones de usuario de PowerApps    | PowerApps almacena varias configuraciones y preferencias del usuario que se utilizan para entregar las experiencias de tiempo de ejecución y de portal de PowerApps.
Notificaciones de PowerApps | PowerApps envía varios tipos de notificaciones a los usuarios que incluyen cuándo se comparte una aplicación con ellos y cuándo se ha completado una operación de exportación de Common Data Service for Apps.
Puerta de enlace | Las puertas de enlace son puertas de enlace de datos locales que un usuario puede instalar para transferir datos de forma rápida y segura entre PowerApps y un origen de datos que no se encuentra en la nube. [Más información](https://go.microsoft.com/fwlink/?linkid=872247)
Permisos de puerta de enlace | Las puertas de enlace se pueden compartir entre usuarios de una organización. [Más información](https://go.microsoft.com/fwlink/?linkid=872249)
Aplicaciones controladas por modelos y permisos de aplicación controlados por modelos  | El diseño de aplicaciones controladas por modelos es un enfoque de componentes centrado en el desarrollo de aplicaciones. Las aplicaciones controladas por el modelos y sus permisos de acceso de usuario se almacenan como datos en la base de datos de Common Data Service for Apps.  [Más información](https://go.microsoft.com/fwlink/?linkid=872248)

PowerApps ofrece las experiencias siguientes para buscar datos personales de un usuario concreto:

- **Acceso al sitio web**: [sitio de PowerApps](https://web.powerapps.com) [Centro de administración de PowerApps](https://admin.powerapps.com/) y [Portal de confianza de servicios de Office 365](https://servicetrust.microsoft.com/)
- **Acceso de PowerShell**: cmdlets de PowerApps (para [creadores de aplicaciones](https://go.microsoft.com/fwlink/?linkid=871448) y [administradores](https://go.microsoft.com/fwlink/?linkid=871804)) y [cmdlets de puerta de enlace local](https://go.microsoft.com/fwlink/?linkid=872238)

Para obtener instrucciones detalladas sobre cómo utilizar estas experiencias para buscar datos personales de un usuario determinado en cada uno de estos tipos de recursos, vea [Export Customer Data in PowerApps]( https://go.microsoft.com/fwlink/?linkid=871888) (Exportación de datos de cliente en PowerApps).

Después de encontrar los datos, puede realizar la acción específica para satisfacer la solicitud del interesado.

### <a name="step-2-find-personal-data-for-the-user-in-microsoft-flow"></a>Paso 2: Búsqueda de datos personales del usuario en Microsoft Flow
Las licencias de PowerApps siempre incluyen funcionalidades de Microsoft Flow. Además de que se incluirse en PowerApps, Microsoft Flow también está disponible como servicio independiente.
Vea Executing DSR requests against Common Data Service for Apps customer data (Ejecución de solicitudes DSR en datos de cliente de Common Data Service for Apps) para obtener instrucciones sobre cómo descubrir datos personales almacenados en el servicio Microsoft Flow.

> [!IMPORTANT]
> Se recomienda que los administradores completen este paso para un usuario de PowerApps

### <a name="step-3-find-personal-data-for-the-user-in-instances-of-common-data-service-cds-for-apps"></a>Paso 3: Búsqueda de datos personales del usuario en instancias de Common Data Service (CDS) for Apps
Ciertas licencias PowerApps, incluido el Plan de la comunidad de PowerApps, ofrecen la posibilidad de que los usuarios de su organización creen instancias de CDS for Apps y creen y compilen aplicaciones en CDS for Apps. El Plan de la comunidad de PowerApps es una licencia gratuita que permite que los usuarios prueben CDS for Apps en un entorno individual. Vea la página [Precios de PowerApps](https://powerapps.microsoft.com/pricing/) para saber qué funcionalidades se incluyen en cada licencia de PowerApps.

Vea Executing DSR requests against Common Data Service for Apps customer data (Ejecución de solicitudes DSR en datos de cliente de Common Data Service for Apps) para obtener instrucciones sobre cómo descubrir datos personales almacenados en CDS for Apps.

> [!IMPORTANT]
> Se recomienda que los administradores completen este paso para un usuario de PowerApps

## <a name="rectify"></a>Rectificar
Si el interesado le ha pedido que rectifique los datos personales que residen en los datos de su organización, usted y su organización tendrán que determinar si es apropiado cumplir con la solicitud. La rectificación de los datos puede incluir la realización de acciones tales como la edición, redacción o eliminación de datos personales de un documento u otro tipo o elemento.

PowerApps tiene dependencias en Azure Active Directory para determinar la identidad. Las identidades incluyen datos personales y, por lo tanto, se pueden editar en Azure Active Directory. Los clientes empresariales pueden administrar las solicitudes de rectificación DSR, incluidas las funciones de edición limitadas según la naturaleza de un determinado servicio Microsoft.  Como procesador de datos, Microsoft no ofrece la capacidad de corregir los registros generados por el sistema porque reflejan actividades reales y constituyen un registro histórico de eventos dentro de los servicios de Microsoft. Para obtener más información, vea la documentación de Azure sobre solicitudes del interesado del RGDP que se encuentra en el [Portal de confianza de servicios de Office 365](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).

## <a name="restrict"></a>Restringir
Es posible que los interesados soliciten que se restrinja el procesamiento de sus datos personales.  Proporcionamos tanto interfaces de programación de aplicaciones (API) preexistentes como interfaces de usuario (IU).  Estas experiencias proporcionan al administrador de inquilinos del cliente empresarial la capacidad de administrar dichas solicitudes mediante una combinación de exportación de datos y eliminación de datos. Un cliente puede solicitar:

- La exportación de una copia electrónica de los datos personales del usuario, que incluya:

    - cuentas
    - registros generados por el sistema
    - registros asociados
- La eliminación de la cuenta y los datos asociados que residen en sistemas de Microsoft.

## <a name="export"></a>Exportar
El "derecho a la portabilidad de los datos" permite al interesado solicitar una copia de sus datos personales en formato electrónico (es decir, en un formato "estructurado", comúnmente utilizado, legible por máquina e interoperable) que pueda transmitirse a otro poseedor de los datos.

Vea [Executing Export Data Subject Rights (DSR) Requests against PowerApps Customer Data](https://go.microsoft.com/fwlink/?linkid=871888) (Ejecución de solicitudes de exportación de derechos del interesado (DSR) sobre datos de cliente de PowerApps) para obtener más detalles.

## <a name="delete"></a>Eliminar
El "derecho al olvido" mediante la eliminación de datos personales de los datos de cliente de una organización es una protección de clave en el RGDP. La eliminación de datos personales incluye la eliminación de registros generados por el sistema, pero no de información del registro de auditoría.

PowerApps permite a los usuarios compilar aplicaciones de línea de negocio que sean parte fundamental de las operaciones diarias de su organización. Cuando un usuario deja la organización, habrá que realizar una revisión manual y determinar si se deben eliminar determinados datos y recursos que haya creado. Los datos de otros clientes se eliminarán automáticamente cuando se elimine la cuenta del usuario de Azure Active Directory.

Vea [Executing Delete Data Subject Rights (DSR) Requests against PowerApps Customer Data](https://go.microsoft.com/fwlink/?linkid=871883) (Ejecución de solicitudes de eliminación de derechos del interesado (DSR) sobre datos de cliente de PowerApps) para obtener más detalles.
