---
title: Comportamiento y formato del campo Fecha y hora en Common Data Service | MicrosoftDocs
description: Comportamiento y formato de los campos de fecha y hora que se usan en un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: fe9a2e6e8cef5f2199eb4bd5aa98aacea8d14e67
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979313"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Comportamiento y formato del campo de fecha y hora

En Common Data Service, el tipo de datos Fecha y hora se usa en muchos campos de entidad del sistema. Por ejemplo, puede mostrar cuándo se usó por última vez una cuenta en una campaña de marketing o mostrar la fecha y la hora en que un caso se remitió a una instancia superior. También puede crear entidades personalizadas que incluyan los campos de fecha y hora. En función de lo que representa el campo, puede seleccionar uno de los comportamientos siguientes de campo para formularios y cuadrículas de portal: 
- **Local del usuario**: Los valores de campo se muestran en la hora local del usuario y reciben formato de acuerdo su idioma/configuración regional de portal actuales. Los valores se almacenan en formato de la zona de UTC en Common Data Service. Cuando un usuario en Common Data Service (u otro portal de usuario) de una zona horaria distinta ve dicho valor, lo ve convertido a su propia zona horaria.
- **Solo fecha**: Los valores de campo contienen solo la fecha y se muestran sin la conversión de la zona horaria. La parte de hora del valor siempre es 12:00 AM. El valor introducido por un usuario lo ven igual los demás usuarios de zonas horarias diferentes (por ejemplos, fechas de nacimiento).
  
  > [!Note]
  > El comportamiento de este campo no se puede cambiar después de que se ha guardado.
  
- **Independiente de la zona horaria**: Los valores de campo contienen sólo la fecha y la hora y se muestran sin la conversión de la zona horaria. El valor introducido por un usuario lo ven igual los demás usuarios de zonas horarias diferentes.
  
  > [!Note]
  > El comportamiento de este campo no se puede cambiar después de que se ha guardado.

También puede reemplazar el formato de fecha y hora predeterminado que se va a usar en los portales creando los siguientes valores del sitio:
- DateTime/DateFormat: el formato de fecha empleado en el portal. 
- DateTime/TimeFormat: el formato de hora empleado en el portal. 
- DateTime/DateTimeFormat: El formato de la fecha y hora completo usado en el portal.

De forma predeterminada, el portal usa los formatos estándar de fecha y hora de la configuración del idioma de la página web.
Los formatos de fecha y hora aceptados se especifican [aquí](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).
