---
title: "Creación de una aplicación desde cero mediante una base de datos de Common Data Service | Microsoft Docs"
description: "Cree una aplicación para agregar, actualizar y eliminar registros."
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: f3cc5a8116f84d61576d75b22a8e3197d6ec7e42
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="create-an-app-from-scratch-using-a-common-data-service-database"></a>Crear una aplicación desde cero mediante una base de datos de Common Data Service
Cree una aplicación para administrar datos que se almacenan en Common Data Service, usando entidades estándar (que están integradas), entidades personalizadas (creadas por la organización) o ambas.

Al crear una aplicación desde Common Data Service, no es necesario crear una conexión desde Microsoft PowerApps, como ocurre con orígenes de datos tales como SharePoint, Dynamics 365 y Salesforce. Solo necesita especificar las entidades que desea mostrar, administrar o usar para ambas actividades en la aplicación.

[!VIDEO nb:cid:UUID:5db63c4d-6aeb-45c5-9609-8f4bbdd37bc6]


1. Cree una base de datos de Common Data Service. Para más información, consulte [Crear una base de datos de Common Data Service](create-database.md).
2. En [powerapps.com](https://web.powerapps.com), en el panel de navegación izquierdo, pulse o haga clic en **Nueva aplicación**.
3. En el cuadro de diálogo que aparece, pulse o haga clic en **PowerApps Studio para web**. (También puede hacer clic o pulsar en **PowerApps Studio para Windows** y seguir las instrucciones para instalarlo. Aunque las instrucciones siguientes usan PowerApps Studio para web, las de la aplicación de Microsoft Windows son similares).
4. En **Comenzar con una plantilla o un lienzo en blanco**, pulse o haga clic en **Diseño de teléfono** en el icono **Aplicación vacía**.
5. Si se le pide, pulse o haga clic en **Omitir** para omitir el tutorial.
6. Pulse o haga clic en la pestaña **Contenido**.
7. Pulse o haga clic en **Orígenes de datos**.
8. En el panel de la derecha, pulse o haga clic en **Agregar origen de datos**.
9. Pulse o haga clic en la instancia de Common Data Service que desee utilizar.
10. En la lista de entidades, active la casilla de una o varias entidades que desee usar y pulse o haga clic en **Conectar**.

Las entidades especificadas aparecen en la lista de orígenes de datos, y puede crear la aplicación como se describe en [Crear una aplicación desde cero](get-started-create-from-blank.md).

