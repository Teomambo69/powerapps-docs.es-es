---
title: Migración de aplicaciones entre entornos e inquilinos | Microsoft Docs
description: Tutorial sobre cómo migrar aplicaciones de PowerApps entre entornos e inquilinos
author: jamesol-msft
manager: kvivek
ms-topic: conceptual
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 651301dafa17c6ec159d462f018d6ec1984485ba
ms.sourcegitcommit: 7403ea7f103564fa7d1ae73a08a7dbdfeba7d999
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2018
ms.locfileid: "43263453"
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
| Conectores personalizados |No |Si una aplicación depende de un conector personalizado, actualmente <b>no</b> se admite la exportación del conector como parte del paquete. <p></p> Si tiene una aplicación que depende de un conector personalizado, la única opción en este momento es volver a crear o actualizar manualmente el conector en el entorno de destino y seleccionar dicho conector al importar el paquete. |
| Conexiones |No |Si una aplicación depende de una conexión (por ejemplo, una conexión SQL con credenciales), actualmente se admite la exportación de la conexión o las credenciales como parte del paquete. <p></p> Si tiene una aplicación que depende de una conexión compartida (como SQL), la única opción en este momento es volver a crear manualmente esa conexión en el entorno de destino con las credenciales apropiadas, y seleccionar dicha conexión al importar el paquete. |
| Personalizaciones de CDS |No |La exportación de personalizaciones de CDS ya no se admite como parte del empaquetado. Ahora esto se admite a través de la exportación e importación de la solución predeterminada de entorno, como se describe en el artículo siguiente. |
| Puertas de enlace |No |Las puertas de enlace solo se admiten en los entornos predeterminados (y {nombre del inquilino} (en la versión preliminar)), por lo que no se pueden exportar o migrar. |

## <a name="how-do-i-get-access-to-packaging-for-my-app"></a>¿Cómo se accede al empaquetado de una aplicación?
La capacidad para exportar una aplicación está disponible para cualquier usuario con permiso para editar la aplicación.

La capacidad para importar una aplicación está disponible para cualquier usuario con permiso de "creador de entorno" en el entorno de destino.

Un usuario debe tener un plan 2 de PowerApps o una licencia de evaluación gratuita del plan 2 de PowerApps para exportar o importar cualquier aplicación.

> [!NOTE]
> Mientras el empaquetado esté en versión preliminar, todos los usuarios con una licencia válida de PowerApps podrán probarlo en sus aplicaciones y entornos.

## <a name="exporting-an-app"></a>Exportación de una aplicación
1. En http://web.powerapps.com, pulse o haga clic en **Aplicaciones**, haga clic en el botón de puntos suspensivos de la aplicación que quiere migrar y, después, haga clic en **Exportar (versión preliminar)**.

    ![Seleccione Exportar](./media/environment-and-tenant-migration/select-export.png)
2. Cuando se abra la página de exportación del paquete, escriba un nombre y una descripción para el paquete.

    ![Revisión de los detalles del paquete](./media/environment-and-tenant-migration/package-details.png)
3. En la sección “Revisar el contenido del paquete”, puede agregar también comentarios o notas, o cambiar la configuración de cómo se importará cada recurso individual en el entorno de destino durante la importación del paquete.

    ![Configuración del contenido del paquete](./media/environment-and-tenant-migration/export-package-content.png)

4. Cuando termine, seleccione **Exportar** y el archivo de paquete comienzará a descargarse en cuestión de segundos.

## <a name="importing-an-app"></a>Importación de una aplicación
1. En http://web.powerapps.com, pulse o haga clic en **Aplicaciones** y, después, en **Importar paquete (versión preliminar)**.

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

## <a name="exporting-cds-customizations-and-model-driven-apps"></a>Exportación de personalizaciones de CDS y aplicaciones controladas por modelos
La exportación de cualquier personalización de entidad o conjunto de opciones, o de las aplicaciones controladas por modelos que se hayan creado en https://web.powerapps.com se admite mediante la exportación de la solución de entorno predeterminada como sigue:
> [!NOTE]
>  Si quiere obtener más información sobre las soluciones de PowerApps, vea [Introduction to solutions](../developer/common-data-service/introduction-solutions.md) (Introducción a las soluciones).
>
>

1. En http://web.powerapps.com, seleccione el modo de diseño **Basado en modelos (versión preliminar)** en su entorno.

    ![Seleccionar el modo de diseño Basado en modelos](./media/environment-and-tenant-migration/select-model-driven.png)

2. Haga clic en **Opciones avanzadas** en la barra de navegación de la izquierda para iniciar el Explorador de soluciones para la solución predeterminada de este entorno.

    ![Hacer clic en Opciones avanzadas](./media/environment-and-tenant-migration/select-advanced.png)

3. Haga clic en **Exportar solución** y complete los pasos necesarios.  En cuestión de segundos se iniciará la descarga de un archivo de paquete de solución.

    ![Seleccione Exportar](./media/environment-and-tenant-migration/select-export-solution.png)

## <a name="importing-cds-customization-and-model-driven-apps"></a>Importación de personalizaciones de CDS y aplicaciones controladas por modelos
Desafortunadamente, la importación de un paquete de solución de CDS requiere una solución alternativa manual en la experiencia, en la que estamos trabajando activamente para corregirla:

1. En http://web.powerapps.com, seleccione el modo de diseño **Basado en modelos (versión preliminar)** en su entorno.

    ![Seleccionar el modo de diseño Basado en modelos](./media/environment-and-tenant-migration/select-model-driven.png)

2. Haga clic en **Opciones avanzadas** en la barra de navegación de la izquierda para iniciar el Explorador de soluciones para la solución predeterminada de este entorno.

    ![Hacer clic en Opciones avanzadas](./media/environment-and-tenant-migration/select-advanced.png)

3. Copie la dirección URL desde el explorador, realice los cambios siguientes y, después, vaya a la nueva dirección URL en el explorador:

    * Estructura actual de la dirección URL: `https://{orguniquename}.crm.dynamics.com/tools/solution/edit.aspx?id={solutionname}`

        ![Editar la dirección URL](./media/environment-and-tenant-migration/edit-url.png)

    * Nueva estructura de la dirección URL: `https://{orguniquename}.crm.dynamics.com/tools/solution/SolutionImportWizard.aspx`

        ![Selección del paquete](./media/environment-and-tenant-migration/select-package.png)

4. Seleccione el archivo de paquete de solución de CDS que quiera importar y complete el asistente.

5. Si la importación se realiza correctamente, verá el cuadro de diálogo de confirmación siguiente. Para que los cambios en la solución estén disponible para otros personalizadores dentro del entorno, haga clic en **Publicar todas las personalizaciones**.

    ![Importación correcta](./media/environment-and-tenant-migration/successful-import.png)
