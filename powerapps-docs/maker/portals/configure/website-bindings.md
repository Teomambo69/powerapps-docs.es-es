---
title: Crear y administrar enlaces de sitios web en los portales | MicrosoftDocs
description: Aprenda a crear y administrar enlaces de sitios web en los portales.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/12/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f2cc1c3aad7f8aaf4b9dc1f554d7a7a1d91d62e8
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866639"
---
# <a name="create-and-manage-website-bindings"></a>Crear y administrar enlaces a sitios web

En un portal, el método predeterminado de selección de un sitio web es buscar un sitio web mediante la coincidencia del nombre del sitio web definido en el archivo web.config de ese portal concreto. Los enlaces al sitio web proporcionan métodos alternativos de selección de un sitio web cuando se carga un portal mediante el nombre de host o una ruta de la solicitud para seleccionar el sitio web adecuado. Esto elimina la necesidad de modificar archivos web.config independientes para cada versión de un sitio web específico. Esto simplifica la implementación de portales en distintos entornos de producción, de ensayo y de desarrollo. Además, esto permite que un código base del portal común funcione en varios sitios web.

## <a name="manage-website-bindings"></a>Administrar enlaces a sitios web

Los enlaces a sitios web se pueden crear, editar y eliminar en los portales de Power Apps. 

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Enlaces a sitios web**.

3. Para crear un nuevo enlace a sitios web, seleccione **Nuevo**.

4. Para editar un enlace a sitios web existente, seleccione el nombre del enlace a sitios web.

5. Especifique los valores adecuados en los campos.

6. Seleccione **Guardar y cerrar**.

### <a name="website-binding-attributes"></a>Atributos de enlace a sitios web

Estos son los atributos comunes a todos los enlaces.

|Nombre|Descripción|
|-----|----------|
|Nombre| Un título para identificar el enlace a los sitios web cuando se visualizan los registros|
|Sitio web|El [sitio web](websites.md) que el portal debe seleccionar.|
|Fecha de publicación|Una fecha que determina cuándo se permite que se seleccione el sitio web.|
|Fecha de expiración|Una fecha que determina cuándo el sitio web dejará de seleccionarse.|
|||

#### <a name="application-settings"></a>Configuración de aplicación

Especifique los valores de estos atributos para un enlace de nivel de aplicación. Estas asignaciones de enlace se basaron en la aplicación o sitio web de IIS.

|Nombre|Descripción|
|-----|----------|
|Nombre de sitio|El nombre del sitio web de IIS.|
|Ruta de acceso virtual|El nombre de la aplicación de IIS en el sitio web.|
|||

Para los servicios en la nube y sitios web de Azure, los valores de ruta virtual y el nombre de sitio están determinados por los nodos <Site> y <VirtualApplication> del archivo **ServiceDefinition.csdef**.

```
<ServiceDefinition>
  <WebRole>
    <Sites>
      <Site name=Dynamics Portals>
        <VirtualApplication name=customer-portal/>
```

### <a name="see-also"></a>Vea también
[Crear y administrar sitios web](websites.md)
