---
title: Configuración de Mapas de Bing en una aplicación basada en modelos con PowerApps | Microsoft Docs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 44977925bfa92647ddbc29b7a82028f55b146921
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701845"
---
# <a name="configure-bing-maps-in-a-model-driven-app"></a>Configuración de Mapas de Bing en una aplicación basada en modelos

 Mapas de Bing se puede mostrar en un formulario para las entidades de cuenta, contacto, cliente potencial, oferta, pedido, factura, competidor y usuario del sistema. Puede quitar el área de Mapas de Bing en el editor de formularios o agregarla de nuevo mediante el botón **Mapas de Bing** situado en la pestaña **Insertar** del editor de formularios.  
  
 Para habilitar Mapas de Bing en el sistema, se debe habilitar la opción **Mostrar Mapas de Bing en los formularios**.  
  
|Pestaña|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**General**|**Etiqueta**|**Obligatorio**: una etiqueta para mostrar de los Mapas de Bing.|  
||**Mostrar etiqueta en el formulario**|Indica si se debe mostrar la etiqueta.|  
||**Select an address to use with the Bing Maps control** (Seleccionar una dirección para usar con el control de Mapas de Bing)|Elija qué dirección debe usar para proporcionar datos para el mapa.|  
||**Visible de forma predeterminada**|Mostrar mapas de Bing es opcional y puede controlarse mediante scripts. Más información: [Opciones de visibilidad](visibility-options-legacy.md)|  
|**Formato**|**Select the number of columns the control occupies** (Seleccionar el número de columnas que ocupa el control)|Cuando la sección que contiene Mapas de Bing tiene más de una columna, puede establecer el campo para que ocupe hasta el número de columnas que tiene la sección.|  
||**Select the number of rows the control occupies** (Seleccionar el número de filas que ocupa el control)|Puede controlar la altura de Mapas de Bing mediante la especificación de un número de filas.|  
||**Automatically expand to use available space** (Expandir automáticamente para usar el espacio disponible)|Puede permitir que la altura de Mapas de Bing se expanda hasta el espacio disponible.|  

## <a name="next-steps"></a>Pasos siguientes

[Uso del formulario principal y sus componentes](use-main-form-and-components.md)