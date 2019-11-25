---
title: Crear revisiones para simplificar las actualizaciones de la solución (Common Data Service) | Microsoft Docs
description: Si se agrega una entidad a una solución y se exporta esa solución, las revisiones le ayudan a administrar las entidades y todos los activos relacionados con dichas entidades.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 24e1410afbf7323daad3e274f1aedfc4fe39ff6c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749575"
---
# <a name="create-patches-to-simplify-solution-updates"></a>Crear revisiones para simplificar las actualizaciones de la solución

Si se agrega una entidad a una solución y se exporta esa solución, la entidad y todos sus activos relacionados se exportan en esa solución. Estos activos incluyen atributos, formularios, vistas, relaciones, visualizaciones y cualquier otro activo que se empaquete con la entidad. Exportar todos los objetos significa que puede editar involuntariamente objetos en la implementación de destino, o transferir dependencias involuntarias.  
  
 Para evitarlo, puede crear y publicar revisiones de la solución que contengan subcomponentes de entidades, en lugar de publicar la entidad completa y todos sus activos.  La solución original y una o varias revisiones relacionadas se pueden consolidar (combinar) en un momento posterior en una versión actualizada de la solución, que a continuación puede reemplazar la solución original en la organización de Common Data Service de destino.  
  
## <a name="patches"></a>Revisiones  
 Puede aplicar revisiones a soluciones administradas o no administradas e incluir solo cambios en las entidades y los activos relacionados. Las revisiones no contienen componentes del sistema no personalizados ni relaciones de las que dependa porque estos componentes ya existen en la organización en la que se ha realizado la implementación. En algún momento del ciclo de desarrollo, puede consolidar todas las revisiones en una nueva versión de la solución para reemplazar la solución original desde la que se crearon las revisiones.  
  
 Las revisiones se almacenan en la base de datos de Common Data Service como registros de entidad de `Solution`. Un atributo de `ParentSolutionId` no nulo indica que la solución es una revisión. Las revisiones se pueden crear y administrar a través del Servicio de organización o las API web, que son útiles para desarrollar automatización como un script de instalación del producto. Sin embargo, la aplicación web de Common Data Service proporciona varios formularios web que le permiten crear y administrar revisiones interactivamente.  
  
- Las revisiones solo se pueden crear desde una solución primaria mediante <xref:Microsoft.Crm.Sdk.Messages.CloneAsPatchRequest> o <xref href="Microsoft.Dynamics.CRM.CloneAsPatch?text=CloneAsPatch Action" />.  
  
- El elemento primario no puede ser una revisión.  
  
- Las revisiones sólo pueden tener una solución primaria.  
  
- Una revisión crea una dependencia (en el nivel de soluciones) de su solución primaria.  
  
- Puede instalar sólo una revisión si la solución primaria está presente.  
  
- No puede instalar una revisión a menos que el nombre único y el número de versión principal o secundaria de la solución primaria, identificada por `ParentSolutionId`, no coincidan con los de la solución primaria instalada en la organización de destino.  
  
- Una versión de revisión debe tener el mismo número de versión principal o secundaria, pero un número de compilación y versión superior, que el número de versión de la solución primaria. El nombre para mostrar puede ser distinto.  
  
- Si una solución tiene revisiones, las revisiones posteriores deben tener un número de versión numérico más alto que cualquier revisión existente para esa solución.  
  
- Las revisiones admiten las mismas operaciones que las soluciones, como actualización aditiva, pero no eliminación. No puede quitar componentes de una solución con una revisión. Para quitar componentes de una solución, realice una actualización.  
  
- Las revisiones exportadas como administradas se deben importar sobre una solución primaria administrada. La regla es que la protección de revisiones (administradas o no administradas) debe coincidir con la primaria.  
  
- No use revisiones no administradas con fines de producción.  
  
- Las revisiones se admiten solo en las organizaciones de Common Data Service versión de 8.0 o superior.  
  
  Las herramientas SolutionPackager y PackageDeployer de esta versión admiten revisiones de la solución. Consulte la ayuda en línea de la herramienta para conocer las opciones de línea de comandos que estén relacionadas con revisiones.  
  
## <a name="create-a-patch"></a>Crear una revisión  
 Cree una revisión desde una solución no administrada en una organización con el mensaje <xref:Microsoft.Crm.Sdk.Messages.CloneAsPatchRequest> o <xref href="Microsoft.Dynamics.CRM.CloneAsPatch?text=CloneAsPatch Action" />, o mediante la aplicación web. Una vez creada la revisión, la solución original pasa a estar bloqueada y no es posible cambiarla o exportarla mientras haya revisiones dependientes que existan en la organización que identifica la solución como solución primaria. La versión de revisión es similar a la versión de la solución y se especifica en el siguiente formato: *major.minor.build.release.* No puede realizar cambios a las versiones principal o de menor importancia existentes de la solución cuando crea una revisión.  
  
## <a name="export-and-import-a-patch"></a>Exportar e importar una revisión  
 Puede utilizar el Servicio de organización o las API web, la aplicación web o la herramienta Package Deployer para exportar e importar una revisión. La solicitudes relevantes de mensajes del Servicio de organización son <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> y <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest>. Las acciones correspondientes para API web son <xref href="Microsoft.Dynamics.CRM.ImportSolution?text=ImportSolution Action" /> y <xref href="Microsoft.Dynamics.CRM.ExportSolution?text=ExportSolution Action" />.  
  
