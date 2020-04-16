---
title: Crear, instalar y actualizar una solución administrada (Common Data Service) | Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 0b532294163233f8eefd06851b1cb142f931eb4d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156364"
---
# <a name="create-install-and-update-a-managed-solution"></a>Crear, instalar y actualizar una solución administrada

Cree una solución administrada exportando una solución no administrada como solución administrada. Las organizaciones que usen su solución administrada instalarán esta y cualquier actualización que cree para ella.  
  
 Más información: [Usar soluciones para las personalizaciones](/dynamics365/customer-engagement/customize/use-solutions-for-your-customizations).  
  
<a name="BKMK_CreateManagedSolution"></a>   

## <a name="create-a-managed-solution"></a>Creación de una solución administrada  
 Para poder crear una solución administrada primero debe crear una solución no administrada. Para obtener más información acerca de cómo crear una solución no administrada, consulte [Creación de una solución no administrada](create-export-import-unmanaged-solution.md#BKMK_CreateUnmanagedSolution).  
  
 Para crear una solución administrada, seleccione la opción **Administrada** en el cuadro de diálogo **Tipo de paquete** al exportar la solución.  
  
 Una solución administrada solo incluye los componentes de la solución personalizables que se hayan personalizado. Esto no solo evita el cambio involuntario de los componentes de la solución existentes en el sistema donde está instalada la solución, sino que también mantiene más pequeño el tamaño de la solución administrada.  
  
 Antes del último paso de creación de una solución administrada, debe decidir si hay algunas capacidades de personalización que no desea no permitir que lleven a cabo los usuarios que instalan la solución administrada. Cada componente de la solución contiene un conjunto de propiedades administradas que controlan las capacidades de personalización que desea permitir. La configuración predeterminada permite todas las capacidades de personalización. Más información: [Usar propiedades administradas](use-managed-properties.md)  
  
 Puede crear una solución administrada mediante programación con el mensaje <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest>. Más información: [Exportar o empaquetar una solución](work-solutions.md#BKMK_ExportPackageSolution)  
  
> [!IMPORTANT]
>  No debe volver a importar una solución administrada a la organización que usó para crearla.  
  
<a name="BKMK_InstallManagedSolution"></a>   

## <a name="install-a-managed-solution"></a>Instalar una solución administrada  
 Una solución administrada se instala del mismo modo en que se importa una solución no administrada. La diferencia está en cómo se ha empaquetado la solución.  
  
> [!IMPORTANT]
>  La instalación de una solución o la publicación de personalizaciones puede interferir en el funcionamiento normal del sistema. Se recomienda programar importaciones de la solución cuando menos afecte a los usuarios.  
  
 Si la solución no se importó correctamente, puede hacer clic en el cuadro de diálogo **Descargar registro** para descargar un informe que proporciona información acerca de los errores producidos que impidieron la importación correcta de la solución administrada. Este archivo es un documento XML configurado para abrirse con Office Excel.  
  
 Puede importar o actualizar una solución administrada mediante programación con el mensaje <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest>. Cuando se usa este mensaje, puede solicitar una referencia a un registro de entidad `ImportJob` que incluirá los detalles del éxito de la importación. Más información: [Instalar o actualizar una solución](work-solutions.md#BKMK_InstallUpgradeSolution).  
  
 El mensaje <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> se puede llamar con <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest>. Más información: [Ejecutar mensajes en segundo plano (asincrónicamente)](/dynamics365/customer-engagement/developer/org-service/use-messages-request-response-classes-execute-method#bkmk_executeasync).  
  
 Existen límites en cuanto al tamaño de una solución que puede instalar. Más información: [Tamaño máximo de la solución que se va a importar](create-export-import-unmanaged-solution.md#BKMK_MaxSizeOfSolution)  
  
<a name="BKMK_UpdateManagedSolution"></a>   

### <a name="update-a-managed-solution"></a>Actualizar una solución administrada  
 Al instalar una solución administrada que ya existe en la organización, el diálogo para importar la solución ofrecerá las siguientes opciones:  
  
 **Mantener personalizaciones (recomendado)**  
 Esta opción mantiene las personalizaciones no administradas realizadas en los componentes, pero también implica que algunas de las actualizaciones incluidas en esta solución no surtirán efecto.  
  
 **Sobrescribir personalizaciones**  
 Esta opción sobrescribe las personalizaciones no administradas realizadas anteriormente en los componentes incluidos en esta solución. Todas las actualizaciones incluidas en esta solución surtirán efecto.  
  
> [!NOTE]
>  Se recomienda que indique a los usuarios que instalan la solución administrada que usen la opción **Sobrescribir personalizaciones** para investigar problemas en los que las personalizaciones entran en conflicto con el comportamiento de las soluciones. Siempre deben exportar las soluciones no administradas en primer lugar, de modo que puedan volver a aplicarlas si es necesario.  
  
### <a name="see-also"></a>Vea también  
 [Empaquetar y distribuir extensiones con soluciones de Dynamics 365](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Introducción a las soluciones](introduction-solutions.md)   
 [Planificación del desarrollo de soluciones](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Componentes de la solución y seguimiento de las dependencias](dependency-tracking-solution-components.md)   
 [Crear, exportar o importar una solución no administrada](create-export-import-unmanaged-solution.md)   
 [Desinstalar o eliminar una solución](uninstall-delete-solution.md)   
 [Esquema de archivo de soluciones de personalización](/dynamics365/customer-engagement/developer/customize-dev/customization-solutions-file-schema)
