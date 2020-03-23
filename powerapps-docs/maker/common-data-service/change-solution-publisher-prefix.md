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
ms.openlocfilehash: c8d16a0c8451abc769990dbd88e6ad7f1e7846a5
ms.sourcegitcommit: c9c1c78dadc92913558dab44af0890e90e2adcd0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2020
ms.locfileid: "3088601"
---
# <a name="solution-publisher-overview"></a>información general del editor de soluciones

Cada aplicación creada o personalización realizada es parte de una solución. Cada solución tiene un editor. Usted especifica el editor al crear una solución. 

> [!div class="mx-imgBorder"] 
> <img src="media/solution-publisher-select.png" alt="Select solution publisher" height="731" width="416">

El editor de soluciones indica quién desarrolló la aplicación. Por esta razón, debe crear un editor de soluciones que sea significativo. Puede ver el editor de soluciones para una solución seleccionando **Configuración** desde el área **Soluciones** en Power Apps.

## <a name="solution-publisher-prefix"></a>Prefijo del editor de soluciones
Un editor de soluciones incluye un prefijo. El prefijo puede ayudar a determinar qué editor es responsable del componente. Por ejemplo, la *Solución Contoso* que se muestra aquí incluye un prefijo del editor de soluciones que es *contoso*. 

> [!div class="mx-imgBorder"] 
> ![Prefijo del editor de soluciones de recaudación de fondos](media/publisher-prefix.png)

> [!NOTE]
> Si cambia un prefijo del editor de soluciones, debe hacerlo antes de crear nuevas aplicaciones o elementos de metadatos. Puede cambiar los nombres de los elementos de metadatos. 

## <a name="common-data-services-default-solution"></a>Solución predeterminada de Common Data Services
La solución predeterminada en Power Apps es la solución predeterminada de Common Data Services, que está asociada con el editor predeterminado de Common Data Service. El prefijo de personalización de editor predeterminado se asignará aleatoriamente para este editor, por ejemplo, podría ser *cr8a3*. Esto significa que el nombre de cada nuevo elemento de metadatos creado en la solución predeterminada tendrá que anexarse a los nombres usados para identificar los elementos. Si crea una nueva entidad denominada *Animal*, el nombre único usado por Common Data Service sería *cr8a3_animal*. Lo mismo se aplica a los nuevos campos (atributos), relaciones u opciones de conjuntos de opciones. Si va a personalizar la solución predeterminada, considere cambiar el prefijo del editor. 

## <a name="create-a-solution-publisher"></a>Crear un editor de soluciones
1.  En el portal de Power Apps, seleccione **Soluciones**. 
2.  En la barra de comandos, seleccione **Nueva solución**, en el panel derecho, seleccione la lista desplegable **Editor** y luego seleccione **+ Editor**. 
    > [!div class="mx-imgBorder"] 
    > <img src="media/create-new-pubisher.png" alt="Create a new publisher" height="738" width="400">
3.  En el formulario **Nuevo editor**, especifique la información necesaria y opcional: 
   - **Nombre para mostrar**. Introduzca el nombre para mostrar del editor. 
   - **Nombre**. Introduzca el nombre único del editor. 
   - **Prefijo**. Especifique el prefijo de editor que desee. 
   -    **Prefijo de valor de opción**. Este campo genera un número basado en el prefijo del editor. Este número se usa al agregar opciones de conjuntos de opciones y ofrece un mensaje de la solución usada para agregar la opción. 
   - **Detalles de contacto**. Opcionalmente, puede agregar información de contacto y dirección.
4. Seleccione **Guardar y cerrar**.

## <a name="change-a-solution-publisher"></a>Cambiar un editor de soluciones
Puede cambiar un editor de soluciones para una solución no administrada siguiendo estos pasos:
1.  En el portal Power Apps, seleccione **Soluciones**, elija **...** junto a la solución que desea actualizar y luego seleccione **Configuración**. 
2.  En el panel **Configuración de soluciones**, seleccione **Editar editor**. 
3.  Edite los campos **Nombre para mostrar** y **Prefijo** y ponga los valores que desee. Este campo **Prefijo de valor de opción** genera un número basado en el prefijo del editor. Este número se usa al agregar opciones de conjuntos de opciones y ofrece un mensaje de la solución usada para agregar la opción. 
4.  Además del prefijo, también puede cambiar el nombre para mostrar del editor de soluciones, la información de contacto y la dirección en la sección **Detalles de contacto**. 
5.  Seleccione **Guardar y cerrar**.

### <a name="see-also"></a>Vea también
[Crear una solución](create-solution.md)