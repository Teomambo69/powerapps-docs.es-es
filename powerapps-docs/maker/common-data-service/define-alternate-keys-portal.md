---
title: Definir las claves alternativas con el portal Power Apps | MicrosoftDocs
description: Aprenda a definir claves alternativas usando el portal de Power Apps
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
ms.openlocfilehash: b0528015899ccc624fed1d83566c445f348343c9
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040455"
---
# <a name="define-alternate-keys-using-power-apps-portal"></a>Definir las claves alternativas con el portal de Power Apps

El [portal de Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) proporciona una forma fácil de ver y crear claves alternativas de entidad con Common Data Service.

El portal permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. <br />Más información: 
- [Definir claves alternativas para hacer referencia a registros](define-alternate-keys-reference-records.md)
- [Definir las claves alternativas con el explorador de soluciones](define-alternate-keys-solution-explorer.md)

## <a name="view-alternate-keys"></a>Ver claves alternativas

1. Desde el [portal de Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **Datos** > **Entidades** y seleccione la entidad que desea ver.
2. Seleccione **Claves** para ver una lista de las claves alternativas que están definidas.

    ![Ver claves alternativas](media/view-alternate-keys-portal.png)

## <a name="create-an-alternate-key"></a>Crear una clave alternativa

1. Mientras [visualiza claves alternativas](#view-alternate-keys), seleccione **Agregar clave**.
2. Use el panel para establecer un **Nombre para mostrar** y seleccione los campos que se usarán para crear la clave alternativa.

    El campo **Nombre** se rellenará automáticamente según el nombre para mostrar.

    ![Definición de clave alternativa de ejemplo](media/alternate-key-account-number-sic-code.png)

1. Seleccione **Hecho** para cerrar el panel.
2. Haga clic en **Guardar entidad** para crear la clave alternativa.

> [!NOTE]
> La clave alternativa no estará disponible inmediatamente. Se inicia un trabajo del sistema cuando guarda la entidad para crear índices de la base de datos para admitir la clave alternativa.

## <a name="delete-an-alternate-key"></a>Eliminar una clave alternativa

Mientras [visualiza claves alternativas](#view-alternate-keys), seleccione la clave que desea eliminar y elija **Eliminar clave** en la barra de comandos.

### <a name="see-also"></a>Vea también

[Definir claves alternativas para hacer referencia a registros](define-alternate-keys-reference-records.md)<br />
[Definir claves alternativas usando el explorador de soluciones](define-alternate-keys-solution-explorer.md)<br />
[Documentación para desarrolladores: Definir claves alternativas para una entidad](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
