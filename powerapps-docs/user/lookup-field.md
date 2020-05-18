---
title: Uso del campo de búsqueda en un registro | Microsoft Docs
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
ms.openlocfilehash: bdb1b0bf1a500087f11804f6da55d1c3abe2eaf3
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "3303562"
---
#  <a name="use-the-lookup-field-on-a-record"></a>Uso del campo de búsqueda en un registro

La búsqueda ayuda a elegir registros de una entidad relacionada. Al seleccionar una entidad relacionada y especificar criterios de búsqueda, como un nombre o una dirección de correo electrónico, la búsqueda comienza automáticamente a resolver el texto parcial y muestra los registros coincidentes. Si no se muestra ningún registro después de haber escrito el texto completo de los criterios de búsqueda, se muestra un mensaje especificando que no hay ningún registro.

Por ejemplo, puede buscar el nombre **Adrian Dumitrascu**. Cuando escribe **ad**, los posibles registros coincidentes se rellenan y se muestran automáticamente.

  > [!div class="mx-imgBorder"]
  > ![Rellena automáticamente los registros que coinciden](media/automatically-populate-matching-records.png "Registros coincidentes rellenados automáticamente")
  
>[!NOTE] 
>Un administrador puede definir los criterios que la búsqueda usa para resolver texto parcial de búsqueda.

Además, puede crear un nuevo registro seleccionando el botón **Nuevo**. Debe tener permisos suficientes para ver el botón **Nuevo** y para crear un registro. Cuando seleccione el campo de búsqueda, los cinco registros usados más recientemente se muestran junto con cinco registros favoritos. Los registros que se muestran dependen de su historial de vista y los favoritos que haya anclado. 

Por ejemplo, si solo tiene tres registros en el historial, la búsqueda mostrará esos tres, junto con siete de los registros favoritos. Si no ha anclado ningún favorito, solo se muestran los registros que se han visto más recientemente.

## <a name="types-of-lookups"></a>Tipos de búsquedas

Las búsquedas se clasifican así: 

- **Búsqueda simple:** Seleccione un solo registro en un campo de una sola entidad. 

- **Campos de tipo PartyList:** Use para seleccionar varios registros de varias entidades en una búsqueda. Utilice campos de tipo PartyList para seleccionar varios registros. Esto permite agregar cada registro realizando una nueva búsqueda varias veces. Cada vez que seleccione un registro, podrá realizar una nueva búsqueda de otro registro.
  
- **Campos Referente a:** Use para seleccionar un solo registro de varias entidades en una búsqueda. 

## <a name="search-in-a-lookup-field"></a>Búsqueda en un campo de búsqueda 
Para realizar una búsqueda, seleccione el cuadro de texto y escriba los criterios de búsqueda. Si los registros recientes están habilitados para la búsqueda, se muestran al seleccionar el cuadro de texto.

  > [!div class="mx-imgBorder"]
  > ![Examen de un campo de búsqueda](media/MRU.png "Examen de un campo de búsqueda")  
  
>[!NOTE]   
> El resultado de búsqueda predeterminado de la búsqueda es **empieza por**. Esto significa que los resultados incluyen registros que empiezan por una palabra determinada. Por ejemplo, si quiere buscar **Alpine Ski House**, escriba **alp** en el cuadro de búsqueda; si escribe **ski**, el registro no se muestra en el resultado de la búsqueda.
>
> Para búsquedas con comodines, utilice asteriscos: por ejemplo, escriba \*esquiar o \*esquí\*.

## <a name="browse-in-a-lookup-field"></a>Examen de un campo de búsqueda
Para examinar una búsqueda, seleccione el icono de búsqueda (lupa). En el menú desplegable se muestra una lista completa de elementos.

  > [!div class="mx-imgBorder"]
  > ![Búsqueda en un campo de búsqueda](media/MRU_1.png "Búsqueda en un campo de búsqueda")  
 
## <a name="most-recently-used-record-type-images"></a>Imágenes de los tipos de registros usados más recientemente
La lista de registros usados más recientemente muestra una imagen para ayudar a distinguir entre tipos de registros.

>[!NOTE] 
>Los registros recientes no se filtran por término de búsqueda, vista seleccionada o registros relacionados.

  > [!div class="mx-imgBorder"]
  > ![Campos de búsqueda que muestran una imagen](media/Lookup_03-MRU_Entity_Images_56[1].png "Campos de búsqueda que muestran una imagen")  
  
## <a name="record-type-selection-list"></a>Lista de selección de tipo de registro  
Cuando los resultados abarcan varios tipos de registros, puede ver cuántos tipos hay y seleccionarlos en la lista.

  > [!div class="mx-imgBorder"]
  > ![Visualización del número de registros](media/Lookup_04-MultipleEntityTypes[1].gif "Visualización del número de registros")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>Creación de un nuevo registro si no se encuentra ninguno existente

Si no encuentra un registro, seleccione **Nuevo** en el área de búsqueda para crear un nuevo registro.


### <a name="replace-an-existing-record-from-a-lookup-field"></a>Reemplace un registro existente desde un campo de búsqueda

Puede reemplazar un registro existente mientras usa búsquedas de tipo simple y referente a. Busque un registro. A continuación seleccione el registro, y reemplácelo con un nuevo registro.

### <a name="change-a-view-in-a-lookup-field"></a>Cambiar una vista en un campo de búsqueda 

Seleccionar **Cambiar vista** le permite determinar:
 - Cómo desea ver registros como **Contactos seguidos**, **Vista de búsqueda de contactos** o **Contactos de activos**.
 - Lo que desea ver en los registros, como nombre, correo electrónico, o número de teléfono. Por ejemplo, si desea ver solo los contactos que sigue, seleccione **Cambiar vista** \> **Contactos seguidos**. Solo se muestran los contactos en seguimiento, como se muestra aquí. 

    ![Cambio de vista de tipos de contactos](media/change-view.png "Cambio de vista de tipos de contactos")

### <a name="filter-by-only-my-records-or-filter-by-related-primary-contact"></a>Filtrado por solo mis registros o contacto principal relacionado

Para aplicar filtros adicionales, en el menú **Cambiar vista**, seleccione **Solo mis registros** o **Filtrar por contacto principal relacionado(a)**.

![Adición de más filtros](media/extra_filters.png "Adición de más filtros")

### <a name="choose-from-multiple-records"></a>Elección entre varios registros

Cuando la búsqueda tiene más registros en un campo de los que caben en el área de visualización disponible, esta se contrae, es decir, los registros que caben en el área de visualización se muestran junto al número de registros que no se muestran. Para ver todos los registros, seleccione el número. Las imágenes siguientes muestran la diferencia entre campos contraídos y no contraídos.

**Contraído:**

![Área de visualización multibúsqueda contraída](media/collapsed-multi-lookup-display-area.png "Área de visualización de varias búsquedas contraída")


**No contraído:**

![Área de visualización de varias búsquedas no contraída](media/non-collapsed-multi-lookup-display-area.png "Área de visualización de varias búsquedas no contraída")
