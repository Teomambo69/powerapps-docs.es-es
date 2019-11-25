---
title: No duplicar el registro de paso de complemento | MicrosoftDocs
description: Duplicar el registro de paso de complemento provocará que el complemento se desencadene varias veces en el mismo mensaje o evento.
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
ms.openlocfilehash: 84da790ddb69dbbfc01f3a7a4a44fff39bcf183d
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749398"
---
# <a name="do-not-duplicate-plug-in-step-registration"></a>No duplicar el registro de paso de complemento

**Categoría**: rendimiento

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Duplicar el registro de paso de complemento provocará que el complemento se desencadene varias veces en el mismo mensaje o evento. Esto puede provocar:

- Retraso en el procesamiento de trabajos asincrónicos cuando está registrado como modo asincrónico de ejecución.
- Experiencia deficiente de rendimiento para el usuario cuando está registrado como modo de ejecución sincrónica. Las experiencias incluyen:
    - Aplicaciones basadas en modelos que dejan de responder
    - Interacciones lentas con el cliente
    - El explorador deja de responder

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Asegúrese de que actualiza los pasos de registro del complemento en lugar de eliminarlos y volver a crearlos.  Además, cree y actualice los pasos de registro de complementos solo con métodos compatibles.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

> [!WARNING]
> Estos patrones deben evitarse.

Eliminar y volver a crear un paso en la instancia de origen (prueba, desarrollo, previa a la producción) también creará un paso duplicado que se registra en el entorno de destino si ese paso se hubiera registrado antes.

![Duplicar el registro del paso del complemento](../media/duplicate-plugin-registration-step.png)

Si se crea manualmente `SDKMessageProcessingSteps` con un nuevo GUID o se actualiza el GUID existente en el archivo `customizations.xml` se obtendrá un paso duplicado que se registrará. Estos tipos de tareas son incompatibles según se describe en [Cuándo editar el archivo de personalizaciones](/powerapps/developer/model-driven-apps/when-edit-customization-file).

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

El registro de paso de complemento duplicado puede producir una parada de SQL cuando los eventos se registran en un mensaje de actualización. Cuando se emita una actualización en un registro, SQL creará un bloqueo de fila en ese registro. Si otra transacción intenta actualizar el mismo registro, tendrá que esperar hasta que se termine el bloqueo para poder realizar la actualización. Si se produce un tiempo de espera, la transacción se revierte y no se confirma la actualización en la base de datos SQL.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Registrar un ensamblado de complementos](../../register-plug-in.md)
[Paradas](https://technet.microsoft.com/library/ms177433.aspx)<br />
