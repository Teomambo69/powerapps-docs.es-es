---
title: Definir acciones de la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo definir acciones que se deben realizar mediante una barra de comandos o control de la cinta de opciones en un elemento <CommandDefinition> junto con las reglas que supervisan si el control está habilitado o está visible en la cinta de opciones.
keywords: ''
ms.date: 10/31/2018
ms.service:
- PowerApps
ms.topic: article
ms.assetid: fbb7ff68-e4be-d8c2-069f-6a4a69665b56
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8f17a21544a1f218b7f3c21264e723bd3750a843
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115644"
---
# <a name="define-ribbon-actions"></a>Definir acciones de la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-actions -->

Defina las acciones que se deben realizar mediante una barra de comandos o control de la cinta de opciones en un elemento de `<CommandDefinition>` junto con las reglas que supervisan si el control está habilitado o está visibles en la cinta de opciones.  
  
 Un control de la cinta de opciones puede realizar dos tipos de acciones y puede incluir varias acciones:  
  
- **Funciones de JavaScript**: Un elemento de `<JavaScriptFunction>` hace referencia a una función definida en un recurso web de script.  
  
- **Abrir una dirección URL**: La cinta de opciones abre una dirección URL desde un atributo de Dirección en el elemento de `<Url>`. Los parámetros adicionales pueden pasar información acerca de cómo se pasan los parámetros querystring y el modo en el que se abre la ventana.  
  
     Existen varias opciones disponibles para pasar parámetros a una dirección URL con la cinta de opciones. Más información: [Pasar parámetros a una dirección URL con la cinta de opciones](pass-parameters-url-by-using-ribbon.md)  
  
## <a name="passing-parameters-to-ribbon-actions"></a>Paso de parámetros a las acciones de la cinta de opciones  

 Use los siguientes elementos para definir los datos que pasará a la acción personalizada:  
  
 `<BoolParameter>`  
[!INCLUDE[ribbon_element_BoolParameter](../../includes/ribbon-element-boolparameter.md)]
  
 `<CrmParameter>`  
 [!INCLUDE[ribbon_element_CrmParameter](../../includes/ribbon-element-crmparameter.md)] Más información: [Pasar los datos desde una página como parámetro a las acciones de la cinta de opciones](/dynamics365/customer-engagement/developer/customize-dev/pass-dynamics-365-data-page-parameter-ribbon-actionsd)  <!-- TODO need to update the relevant link from the powerapps repo -->
  
 `<DecimalParameter>`  
 [!INCLUDE[ribbon_element_DecimalParameter](../../includes/ribbon-element-decimalparameter.md)]
  
 `<IntParameter>`  
 [!INCLUDE[ribbon_element_IntParameter](../../includes/ribbon-element-intparameter.md)]
  
 `<StringParameter>`  
 [!INCLUDE[ribbon_element_StringParameter](../../includes/ribbon-element-stringparameter.md)]
  
 Cuando los parámetros se pasan a un elemento de `<Url>`, se pasan como cadena de consulta. Por lo tanto, debe incluir un valor de nombre para representar la "clave" en la cadena de consulta del par clave/valor.  
  
 Los parámetros pasados a `<JavaScriptFunction>` no requieren un nombre pero se deben incluir en el pedido esperado por la función y deben ser del tipo de datos correctos.  
  
## <a name="see-also"></a>Vea también  

 [Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Definir reglas de visualización de la cinta de opciones](define-ribbon-display-rules.md)   
 [Pasar los datos desde una página como parámetro de las acciones de la cinta de opciones](/dynamics365/customer-engagement/developer/customize-dev/pass-dynamics-365-data-page-parameter-ribbon-actionsd)  
<!-- TODO need to update the relevant link from the powerapps repo-->
