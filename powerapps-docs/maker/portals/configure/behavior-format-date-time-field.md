---
title: Comportamiento y formato del campo de fecha y hora en Common Data Service | MicrosoftDocs
description: Comportamiento y formato de los campos de fecha y hora que se usan en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 785b5fa7def4a5b8e4964e888567d64643405708
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553334"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Comportamiento y formato del campo de fecha y hora

En Common Data Service, el tipo de datos de fecha y hora se usa en muchos campos de entidad del sistema. Por ejemplo, puede mostrar Cuándo se usó por última vez una cuenta en una campaña de marketing o Mostrar la fecha y la hora en que se ha escalado un caso. También puede crear entidades personalizadas que incluyan los campos de fecha y hora. En función de lo que represente el campo, puede elegir uno de los siguientes comportamientos de campo para los formularios y cuadrículas del portal: 
- **Usuario local**: los valores de campo se muestran en la hora local del usuario y se les da formato según su idioma o configuración regional actual del portal. Los valores se almacenan en formato de zona horaria UTC en Common Data Service. Cuando un usuario de Common Data Service (u otro usuario del portal) en una zona horaria diferente ve ese valor, verá que se ha convertido en su propia zona horaria.
- **Solo fecha**: los valores de campo solo contienen la fecha y se muestran sin conversión de zona horaria. La parte de hora del valor siempre es 12:00 AM. El valor especificado por un usuario lo ven otros usuarios en distintas zonas horarias (por ejemplo, fechas de nacimiento).
  
  > [!Note]
  > El comportamiento de este campo no se puede cambiar una vez guardado.
  
- **Independiente de la zona horaria**: los valores de campo contienen la fecha y la hora, y se muestran sin conversión de zona horaria. Otros usuarios de distintas zonas horarias ven el mismo valor especificado por un usuario.
  
  > [!Note]
  > El comportamiento de este campo no se puede cambiar una vez guardado.

También puede invalidar el formato de fecha y hora predeterminado que se va a usar en los portales mediante la creación de la siguiente configuración del sitio:
- DateTime/DateFormat: formato de fecha usado en el portal. 
- DateTime/hora: el formato de hora que se usa en el portal. 
- DateTime/DateTimeFormat: el formato de la fecha y hora completas usadas en el portal.

De forma predeterminada, el portal usa los formatos de fecha y hora estándar especificados por la configuración de idioma del sitio Web.
Los formatos de fecha y hora aceptados se especifican [aquí](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).
