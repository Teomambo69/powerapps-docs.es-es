---
title: Seguridad de Common Data Service | Microsoft Docs
description: Utilizar la seguridad basada en roles para controlar el acceso a entidades
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: uwm8ghMUCeI
courseduration: 8m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: d557f7a8a276c89910713bcd5a19d0908d1c52f0
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="common-data-service-security"></a>Seguridad de Common Data Service
En este tema se describe la seguridad en Common Data Service. El servicio utiliza un sistema basado en roles para conceder permisos a los usuarios para acceder a los datos. El modelo de seguridad es una jerarquía en la que cada nivel representa un nivel de acceso diferente. En el nivel más bajo se encuentran los permisos individuales de creación, lectura, actualización y eliminación relativos a una sola entidad. Una colección de estos permisos de nivel de entidad constituye un conjunto de permisos. Un rol puede usar uno o varios conjuntos de permisos. Un rol está en el nivel superior: abarca todos los permisos que necesita un usuario o un grupo de usuarios.

## <a name="understanding-roles-and-permission-sets"></a>Descripción de los roles y los conjuntos de permisos
En la mayor parte de este curso, nos hemos centrado en powerapps.com y PowerApps Studio. En este tema, nos centraremos en el centro de administración de PowerApps. Si hace clic en un entorno del centro de administración, en **Seguridad** puede ver las pestañas **Environment roles** (Roles de entorno), que ya analizamos en un tema anterior, **Roles de usuario** y **Conjuntos de permisos**. De forma predeterminada, hay dos roles de usuario:

* **Propietario de la base de datos** es un rol administrativo que proporciona acceso completo a todas las entidades.
* **Usuario de la organización** es el rol predeterminado asignado a todos los usuarios. Este rol proporciona a todos los usuarios acceso a las entidades que contienen datos públicos.

![Roles de usuario del centro de administración](./media/learning-common-data-service-security/user-roles.png)

De forma predeterminada, hay dos conjuntos de permisos para cada entidad 

* **Mantener** proporciona un control total: permite crear, leer, actualizar y eliminar permisos.
* **Ver** proporciona acceso de solo lectura.

La siguiente imagen muestra el conjunto de permisos predeterminado de la entidad Account. 

![Conjuntos de permisos del centro de administración](./media/learning-common-data-service-security/permission-sets.png)

En el vídeo, se explica cómo crear roles y conjuntos de permisos adicionales para que pueda habilitar un acceso específico para sus aplicaciones. Se crea un conjunto de permisos denominado **Mantener revisión del producto** que proporciona acceso completo a la entidad personalizada que se creó en un tema anterior y un rol **Propietario de ReviewApp** al que se asigna el conjunto de permisos.  

## <a name="restrict-access-to-a-database"></a>Restricción del acceso a una base de datos
Cuando se creó una base de datos en un tema anterior, usamos el valor predeterminado de acceso abierto a la base de datos. Para cambiar el acceso, en la pestaña **Base de datos** haga clic en **Restringir acceso**y, a continuación, confirme que desea realizar el cambio.

![Restringir el acceso a la base de datos](./media/learning-common-data-service-security/restrict-access.png)

En el modo restringido, cada usuario debe tener uno o varios roles asignados. Un rol se puede configurar para un puesto específico dentro de la empresa y se puede asignar a cualquier persona que ocupe ese puesto. Los usuarios también se pueden agregar automáticamente a un rol según los grupos de Azure Active Directory a los que pertenezcan.

## <a name="wrapping-it-up"></a>En resumen
La seguridad puede ser un tema complejo, pero solo recuerde la jerarquía de permisos. Empieza por los permisos de creación, lectura, actualización y eliminación sobre una entidad, los cuales pueden formar conjuntos de permisos que, posteriormente, se asignan a roles. Es un sistema flexible que le permite controlar el acceso a los datos de una manera bastante específica. 

Con esto llegamos al final de la sección sobre Common Data Service y también al final de este curso de aprendizaje guiado. Confiamos en que haya disfrutado y aprendido mucho. Si tiene cualquier comentario háganoslo saber y manténgase atento porque tenemos previsto volver a agregar contenido con el tiempo. Para obtener contenidos más detallados, puede visitar ahora mismo la [documentación de PowerApps](https://powerapps.microsoft.com/tutorials/getting-started/). 

