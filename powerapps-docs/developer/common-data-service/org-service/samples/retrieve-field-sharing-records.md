---
title: 'Ejemplo: Recuperar los registros de uso compartido de campo (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar los registros de uso compartido de campo para una entidad.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 5b8f151fddc3561654d62ef4d415c6401f7d5ff1
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155633"
---
# <a name="sample-retrieve-field-sharing-records"></a>Ejemplo: recuperar los registros de uso compartido de campo

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-retrieve-field-sharing-records -->

Este ejemplo muestra cómo recuperar los registros de `PrincipalObjectAttributeAccess` (uso compartido de campo) para una entidad. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveFieldSharing).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `PrincipleObjectAttributeAccess` está diseñada para usarse en un escenario donde recupera registros de uso compartido de campo para una entidad.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateAttributeRequest` crea los campos personalizados necesarios para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. El `WhoAMIRequest` recupera información del usuario actual.
2. El mensaje `RetrieveUserPrivilegesRequest` comprueba si el usuario actual tiene `prvReadPOAA`.
3. El `PrincipalObjectAttributeAccess` crea la entidad POAA para los campos personalizados creados en Setup(#setup).
4. Usar la `QueryExpression` para recuperar permisos de atributo de usuario compartidos.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
