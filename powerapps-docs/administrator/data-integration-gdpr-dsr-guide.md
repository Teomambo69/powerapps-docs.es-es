---
title: Datos de cliente de Integración de datos para administradores
description: Identificación, exportación y eliminación de datos personales en la integración de datos para los administradores de CDS for Apps
author: sabinn-msft
ms.service: powerapps
ms.topic: how-to
ms.component: cds
ms.date: 05/20/2018
ms.author: sabinn
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 4a0cb3dfedfcc79c2c68575c8c001af6a800c269
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862142"
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-data-integration-for-common-data-service-for-apps-customer-data"></a>Respuesta a solicitudes de derechos del interesado (DSR) para integración de datos para datos de cliente de Common Data Service for Apps

## <a name="introduction-to-dsr-requests"></a>Introducción a las solicitudes de DSR

El Reglamento general de protección de datos (RGPD) de la Unión Europea (UE) otorga derechos a las personas (denominadas “interesados” en el reglamento) para administrar los datos personales recopilados por un empleador u otro tipo de agencia u organización (denominado “responsable de los datos” o simplemente “responsable”). Los datos personales se definen de manera muy amplia en RGPD como cualquier dato que se refiera a una persona física identificada o identificable. El RGPD permite que los interesados hagan lo siguiente en cuanto a sus datos personales:

- Obtener copias
- Solicitar correcciones
- Restringir el procesamiento
- Eliminarlo
- Recibirlo en formato electrónico para poder moverlo a otro poseedor

Una solicitud formal realizada por un interesado al poseedor de los datos para que tome medidas en sus datos personales se denomina Solicitud de derechos del interesado (DSR).

En este artículo se describe cómo Microsoft se prepara para el RGPD y también se proporcionan ejemplos de los pasos que se pueden seguir como apoyo al cumplimiento del RGPD al usar Integración de datos para administradores a través del portal para administradores de CDS for Apps. Aprenderá a usar los productos, los servicios y las herramientas administrativas de Microsoft para ayudar a los clientes poseedores de los datos a buscar datos personales en la nube de Microsoft, acceder a ellos y actuar en ellos para responder a las solicitudes de DSR.

### <a name="searching-for-and-identifying-personal-data"></a>Búsqueda e identificación de datos personales

Integración de datos para administradores en CDS for Apps permite que cualquier usuario de la aplicación de integración vea sus datos mediante la pestaña de integración de datos en:

[https://admin.powerapps.com/dataintegration](https://admin.powerapps.com/dataintegration)

Los datos almacenados para el usuario se muestran en el portal. Todos los proyectos son visibles en la pestaña Proyectos:

![Ver los proyectos en la pestaña Proyectos](./media/data-integration-gdpr-dsr/projects-tab.png)

Todos los conjuntos de conexiones son visibles en la pestaña Conjuntos de conexiones:

![Ver los conjuntos de conexiones en la pestaña Conjuntos de conexiones](./media/data-integration-gdpr-dsr/connections-tab.png)

Todas las plantillas son visibles en la pestaña Plantillas:

![Ver las plantillas en la pestaña Plantillas](./media/data-integration-gdpr-dsr/templates-tab.png)

## <a name="securing-and-controlling-access-to-personal-information"></a>Protección y control del acceso a la información personal

En Integración de datos para administradores en CDS for Apps, solo se puede tener acceso a los datos almacenados por la aplicación de integración de datos a través del portal para administradores.

## <a name="deleting-personal-data"></a>Eliminación de datos personales

En Integración de datos para administradores en CDS for Apps, el usuario al que estén asociados los datos puede eliminar los datos, proyectos y conjuntos de conexiones que haya creado. Para eliminar sus datos personales, los usuarios pueden iniciar sesión en el portal para administradores: [https://admin.powerapps.com](https://admin.powerapps.com)

Los usuarios pueden eliminar los proyectos si se desplazan a la pestaña Proyectos, hacen clic en el botón de puntos suspensivos junto al proyecto y, después, seleccionan la opción Eliminar:

![Eliminar proyectos haciendo clic en el botón de puntos suspensivos](./media/data-integration-gdpr-dsr/projects-del.png)

Los usuarios pueden eliminar las plantillas si se desplazan a la pestaña Plantillas, hacen clic en el botón de puntos suspensivos junto a la plantilla y, después, seleccionan la opción Eliminar:

![Eliminar plantillas haciendo clic en el botón de puntos suspensivos](./media/data-integration-gdpr-dsr/templates-del.png)

Los usuarios pueden eliminar los conjuntos de conexiones si se desplazan a la pestaña Conjuntos de conexiones, hacen clic en el botón de puntos suspensivos junto al conjunto de conexiones y, después, seleccionan la opción Eliminar:

![Eliminar conjuntos de conexiones haciendo clic en el botón de puntos suspensivos](./media/data-integration-gdpr-dsr/connsets-del.png)

## <a name="exporting-personal-data"></a>Exportación de datos personales

En Integración de datos para administradores en CDS for Apps, el usuario al que estén asociados los datos puede exportar los datos que haya creado. Para exportar sus datos personales, los usuarios pueden iniciar sesión en el portal para administradores:

[https://admin.powerapps.com](https://admin.powerapps.com)

Para exportar proyectos o proyectos con el historial de ejecución, los usuarios pueden navegar a la pestaña Proyectos, hacer clic en el botón de puntos suspensivos junto al proyecto y, después, seleccionar la opción de exportación que quieran:

![Exportar proyectos haciendo clic en el botón de puntos suspensivos](./media/data-integration-gdpr-dsr/projects-exp.png)

Para exportar las plantillas, los usuarios se pueden desplazar a la pestaña Plantillas, hacer clic en el botón de puntos suspensivos junto a la plantilla y, después, seleccionar la opción Exportar:

![Exportar plantillas haciendo clic en el botón de puntos suspensivos](./media/data-integration-gdpr-dsr/templates-exp.png)

Para exportar los conjuntos de conexiones, los usuarios se pueden desplazar a la pestaña Conjuntos de conexiones, hacer clic en el botón de puntos suspensivos junto al conjunto de conexiones y, después, seleccionar la opción Exportar:

![Exportar conjuntos de conexiones haciendo clic en el botón de puntos suspensivos](./media/data-integration-gdpr-dsr/connsets-exp.png)
