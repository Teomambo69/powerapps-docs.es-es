---
title: Recuperar metadatos publicados | MicrosoftDocs
description: La recuperación de metadatos no publicados no solo agregará sobrecarga al procesamiento de la solicitud, con un rendimiento inferior, pero también puede devolver metadatos que no espera el solicitante.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5600d4225868dc67096dc3f72ee30b3166ed30d5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749385"
---
# <a name="retrieve-published-metadata"></a>Recuperar metadatos publicados

**Categoría**: rendimiento, uso

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Recuperar metadatos no publicados podría causar:

- Rendimiento más lento
- Confusión para los usuarios

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

No es común recuperar personalizaciones sin publicar y en raras ocasiones tendrá necesidad de recuperar esas personalizaciones.

Un ejemplo donde necesitaría recuperar personalizaciones sin publicar es si desea crear una aplicación para editar metadatos personalizables.  Por ejemplo, si fuera a crear un editor de metadatos personalizables, debe recuperar cualquier definición sin publicar de esos elementos. Si un desarrollador define algunos cambios pero no los publica, la aplicación debe poder recuperarlos para asegurarse de que el programador está recuperando las personalizaciones desarrolladas más recientemente. Si no es así, podría resultar en la pérdida de personalizaciones sin publicar.

Sin embargo, si no está creando un editor o no tiene una necesidad explícita de recuperar definiciones sin publicar, entonces recupere solo las que están publicadas. Los ejemplos siguientes muestran cómo recuperar personalizaciones publicadas:

### <a name="default-behavior"></a>Comportamiento predeterminado

De forma predeterminada, la recuperación de metadatos solo obtendrá personalizaciones publicadas

```csharp
public RetrieveAllEntitiesAttributesResponse GetAllEntitiesImplicit(IOrganizationService service)
{
    var request = new RetrieveAllEntitiesRequest();
    request.EntityFilters = EntityFilters.Attributes;

    return service.Execute(request) as RetrieveAllEntitiesAttributesResponse;
}
```

### <a name="explictly-controlling-the-behavior"></a>Controlar el comportamiento explícitamente

Se establece de forma explícita la propiedad `RetrieveAsIfPublished` para recuperar solo personalizaciones publicadas

```csharp
public RetrieveAllEntitiesAttributesResponse GetAllEntitiesExplicit(IOrganizationService service)
{
    var request = new RetrieveAllEntitiesRequest()
    {
        RetrieveAsIfPublished = false
        EntityFilters = EntityFilters.Attributes
    };

    return service.Execute(request) as RetrieveAllEntitiesAttributesResponse;
}
```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

Las siguientes operaciones permiten recuperar metadatos no publicados con el parámetro `RetrieveAsIfPublished`:

- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllOptionSetsRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveOptionSetRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityKeyRequest>

Los ejemplos de recuperación de personalizaciones sin publicar se documentan a continuación:

> [!WARNING]
> Estos escenarios deben evitarse.

```csharp
public RetrieveEntityKeyResponse GetEntityKey(IOrganizationService service, string entityName, string keyName)
{
    var request = new RetrieveEntityKeyRequest()
    {
        EntityLogicalName = entityName,
        LogicalName = keyName,
        RetrieveAsIfPublished = true
    };

    return service.Execute(request) as RetrieveEntityKeyResponse;
}

public RetrieveRelationshipResponse GetRelationship(IOrganizationService service, Guid id)
{
    var request = new RetrieveRelationshipRequest()
    {
        MetadataId = id,
        RetrieveAsIfPublished = true
    };

    return service.Execute(request) as RetrieveRelationshipResponse;
}

public RetrieveEntityAttributesResponse GetEntity(IOrganizationService service, Guid id)
{
    var request = new RetrieveEntityRequest()
    {
        MetadataId = id,
        RetrieveAsIfPublished = true,
        EntityFilters = EntityFilters.Attributes
    };

    return service.Execute(request) as RetrieveEntityAttributesResponse;
}
```

## <a name="web-api-functions"></a>Funciones de la API web

Estas instrucciones también se aplican a las siguientes funciones de la API web:

- <xref href="Microsoft.Dynamics.CRM.RetrieveAllEntities?text=RetrieveAllEntities Function" />
- <xref href="Microsoft.Dynamics.CRM.RetrieveEntity?text=RetrieveEntity Function" />

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

El servicio de Microsoft Dynamics 365 permite recuperar determinados metadatos que estén publicados o sin publicar. Desde Dynamics CRM 2011, los metadatos publicados se devuelven, de forma predeterminada, desde la memoria caché de los metadatos en la aplicación a menos que el programador establezca de forma predeterminada el valor de la propiedad `RetrieveAsIfPublished` en `true`.

La recuperación de metadatos no publicados no solo agregará sobrecarga al procesamiento de la solicitud, con un rendimiento inferior, pero también puede devolver metadatos que no espera el solicitante. Por ejemplo, recuperar los metadatos del conjunto de opciones sin publicar devolvería un valor de etiqueta que no está visible en la interfaz de usuario, por lo que sería confuso para el usuario final.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

<xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>.<xref href="Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest.RetrieveAsIfPublished?text=RetrieveAsIfPublished Property" /><br />
[Trabajar con metadatos usando el servicio de la organización](../../org-service/work-with-metadata.md)<br />
[Usar la API web con metadatos](../../webapi/use-web-api-metadata.md)<br />
[Publicación de personalizaciones](/powerapps/developer/model-driven-apps/publish-customizations#retrieving-unpublished-metadata)