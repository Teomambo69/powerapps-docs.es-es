---
title: Crear permisos de acceso al sitio web en los portales de Dynamics 365 | MicrosoftDocs
description: Aprenda cómo crear y asociar los permisos de acceso al sitio web a elementos en un portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761101"
---
# <a name="create-website-access-permissions"></a>Crear permisos de acceso al sitio web

Los permisos de acceso al sitio web son un conjunto de permisos, asociados con un [rol web](create-web-roles.md), lo que permite la edición del lado frontal de los distintos elementos administrados de contenido dentro del portal que no sean solo páginas web. La configuración de permisos determina los componentes se pueden ser administradas en el portal.

| Nombre                         | Descripción                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| Administrar fragmentos de contenido      | Permite la edición de los controles de fragmentos.                                                          |
| Administrar marcadores de sitio          | Permite la edición de hipervínculos que usan marcadores de sitio.                                           |
| Administrar conjuntos de vínculos web         | Permite la edición de [conjuntos de vínculos web](manage-web-links.md), incluido agregar y quitar vínculos web de un conjunto de vínculos web. |
| Vista previa de entidades sin publicar | Permite ver entidades expuestas al portal que tienen un estado de publicación de Borrador.             |
|||

Para crear un permiso de acceso al sitio web y agregarlo a un rol web:

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Permisos de acceso a sitios web**.

3. Seleccione **Nuevo**.

4. En **General**, especifique el nombre y el sitio web y seleccione los permisos necesarios.

5. En **Roles web**, seleccione y agregue el rol web al que asociar el permiso.

6. Guarde los cambios.

    ![Crear permiso de acceso al sitio web](../media/website-access-permission.png "Crear permiso de acceso al sitio web")  
