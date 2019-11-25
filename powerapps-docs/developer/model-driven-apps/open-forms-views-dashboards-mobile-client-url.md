---
title: Abrir formularios, vistas y paneles en el cliente móvil de Dynamics 365 con una dirección URL (aplicaciones basadas en modelos) | Microsoft Docs
description: Use el nuevo controlador de aplicaciones para que los clientes móviles de Dynamics 365 se vinculen directamente a los formularios, las vistas y los paneles de Dynamics 365 desde aplicaciones externas de modo que al hacer clic en el vínculo de una aplicación externa, el elemento de destino se abra en Dynamics 365 para smartphones o en Dynamics 365 para tabletas.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0c4e3c0fe4188b3b9f2d95cb479a23f6e54c193b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749421"
---
# <a name="open-forms-views-and-dashboards-in-mobile-client-with-a-url"></a>Abrir formularios, vistas y paneles en el cliente móvil con una dirección URL

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/open-forms-views-dashboards-mobile-client-url

At this point I understand this mobile client is still branded as 'Dynamics 365'
 -->
 
 Use el nuevo controlador de aplicaciones para que los clientes móviles se vinculen directamente a los formularios, las vistas y los paneles de desde aplicaciones externas de modo que al hacer clic en el vínculo de una aplicación externa, el elemento de destino se abra en Dynamics 365 for phones o en Dynamics 365 for tablets. También puede abrir un formulario vacío para crear un registro de entidad.  
  
 Si ya ha iniciado sesión en la instancia de Dynamics 365 for phones o Dynamics 365 for tablets, el registro de destino se muestra en el cliente móvil al hacer clic en el vínculo en la aplicación externa. De lo contrario, le pide iniciar sesión en su instancia en el cliente móvil y, al hacerlo, se muestra el elemento de destino. Debe tener Dynamics 365 for phones o Dynamics 365 for tablets instaladas en su dispositivo móvil para usar esta característica.  
  
<a name="Parameters"></a>

## <a name="query-string-parameters-for-the-url"></a>Parámetros de cadena de consulta para la dirección URL

 Use los siguientes parámetros del controlador de aplicaciones y cadena de consulta para crear la dirección URL.  
  
```  
ms-dynamicsxrm://?pagetype=<VALUE>&etn=<VALUE>&id=<VALUE>  
```  
  
 Se utilizan los parámetros de cadena de consulta que se muestran en la tabla siguiente.  
  
|Parámetro de cadena de consulta|Descripción|  
|----------------------------|-----------------|  
|pagetype|Especifique el tipo de página para abrir. Los valores válidos son `entity`, `view`, `dashboard`, y `create`.<br /><br /> Este parámetro es necesario.|  
|etn|Especifique el nombre lógico de la entidad para la que desea abrir o crear un registro.  El nombre lógico de las entidades está en minúsculas, y se define en <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.LogicalName>. .<br /><br /> Se requiere este parámetro si el parámetro `pagetype` se establece en `entity`, `view` o `create`.|  
|identificador|Especifique el Id. del registro de entidad, vista o panel que desea abrir.<br /><br /> Se requiere este parámetro si el parámetro `pagetype` se establece en `entity` o `dashboard`.<br /><br /> Es opcional si el parámetro `pagetype` se establece en `view`. Si no especifica el Id. de la vista, se muestra la vista predeterminada para la entidad especificada en el parámetro `etn`.|  
  
<a name="Example"></a>

## <a name="example-urls"></a>Direcciones URL de ejemplo

 Estas son algunas direcciones URL de ejemplo para abrir formularios, vistas y paneles.  
  
|Acción|Dirección URL de ejemplo|  
|------------|-----------------|  
|Abrir una entidad de cuenta con Id. del registro de cuenta como 91330924-802A-4B0D-A900-34FD9D790829|`ms-dynamicsxrm://?pagetype=entity&etn=account&id=91330924-802A-4B0D-A900-34FD9D790829`|  
|Abrir una vista con Id. de registro de vista como 899D4FCF-F4D3-E011-9D26-00155DBA3819 para la entidad de contacto|`ms-dynamicsxrm://?pagetype=view&etn=contact&id=899D4FCF-F4D3-E011-9D26-00155DBA3819`|  
|Abrir una vista predeterminada para la entidad de cuenta|`ms-dynamicsxrm://?pagetype=view&etn=account`|  
|Abrir un panel con Id. de registro de panel como 2E3D0841-FA6D-DF11-986C-00155D2E3002|`ms-dynamicsxrm://?pagetype=dashboard&id=2E3D0841-FA6D-DF11-986C-00155D2E3002`|  
|Abrir un formulario para crear un registro de cuenta|`ms-dynamicsxrm://?pagetype=create&etn=account`|  
  
### <a name="see-also"></a>Vea también

 [Abrir formularios, vistas, diálogos e informes con una dirección URL](open-forms-views-dialogs-reports-url.md)  
 [Ampliar el cliente](/dynamics365/customer-engagement/developer/extend-client)
