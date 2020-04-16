---
title: Definir comandos de la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Un comando de la cinta de opciones crea una definición reutilizable a la que los elementos de control de la cinta de opciones pueden hacer referencia.
keywords: ''
ms.date: 03/27/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 60933770-8c7c-499c-12b4-8b64f6eedb35
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3ea2f5cfdffb19589719780e7da1afaf3c510243
ms.sourcegitcommit: ebb4bb7ea7184e31dc95f0c301ebef75fae5fb14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2020
ms.locfileid: "3218557"
---
# <a name="define-ribbon-commands"></a>Definir comandos de la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-commands -->

Un comando *de la cinta de opciones* crea una definición reutilizable a la que los elementos de control de la cinta de opciones pueden hacer referencia.  
  
## <a name="ribbon-command-elements"></a>Elementos del comando de la cinta de opciones  
 El elemento `<CommandDefinition>` define un comando en la cinta de opciones. El atributo `Id` especifica un identificador único para el comando al que los elementos de control de la cinta de opciones pueden hacer referencia con el parámetro `Command`.  
  
 Un comando de la cinta de opciones define tres cosas:  
  
- **Reglas de habilitación**: especifica si se habilita un control de la cinta de opciones específico.  
  
- **Reglas de visualización**: especifica si se puede ver un elemento específico de la cinta de opciones.  
  
- **Acciones**: especifica el código que se ejecuta cuando se usa un control de la cinta de opciones.  
  
> [!IMPORTANT]
>  Todas las definiciones del comando se descargan en el equipo de un usuario para poder evaluarlas en tiempo de ejecución. Esto significa que un usuario sin los privilegios para ver un determinado control en la cinta de opciones puede usar el comando del explorador **Ver código fuente**, revisar el código y determinar que existe un control que no puede ver.  
  
### <a name="see-also"></a>Vea también  
 [Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Usar etiquetas localizadas con cintas de opciones](use-localized-labels-ribbons.md)   
 [Definir reglas de habilitación de la cinta de opciones](define-ribbon-enable-rules.md) [Solucionar problemas de cinta](https://support.microsoft.com/help/4552163)
