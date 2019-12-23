---
title: Definir acciones personalizadas para modificar la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo definir acciones personalizadas para modificar la cinta de opciones.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 72544b02-4eed-4d70-666e-a0d880f526af
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 414541da940771c68acf49f338308a8b4a80e751
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2863094"
---
# <a name="define-custom-actions-to-modify-the-ribbon"></a>Definir acciones personalizadas para modificar la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-custom-actions-modify-ribbon -->

El valor predeterminado, una barra de comandos de la aplicación o la cinta de opciones están definidos por los metadatos de Common Data Service. Estos datos predeterminados no se puede cambiar, pero se pueden incluir definiciones de acciones específicas que reemplazarán la cinta de opciones predeterminada.  
  
## <a name="types-of-custom-actions"></a>Tipos de acciones personalizadas  
 Existen dos tipos de acciones personalizadas para las cintas de opciones:  
  
- `<CustomAction>`: [!INCLUDE[ribbon_element_CustomAction](../../includes/ribbon-element-customaction.md)]  
  
- `<HideCustomAction>`: [!INCLUDE[ribbon_element_HideCustomAction](../../includes/ribbon-element-hidecustomaction.md)]  
  
### <a name="custom-actions"></a>Acciones personalizadas  
 Una acción personalizada es una instrucción de cómo se desea cambiar la definición de la cinta de opciones predeterminada. Se evalúa y se aplica a la cinta de opciones en tiempo de ejecución. Para establecer el contexto de una acción personalizada, debe incluir información sobre la ubicación de los elementos que desea cambiar. Use el atributo `Location` para especificar dónde se aplica el cambio.  
  
 Cuando se agrega un nuevo elemento de la cinta de opciones, se hace referencia al elemento que contiene, por ejemplo, una pestaña o grupo existente. Después, se incluye el sufijo `._children` para indicar que esta acción personalizada agregará algo a un elemento existente.  
  
 Cuando se cambia la definición del elemento existente, el valor `Location` se corresponde con el identificador de ese elemento.  
  
 También debe especificar un identificador único para la acción personalizada. Use el atributo **Id** para configurar este valor. Se recomienda usar una convención de nomenclatura que garantice un valor único. Para mantener la coherencia y la legibilidad, recomendamos que use un punto para separar componentes. El primer elemento de la convención de nomenclatura debe ser algo relacionado con el editor de soluciones o solución, por ejemplo, `Contoso.contact.form.CustomButton.CustomAction`.  
  
> [!TIP]
>  De forma consistente, al aplicar sus convenciones de nomenclatura al atributo `Id` aumentará en gran medida su productividad mientras se modifica RibbonDiffXml.  
  
 Basado en la información de ubicación que se proporciona, el valor del atributo `Sequence` determina el orden en el que se representan elementos. Si desea un control personalizado para que aparezca entre dos controles existentes, debe seleccionar un valor de secuencia que esté entre los valores de secuencia de los elementos existentes.  
  
### <a name="hide-custom-actions"></a>Ocultar acciones personalizadas  
 `<HideCustomAction>` es una instrucción que se usa cuando se desea quitar un elemento de cinta de opciones existente de manera que no se representa. Esto no oculta el elemento de la cinta de opciones, quita el elemento de la cinta de opciones en tiempo de ejecución de modo que no existe en la cinta de opciones.  
  
> [!NOTE]
>  Puesto que el elemento `HideCustomAction` quita un nodo especificado de la cinta de opciones, quitar elementos de la cinta de opciones de esta manera puede no ser la mejor opción para cada situación.  
> 
> - Si desea quitar el botón que está asociado a un privilegio específico, deberá ajustar los privilegios de la entidad en los roles de seguridad de su implementación. Esto permitirá la visualización de la cinta de opciones predeterminada y permite reglas para ocultar o deshabilitar elementos de la cinta de opciones, de modo que los usuarios no tienen los privilegios necesarios para realizar estas acciones.  
>   -   Si desea reemplazar un elemento de cinta de opciones existente con un elemento personalizado de la cinta de opciones, puede sobrescribir ese elemento especificando un valor `CustomAction.Location` idéntico al elemento existente.  
  
 El elemento **HideActionId** proporciona un identificador único para la acción. Para mantener la coherencia y la legibilidad, debe seguir la misma convención de nomenclatura que la descrita para los elementos `<CustomAction>`. El atributo **Location** debe coincidir con el identificador del elemento de la cinta de opciones que desea quitar.  
  
### <a name="see-also"></a>Vea también  
 [Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Pasar los datos desde una página como parámetro de las acciones de la cinta de opciones](/dynamics365/customer-engagement/developer/customize-dev/pass-dynamics-365-data-page-parameter-ribbon-actions)<br/>   <!-- TODO need to update the relevant Power Apps repo link-->
 [Definir la escalabilidad para elementos de la cinta de opciones](define-scaling-ribbon-elements.md)
