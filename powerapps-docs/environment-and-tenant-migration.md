---
title: "Migración de aplicaciones entre entornos e inquilinos | Microsoft Docs"
description: Migrar aplicaciones entre entornos e inquilinos
services: 
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/28/2017
ms.author: jamesol
ms.openlocfilehash: 8c2745a47b742ccc5f21f3302c39546edd361242
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="environment-and-tenant-app-migration-through-packaging"></a>Migración de aplicaciones entre entornos e inquilinos mediante empaquetado
Obtenga información sobre cómo migrar recursos de un entorno a otro mediante empaquetado. Estos entornos pueden estar en el mismo inquilino o en varios distintos.

## <a name="the-scenario"></a>El escenario
Uno de los escenarios habituales en los que puede que desee migrar recursos es en el que tiene entornos de prueba o desarrollo, y un entorno de producción. Los desarrolladores y evaluadores tienen un amplio acceso a las aplicaciones en sus entornos. Pero cuando llega el momento de migrar una nueva aplicación a producción, dicho entorno tiene un riguroso control sobre los permisos para actualizarlo y cambiarlo.

Otro escenario es en el que cada cliente tiene su propio entorno y datos. Al agregar un nuevo cliente, se crearía un nuevo entorno para este y migraría las aplicaciones a dicho entorno.

## <a name="which-resources-can-i-migrate-through-packaging"></a>¿Qué recursos puedo migrar mediante empaquetado?
Al exportar una aplicación, en el paquete también se exportan los recursos dependientes de la aplicación.  Inicialmente solo se admitirá un subconjunto de todos los tipos de recursos posibles, tal y como se describe en la tabla siguiente.

| Tipo de recurso | Admitido | Opciones de importación |
| --- | --- | --- |
| App |Sí |Hay dos opciones para importar una aplicación en un entorno: <ol><li><b>Crear una nueva</b>: la aplicación se creará como una nueva aplicación en el entorno donde se importe el paquete.</li> <li><b>Actualizar</b>: la aplicación ya existe en el entorno y se actualizará al importar este paquete.</li></ol> |
| Flujo |Sí |Hay dos opciones para importar un flujo en un entorno: <ol><li><b>Crear uno nuevo</b>: el flujo se creará como un flujo nuevo en el entorno donde se importe el paquete.</li> <li><b>Actualizar</b>: el flujo ya existe en el entorno y se actualizará al importar este paquete.</li></ol> <b>Nota: </b>Todos los recursos de los que el flujo depende también se incluirán en el paquete de aplicación que se exporte y deberán configurarse cuando se importe el paquete. |
| Listas desplegables y personalizaciones de entidades CDS |Sí |Hay dos opciones para importar listas desplegables o entidades CDS en un entorno: <ol><li><b>Sobrescribir</b>: si hay un recurso con el mismo nombre, esta importación lo reemplazará. Si no existe ningún un recurso que coincida, se creará un nuevo recurso. <li><b>Combinar</b>: si hay una entidad o lista de selección con el mismo nombre, se agregarán los nuevos campos o entradas, pero no se quitarán los campos o las entradas que falten.</li></ol> |
| Conectores personalizados |No |Si una aplicación depende de un conector personalizado, actualmente <b>no</b> se admite la exportación del conector como parte del paquete. <p></p> Si tiene una aplicación que depende de un conector personalizado, la única opción en este momento es volver a crear o actualizar manualmente el conector en el entorno de destino y seleccionar dicho conector al importar el paquete. |
| Conexiones |No |Si una aplicación depende de una conexión (por ejemplo, una conexión SQL con credenciales), actualmente se admite la exportación de la conexión o las credenciales como parte del paquete. <p></p> Si tiene una aplicación que depende de una conexión compartida (como SQL), la única opción en este momento es volver a crear manualmente esa conexión en el entorno de destino con las credenciales apropiadas, y seleccionar dicha conexión al importar el paquete. |
| Conjuntos de permisos y roles personalizados de CDS |No |En este momento no se admite la exportación de conjuntos de permisos o roles personalizados de CDS; la única opción es volver a crear manualmente estas entidades en el entorno de destino. |
| Puertas de enlace |No |Las puertas de enlace solo se admiten en los entornos predeterminados (y {nombre del inquilino} (en la versión preliminar)), por lo que no se pueden exportar o migrar. |
| Filas de datos CDS |No |En este momento no se admite la exportación de filas de entidades CDS; la única opción es [exportar e importar](data-platform-export-data.md) manualmente los datos después de aplicar los cambios al esquema CDS en un entorno nuevo. |

