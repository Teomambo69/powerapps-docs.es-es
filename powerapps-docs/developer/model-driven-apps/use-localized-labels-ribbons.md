---
title: Usar etiquetas localizadas con cintas de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre el uso de etiquetas localizads con cintas de opciones.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c4eb7d7bf269541aef706a6e47ae25d7511a1590
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275908"
---
# <a name="use-localized-labels-with-ribbons"></a>Usar etiquetas localizadas con cintas de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/use-localized-labels-ribbons -->

Aunque los elementos de la cinta de opciones que muestran el texto permiten la entrada directa de texto, se recomienda usar etiquetas localizadas para definir el texto que se muestra en la cinta de opciones. Habilita capacidades multilingües y una mejor administración del texto compartido.  
  
## <a name="using-localized-labels"></a>Uso de etiquetas localizadas  

 El elemento `<RibbonDiffXml>` incluye el elemento `<LocLabels>`. Como se muestra en el siguiente ejemplo, aquí es donde puede especificar qué texto desea mostrar en la información sobre herramientas y las etiquetas de la cinta de opciones con el elemento `<Titles>`.  
  
```xml  
<LocLabels>  
 <LocLabel Id="MyISV.account.SendToOtherSystem.LabelText">  
  <Titles>  
   <Title languagecode="1033"  
          description="Send to Other System" />  
  </Titles>  
 </LocLabel>  
 <LocLabel Id="MyISV.account.SendToOtherSystem.ToolTip">  
  <Titles>  
   <Title languagecode="1033"  
          description="Sends this Record to another system" />  
  </Titles>  
 </LocLabel>  
</LocLabels>  
```  
  
 En la definición de un elemento de la cinta de opciones que muestra el texto, la siguiente presentación muestra cómo se puede hacer referencia a la etiqueta localizada con la directiva `$LocLabels:`.  
  
```xml  
ToolTipTitle="$LocLabels:MyISV.account.SendToOtherSystem.LabelText"  
ToolTipDescription="$LocLabels:MyISV.account.SendToOtherSystem.ToolTip"  
```  
  
## <a name="force-a-line-break-in-a-ribbon-control-label"></a>Forzar un salto de línea en una etiqueta del control de la cinta de opciones  

 Si tiene una etiqueta del control de la cinta de opciones que es muy larga, el texto se ajustará para adaptarse al espacio disponible. Puede especificar el lugar donde desea incluir un salto de línea usando los siguientes caracteres: `&#x200b;&#x200b;`.  
  
 Si el texto de la etiqueta es muy largo sin un espacio para que se ajuste el texto, el ancho del control se amplía para permitir que se muestre la etiqueta completa.  
  
### <a name="see-also"></a>Vea también  
 [Personalizar comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Exportar, preparar para editar e importar la cinta de opciones](export-prepare-edit-import-ribbon.md)   
 [Usar etiquetas localizadas con cintas de opciones](use-localized-labels-ribbons.md)   
 [Definir comandos de la cinta de opciones](define-ribbon-commands.md)
