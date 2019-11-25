---
title: 'Vista previa: Usar variables de entorno en soluciones | MicrosoftDocs'
description: Usar variables de entorno para migrar datos de configuración de aplicaciones en soluciones.
Keywords: variables de entorno, variables, aplicación basada en modelo, datos de configuración
author: caburk
ms.author: caburk
manager: kvivek
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0c3189fceebb785a022d04c58ff6cf71fd388bc
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758300"
---
# <a name="preview-environment-variables-overview"></a>Vista previa: Información general sobre las variables de entorno 

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Las aplicaciones y los flujos requieren a menudo distintas opciones de configuración a través de entornos. Las variables de entorno como parámetros de entrada configurables permiten la administración de datos por separado en comparación valores de codificación rígida en la personalización o usando herramientas adicionales. Dado que son componentes de la solución, el rendimiento es mucho mejor que la importación de datos de configuración como datos de registro.

Beneficios de usar variables de entorno:
- No es necesario editar manualmente valores configurables en un entorno de producción.
- Configure una o más variables en un solo lugar y haga referencia a ellas como un parámetro en distintos varios componentes de la solución.
- Actualice los valores sin un cambio de código.
- Seguridad de nivel granular administrada por [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro).
- Número ilimitado de variables (el tamaño máximo de la solución es 29 MB).
- Mantenga las definiciones y los valores de forma independiente o conjuntamente.
- Con ayuda de las herramientas [SolutionPackager](/powerapps/developer/common-data-service/compress-extract-solution-file-solutionpackager) y [DevOps](/powerapps/developer/common-data-service/build-tools-overview) habilite la integración continua y la entrega continua (CI/CD).
- Compatibilidad para localización.
- Se puede usar para controlar marcas de características y otras configuraciones de la aplicación.

> [!IMPORTANT]
> - Esta es una característica de vista previa.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 

## <a name="how-they-work"></a>¿Cómo funcionan?
Las variables de entorno se pueden crear y administrar en la interfaz de la solución moderna o [mediante código](https://docs.microsoft.com/powerapps/developer/common-data-service/work-with-data-cds). Un archivo JSON aparte se crea en la paquete de solución para los valores, que también se puede administrar en control de código fuente y modificar en una canalización de compilación. Se admite la exportación e importación de Excel. Después de crear variables de entorno, puede usarlas como entradas en complementos, flujos y otros componentes.

## <a name="default-value"></a>Valor predeterminado
Este campo forma parte de la entidad de definición de variables de entorno y no es obligatorio. Defina un valor predeterminado para entornos de producción o cuando los valores no deban cambiar para diferentes entornos.

## <a name="value"></a>Valor
También conocido como valor actual o valor de reemplazo, este campo es opcional y es parte de la entidad de valores de variable de entorno. Establezca el valor cuando desee reemplazar el valor predeterminado en el entorno actual. Quite el valor de la solución si no desea usarlo en el siguiente entorno. Los valores también se separarán en un archivo JSON aparte en el archivo solution.zip que se exporta. 

>[!NOTE]
> Un valor no puede existir sin una definición. La interfaz sólo permite la creación de un valor por definición. 

La separación del valor predeterminado y el valor actual permite mantener la definición y el valor predeterminado por separado del valor actual. También permite que extendamos la funcionalidad en el futuro para dar compatibilidad con varios valores de ámbito de un contexto específico en tiempo de ejecución.

## <a name="notifications"></a>Notificaciones
Se muestra una notificación cuando las variables de entorno no tienen valores. Este es un aviso para establecer los valores de modo que no fallen los componentes dependientes de variables. También permite que los partners entreguen variables sin valores y se solicite al cliente que especifique los valores.

>[!NOTE]
> Se recomienda a partners crear sus propias interfaces que requieran que los clientes proporcionen los valores. Las notificaciones ayudan a evitar errores si se salta este paso. 

## <a name="security"></a>Seguridad
Las entidades environmentvariabledefinition y environmentvariablevalue son [propiedad del usuario o del equipo](https://docs.microsoft.com/powerapps/maker/common-data-service/types-of-entities). Al crear una aplicación que usa variables de entorno, asegúrese de asignar usuarios el nivel adecuado de permiso. Más información: [Seguridad en Common Data Service](https://docs.microsoft.com/power-platform/admin/wp-security). 

## <a name="current-limitations"></a>Limitaciones actuales
- Almacenamiento en caché. Los complementos deberán ejecutar una consulta para capturar los valores. 
- Las aplicaciones de lienzo y los flujos pueden consumir variables de entorno al igual que datos de registro de la entidad. En el futuro planeamos crear acciones adicionales en diseñadores de aplicaciones de lienzo y flujos. Esto simplificará la creación y aportará mejor visibilidad de las variables de entorno que está usando una aplicación o un flujo específicos.
- Integración de Azure Key Vault para administración de secretos. Las variables de entorno actuales no deben usarse para almacenar datos seguros como contraseñas y claves.
- Los tipos de datos se validan en la interfaz de la solución moderna solo, pero no actualmente en el servidor durante la vista previa. 
- No se aplican dependencias para algunos tipos de componentes.
- Si usa Excel para importar variables de entorno, asegúrese de anteponer el prefijo del editor a SchemaName.

### <a name="see-also"></a>Vea también
[Use complementos para ampliar los procesos de negocio](https://docs.microsoft.com/powerapps/developer/common-data-service/plug-ins) </BR>
[Ejemplos de la API web](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/web-api-samples) </BR>
[Crear aplicación de lienzo desde cero mediante Common Data Service.](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) </BR>
[Crea un flujo con Common Data Service](https://docs.microsoft.com/flow/connection-cds)
