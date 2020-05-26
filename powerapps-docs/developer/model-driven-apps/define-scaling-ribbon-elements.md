---
title: Definir la escalabilidad de elementos de la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo definir la escalabilidad para los elementos de la cinta de opciones.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
- ''
ms.topic: article
ms.assetid: c2cc39d2-e540-0800-f04f-3fa66df21191
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0de4ce4a3475be0f5f6a6b4ed67284722601cc7a
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275816"
---
# <a name="define-scaling-for-ribbon-elements"></a>Definir escalabilidad para elementos de la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-scaling-ribbon-elements -->

Para las cintas de opciones de aplicación y las cintas de opciones actualizadas de formulario de entidad no hay escalabilidad. La escalabilidad solo se aplica a los formularios de las entidades que no se actualizaron y las cintas de opciones de lista que se muestran mediante Dynamics 365 for Outlook.  
  
 El objetivo de la cinta es mantener la visibilidad de los controles relevantes incluso cuando el tamaño horizontal de la ventana cambia. Para lograrlo, la definición de la interfaz de usuario permite controlar cómo los controles de un grupo cambian de tamaño en respuesta a los cambios en el tamaño de la ventana. Esto se conoce como *escalabilidad*.  
  
## <a name="associate-groups-and-controls-to-layout-templates"></a>Asociar grupos y controles a las plantillas de diseño  
 Cada elemento de `<Group>` en la cinta está asociado con `<GroupTemplate>`. `GroupTemplate` especifica una o varias formas de presentar los controles en el grupo usando los elementos `<Layout>`. Cada `Layout` puede contener uno de dos tipos de definición del modo en que los controles se muestran en el grupo.  
  
- `<OverflowSection>` permite que los controles cambien la posición relativa en función del tamaño disponible.  
  
- `<Section>` controla el número de filas que se mostrarán y dónde se muestra cada control.  
  
  Casi todos los elementos `Layout` usados en cintas usan elementos `OverflowSection`.  
  
  Cada elemento `<Tab>` debe contener un `<MaxSize>` en `<Scaling>`. Se requiere el elemento `MaxSize` porque establece la presentación predeterminada de cada `Group` en `Tab` sin ninguna escalabilidad aplicada. La escalabilidad se produce cuando `Tab` está asociado con uno o varios `<Scale>`. Cada elemento `MaxSize` y `Scale` se asocia mediante el atributo `Size` con uno de los elementos `Layout` de `GroupTemplate` usado por cada `Group` dentro de una `Tab`.  
  
> [!NOTE]
>  El valor del atributo `Size` de los elementos `MaxSize` o `Scale` debe coincidir con el `Title` de los elementos disponibles en `Layout` especificado en `GroupTemplate`. Estos valores son cadenas y no hay validación en el XSD para ayudarle a seleccionar los valores que son coincidentes. El XML distingue siempre mayúsculas de minúsculas.  
  
 En el siguiente diagrama se muestra cómo los elementos `MaxSize`, `Scale`, `Group`, `Layout` y `OverflowSection` deben hacerse referencia para habilitar la escalabilidad cuando se usa un elemento `<OverflowSection>`.  
  
 ![Relaciones de elementos con OverflowSection](media/ribbon-ui-definition.png "Relaciones de elementos con OverflowSection")  
  
 En el siguiente diagrama se muestra cómo los elementos `MaxSize`, `Scale`, `Group`, `Layout` y `ControlRef` deben hacerse referencia para habilitar la escalabilidad cuando se usa un elemento `<Section>`.  
  
 ![Relaciones de elementos con Section](media/ui-definition.png "Relaciones de elementos con Section") 
  
### <a name="use-existing-group-templates"></a>Usar plantillas de grupo existentes  
 Al crear un nuevo grupo, en lugar de definir las nuevas plantillas de grupo, puede volver a usar los elementos `GroupTemplate` existentes.  
  
 Asocie el nuevo grupo a esa plantilla. Para cada control del grupo, use un valor `TemplateAlias` a partir de uno de los elementos `<Section>` o `<OverflowSection>` que se encuentran en uno de los elementos `Layout` usados para esa `GroupTemplate`. Cada `<OverflowSection>` incluye un `isv``TemplateAlias` que no se usa. Esta `TemplateAlias` se proporciona para permitir que los ISV agreguen controles a ese grupo.  
  
### <a name="control-how-scaling-is-applied"></a>Controlar cómo se aplica la escalabilidad  
 Cada elemento `Scale` del elemento `Scaling` de una pestaña determinada representa un paso de la escala. Cada `Scale` la aplica de forma secuencial el orden en que aparece el elemento `Scale`. Para reducir el espacio horizontal disponible para la cinta, cada elemento de la escala se aplica en orden descendente. Cuando aumenta el espacio horizontal disponible, desde el campo más pequeño el elemento inferior de la escala está activo. Cada uno de los elementos `Scale` disponibles se aplican en orden de inferior a superior hasta que todos los elementos `MaxSize` están activos.  
  
> [!NOTE]
>  Los valores de atributo `Sequence` del elemento `Scale` no se usan para fijar el orden en el que se aplica la escalabilidad. La escalabilidad se aplica según el orden relativo en que aparecen los elementos `MaxSize` y `Scale` en RibbonDiffXML. El valor de `Sequence` es importante para ambos elementos `MaxSize` y `Scale` porque todos los elementos `MaxSize` deben agruparse juntos sobre los elementos `Scale`. Cuando se agrega un nuevo elemento `MaxSize` o `Scale`, asegúrese de revisar los intervalos de los valores predeterminados de `Sequence` asignados a todos los elementos `MaxSize` y `Scale`. Un error común es asignar los valores de `Sequence` que pueden provocar la superposición de los intervalos.  
  
### <a name="see-also"></a>Vea también  
 [Personalizar comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Definir acciones personalizadas para modificar la cinta de opciones](define-custom-actions-modify-ribbon.md)   
 [Definir las reglas de visualización de la pestaña de la cinta de opciones](define-ribbon-tab-display-rules.md)
