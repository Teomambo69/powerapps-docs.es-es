---
title: Crear permisos de acceso a sitios web en Dynamics 365 portales | MicrosoftDocs
description: Aprenda a crear y asociar permisos de acceso a sitios web a los elementos de un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0ac02992498204efc42a52e736284ea134ed42f5
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551034"
---
# <a name="create-website-access-permissions"></a>Crear permisos de acceso al sitio web

Permisos de acceso al sitio web es un conjunto de permisos, asociado a un [rol Web](create-web-roles.md), que permite la edición en paralelo de los distintos elementos administrados por contenido dentro del portal, aparte de las páginas Web. La configuración de permisos determina qué componentes se pueden administrar en el portal.

| Nombre                         | Descripción                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| Administrar fragmentos de contenido      | Permite la edición de controles de fragmento de código.                                                          |
| Administrar marcadores de sitio          | Permite la edición de hipervínculos que usan marcadores de sitio                                           |
| Administrar conjuntos de vínculos Web         | Permite la edición de [conjuntos de vínculos Web](manage-web-links.md), incluida la adición de vínculos Web de eliminación de un conjunto de vínculos Web. |
| Vista previa de entidades no publicadas | Permite ver las entidades expuestas por el portal que tienen un estado de publicación draft.             |
|||

Para crear un permiso de acceso al sitio web y agregarlo a un rol Web:

1. Abra la [aplicación administración del portal](configure-portal.md).

2. Vaya a **portales** > **permisos de acceso al sitio web**.

3. Seleccione **Nueva**.

4. En **General**, escriba nombre, sitio web y seleccione los permisos necesarios.

5. En **roles web**, seleccione y agregue el rol Web al que desea asociar el permiso.

6. Guarde los cambios.

    ![Crear permiso de acceso a sitios web](../media/website-access-permission.png "Crear permiso de acceso a sitios web")  
