---
title: Definir claves alternativas con el explorador de soluciones | MicrosoftDocs
description: Aprenda a definir claves alternativas que se pueden usar para hacer referencia a los registros de Common Data Service usando el explorador de soluciones
ms.custom: ''
ms.date: 05/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c13838bdd957d78552d71636b4a165902154e82c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865792"
---
# <a name="define-alternate-keys-using-solution-explorer"></a>Definir las claves alternativas con el explorador de soluciones

El explorador de soluciones proporciona una forma de ver y crear claves alternativas para Common Data Service.

El [portal de Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. <br />Más información: 
- [Definir claves alternativas para hacer referencia a registros](define-alternate-keys-reference-records.md)<br />
- [Definir las claves alternativas con el portal Power Apps](define-alternate-keys-portal.md)

## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier clave alternativa que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-alternate-keys"></a>Ver claves alternativas

1. Con el explorador de soluciones abierto, en **Componentes** expanda **Entidades** y seleccione la entidad donde desea ver claves alternativas.
2. Expanda la entidad y seleccione **Claves**.

    ![Ver claves alternativas](media/view-alternate-keys-solution-explorer.png)

## <a name="create-an-alternate-key"></a>Crear una clave alternativa

1. Mientras [visualiza claves alternativas](#view-alternate-keys), seleccione **Nuevo**.
1. En el formulario, escriba el **Nombre para mostrar**. El campo **Nombre** se rellenará automáticamente según el **Nombre para mostrar**. 
2. De la lista **Atributos disponibles**, seleccione cada atributo y después **Agregar >** para mover el atributo a la lista **Atributos seleccionados**.
    ![Crear clave alternativa](media/create-alternate-key-solution-explorer.png)
1. Seleccione **Aceptar** para cerrar el formulario.

### <a name="optional-view-the-system-job-tracking-creation-of-indexes"></a>(Opcional) Ver el seguimiento del trabajo del sistema de creación de índices
1. Mientras [visualiza claves alternativas](#view-alternate-keys) después de haber creado una nueva clave alternativa, verá una fila para la clave que ha creado.
2. En la columna **Trabajo del sistema** encontrará un vínculo al trabajo del sistema que supervisa la creación de los índices para admitir la clave alternativa. 
    
    Este trabajo del sistema tendrá un nombre que sigue este patrón: `Create index for {0} for entity {1}` donde `0` es el **Nombre para mostrar** de la clave alternativa y `1` es el nombre de la entidad.

    El vínculo al trabajo del sistema no se mostrará una vez que el trabajo del sistema haya finalizado correctamente. Más información: [Supervisar y administrar trabajos del sistema](/dynamics365/customer-engagement/admin/monitor-manage-system-jobs)


## <a name="delete-an-alternate-key"></a>Eliminar una clave alternativa

Mientras [visualiza claves alternativas](#view-alternate-keys), seleccione ![Eliminar](media/delete.gif).

### <a name="see-also"></a>Vea también

[Definir claves alternativas para hacer referencia a registros](define-alternate-keys-reference-records.md)<br />
[Definir las claves alternativas con el portal Power Apps](define-alternate-keys-portal.md)<br />
[Documentación para desarrolladores: Definir claves alternativas para una entidad](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
