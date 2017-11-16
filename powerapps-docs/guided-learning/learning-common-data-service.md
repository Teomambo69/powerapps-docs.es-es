---
title: Common Data Service | Microsoft Docs
description: "Descripción de este eficaz modo de almacenar y modelar datos"
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: os33pHQ9jSU
courseduration: 5m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 37385bb20f15296e3002f3258cae437220a63910
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="the-common-data-service"></a>Common Data Service
Los datos son fundamentales en los procesos y aplicaciones empresariales: datos de Excel, datos de orígenes locales como SQL Server y de orígenes en la nube como Salesforce y SharePoint Online. Los datos pueden estar relacionados con clientes, ventas, empleados y muchas otras cosas, pero el tema común es que los datos son cruciales para la empresa y desempeñan un papel clave en las aplicaciones que se crean en PowerApps. Hasta ahora ha visto y trabajado con diferentes tipos de orígenes de datos en el curso y anteriormente presentamos Microsoft Common Data Service. En esta sección, se empleará algo de tiempo en profundizar en los detalles, explicando las ventajas y mostrándole cómo utilizar el servicio.

## <a name="understanding-the-service"></a>Descripción del servicio
Orientémonos con un par de diagramas. Es posible que haya visto el primer diagrama anteriormente: muestra los componentes de la plataforma de aplicaciones empresariales de Microsoft. Llegados a este punto, obviamente estará familiarizado con PowerApps, pero es posible que también haya utilizado Microsoft Flow, Power BI u otros componentes. Como puede ver, Common Data Service, los conectores y las puertas de enlace son importantes para todos estos componentes. En este momento, Common Data Service se utiliza principalmente con PowerApps y Microsoft Flow, pero estará disponible para otros componentes con el tiempo.

![Diagrama de la plataforma empresarial](./media/learning-common-data-service/business-platform.png)

Ahora que sabe dónde encaja Common Data Service, echemos un vistazo a sus componentes. Considere Common Data Service como una jerarquía. En el nivel inferior, el servicio almacena los datos de forma confiable y escalable, y hace que los datos estén disponibles, con el fin de que varias aplicaciones puedan usarlos. El siguiente nivel es una instancia de Common Data Model que incluye muchas entidades usadas en las aplicaciones y los procesos empresariales: entidades como Account, Contact, Product y Sales Order. Puede ampliar las entidades estándar y crear otras personalizadas que satisfagan sus necesidades empresariales.

![Diagrama de la arquitectura de Common Data Service](./media/learning-common-data-service/architecture.png)

Una entidad es simplemente una combinación de los metadatos que la describen (nombres de campo, tipos de datos, etc.) y de los datos que almacena en ella. Si conoce Access u otra base de datos, una entidad es muy similar a una tabla. Las entidades se describirán más detalladamente en el siguiente tema pero, por ahora, tenga en cuenta las ventajas que supone trabajar con datos de entidad en Common Data Service:

* **Fáciles de administrar**: tanto los metadatos como los datos se almacenan en la nube. No tiene que preocuparse por los detalles de cómo se almacenan.
* **Fáciles de compartir**: puede compartir fácilmente datos con sus compañeros porque PowerApps administra los permisos.
* **Fáciles de proteger**: los datos se almacenan con seguridad para que los usuarios solo los puedan ver si se les concede acceso. La seguridad basada en roles le permite controlar el acceso a entidades de los diferentes usuarios dentro de la organización.
* **Metadatos completos**: se saca provecho de los tipos de datos y las relaciones directamente desde PowerApps. Por ejemplo, la definición de una dirección URL de tipo de campo presentará los datos como un hipervínculo dentro de la aplicación.
* **Herramientas de productividad**: las entidades están disponibles en los complementos para Microsoft Excel y Outlook para aumentar la productividad y garantizar que los datos sean accesibles.
* **Listas desplegables**: incluya listas desplegables a partir de un amplio conjunto de listas estándar para proporcionar listas desplegables rápidas en las aplicaciones y entidades.

## <a name="create-a-common-data-service-database"></a>Crear una base de datos de Common Data Service
Cree una base de datos de Common Data Service en un *entorno*. Ya aprendió a utilizar entornos anteriormente en este curso, así que hagamos tan solo un resumen: un entorno es un contenedor para aplicaciones y otros recursos como Common Data Service. Cada entorno puede tener una instancia del servicio asociada con él. Si usted es un administrador del entorno y desea agregar el servicio a un entorno, siga estos pasos.

En la pestaña **Inicio**, haga clic en **Crear base de datos**.

![Crear base de datos en Common Data Service](./media/learning-common-data-service/create-database.png)

Especifique si desea restringir el acceso a la base de datos y, después, haga clic en **Crear mi base de datos**.

![Especificar el acceso en Common Data Service](./media/learning-common-data-service/specify-access.png)

Una vez completado el proceso, verá todas las entidades estándar que se incluyen en Common Data Model. A continuación se muestran algunas de ellas.

![Entidades estándar de Common Data Service](./media/learning-common-data-service/standard-entities.png)

Si no ha trabajado con bases de datos anteriormente, puede que no esté familiarizado con algunas de estas explicaciones. Pero el concepto general es bastante sencillo: Common Data Service proporciona una forma segura y confiable de almacenar datos y tratar esos datos en términos de entidades comunes como Account, Contact, Product y Sales Order. En el tema siguiente, se ofrecerán más detalles acerca de las entidades.

