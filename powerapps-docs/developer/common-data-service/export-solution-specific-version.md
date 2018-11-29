---
title: Exportación de una solución para una versión específica (Common Data Service para aplicaciones) | Microsoft Docs
description: Obtenga información sobre cómo obtener y administrar la versión de Dynamics 365 para la que desea exportar una solución
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
# <a name="export-a-solution-for-a-specific-version"></a>Exportación de una solución para una versión específica

> [!NOTE]
>  Este tema describe una funcionalidad que está disponible para actualizaciones de versiones secundarias a versiones principales de Common Data Service para aplicaciones. Esta característica no está disponible para la versión inicial de CDS for Apps, pero lo estará cuando la versión secundaria actualice funcionalidad adicional incluida.  

 Cada nueva versión de CDS for Apps contendrá las funcionalidades que no se encuentran en versiones anteriores. Las soluciones que usan nuevas funcionalidades no se pueden importar a una organización con una versión anterior. Las soluciones exportadas de organizaciones con una versión anterior se pueden importar a organizaciones con una versión más reciente.  

 Después de actualizar a la organización que se usa para definir la solución, aún podrá exportar una solución que apunte a una versión anterior. Cuando se selecciona una versión inferior de destino, los componentes de la solución que dependen de las funcionalidades introducidas desde esa versión no se incluirán en la solución exportada.  

> [!NOTE]
>  No se puede seleccionar una versión anterior cuando se exporta la solución predeterminada.  

<a name="BKMK_ExportSolutionForVersion"></a>   

## <a name="target-a-specific-version-when-you-export-a-solution"></a>Diríjase a una versión específica cuando exporte una solución  
 Cuando se exporta una solución de CDS for Apps tendrá la opción de seleccionar la solución para una versión determinada de Dynamics 365. Para la versión de 8.2.0.0 de Dynamics 365 las opciones son 8.2 (valor predeterminado), 8.1 y 8.0. Cuando se selecciona 8.0, las nuevas funcionalidades introducidas en la 8.1.0.0 no se incluirán en la solución exportada y cualquier organización que siga utilizando versiones anteriores de 8.1.0.0 podrá instalar la solución.  

 Cuando exporta la solución para dirigirse a una versión anterior, el diálogo de exportación puede mostrar dos mensajes posibles:  

 **Esta solución admite la versión de Dynamics 365 de destino**  
 Esto significa que los componentes de solución de su solución no dependen de las funcionalidades ni de los componentes de la solución introducidos desde la versión.  

 **Los siguientes componentes se quitaron o modificaron como parte de la exportación**  
 Debajo de este mensaje aparece una tabla en la que se muestran los elementos de componentes de la solución que se modificaron o no se incluyeron en la solución exportada.  

 La información visible en el diálogo se puede encontrar también en el archivo de la solución exportada. Cuando se exporta una solución para dirigirse a una versión determinada, el nombre del archivo especifica la solución de destino mediante la siguiente convención de nomenclatura:*Solution Name*<em>*Solution_Version_Number*_target_CRM\\</em>*Target Dynamics 365 version number*.zip. Por ejemplo, una solución no administrada con el nombre Sample Solution con la versión de solución 2.0 que se exporta para dirigirse a la versión 8.0 tendrá el nombre SampleSolution_2_0_target_CRM_8.0.zip. Cuando extraiga el contenido de este archivo comprimido encontrará un archivo filteredcomponents.xml con los datos que detallan qué acciones se realizaron. Puede abrir este archivo mediante Excel para ver un informe de qué componentes de la solución se modificaron o se quitaron.  

<a name="BKMK_Changes"></a>   

## <a name="what-changes-are-applied-to-a-solution-exported-for-an-earlier-version"></a>¿Qué cambios se aplican a una solución exportada para una versión anterior?  
 A partir de la versión 6.0.0.0 de Dynamics 365, cada tipo de componente de la solución tiene una propiedad `IntroducedVersion`. Este valor captura el número de versión actual de la solución con la que se asoció el componente de la solución cuando se creó. Todos los componentes de la solución introducidos por Microsoft forman parte de una solución oculta del sistema donde el número de versión se corresponde con la versión de CDS for Apps.  

