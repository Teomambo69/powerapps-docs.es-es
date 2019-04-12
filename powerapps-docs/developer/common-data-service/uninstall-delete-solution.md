---
title: Desinstalación o eliminar una solución (Common Data Service) | Microsoft Docs
description: Este documento describe cómo funcionan las acciones de desinstalación y eliminación de soluciones administradas y no administradas en Dynamics 365
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
---
# <a name="uninstall-or-delete-a-solution"></a>Desinstalar o eliminar una solución

Puede eliminar las soluciones administradas y no administradas de la misma manera, pero las acciones resultantes son muy diferentes. Si elimina una solución administrada desinstalará la solución administrada.  
  
<a name="BKMK_DeleteSolution"></a>   
## <a name="delete-a-solution"></a>Eliminar una solución  
 Según el tipo de solución que desee eliminar, verá uno de los siguientes mensajes **Confirmar eliminación**:  
  
 **Solución administrada**  
 "Va a eliminar una solución administrada. La solución y todos sus componentes se eliminarán. Esta acción no se puede deshacer. La desinstalación de esta solución podría tardar varios minutos. No se puede cancelar la desinstalación una vez iniciada. ¿Desea continuar?"  
  
 **Solución no administrada**  
 "Va a eliminar una solución no administrada. La solución se eliminará pero no se eliminarán los componentes incluidos en esta solución. Esta acción no se puede deshacer. ¿Desea continuar?"  
  
 Para eliminar una solución en forma de programa use el método de <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>. . Más información: [Eliminar una solución](work-solutions.md#BKMK_DeleteSolution)  
  
<a name="BKMK_UinstallAManagedSolution"></a>   
### <a name="uninstall-a-managed-solution"></a>Desinstalar una solución administrada  
 Si elimina una solución administrada se desinstalará la solución. Se eliminarán todos los componentes de la solución definidos en la solución.  
  
> [!IMPORTANT]
>  Cuando desinstala una solución administrada, se pierden los siguientes datos: datos almacenados en las entidades personalizadas que forman parte de la solución y datos almacenados en atributos personalizados en las entidades del sistema que forman parte de la solución.  
  
<a name="BKMK_DeleteUnmanagedSolution"></a>   
### <a name="delete-an-unmanaged-solution"></a>Eliminar una solución no administrada  
 Una solución no administrada es un grupo de componentes de la solución. La eliminación de la solución elimina un registro de solución único en la base de datos. Los componentes de la solución no se verán afectados por la eliminación de la solución, permanecen en el sistema.  
  
<a name="BKMK_AccessSolutionsGridWithUrl"></a>   
## <a name="access-the-solutions-list-with-a-url"></a>Acceso a la lista de soluciones con una dirección URL  
 Si necesita navegar directamente a la lista de soluciones puede usar la siguiente dirección URL:  
  
```http
<organization root url>/tools/Solution/home_solution.aspx?etn=solution  
```  
  
### <a name="see-also"></a>Vea también  
 [Empaquetar y distribuir extensiones](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Eliminar una solución](work-solutions.md#BKMK_DeleteSolution)   
 [Introducción a las soluciones](introduction-solutions.md)   
 [Planificación del desarrollo de soluciones](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Componentes de la solución y seguimiento de las dependencias](dependency-tracking-solution-components.md)   
 [Creación de una solución administrada](create-install-update-managed-solution.md#BKMK_CreateManagedSolution)   
 [Exportar una solución no administrada](create-export-import-unmanaged-solution.md#BKMK_UnmanagedSolution)   
 [Importar una solución no administrada](create-export-import-unmanaged-solution.md#BKMK_ImportUnmanagedSolution)   
 [Creación de una solución administrada](create-install-update-managed-solution.md#BKMK_CreateManagedSolution)   
 [Crear soluciones que admitan varios idiomas](create-solutions-support-multiple-languages.md)   
 [Instalar una solución administrada](create-install-update-managed-solution.md#BKMK_InstallManagedSolution)
