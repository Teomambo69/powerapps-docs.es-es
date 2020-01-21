---
title: 'Ejemplo: Crear y actualizar metadatos de entidad (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear y actualizar metadatos de entidad.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 394bd033c7664542c58286c117f0fce679040066
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934582"
---
# <a name="create-and-update-entity-metadata"></a>Crear y actualizar metadatos de entidad

En este tema se muestra cómo crear mediante programación una entidad personalizada propiedad del usuario llamada **Cuenta bancaria** y agregar cuatro tipos diferentes de atributos a la misma.

También puede crear entidades personalizadas propiedad de la organización. Más información: [Propiedad de entidad](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/introduction-entities#entity-ownership). Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreateUpdateEntityMetadata).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `CreateEntityRequest` está diseñado para usarse en un escenario que contiene los datos necesarios para crear una entidad personalizada y, opcionalmente, para agregarla a una solución no administrada especificada.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `createrequest` crea la entidad personalizada. 
2. El método `Entity` se utiliza para definir la entidad.
3. El método `StringAttributeMetadata` define del atributo principal de la entidad.
4. El método `CreateBankNameAttributeRequest` crea un atributo de cadena para la entidad.
5. El método `CreateBalanceAttributeRequest` crea un atributo monetario para la entidad.
6. El método `CreateCheckedDateRequest` crea un atributo DateTime para la entidad.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