<!--
| IntroducedVersion Value |                                                             Solution components introduced                                                             |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|         5.0.0.0         | Before [!INCLUDE[pn_crm_2013_shortest](../includes/pn-crm-2013-shortest.md)] and [!INCLUDE[pn_crm_online_fall13](../includes/pn-crm-online-fall13.md)] |
|         6.0.0.0         |    [!INCLUDE[pn_crm_2013_shortest](../includes/pn-crm-2013-shortest.md)] and [!INCLUDE[pn_crm_online_fall13](../includes/pn-crm-online-fall13.md)]     |
|         6.1.0.0         |     [!INCLUDE[pn_crm_2013_sp](../includes/pn-crm-2013-sp.md)] and [!INCLUDE[pn_v6_online_ur1_shortest](../includes/pn-v6-online-ur1-shortest.md)]      |
|         7.0.0.0         |                                  [!INCLUDE[pn_crm_2015_and_online_full](../includes/pn-crm-2015-and-online-full.md)]                                   |
|         7.1.0.0         |                                  [!INCLUDE[pn_crm_online_2015_update_1](../includes/pn-crm-online-2015-update-1.md)]                                   |
|         8.0.0.0         |               [!INCLUDE[pn_crm_online_2016_update_shortest](../includes/pn-crm-online-2016-update-shortest.md)] and CRM 2016 on-premises               |
|         8.1.0.0         |          [!INCLUDE[pn_crm_8_1_0_online](../includes/pn-crm-8-1-0-online.md)] and [!INCLUDE[pn_crm_8_1_0_op](../includes/pn-crm-8-1-0-op.md)]           |
|         8.2.0.0         |                                            [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]                                             |
|         9.0.0.0         |                                          [!INCLUDE[pn_crm_9_0_0_online](../includes/pn-crm-9-0-0-online.md)]                                           |
-->

 Se usan los datos de `IntroducedVersion` al exportar la solución para que coincida con la versión de destino. Esto puede provocar tres acciones posibles:  

 **Quitar**  
 No se agregarán a la solución los componentes de la solución que no existían en la versión de destino o que contienen dependencias de los componentes que no pueden funcionar con la versión de destino.  

 **Modificar**  
 Cuando un componente de la solución tiene una dependencia de un componente de la solución que se ha quitado, cuando sea posible, el componente de la solución se modificará para quitar la dependencia. Por ejemplo, si una definición del formulario hace referencia a un atributo que no existía en la versión, el formulario se modificará para quitar la referencia. Si el componente de la solución no se puede modificar para quitar la dependencia, se quitará el componente de la solución.  

 **Reemplazar**  
 Cuando un componente de la solución existía en la versión de destino pero se modificó para tener una dependencia de un componente de la solución que se eliminará, dicho componente de la solución puede ser reemplazado con la definición del componente de la solución que se definió para la versión de destino.  

<a name="BKMK_TargetVersion"></a>   

## <a name="select-a-target-version-programmatically"></a>Seleccione una versión de destino mediante programación  

 Use <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> para exportar una solución mediante programación. Desde la versión 6.0.0.0 de Dynamics 365 este mensaje tiene una nueva propiedad opcional <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest.TargetVersion>`String` que puede usar para ajustar a “8.0.0.0” si desea exportar a la versión anterior.  

### <a name="see-also"></a>Vea también  
 [Empaquetar y distribuir las extensiones con soluciones](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Crear, exportar o importar una solución no administrada](create-export-import-unmanaged-solution.md)   
 [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)   
 [Mantener soluciones administradas](maintain-managed-solutions.md)   
 [Manual de personalización: Usar soluciones para las personalizaciones](http://go.microsoft.com/fwlink/p/?LinkID=322003)
