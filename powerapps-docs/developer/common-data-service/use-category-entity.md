---
title: Usar la entidad Categoría (Common Data Service) | MicrosoftDocs
description: Obtenga más información sobre cómo categorizar los registros de entidad utilizando la entidad de categoría.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-category-entity"></a>Usar la entidad Categoría

Categorizar los registros de entidad en Common Data Service ayuda a etiquetar los registros para poder buscarlos fácilmente. Use la entidad `Category` para crear y administrar una estructura jerárquica de categorías en Common Data Service, y luego asociar los registros de entidad a una o varias categorías.  
  
 Una categoría puede tener varias categorías secundarias, pero una categoría secundaria solo puede tener una categoría principal. Si elimina un registro principal de `Category` se eliminarán automáticamente todos sus registros secundarios y asociaciones de entidad. Define una categoría principal para una categoría mediante el atributo `Category.ParentCategoryId`.  
  
 Use el atributo `Category.SequenceNumber` para definir mediante programación el orden de visualización de las categorías de la jerarquía.  Cuando agrega una nueva categoría mediante el cliente web, se agrega automáticamente después de la última categoría de la jerarquía. También puede usar el atributo `Category.CategoryNumber` para definir o actualizar mediante programación un número para categoría que le ayude a distinguir fácilmente un grupo de categorías. El número de categorías se puede establecerse en cualquier valor mediante programación, pero se configura automáticamente al crear una categoría mediante el cliente web basándose en el prefijo de numeración automática especificado por el administrador para las categorías en el cliente web (**Configuración** > **Administración** > **Numeración automática** > pestaña **Categorías**).  
  
 Puede asociar registros de `Category` con registros de entidad personalizados y del sistema empleando relaciones y conexiones. Un registro de categoría puede asociarse con diferentes registros de entidad. Por ejemplo, puede asociar mediante programación un registro de `Category` con registros de `Account`, `Contact` y `Incident`.   

