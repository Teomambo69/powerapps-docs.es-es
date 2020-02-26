---
title: información general del editor de soluciones | MicrosoftDocs
ms.custom: ''
ms.date: 02/03/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: ece684h8-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b54afabbed9e7dfcc53fe887f600593e77a02a7f
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "3017590"
---
# <a name="solution-publisher-overview"></a>información general del editor de soluciones

Cada aplicación creada o personalización realizada es parte de una solución. Cada solución tiene un editor. Usted especifica el editor al crear una solución. 

> [!div class="mx-imgBorder"] 
> <img src="media/solution-publisher-select.png" alt="Select solution publisher" height="731" width="416">

El editor de soluciones especifica quién desarrolló la aplicación. El prefijo puede ofrecer una forma rápida de conocer qué solución se agregó al elemento. Por estas razones, debe crear un editor de soluciones y especificar un prefijo que sea significativo. Esto es especialmente importante cuando se visualizan elementos de metadatos incluidos desde soluciones importadas. Por ejemplo, la solución que contiene la aplicación de ejemplo de recaudación de fondos utiliza *muestra* como prefijo del editor. 

> [!div class="mx-imgBorder"] 
> ![Prefijo del editor de soluciones de recaudación de fondos](media/fundraiser-sample-app-prefix.png)

> [!NOTE]
> Si cambia un prefijo del editor de soluciones, debe hacerlo antes de crear nuevas aplicaciones o elementos de metadatos. Puede cambiar los nombres de los elementos de metadatos. 

## <a name="common-data-services-default-solution"></a>Solución predeterminada de Common Data Service
La solución por defecto en Power Apps es la solución predeterminada de Common Data Service, que está asociada con el editor predeterminado de Common Data Service. El prefijo de personalización de editor predeterminado se asignará aleatoriamente para este editor, por ejemplo, podría ser *cr8a3*. Esto significa que el nombre de cada nuevo elemento de metadatos creado en la solución predeterminada tendrá que anexarse a los nombres usados para identificar los elementos. Si crea una nueva entidad denominada *Animal*, el nombre único usado por Common Data Service sería *cr8a3_animal*. Lo mismo se aplica a los nuevos campos (atributos), relaciones u opciones de conjuntos de opciones. Si va a personalizar la solución predeterminada, considere cambiar el prefijo del editor. 

## <a name="create-a-solution-publisher"></a>Crear un editor de soluciones
1.  En el portal Power Apps, seleccione el icono **Configuración** (engranaje) y, después, seleccione **Configuración avanzada**. 
2.  Seleccione **Configuración** > **Personalizaciones** > **Editores**. 
3.  En la barra de comandos **Vista principal del editor**, seleccione **Nuevo**. 
4.  Escriba la información necesaria: 
   - **Nombre para mostrar**. Introduzca el nombre para mostrar del editor. 
   - **Nombre**. Introduzca el nombre único del editor. 
   - **Prefijo**. Especifique el prefijo de editor que desee. 
   -    **Prefijo de valor de opción**. Este campo genera un número basado en el prefijo del editor. Este número se usa al agregar opciones de conjuntos de opciones y ofrece un mensaje de la solución usada para agregar la opción. 
   - **Detalles de contacto**. Opcionalmente, puede agregar información de contacto y dirección.
5. Seleccione **Guardar y cerrar**.

## <a name="change-a-solution-publisher"></a>Cambiar un editor de soluciones
Puede cambiar un editor de soluciones para una solución no administrada siguiendo estos pasos:
1.  En el portal Power Apps, seleccione **Soluciones**, elija **...** junto a la solución que desea actualizar y luego seleccione **Configuración**. 
2.  En el panel **Configuración de soluciones**, seleccione **Editar editor**. 
3.  Edite los campos **Nombre para mostrar** y **Prefijo** y ponga los valores que desee. Este campo **Prefijo de valor de opción** genera un número basado en el prefijo del editor. Este número se usa al agregar opciones de conjuntos de opciones y ofrece un mensaje de la solución usada para agregar la opción. 
4.  Además del prefijo, también puede cambiar el nombre para mostrar del editor de soluciones, la información de contacto y la dirección en la sección **Detalles de contacto**. 
5.  Seleccione **Guardar y cerrar**.

### <a name="see-also"></a>Vea también
[Crear una solución](create-solution.md)