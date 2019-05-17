---
title: Manifest | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: 31af2963-b4ca-4347-98f6-4a3f6277f43a
---
El manifiesto es el archivo de metadatos que define un componente. Es un documento `XML` que describe:

- El espacio de nombres del componente.
- El tipo de datos que se puede configurar, un campo o un conjunto de datos.
- Las propiedades que se pueden configurar en la aplicación cuando se agrega el componente.
- Una lista de archivos de recursos que el componente necesita. 
  - Uno de ellos debe ser un recurso web de JavaScript. Este JavaScript debe incluir una función que creará instancias de un objeto. Esto implementa una interfaz que expone métodos que son necesarios para que funcione el componente. Esto se llama la biblioteca de implementación de componentes.
- El nombre de una función JavaScript en la biblioteca de implementación del componente que devolverá un objeto que aplica la interfaz del componente necesario.

Cuando alguien configura un componente en la aplicación, los datos del manifiesto filtrarán los componentes disponibles para que sólo los componentes válidos para el contexto estén disponibles para configuración. Las propiedades definidas en el manifiesto para un componente se generan como campos de configuración para que la persona que configura el componente pueda especificar valores. Estos valores de propiedad están disponibles entonces para la función de componente en tiempo de ejecución.