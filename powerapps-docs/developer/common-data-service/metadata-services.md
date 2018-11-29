---
title: Trabajar con metadatos mediante código (Common Data Service para aplicaciones) | Microsoft Docs
description: 'La [API web](webapi/overview.md) y el [Servicio de organización](org-service/overview.md) incluyen funciones para realizar operaciones CRUD en el esquema de la entidad'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="work-with-metadata-using-code"></a>Trabajar con metadatos mediante código

La [API web](webapi/overview.md) y el [Servicio de organización](org-service/overview.md) incluyen funciones para realizar operaciones CRUD en el esquema de la entidad. Aunque puede realizar estas operaciones con código, normalmente usará diseñadores para agregar, actualizar o eliminar elementos de esquema personalizados. Los usuarios deben tener privilegios de administrador para aplicar los cambios de esquema, pero todos los usuarios podrán leer metadatos.

## <a name="why-work-with-metadata"></a>¿Por qué trabajar con metadatos?

Un uso más común para los servicios de metadatos es recuperar metadatos sobre el entorno en el que se ejecuta la extensión. Puesto que cada entorno puede ser distinto y los metadatos de esquema contienen gran parte de la información sobre la configuración del entorno, es posible que deba recuperar esta información para permitir que sus extensiones se adapten a otras personalizaciones aplicadas en ese entorno.

Algunos ejemplos:
- El número de opciones disponibles en un atributo optionset puede variar. En lugar de escribir en el código los valores del entorno, vea si hay opciones diferentes. Puede consultar el sistema para determinar si el entorno actual tiene opciones diferentes.
- El nombre para mostrar de una entidad se puede cambiar. El nombre para mostrar predeterminado de una entidad de cuenta es *Cuenta*. Se puede cambiar a *Empresa*. Si desea mostrar un mensaje a un usuario y hacer referencia al nombre de una entidad, no debe escribir dicho nombre en el código, sino usar el valor que coincida con lo que el usuario está acostumbrado a ver, y usar en su lugar el nombre para mostrar recuperado de los metadatos de la entidad.

## <a name="browse-the-metadata-for-your-organization"></a>Examinar los metadatos de la organización

Desarrollar una buena comprensión de los metadatos en el sistema le pueden ayudar a entender cómo funciona la plataforma de Common Data Service for Apps. Los diseñadores disponibles para editar metadatos no pueden mostrar todos los detalles encontrados en los metadatos. Puede instalar una aplicación basada en modelos llamada *Explorador de metadatos* que le permitirá ver todas las entidades y propiedades de metadatos ocultas que se encuentran en el sistema. Más información sobre el *Explorador de metadatos*: [Explorar los metadatos de su organización](browse-your-metadata.md)

## <a name="programmatically-work-with-metadata"></a>Trabajar con metadatos mediante programación

Para obtener más información sobre cómo trabajar mediante programación con metadatos utilizando:
- **API web**: [Usar la API web con metadatos de CDS para aplicaciones](webapi/use-web-api-metadata.md)
- **Servicio de organización**: [Usar el servicio de organización con metadados de CDS para aplicaciones](org-service/work-with-metadata.md)