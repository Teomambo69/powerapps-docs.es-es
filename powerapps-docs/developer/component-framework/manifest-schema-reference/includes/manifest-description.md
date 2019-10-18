---
title: Manifiesto | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 31af2963-b4ca-4347-98f6-4a3f6277f43a
ms.openlocfilehash: 22750956cea12e1ed17bbc1ee8d4f015cf0ce2c1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338928"
---
El manifiesto es el archivo de metadatos que define un componente. Es un archivo `XML` que describe:

- Espacio de nombres del componente.
- El tipo de datos que se puede configurar, ya sea un campo o un conjunto de datos.
- Propiedades que se pueden configurar en la aplicación cuando se agrega el componente.
- Una lista de archivos de recursos que necesita el componente. 
  - Uno de ellos debe ser un recurso Web de JavaScript. Este elemento JavaScript debe incluir una función que cree una instancia de un objeto. Así, se implementa una interfaz que expone los métodos que son necesarios para que el componente funcione. A esto se le denomina “biblioteca de implementación de componentes”.
- El nombre de una función de JavaScript en la biblioteca de implementación de componentes que devolverá un objeto que aplica la interfaz de componentes necesaria.

Cuando el usuario configura un componente personalizado en una aplicación de lienzo o en una aplicación controlada por modelos, los datos del manifiesto filtran los componentes disponibles para que solo estén disponibles para la configuración los componentes válidos para el contexto. Las propiedades definidas en el manifiesto de un componente se representan como campos de configuración para que el usuario que configura el componente pueda especificar valores. Estos valores de propiedad están disponibles para la función de componente en tiempo de ejecución.
