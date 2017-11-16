---
title: "Generación de una aplicación (Common Data Service) | Microsoft Docs"
description: "Generación de una aplicación con tres pantallas en Common Data Service"
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: Gi5TQF7_pz8
courseduration: 6m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 64e34da9afcecde950094ff40808c99176bccc13
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="generate-an-app-common-data-service"></a>Generación de una aplicación (Common Data Service)
En esta sección del curso, vamos a crear una aplicación basada en *entidades*, en Common Data Service. Las entidades son fragmentos de datos compartidos que se pueden modificar, almacenar, recuperar, y con los que se puede interactuar. Vamos a generar la aplicación a partir de una entidad, le mostraremos cómo personalizar la aplicación, agregaremos otro origen de datos y llamaremos a un flujo desde la aplicación. Si ya completó la sección sobre cómo crear una aplicación a partir de una lista de SharePoint, trataremos algunos de esos mismos aspectos, pero con más detalle, especialmente sobre la personalización de la aplicación.

Vamos a crear una aplicación de administración de casos que podría usar un departamento de TI para realizar el seguimiento de los problemas de hardware y software de una organización, así como para priorizarlos y actuar. A medida que avance por los temas, también se le podrían ocurrir otros usos para una aplicación como esta. Usamos datos de Common Data Service porque son adecuados para el almacenamiento de datos de aplicación, pero podría crear la misma aplicación con un origen de datos diferente.

PowerApps incluye una plantilla de administración de casos más compleja que usa las mismas entidades que la aplicación que vamos a crear. Después de haber completado esta sección, le recomendamos que explore esa plantilla para hacerse una idea de lo que puede crear en PowerApps.

## <a name="create-a-common-data-service-database"></a>Crear una base de datos de Common Data Service
El primer paso para crear esta aplicación es crear una base de datos de Common Data Service si aún no tiene una. Cree una base de datos de Common Data Service en un *entorno*. Un entorno es un contenedor de aplicaciones y otros recursos (aprenderá más acerca de los entornos más adelante en el curso). Un *administrador de entornos* puede seguir estos pasos para crear una base de datos (si no es un administrador, consulte con un administrador de su organización).

En la pestaña **Inicio**, haga clic en **Crear base de datos**.

![Crear base de datos en Common Data Service](./media/learning-case-app-generate/create-database.png)

Especifique si desea restringir el acceso a la base de datos (la mantendremos abierta) y, después, haga clic en **Crear mi base de datos**.

![Especificar el acceso en Common Data Service](./media/learning-case-app-generate/specify-access.png)

Una vez completado el proceso, verá todas las entidades estándar que se incluyen en Common Data Model. A continuación se muestran algunas de ellas.

![Entidades estándar de Common Data Service](./media/learning-case-app-generate/standard-entities.png)

## <a name="generate-an-app-from-the-case-entity"></a>Generar una aplicación a partir de la entidad Case
Una vez creada la base de datos, conectamos con la entidad Case y generamos una aplicación. Haga clic en **Nueva aplicación** y en **PowerApps Studio para web**.

![Nueva aplicación en PowerApps Studio para web](./media/learning-case-app-generate/choose-studio.png)

Estamos creando una aplicación de teléfono para una entidad de Common Data Service; en **Common Data Service**, haga clic o pulse **Diseño de teléfono**.

![Aplicación de teléfono de Common Data Service](./media/learning-case-app-generate/common-phone.png)

En la siguiente pantalla, elija una conexión y la entidad a la que va a conectarse y haga clic en **Conectar**.

![Conectarse a la entidad Case](./media/learning-case-app-generate/connect-entity.png)

Después de hacer clic en **Conectar**, PowerApps empieza a generar la aplicación. PowerApps hace todo tipo de inferencias sobre los datos para poder generar una aplicación útil como punto de partida.

## <a name="view-the-app-in-powerapps-studio"></a>Ver la aplicación en PowerApps Studio
La nueva aplicación de tres pantallas se abre en PowerApps Studio. Todas las aplicaciones que se generan a partir de datos tienen el mismo conjunto de pantallas:

* La pantalla **Examinar**: donde puede examinar, ordenar, filtrar y actualizar los datos que se extraigan de la lista, así como agregar elementos solo con hacer clic en el icono (+).
* La pantalla **Detalles**: donde puede obtener información más detallada sobre un elemento y decidir si lo elimina o lo edita.
* La pantalla **Editar o crear**: donde puede editar un elemento existente o crear uno nuevo.

En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura.

![Alternancia de las vistas](./media/learning-case-app-generate/toggle-view.png)

Haga clic o pulse en las miniaturas para ver los controles en la pantalla correspondiente.

![La aplicación generada](./media/learning-case-app-generate/finished-app.png)

Después, exploraremos la aplicación con más detalle y la personalizaremos para que se adapte mejor a nuestras necesidades.