### <a name="patching-examples"></a>Ejemplos de revisión  
 La siguiente tabla muestra los detalles de un ejemplo de revisión. Tenga en cuenta que en este ejemplo, la solución y revisiones se importan en orden numérico y son aditivas, lo que es coherente con la importación de la solución en general.  
  
|Nombre de la revisión|Descripción|  
|----------------|-----------------|  
|SolutionA, versión 1.0 (no administrada)|Contiene entityA con 6 campos.|  
|SolutionA, versión 1.0.1.0 (no administrada)|Contiene entityA con 6 campos (3 actualizados) y agrega entityB con 10 campos.|  
|SolutionA, versión 1.0.2.0 (no administrada)|Contiene entityC con 10 campos.|  
  
 El proceso de importación es el siguiente.  
  
1.  El desarrollador o personalizador primero importa la solución base (SolutionA 1.0) en la organización. El resultado es entityA con 6 campos en la organización.  
  
2.  A continuación, se importa la revisión de la entityA 1.0.1.0. La organización contiene ahora entityA con 6 campos (3 se han actualizado), más entityB con 10 campos.  
  
3.  Finalmente, se importa la revisión SolutionA 1.0.2.0. La organización contiene ahora entityA con 6 campos (3 actualizados), entityB con 10 campos, más entityC con 10 campos.  
  
### <a name="another-patching-example"></a>Otro ejemplo de revisión  
 Veamos otro ejemplo de revisión, con los detalles que se muestran en la tabla siguiente.  
  
|Nombre de la revisión|Descripción|  
|----------------|-----------------|  
|SolutionA, versión 1.0 (solución base no administrada)|Contiene la entidad `Account` donde la longitud del campo de número de cuenta está ajustada entre 20 y 30 caracteres.|  
|SolutionB, versión 2.0 (no administrada, diferente proveedor)|Contiene la entidad `Account` donde la longitud del campo de número de cuenta está ajustada a 50 caracteres.|  
|SolutionA, versión 1.0.1.0 (no administrada, revisión)|Contiene una actualización de la entidad `Account` donde la longitud del campo de número de cuenta está ajustada a 35 caracteres.|  
  
 El proceso de importación es el siguiente:  
  
1.  El desarrollador o personalizador primero importa la solución base (SolutionA 1.0) en la organización. El resultado es una entidad de `Account` con un campo de número de cuenta de 30 caracteres.  
  
2.  Se importa SolutionB. La organización contiene ahora una entidad de `Account` con un campo de número de cuenta de 50 caracteres.  
  
3.  Se importa la revisión SolutionA 1.0.1.0. La organización contiene todavía una entidad `Account` con un campo de número de cuenta de 50 caracteres, aplicado por SolutionB.  
  
4.  Se desinstala SolutionB. La organización contiene ahora una entidad `Account` con un campo de número de cuenta de 35 caracteres, aplicado por la revisión SolutionA 1.0.1.0.  
  
## <a name="delete-a-patch"></a>Eliminar una revisión  
 Puede eliminar una solución de revisión o base (primaria) mediante <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> o, para API web, usar el método `HTTP DELETE`. El proceso de eliminación es diferente para una solución administrada o no administrada que tenga una o más revisiones existentes en la organización.  
  
 Para una solución no administrada, debe desinstalar todas las revisiones de la solución base en primer lugar, en el orden inverso de versión al que se crearon, antes de desinstalar la solución base.  
  
 Para una solución administrada, simplemente desinstale la solución base. El sistema Common Data Service automáticamente desinstala las revisiones en orden inverso de versión antes de desinstalar la solución base. También puede simplemente desinstalar una sola revisión.  
  
## <a name="update-a-solution"></a>Actualizar una solución  
 Actualizar una solución implica consolidar (combinar) todas las revisiones a esa solución en una nueva versión de la solución. Posteriormente, la solución se desbloquea y se pueden editar (solo solución no administrada) o exportar de nuevo. Para una solución administrada, no se permiten más modificaciones de la solución salvo para crear revisiones desde la solución recién actualizada. Para consolidar revisiones en una solución no administrada, use <xref:Microsoft.Crm.Sdk.Messages.CloneAsSolutionRequest> o <xref href="Microsoft.Dynamics.CRM.CloneAsSolution?text=CloneAsSolution Action" />. La clonación de una solución crea una nueva versión de la solución no administrada, incorporando todas sus revisiones, con un número de versión*major.minor* más alto, el mismo nombre único y un nombre para mostrar.  
  
 Una solución administrada se gestiona de una forma un poco diferente. Primero se clona la solución no administrada (A), incorporando todas sus revisiones y después se exporta como solución administrada (B). En la organización de destino que contiene la versión administrada de la solución (A) y sus revisiones, importe la solución administrada (B) y después ejecute <xref:Microsoft.Crm.Sdk.Messages.DeleteAndPromoteRequest> o <xref href="Microsoft.Dynamics.CRM.DeleteAndPromote?text=DeleteAndPromote Action" /> para reemplazar la solución administrada (A) y sus revisiones con la solución administrada actualizada (B) que tenga un número de versión más alto.  
  
### <a name="see-also"></a>Vea también  
 [Use soluciones y revisiones divididas en segmentos para simplificar las actualizaciones de la solución](https://technet.microsoft.com/library/mt628808.aspx)   
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Empaquetar y distribuir las extensiones con soluciones](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Entidad de solución](/reference/entities/solution.md)   
 [Mantener soluciones administradas](maintain-managed-solutions.md)   
 [Publicar la aplicación en AppSource](publish-app-appsource.md)