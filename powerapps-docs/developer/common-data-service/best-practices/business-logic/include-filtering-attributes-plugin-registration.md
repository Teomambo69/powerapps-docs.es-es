---
title: Incluir atributos de filtrado con el registro de complementos | MicrosoftDocs
description: Si no se configura ningún atributo de filtrado para un paso de registro de complementos, el complemento se ejecutará cada vez que un mensaje de la actualización se produzca para ese evento.
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
ms.openlocfilehash: 3f1c948e5fa41a9eccaeb7ea27c42f4ad49c93b0
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749731"
---
# <a name="include-filtering-attributes-with-plug-in-registration"></a>Incluir atributos de filtrado con el registro de complementos

**Categoría**: rendimiento

**Potencial de impacto**: medio

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Si no se configura ningún atributo de filtrado para un paso de registro de complementos, el complemento se ejecutará cada vez que un mensaje de la actualización se produzca para ese evento.  Una combinación de atributos sin filtrado y la funcionalidad de guardado automático podría causar ejecuciones de complementos que no se necesitan lo que provoca un comportamiento indeseable y degrada el rendimiento.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

La mayoría de los complementos registrados para el mensaje de actualización de una entidad no deben ejecutarse en todas las actualizaciones. Generalmente, solo es necesario procesar alguna lógica cuando han cambiado los atributos o un atributo específico. Para evitar un procesamiento adicional en el entorno, reducir al mínimo la lógica necesaria en un complemento y toda la actualización para que se complete lo antes posible, se recomienda que los registros del paso del complemento también incluyan atributos de filtrado para los mensajes de actualización.

![Paso de registro de complementos con atributos de filtrado](../media/plugin-registration-step-with-filtering-attributes.png)

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Los atributos de filtrado son una lista de atributos de entidad que, si se modifican, hacen que el complemento se ejecute.  Estos atributos se pueden establecer al registrar el complemento mediante la herramienta de registro de complementos. Si no se configura ningún atributo, el complemento se ejecutará cada vez que se produzca un mensaje de actualización. Las actualizaciones se pueden producir por varias razones. Cuando se activa la función de guardado automático en el entorno, puede ocurrir varios veces durante la sesión de usuario cuando se está en un formulario de entidad. Si no se especifican atributos de filtrado, el complemento se ejecutará para cualquier cambio de atributo en la entidad diseñada.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Registrar un complemento](../../register-plug-in.md)
[Deshabilitar la función de guardado automático en una aplicación basada en modelos](/powerapps/maker/model-driven-apps/manage-auto-save)