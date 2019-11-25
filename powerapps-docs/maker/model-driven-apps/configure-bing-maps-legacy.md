---
title: Configurar mapas de Bing en una aplicación controlada por modelos con PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 10/18/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: f9729664-561c-4758-86ce-7216d68075d9
caps.latest.revision: 63
ms.author: matp
author: Mattp123
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ff7f5c01e913da60409bb60c637b37ebd4bfa096
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756496"
---
# <a name="configure-a-map-on-a-form"></a>Configurar un mapa en un formulario
De forma predeterminada, el control de mapas de Bing se configura en el formulario principal para las entidades de cuenta y contacto, lo que proporciona la capacidad de mostrar un mapa en registros de entidad. Aunque no está configurado de forma predeterminada, el control de mapas de Bing puede agregarse a la entidad de usuario del sistema. El control de mapas de Bing también se puede usar con algunas entidades incluidas con aplicaciones basadas en modelo en Dynamics 365, como Dynamics 365 Sales y Dynamics 365 Customer Service. Por ejemplo, las entidades cliente potencial, oferta, pedido, facturación, y competidor. El control de mapas de Bing no se puede usar con entidades personalizadas.  

Cuando está habilitado, el mapa muestra la ubicación especificada en los campos compuestos de dirección para el registro dado. 

> [!div class="mx-imgBorder"] 
> ![Control de mapas de Bing en una aplicación](media/bing-map-example.png "Control de mapas de Bing en una aplicación")

> [!IMPORTANT]
> Para usar mapas debe estar habilitada la configuración del sistema Mostrar Mapas de Bing en los formularios. Más información: [Habilitar mapas para el entorno](#enable-maps-for-your-environment)

Puede quitar el área de mapas de Bing en el editor de formularios o volver a agregarlo con el botón **Mapas de Bing** en la ficha **Insertar** del editor de formularios clásico.

## <a name="enable-maps-for-your-environment"></a>Habilitar mapas para el entorno
1. Abra una aplicación basada en modelo y después seleccione **Configuración** > **Configuración avanzada**. 
2. Seleccione **Configuración** > **Administración** > **Configuración del sistema**. 
3. En la pestaña **General**, seleccione **Mostrar mapas de Bing en formularios** y a continuación seleccione **Aceptar**. 
 
    ![Habilitar mapas en formularios](media/enable-maps.png)

## <a name="configure-a-map"></a>Configurar un mapa 
1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. Vaya a **Datos** > **Entidades** y seleccione la entidad que desea configurar un mapa en el formulario principal. 
3. Seleccione la pestaña **Formularios** y seleccione el formulario principal y, en la barra de comandos seleccione **Cambiar a clásico**. 
4. En el diseñador de formularios clásico, haga doble clic en el control **Vista del mapa** para ver y editar las propiedades. Más información: [Ver y editar propiedades de mapa](#view-and-edit-map-properties)

    ![Control de vista de mapa](media/map-view-control.png)

Para quitar el control de mapa del formulario, seleccione el control **Vista de mapa** y después presione la tecla Eliminar.

## <a name="view-and-edit-map-properties"></a>Vea y edite propiedades de mapa

|      Pestaña       |                        Propiedad                         |                                                                                                  Descripción                                                                                                   |
|----------------|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Generales**   |                        **Etiqueta**                        |                                                                              **Requerido**: etiqueta para mostrar para mapas de Bing.                                                                               |
|                |              **Mostrar etiqueta en el formulario**              |                                                                                     Si la etiqueta debe mostrarse.                                                                                     |
|                | **Seleccione una dirección para utilizar con este control de mapas de Bing** |                                                                        Elija qué dirección se debe usar para proporcionar datos para el mapa.                                                                        |
|                |                 **Visible de forma predeterminada**                  | Mostrar Mapas de Bing es opcional y se puede controlar mediante reglas de negocio o scripts. Más información: [Opciones de visibilidad](visibility-options-legacy.md) |
| **Formato** |  **Seleccione el número de columnas que ocupa el control**  |                              Cuando la sección que contiene mapas de Bing tiene más de una columna puede establecer el campo para ocupar hasta el número de columnas que tiene la sección.                              |
|                |   **Seleccione el número de filas que ocupa el control**    |                                                                  Puede controlar el alto de mapas de Bing especificando varias filas.                                                                   |
|                |     **Expandir automáticamente para usar el espacio disponible**     |                                                                        Puede permitir que el alto de mapas de Bing se expanda el espacio disponible.                                                                        |

### <a name="see-also"></a>Vea también
[Crear y diseñar formularios de aplicaciones controladas por modelos](create-design-forms.md) 
