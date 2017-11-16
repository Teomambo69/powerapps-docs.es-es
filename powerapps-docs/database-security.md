---
title: "Configuración de la seguridad de base de datos | Microsoft Docs"
description: "En este tema se explica cómo configurar la seguridad de base de datos."
services: powerapps
documentationcenter: na
author: maertenm
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/08/2017
ms.author: kfend
ms.openlocfilehash: a8c13158ab2c3f152aa99357684c818f48e637ae
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="configure-database-security"></a>Configurar seguridad de base de datos
Common Data Service usa un modelo de seguridad basado en rol que ayuda a proteger el acceso a la base de datos. En este tema se explica cómo crear los artefactos de seguridad necesarios para ayudarle proteger una aplicación. Estos roles de usuario controlan el acceso en tiempo de ejecución a los datos y son independientes de los roles de entorno que rigen los administradores de entorno y los creadores de entorno. Para obtener información general acerca de los entornos, consulte [Environments overview](environments-overview.md) (Introducción a los entornos).

Es importante que sepa el nivel de acceso a estas entidades que necesitan los usuarios de la aplicación. Common Data Service admite los permisos de creación, lectura, actualización y eliminación (CRUD) en las entidades.

* **Crear:** el usuario puede crear entradas nuevas en la entidad.
* **Leer:** el usuario puede ver y buscar entradas existentes en la entidad.
* **Actualizar:** el usuario puede actualizar o editar una entrada existente en la entidad.
* **Eliminar:** el usuario puede eliminar o quitar una entrada existente en la entidad.

Los dos niveles de permiso que se usan con más frecuencia son el acceso de solo lectura y el acceso total. Common Data Service incluye conjuntos de permisos en estos dos niveles de permisos para todas sus entidades. Los conjuntos de permisos de visualización proporcionan acceso de lectura a una entidad. Los conjuntos de permisos de mantenimiento proporcionan acceso completo a una entidad.