## <a name="how-do-i-get-access-to-packaging-for-my-app"></a>¿Cómo se accede al empaquetado de una aplicación?
La capacidad para exportar una aplicación está disponible para cualquier usuario con permiso para editar la aplicación.

La capacidad para importar una aplicación está disponible para cualquier usuario con permiso de "creador de entorno" en el entorno de destino.

Un usuario debe tener un plan 2 de PowerApps o una licencia de evaluación gratuita del plan 2 de PowerApps para exportar o importar cualquier aplicación.

> [!NOTE]
> Mientras el empaquetado esté en versión preliminar, todos los usuarios con una licencia válida de PowerApps podrán probarlo en sus aplicaciones y entornos.

## <a name="exporting-an-app"></a>Exportación de una aplicación
1. En http://web.powerapps.com, pulse o haga clic en **Aplicaciones**, seleccione el botón de puntos suspensivos de la aplicación que desea migrar y, a continuación, seleccione **Exportar (versión preliminar)**.
   
    ![Seleccione Exportar](./media/environment-and-tenant-migration/select-export.png)
2. Cuando se abra la página de exportación del paquete, escriba un nombre y una descripción para el paquete.
   
    ![Revisión de los detalles del paquete](./media/environment-and-tenant-migration/package-details.png)
3. En la sección “Revisar el contenido del paquete”, puede agregar también comentarios o notas, o cambiar la configuración de cómo se importará cada recurso individual en el entorno de destino durante la importación del paquete.
   
    ![Configuración del contenido del paquete](./media/environment-and-tenant-migration/export-package-content.png)

4. Cuando termine, seleccione **Exportar** y el archivo de paquete comienzará a descargarse en cuestión de segundos.

## <a name="importing-an-app"></a>Importación de una aplicación
1. En http://web.powerapps.com, haga clic o pulse **Aplicaciones** y seleccione **Importar paquete (versión preliminar)**.
   
    ![Seleccione Importar](./media/environment-and-tenant-migration/select-import.png)
2. Seleccione **Cargar** y seleccione el archivo de paquete de aplicación que va a importar.
   
    ![Selección del archivo de paquete](./media/environment-and-tenant-migration/select-file.png)
3. Una vez cargado el paquete, debe revisar el contenido del mismo y debe proporcionar datos adicionales para los elementos marcados con un icono rojo; seleccione el icono de llave inglesa para cada elemento y especifique la información necesaria.
   
    ![Revisión del contenido del paquete](./media/environment-and-tenant-migration/import-package-content.png)
4. Una vez que haya proporcionado toda la información necesaria, seleccione **Importar**.
   
    ![Actualización del contenido del paquete](./media/environment-and-tenant-migration/import-package-content-dirty.png)
5. Una vez finalizada la importación, se le redirigirá automáticamente a una página (similar a la siguiente) que describe si la operación de importación fue correcta o no.
   
    ![Revisión de los resultados de la importación](./media/environment-and-tenant-migration/import-results.png)

> [!NOTE]
>  Si va a importar una aplicación y decidió **actualizar** una aplicación existente, los nuevos cambios se guardarán como borrador de las aplicaciones.  Deberá [publicar](http://powerapps.microsoft.com/tutorials/save-publish-app/#publish-an-app) los cambios en orden para que estén disponibles todos los demás usuarios de las aplicaciones.
> 
> 

## <a name="known-limitations"></a>Limitaciones conocidas
| Limitación | Estado |
| --- | --- |
| Se ha informado de que la importación de paquetes de aplicación que contienen más de 3 recursos puede tardar varios minutos en completarse. |Se trata de un problema conocido y pronto se publicará una corrección. |

