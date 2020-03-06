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
ms.openlocfilehash: 482d06a91d3cb3a7c22e41e4e880aa72294d2b3f
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264973"
---
#  <a name="use-the-lookup-field-on-a-record"></a>Uso del campo de búsqueda en un registro

La búsqueda ayuda a elegir registros de una entidad relacionada. Al seleccionar una entidad relacionada y especificar criterios de búsqueda, como un nombre o una dirección de correo electrónico, la búsqueda comienza automáticamente a resolver el texto parcial y muestra los registros coincidentes. Si no se muestra ningún registro después de escribir el texto completo de los criterios de búsqueda, aparece un mensaje que indica que no hay registros.

Por ejemplo, puede buscar el nombre **Adrian Dumitrascu**. Al escribir **ad**, los posibles registros coincidentes se rellenan y se muestran automáticamente.

  > [!div class="mx-imgBorder"]
  > ![Registros coincidentes rellenados automáticamente](media/automatically-populate-matching-records.png "Registros coincidentes rellenados automáticamente")
  
>[!NOTE] 
>Un administrador puede definir los criterios que usa la búsqueda para resolver el texto de búsqueda parcial.

Además, puede crear un nuevo registro si selecciona el botón **Nuevo**. Debe tener suficientes permisos para ver el botón **Nuevo** y crear un registro. Al seleccionar el campo de búsqueda, se muestran los cinco registros usados más recientemente junto con cinco registros favoritos. Los registros que aparecen dependen del historial de vista y de los favoritos que haya anclado. 

Por ejemplo, si solo tiene tres registros en el historial, la búsqueda muestra esos tres junto con siete de los registros favoritos. Si no ha anclado ningún favorito, solo se muestran los registros que se han visto más recientemente.

## <a name="types-of-lookups"></a>Tipos de búsquedas

Las búsquedas se clasifican así: 

- **Búsqueda simple:** seleccione un único registro de un campo de una sola entidad. 

- **Campos de tipo de lista de partes:** use este tipo para seleccionar varios registros de varias entidades en una búsqueda. Use los campos de tipo de lista de partes para seleccionar varios registros. Esto permite agregar cada registro mediante una nueva búsqueda, varias veces. Cada vez que se selecciona un registro, se puede realizar una nueva búsqueda de otro registro.
  
- **Campos de tipo referente a:** use este tipo para seleccionar un solo registro de varias entidades en una búsqueda. 

## <a name="search-in-a-lookup-field"></a>Búsqueda en un campo de búsqueda 
Para realizar una búsqueda, seleccione el cuadro de texto y escriba los criterios de búsqueda. Si los registros recientes están habilitados para la búsqueda, se muestran al seleccionar el cuadro de texto.

  > [!div class="mx-imgBorder"]
  > ![Examen de un campo de búsqueda](media/MRU.png "Examen de un campo de búsqueda")  
  
>[!NOTE]   
> El resultado de búsqueda predeterminado de la búsqueda es **empieza por**. Esto significa que los resultados incluyen registros que empiezan por una palabra determinada. Por ejemplo, si quiere buscar **Alpine Ski House**, escriba **alp** en el cuadro de búsqueda; si escribe **ski**, el registro no se muestra en el resultado de la búsqueda.
>
> Para una búsqueda con caracteres comodín, use asteriscos: Por ejemplo, escriba \*ski o \*ski\*.

## <a name="browse-in-a-lookup-field"></a>Examen de un campo de búsqueda
Para examinar una búsqueda, seleccione el icono de búsqueda (lupa). En el menú desplegable se muestra una lista completa de elementos.

  > [!div class="mx-imgBorder"]
  > ![Búsqueda en un campo de búsqueda](media/MRU_1.png "Búsqueda en un campo de búsqueda")  
 
## <a name="most-recently-used-record-type-images"></a>Imágenes de los tipos de registros usados más recientemente
La lista de registros usados más recientemente muestra una imagen para ayudar a distinguir entre tipos de registros.

>[!NOTE] 
>Los registros recientes no se filtran por término de búsqueda ni vista seleccionada.

  > [!div class="mx-imgBorder"]
  > ![Campos de búsqueda que muestran una imagen](media/Lookup_03-MRU_Entity_Images_56[1].png "Campos de búsqueda que muestran una imagen")  
  
## <a name="record-type-selection-list"></a>Lista de selección de tipo de registro  
Cuando los resultados abarcan varios tipos de registros, puede ver cuántos tipos hay y seleccionarlos en la lista.

  > [!div class="mx-imgBorder"]
  > ![Visualización del número de registros](media/Lookup_04-MultipleEntityTypes[1].gif "Visualización del número de registros")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>Creación de un nuevo registro si no se encuentra ninguno existente

Si no encuentra un registro, seleccione **Nuevo** en el área de búsqueda para crear un nuevo registro.


### <a name="replace-an-existing-record-from-a-lookup-field"></a>Reemplazo de un registro existente en un campo de búsqueda

Puede reemplazar un registro existente mientras usa búsquedas simples y de tipo referente a. Busque un registro. Luego selecciónelo y reemplácelo por uno nuevo.

### <a name="change-a-view-in-a-lookup-field"></a>Cambio de una vista en un campo de búsqueda 

La selección de **Cambiar vista** permite determinar:
 - Cómo se quieren ver registros como **Contactos en seguimiento**, **Vista de búsqueda de contactos** o **Contactos activos**.
 - Qué se quiere ver en los registros, como el nombre, el correo electrónico o el número de teléfono. Por ejemplo, si solo quiere ver los contactos en seguimiento, seleccione **Cambiar vista** \> **Contactos en seguimiento**. Solo se muestran los contactos en seguimiento, como se muestra aquí. 

    ![Cambio de vista de tipos de contactos](media/change-view.png "Cambio de vista de tipos de contactos")

>[!IMPORTANT] 
>La opción **Cambiar vista** no es visible si el administrador no ha configurado la opción para que aparezca en las vistas.

### <a name="choose-from-multiple-records"></a>Elección entre varios registros

Cuando la búsqueda tiene más registros en un campo de los que caben en el área de visualización disponible, esta se contrae, es decir, los registros que caben en el área de visualización se muestran junto al número de registros que no se muestran. Para ver todos los registros, seleccione el número. En las imágenes siguientes se muestra la diferencia entre los campos contraídos y no contraídos.

**Contraídos:**

![Área de visualización de varias búsquedas contraída](media/collapsed-multi-lookup-display-area.png "Área de visualización de varias búsquedas contraída")


**No contraídos:**

![Área de visualización de varias búsquedas no contraída](media/non-collapsed-multi-lookup-display-area.png "Área de visualización de varias búsquedas no contraída")