El modelo de seguridad permite cualquier combinación de estos permisos que se asignarán a un rol de usuario. Los roles combinan los distintos permisos concedidos en los conjuntos de permisos que se les han agregado. Por lo tanto, los miembros de un rol pueden acceder a todos los datos a los que tienen acceso los conjuntos de permisos que se incluyen en el rol. Para más información acerca del modelo de seguridad de Common Data Service, consulte [Modelo de seguridad](https://docs.microsoft.com/en-us/common-data-service/entity-reference/security-model).

## <a name="identify-the-entities"></a>Identificación de las entidades
Para configurar los controles de acceso correctos para una aplicación, debe saber qué entidades usa la aplicación. Para ver una lista de las entidades que usa una aplicación, siga estos pasos.

1. Abra la aplicación en Microsoft PowerApps Studio.
2. En la pestaña **Contenido**, pulse o haga clic en **Orígenes de datos**. La lista de orígenes de datos se muestra en el panel derecho.

## <a name="configure-security"></a>Configuración de la seguridad
Cuando se crea una entidad nueva, también debe crear un conjunto de permisos nuevo o editar uno existente para proporcionar acceso a los datos de la entidad. Cuando se crea una aplicación, es aconsejable crear también un conjunto de permisos que proporcione acceso a todas las entidades que se necesitan para ejecutar la aplicación. La seguridad se administra en el centro de administración.

1. Anta el [centro de administración](https://admin.powerapps.com).
2. Pulse o haga clic en el entorno que contiene la base de datos.
3. Pulse o haga clic en **Seguridad**. Puede usar entonces las pestañas **Conjuntos de permisos** y **Roles de usuario** para configurar la seguridad en la base de datos.

## <a name="create-a-permission-set"></a>Creación de un conjunto de permisos
Para habilitar el acceso a una nueva aplicación, es preciso crear primero un conjunto de permisos nuevo.

1. Pulse o haga clic en **Conjuntos de permisos**.
2. Pulse o haga clic en **Nuevo conjunto de permisos** para crear un conjunto de permisos.
3. Escriba un nombre y una descripción para el conjunto de permisos, y, después, pulse o haga clic en **Crear**. El nuevo conjunto de permisos aparece en la lista de conjuntos de permisos.
4. Pulse o haga clic en el conjunto de permisos que acaba de crear.
5. Pulse o haga clic en la pestaña **Entidades**. La pestaña **Entidades** contiene una lista de todas las entidades de la base de datos. Para cada entidad que se usa en la aplicación, active la casilla para el permiso que desea permitir.
6. Haga clic o pulse en **Guardar**.

## <a name="create-a-policy-technical-preview"></a>Creación de una directiva (Technical Preview)
Para habilitar o restringir el acceso a los registros de una entidad, primero debe crear una directiva.

1. Pulse o haga clic en **Directivas**.
2. Pulse o haga clic en **Nueva directiva**.
3. Escriba un nombre y una descripción para la directiva.
4. Seleccione el tipo de directiva que quiere crear. Si va a crear una directiva de la lista desplegable, escriba la lista que desea usar.
5. Seleccione el operador que quiere utilizar.
6. Seleccione el valor de la directiva para comprobar.
7. Pulse o haga clic en **Crear**.

## <a name="assign-a-policy-technical-preview"></a>Asignación de una directiva (Technical Preview)
Para aplicar una directiva, debe asignarla a una entidad de datos de un conjunto de permisos.

1. Pulse o haga clic en **Conjuntos de permisos**.
2. Pulse o haga clic en el conjunto de permisos al que asignar una directiva.
3. Pulse o haga clic en el botón **Editar** de la entidad que se va a asignar una directiva.
4. Expanda la sección **Asignación de directiva**.
5. Seleccione las operaciones de datos a las que se va a aplicar la directiva (**Crear**, **Leer**, **Actualizar** o **Eliminar**).
6. Seleccione el campo de entidad en el que se basará la directiva.
7. Seleccione la directiva que se va a asignar.
8. Pulse o haga clic en **Asignar**.
9. Haga clic o pulse en **Guardar**.

## <a name="create-and-assign-a-role"></a>Creación y asignación de un rol
Después de incluir los permisos adecuados en un conjunto de permisos, puede crear un rol que se puede asignar a los usuarios.

1. Pulse o haga clic en **Roles de usuario**.
2. Pulse o haga clic en **Nuevo rol**.
3. Escriba un nombre y una descripción para el rol y, después, pulse o haga clic en **Crear**. El nuevo rol aparece en la lista de roles **Usuario**.
4. Pulse o haga clic en el rol que acaba de crear.
5. Pulse o haga clic en la pestaña **Conjuntos de permisos**.
6. Escriba el nombre del conjunto de permisos que ha creado antes. En la lista desplegable que aparece a medida que escribe, haga clic o pulse en el conjunto de permisos para agregarlo al rol. Repita este paso para cada conjunto de permisos que desee para el rol.
7. Pulse o haga clic en la pestaña **Usuarios** del rol.
8. Escriba los nombres o las direcciones de correo electrónico de los usuarios o grupos que desea agregar al rol. En la lista desplegable que aparece a medida que escribe, haga clic o pulse en el usuario. Los usuarios y grupos a los que se va a asignar el rol se agregan a la lista.
9. Haga clic o pulse en **Guardar**.

Los usuarios o grupos de este rol ahora pueden acceder a los datos a los que el conjunto de permisos que está asociado al rol les da acceso. Para utilizar los datos de la base de datos, el usuario debe tener un rol de seguridad y acceder a una aplicación de PowerApps que use los datos.

## <a name="edit-permission-sets-and-roles"></a>Edición de conjuntos de permisos y roles
Para editar roles y conjuntos de permisos cuando se hayan creado, haga clic en el botón **Editar**.

Para eliminar un rol o un conjunto de permisos, use botón **Eliminar**.

## <a name="out-of-box-security-roles"></a>Roles de seguridad de fábrica
Hay dos roles de seguridad de fábrica:

* **Propietario de la base de datos:** el rol de propietario de la base de datos está pensado para usuarios que tengan una función administrativa. El creador del entorno se asigna automáticamente a este rol. Los usuarios de este rol siempre tendrán acceso completo a todas las entidades de la base de datos. Incluso tienen acceso completo a las nuevas entidades que se agregan. Los usuarios de este rol también pueden crear y editar esquemas de entidades en la base de datos. No tiene que agregar conjuntos de permisos a este rol. Solo tendrá que asignarle usuarios.
* **Usuario de la organización:** este rol es el rol predeterminado que se asigna a todos los usuarios. El propósito de este rol es proporcionar a todos los usuarios acceso a las entidades que contienen datos públicos. Si una aplicación se comparte en modo restringido, las entidades que usa la aplicación deben incluirse en este rol. No tiene que asignar este rol, porque ya está asignado a todas las personas de su organización. Solo tiene que agregar los conjuntos de permisos que desea dar a toda la organización.

