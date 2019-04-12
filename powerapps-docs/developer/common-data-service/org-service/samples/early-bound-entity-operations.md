---
title: 'Ejemplo: crear, actualizar el enlace en tiempo de compilación de registros relacionados (Common Data Service) | Microsoft Docs'
description: 'En este ejemplo se muestra cómo crear, recuperar, actualizar y eliminar operaciones en una cuenta mediante la clase enlazada en tiempo de compilación. '
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-early-bound-entity-operations"></a>Ejemplo: operaciones de entidad en tiempo de compilación

<!-- sample-associate-records-early-bound.md 

sample-create-update-records-related-records-early-bound.md

show deep insert equivalent

sample-initialize-record-existing-record.md

https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-create-retrieve-update-delete-records-early-bound

-->

En este ejemplo se muestra cómo crear, recuperar, actualizar y eliminar operaciones en una cuenta mediante la clase enlazada en tiempo de compilación. Este ejemplo usa los siguientes métodos habituales:

- <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>  
  
-   <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>  
  
-   <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>  
  
-   <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>  

Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/EarlyBoundEntityOperations).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `IOrganizationService` está diseñado para usarse en un escenario donde se proporciona acceso mediante programación a los metadatos y los datos de una organización.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprueba la versión actual de la organización.
1. Crea los registros de cuenta de ejemplo necesarios para este ejemplo.

### <a name="demonstrate"></a>Demostración

1. Cree una instancia del objeto de cuenta.
1. Recupera la cuenta con los atributos.
1. Recupera el número de versión de la cuenta.
1. Actualiza la cuenta con atributo de código postal1. 


### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en la [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

