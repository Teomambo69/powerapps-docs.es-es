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
ms.openlocfilehash: 516f4a35cf7d31c45df011b7685ade1526246582
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341295"
---
# <a name="solution-publisher-overview"></a>información general del editor de soluciones

Cada aplicación creada o personalización realizada es parte de una solución. Cada solución tiene un editor. Usted especifica el editor al crear una solución. 

El editor de soluciones indica quién desarrolló la aplicación. Por esta razón, debe crear un editor de soluciones que sea significativo. Puede ver el editor de soluciones para una solución seleccionando **Configuración** desde el área **Soluciones** en Power Apps.

Para obtener más información sobre el editor de soluciones, consulte [Editor de soluciones](/power-platform/alm/solution-concepts-alm#solution-publisher).

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