---
title: Habilitar y deshabilitar la detección de duplicados (Common Data Service) | Microsoft Docs
description: 'Este tema ofrece información sobre cómo habilitar la detección de duplicados para todas las entidades de una organización, para una entidad específica y para operaciones específicas y cómo deshabilitar la detección de duplicados globalmente o para un tipo de entidad anulando la publicación de las reglas de detección de duplicados o eliminando las reglas publicadas.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="enable-and-disable-duplicate-detection"></a>Habilitar y deshabilitar la detección de duplicados

Este tema ofrece información sobre cómo habilitar y deshabilitar la detección de duplicados en Dynamics 365.

<a name="bkmk_enable"></a>

## <a name="enable-duplicate-detection"></a>Habilitar detección de duplicados

Antes de ejecutar la detección de duplicados, habilítela para cada una de las acciones siguientes:  
  
-   Global (para todas las entidades de la organización).  
  
-   Para una entidad.  
  
-   Para operaciones específicas.  
  
> [!NOTE]
>  Debe habilitar la detección de duplicados en las tres áreas para detectar duplicados para una entidad y para las operaciones en una entidad.  
  
### <a name="enable-duplicate-detection-globally"></a>Habilitar detección de duplicados de forma global  
  
-   Use el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> para establecer el atributo de `Organization.IsDuplicateDetectionEnabled` en `true`.
-   Consulte [Activar o desactivar reglas de detección de duplicados para toda la organización](/dynamics365/customer-engagement/admin/turn-duplicate-detection-rules-off-whole-organization) para saber cómo puede usar la interfaz de usuario para habilitar la detección de duplicados para toda la organización.
  
### <a name="enable-duplicate-detection-for-an-entity"></a>Habilitar la detección de duplicados para una entidad  
  
-   Use el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> para establecer la propiedad de <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsDuplicateDetectionEnabled> en `true`.  
  
### <a name="enable-duplicate-detection-for-specific-operations"></a>Habilitar detección de duplicados para operaciones específicas  
  
- Establezca los siguientes atributos en `true`:  
  
  - `Organization.IsDuplicateDetectionEnabledForOnlineCreateUpdate`. Cree y actualice los registros en Common Data Service mediante la aplicación web o Dynamics 365 for Outlook. Este atributo habilita o deshabilita la detección de duplicados para los registros creados o actualizados con mensajes de <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> y de <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>. Sin embargo, no afecta a los registros creados o actualizados con los métodos <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> y <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> .  
  
  - `Organization.IsDuplicateDetectionEnabledForOfflineSync`. Sincronice los registros sin conexión cuando Dynamics 365 for Outlook pase de desconectado a conectado.  
  
  - `Organization.IsDuplicateDetectionEnabledForImport`. Importe datos en masa.  
  
  > [!NOTE]
  >  No tiene que publicar reglas de detección de duplicados para habilitar la detección de duplicados para estas operaciones. Sin embargo, debe publicar reglas de detección de duplicados antes de realizar las operaciones.  

<a name="bkmk_disable"></a>

## <a name="disable-duplicate-detection"></a>Deshabilitar detección de duplicados

Deshabilite la detección de duplicados globalmente o para un tipo de entidad anulando la publicación de las reglas de detección de duplicados o eliminando las reglas publicadas.  
  
 **Deshabilitar la detección de duplicados de forma global**  
  
 Para deshabilitar la detección de duplicados globalmente, use el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> para establecer el atributo `Organization.IsDuplicateDetectionEnabled` en `false`. Esto anula automáticamente la publicación de todas las reglas de detección de duplicados para todos los tipos de entidad de la organización.  
  
 **Deshabilitar la detección de duplicados para una entidad**  
  
 Para deshabilitar la detección de duplicados para un tipo de entidad, haga lo siguiente:  
  
-   Use el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest> para establecer la propiedad de <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsDuplicateDetectionEnabled> en `false`. Esto automáticamente anula la publicación de todas las reglas de detección de duplicados para un tipo de entidad. Esto quita la compatibilidad con la detección de duplicados para el tipo de entidad y no se puede crear una nueva regla de detección de duplicados para este tipo de entidad.  
  
-   Anule la publicación de todas las reglas de detección de duplicados para un tipo de entidad usando el mensaje <xref:Microsoft.Crm.Sdk.Messages.UnpublishDuplicateRuleRequest>.  
  
**Eliminar las reglas de detección de duplicados publicadas**  
  
Elimine todas las reglas publicadas del sistema para deshabilitar la detección de duplicados globalmente o elimine las reglas publicadas para tipos específicos de entidad con el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> .  

## <a name="see-also"></a>Vea también

[Detección de duplicados](detect-duplicate-data-with-code.md)  
[Ejecutar detección de duplicados](run-duplicate-detection.md)   
[Entidades de reglas de duplicados](duplicaterule-entities.md) 