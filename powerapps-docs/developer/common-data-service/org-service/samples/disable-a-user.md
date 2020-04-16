---
title: " Deshabilitación o habilitación de un usuario (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo deshabilitar y habilitar un usuario del sistema.
ms.custom: ''
ms.date: 1/27/2020
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
ms.openlocfilehash: 03cd88528ee3851fc1eae44dab94bcb961af9e59
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155824"
---
# <a name="sample-disable-or-enable-a-user"></a>Ejemplo: habilitación o deshabilitación de un usuario

Este ejemplo muestra cómo deshabilitar y habilitar una cuenta de usuario del sistema en un entorno en línea o local/IFD.

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DisableOrEnableUser).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

La cuenta de usuario de Customer Engagement bajo la cual ejecuta este programa debe tener el rol de Administrador del sistema para habilitar/deshabilitar un usuario del sistema.

Antes de compilar este ejemplo, abra la solución en Visual Studio y seleccione **Ver** > **Lista de tareas**. Hay dos comentarios TODO que debe seguir para proporcionar la información requerida sobre un usuario del sistema existente en su organización.

Vea [Cómo ejecutar ejemplos](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) para obtener información sobre cómo ejecutar este ejemplo.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El ejemplo obtiene el identificador de un usuario del sistema existente y deshabilita o habilita dicha cuenta de usuario.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

Recupera el identificador del usuario del sistema existente que especifique (consulte [Cómo ejecutar esta muestra](#how-to-run-this-sample)).

### <a name="demonstrate"></a>Demostración

Muestra el uso de `SetStateRequest` para deshabilitar y habilitar un usuario del sistema. También muestra cómo recuperar información sobre un usuario del sistema.

Para ver el resumen del usuario del sistema especificado en Customer Engagement, navegue hasta **Configuración** > **Seguridad** > **Usuarios** y seleccione la cuenta de usuario del sistema de destino en la lista. Si lo desea, elija la vista del sistema **Usuarios deshabilitados** para filtrar la lista de todos los usuarios. El estado del usuario debe ser "Deshabilitado".

### <a name="clean-up"></a>Limpiar

Muestra una opción para habilitar la cuenta de usuario que se deshabilitó en el método `Main()`.

Responder "sí" es opcional en caso de que desee examinar la cuenta de usuario deshabilitada en Customer Engagement. Puede habilitar manualmente la cuenta de usuario en Active Directory o Office 365 para lograr el mismo resultado.