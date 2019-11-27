---
title: Usar el campo de búsqueda en un registro | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/06/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4ef67695603f3badeba92f46c6da90e21715c98b
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177843"
---
#  <a name="use-the-lookup-field-on-a-record"></a>Uso del campo de búsqueda en un registro

La búsqueda le ayuda a elegir registros de una entidad relacionada. Cuando se selecciona una entidad relacionada y se especifican los criterios de búsqueda, como un nombre o una dirección de correo electrónico, la búsqueda comienza automáticamente a resolver el texto parcial y muestra los registros coincidentes. Si no se muestra ningún registro después de escribir el texto completo de los criterios de búsqueda, se muestra un mensaje que especifica que no hay registros.

Por ejemplo, puede buscar el nombre **Adrian Dumitrascu**. Cuando escribe **ad**, los posibles registros coincidentes se rellenan y se muestran automáticamente.

  > [!div class="mx-imgBorder"]
  > ![Rellena automáticamente los registros coincidentes](media/automatically-populate-matching-records.png "Rellena automáticamente los registros coincidentes")
  
>[!NOTE] 
>Un administrador puede definir los criterios que utiliza la búsqueda para resolver el texto de búsqueda parcial.

Además, puede crear un nuevo registro seleccionando el botón **nuevo** . Debe tener los permisos necesarios para ver el botón **nuevo** y crear un registro. Al seleccionar el campo de búsqueda, los cinco registros usados más recientemente se muestran junto con cinco registros favoritos. Los registros que se muestran dependen del historial de vistas y de los favoritos que haya anclado. 

Por ejemplo, si solo tiene tres registros en el historial, la búsqueda mostrará los tres, junto con siete de sus registros favoritos. Si no ha anclado ningún favorito, solo se mostrarán los registros que se hayan visto más recientemente.

## <a name="types-of-lookups"></a>Tipos de búsquedas

Las búsquedas se clasifican en lo siguiente: 

- **Búsqueda simple:** Seleccione un único registro en un campo de una sola entidad. 

- **Campos de tipo PartyList:** Se usa para seleccionar varios registros de varias entidades en una búsqueda. Use los campos de tipo PartyList para seleccionar varios registros. Esto le permite agregar cada registro realizando una nueva búsqueda, varias veces. Cada vez que seleccione un registro, podrá realizar una nueva búsqueda de otro registro.
  
- **Campos de tipo con respecto:** Se usa para seleccionar un solo registro de varias entidades en una búsqueda. 

## <a name="search-in-a-lookup-field"></a>Buscar en un campo de búsqueda 
Para buscar una búsqueda, seleccione el cuadro de texto y escriba los criterios de búsqueda. Si los registros recientes están habilitados para su búsqueda, se mostrarán los registros recientes cuando seleccione el cuadro de texto.

  > [!div class="mx-imgBorder"]
  > ![Examinar un campo de búsqueda](media/MRU.png "Examinar un campo de búsqueda")  
  
>[!NOTE]   
> El resultado de búsqueda predeterminado para búsqueda de búsqueda es, comienza por. Esto significa que los resultados incluyen registros que comienzan con una palabra específica. Por ejemplo, si desea buscar **Alpine Ski House**, escriba **Alp** en el cuadro de búsqueda; Si escribe **Ski**, el registro no se mostrará en el resultado de la búsqueda.
>
> Para una búsqueda con caracteres comodín, use asteriscos: por ejemplo, escriba * ski o * Ski.

## <a name="browse-in-a-lookup-field"></a>Examinar en un campo de búsqueda
Para examinar una búsqueda, seleccione el icono de búsqueda (lupa). En el menú desplegable se mostrará una lista completa de elementos.

  > [!div class="mx-imgBorder"]
  > ![Buscar un campo de búsqueda](media/MRU_1.png "Buscar un campo de búsqueda")  
 
## <a name="most-recently-used-record-type-images"></a>Imágenes de tipo de registro usados más recientemente
La lista de registros usados más recientemente muestra una imagen para ayudar a distinguir entre los tipos de registro.

>[!NOTE] 
>Los registros recientes no se filtran por término de búsqueda o vista seleccionada.

  > [!div class="mx-imgBorder"]
  > ![Los campos de búsqueda muestran una imagen](media/Lookup_03-MRU_Entity_Images_56[1].png "Los campos de búsqueda muestran una imagen")  
  
## <a name="record-type-selection-list"></a>Lista de selección de tipo de registro  
Cuando los resultados abarcan varios tipos de registros, puede ver cuántos tipos de registros hay y seleccionarlos en la lista.

  > [!div class="mx-imgBorder"]
  > ![Ver cuántos registros](media/Lookup_04-MultipleEntityTypes[1].gif "Ver cuántos registros")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>Crear un nuevo registro si no encuentra un registro existente

Si no encuentra un registro, seleccione **nuevo** en el área de búsqueda para crear un nuevo registro.


### <a name="replace-an-existing-record-from-a-lookup-field"></a>Reemplazar un registro existente de un campo de búsqueda

Puede reemplazar un registro existente mientras usa búsquedas simples y con relación a tipos. Buscar un registro. A continuación, seleccione el registro y reemplácelo por un nuevo registro.

### <a name="change-a-view-in-a-lookup-field"></a>Cambiar una vista en un campo de búsqueda 

La selección de **cambiar vista** permite determinar:
 - Cómo desea ver los registros, como los **contactos seguidos**, la **vista de búsqueda de contactos**o los **contactos activos**.
 - Lo que desea ver en los registros, como el nombre, el correo electrónico o el número de teléfono. Por ejemplo, si desea ver solo los contactos que sigue, seleccione **cambiar vista** \> **contactos seguidos**. Solo se mostrarán los contactos que esté siguiendo, como se muestra aquí. 

    ![Cambiar los tipos de contactos de vista](media/change-view.png "Cambiar los tipos de contactos de vista")

>[!IMPORTANT] 
>La opción **cambiar vista** no estará visible si el administrador no ha configurado la opción para que aparezca en las vistas.

### <a name="choose-from-multiple-records"></a>Elegir entre varios registros

Cuando lookup tiene más registros en un campo de los que caben en el área de visualización disponible, el área de visualización se contrae, es decir, los registros que se ajustan al área de presentación se muestran junto al número de registros que no se muestran. Para ver todos los registros, seleccione el número. En las imágenes siguientes se muestra la diferencia entre los campos contraídos y no contraídos.

**Contraído**

![Área de presentación de múltiples búsquedas contraída](media/collapsed-multi-lookup-display-area.png "Área de presentación de múltiples búsquedas contraída")


**No contraído:**

![Área de presentación de múltiples búsquedas no contraída](media/non-collapsed-multi-lookup-display-area.png "Área de presentación de múltiples búsquedas no contraída")
