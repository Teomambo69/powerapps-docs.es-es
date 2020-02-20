---
title: Búsqueda por relevancia | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/28/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3a78e555c8818144b41935715ab9f983c7d9714b
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918788"
---
# <a name="using-relevance-search-to-search-for-records"></a>Uso de la búsqueda por relevancia para buscar registros

## <a name="what-is-relevance-search"></a>¿En qué consiste la búsqueda por relevancia?

La búsqueda por relevancia ofrece resultados rápidos y completos de varias entidades en una sola lista ordenados por relevancia. Usa un servicio de búsqueda dedicado ajeno a Common Data Service (con tecnología de [!INCLUDE[pn_Windows_Azure](../includes/pn-windows-azure.md)]) para mejorar el rendimiento de la búsqueda.
  
La búsqueda por relevancia aporta las siguientes mejoras y ventajas:  
<!--note from editor: Edits to these list items are suggested, so they can be parallel throughout this section.-->  
- Mejora el rendimiento mediante la indexación externa y la tecnología de búsqueda de [!INCLUDE[pn_azure_shortest](../includes/pn-azure-shortest.md)].  
  
- Busca coincidencias con cualquier palabra del término de búsqueda en cualquier campo de la entidad, en comparación con la búsqueda rápida, donde todas las palabras del término de búsqueda se deben encontrar en un campo. 

- Busca coincidencias que incluyen palabras flexionadas como **transmitir**, **transmisión** o **transmitido**.  
  
- Devuelve resultados de todas las entidades que permiten búsquedas en una sola lista ordenados por relevancia, lo que significa que cuanto mejor es la coincidencia, el resultado aparecerá más arriba en la lista. Una coincidencia tiene una mayor relevancia si se encuentran más palabras del término de búsqueda en estrecha proximidad entre sí. Cuanto menor sea la cantidad de texto donde se encuentran las palabras de búsqueda, mayor es la relevancia. Por ejemplo, si encuentra las palabras de búsqueda en el nombre y la dirección de una empresa, sería una mejor coincidencia que encontrar las mismas palabras en un artículo largo, muy separadas entre sí.
  
- Resalta las coincidencias en la lista de resultados. Cuando un término de búsqueda coincide con un término de un registro, el término aparece como texto en negrita y cursiva en los resultados de la búsqueda. 

    > [!NOTE]
    > - Determinadas palabras de uso muy común en un idioma (como **el** o **un**) se omiten durante la búsqueda, ya que no ayudan a identificar los registros de forma exclusiva. Puesto que se omiten durante la búsqueda, tampoco se resaltan en los resultados.
    > - Los términos resaltados suelen devolverse como parte del valor completo de un campo, ya que solo se resaltan los términos coincidentes.  

- Incluye resultados de búsqueda del texto de un documento almacenado en Common Data Service, lo que incluye texto en notas, datos adjuntos de correo electrónico o citas. En la búsqueda se admiten los siguientes formatos de archivo: PDF, documentos de Microsoft Office, HTML, XML, ZIP, EML, texto sin formato y JSON.  
  
- Permite buscar registros compartidos con usted y otros de los que es propietario.  
  
  > [!NOTE]
  >  No se admiten modelos de seguridad jerárquica. Aunque vea una fila de Common Data Service porque tiene acceso a ella por medio de la seguridad jerárquica, no ve el resultado en la búsqueda por relevancia.  
  
- También permite buscar conjuntos de opciones y búsquedas. Por ejemplo, imagine que quiere buscar una cuenta de tienda que tenga **Farmacéutica** en el nombre. Al buscar **Tienda farmacéutica**, encuentra el resultado, ya que hay una coincidencia con el campo Sector, que es un conjunto de opciones que permite búsquedas.

  > [!NOTE]
  > - La búsqueda por relevancia está basada en texto y solo permite buscar en campos de tipo Una línea de texto, Varias líneas de texto, Conjuntos de opciones o Búsquedas. No admite la búsqueda en campos con tipos de datos numéricos o de fecha.
  
- Permite usar sintaxis en el término de búsqueda para obtener los resultados deseados. Por ejemplo, escriba **coche plata todoterreno** para incluir coincidencias de cualquier palabra del término de búsqueda en los resultados de la búsqueda. Escriba **coche+plata+todoterreno** para buscar solo coincidencias que incluyan las tres palabras. Escriba **coche&#124;plata&#124;todoterreno** para obtener resultados que contengan **coche**, **plata**, **todoterreno** o las tres palabras. Para obtener más información sobre la sintaxis que se puede usar en las consultas de búsqueda, vea [Sintaxis de consulta simple en Azure Cognitive Search](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search).<!--note from editor: The "More information:" pattern is good when there aren't any additional modifiers, which you have here. -->
  
  > [!NOTE]
  > La búsqueda por relevancia está configurada para requerir coincidencias con cualquiera (en lugar de todos) de los criterios de una consulta, lo que puede dar lugar a resultados diferentes a sus expectativas. Esto es especialmente cierto cuando se incluyen operadores booleanos en la consulta.<!--note from editor: Via style guide, it's always capital "Boolean," and it's "might" instead of "may.-->

## <a name="enable-relevance-search"></a>Habilitación de la búsqueda por relevancia

La búsqueda por relevancia está deshabilitada de forma predeterminada. El administrador debe habilitarla para la organización, lo que permite a todos los usuarios de esta usarla. Después de habilitar la búsqueda por relevancia, es posible que tenga que esperar hasta una hora o más, en función del tamaño de la organización, para empezar a ver resultados de la búsqueda por relevancia para las aplicaciones. Los cambios más pequeños en los datos indexados pueden tardar hasta 15 minutos en aparecer en el sistema.

## <a name="switch-between-relevance-search-and-categorized-search"></a>Cambio entre búsqueda por relevancia y búsqueda categorizada

Si la organización ha activado ambas opciones de búsqueda (búsqueda por relevancia y búsqueda categorizada), puede cambiar entre las dos.

1. Para cambiar entre tipos de búsqueda, en la barra de navegación, seleccione **Buscar**.

2. A la izquierda, seleccione el menú desplegable para cambiar entre **Búsqueda por relevancia** o **Búsqueda categorizada**.

   > [!div class="mx-imgBorder"]
   > ![Cambio entre la búsqueda por relevancia y categorizada](media/switch-global-search.png "Cambio entre búsqueda por relevancia y búsqueda categorizada") 
    
## <a name="set-a-default-search-experience"></a>Establecimiento de una experiencia de búsqueda predeterminada

Si la organización ha activado ambas opciones de búsqueda, puede seleccionar una experiencia de búsqueda predeterminada en la configuración personal.

1. En la esquina superior derecha de la página, seleccione **Configuración** y después **Configuración de personalización**.  
  
   > [!div class="mx-imgBorder"]
   > ![Configuración de personalización](media/personalization-settings.png "Configuración de personalización")  

2. En la pestaña **General**, en la sección **Seleccione la experiencia de búsqueda predeterminada**, en **Experiencia de búsqueda predeterminada**, seleccione la experiencia predeterminada. 

   > [!div class="mx-imgBorder"]
   > ![Selección de la experiencia de búsqueda predeterminada](media/default-search-experience.png "Selección de una experiencia de búsqueda predeterminada")  

## <a name="start-a-search"></a>Inicio de una búsqueda 
 
1.  En la barra de navegación superior, seleccione **Buscar**.  

    > [!div class="mx-imgBorder"]
    > ![Botón de búsqueda global](media/global-search-button.png "Búsqueda global") 
  
2.  Escriba las palabras de búsqueda en el cuadro de búsqueda y seleccione **Buscar**.

    > [!div class="mx-imgBorder"]
    > ![Cuadro de búsqueda por relevancia](media/relevance-search-box.png "Cuadro de búsqueda por relevancia")   

## <a name="filter-records-with-facets"></a>Filtrado de registros con facetas

Con Common Data Service, puede refinar los resultados de búsqueda mediante facetas y filtros. Las facetas y los filtros permiten aumentar el detalle de los resultados de la búsqueda actual y examinarlos sin necesidad de refinar de forma repetida los términos de búsqueda.

Las facetas están disponibles en el panel izquierdo. Inmediatamente después de realizar una búsqueda, están disponibles las siguientes facetas globales para cuatro campos comunes:  
  
-   Tipo de registro  
  
-   Propietario  
  
-   Creada el  
  
-   Fecha de modificación  
  
### <a name="record-type-facets"></a>Facetas de Tipo de registro

Para restringir los resultados de búsqueda a una entidad concreta, seleccione la entidad en la sección **Tipo de registro**.  
 
  > [!div class="mx-imgBorder"]
  > ![Faceta de Tipo de registro para restringir los resultados de búsqueda](media/relevance-search-record-type-facet.png "Faceta de Tipo de registro usada para restringir los resultados de búsqueda")  
  
Al filtrar por un tipo de registro específico, puede incluir actividades y notas relacionadas con el registro seleccionado en los resultados de la búsqueda. Para ello, active la casilla **Actividades y notas relacionadas**. Las actividades y las notas aparecen en los resultados de nivel superior.
 
  > [!div class="mx-imgBorder"]
  > ![Inclusión de notas y actividades relacionadas con un tipo de registro en los resultados de la búsqueda](media/relevance-search-record-type-facet-related-notes-activities.png "Inclusión de notas y actividades relacionadas con un tipo de registro en los resultados de la búsqueda")  
  
Los resultados de búsqueda que se encuentran en entidades de datos adjuntos de correo electrónico o de cita se muestran en los resultados de búsqueda bajo su registro primario, ya sea Correo electrónico o Cita.  
  
Al refinar por tipo de registro, el ámbito de la faceta cambia a la entidad seleccionada y se muestran hasta cuatro facetas específicas de la entidad. Por ejemplo, si selecciona la entidad Cuenta, ve la faceta **Contacto principal** además de las facetas globales.  
  
En el cuadro de diálogo **Definir opciones personales**, también puede elegir otras facetas entre las que el administrador del sistema o el cliente han puesto a su disposición. La configuración del usuario invalida a la predeterminada. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [Configuración de facetas y filtros para la búsqueda](#BKMK_ConfigureFacets)  
  
### <a name="text-based-facets"></a>Facetas basadas en texto

Todas las búsquedas, los conjuntos de opciones y los tipos de registro son facetas basadas en texto. Por ejemplo, la faceta basada en texto Propietario se compone de una lista de valores de campo y sus recuentos correspondientes.  
 
  > [!div class="mx-imgBorder"]
  > ![Faceta basada en texto en búsqueda por relevancia](media/relevance-search-text-based-facets.png "Faceta basada en texto en búsqueda por relevancia")  
  
Los filtros de estas facetas se organizan en orden descendente por recuento. De forma predeterminada, se muestran los cuatro valores de faceta superiores. Si hay más de cuatro valores de faceta, se ve un vínculo **MOSTRAR MÁS** que se puede seleccionar para expandir la lista y ver hasta quince valores de faceta superiores. Seleccione cada valor para filtrar los resultados de búsqueda y mostrar solo los registros cuyo campo tenga el valor seleccionado. Por ejemplo, si selecciona **Jim Glynn**, los resultados de búsqueda muestran todos los registros cuyo propietario es Jim Glynn. Al seleccionar un valor de faceta de búsqueda o conjunto de opciones, los resultados de búsqueda se filtran para incluir únicamente los registros con el valor especificado.  
  
### <a name="date-and-time-facets"></a>Facetas de fecha y hora

Al igual que ocurre con otras facetas, puede usar las facetas de fecha y hora para filtrar y ver resultados de búsqueda de un momento concreto. Para seleccionar un intervalo de valores, arrastre el control deslizante o seleccione una de las columnas verticales.  
 
  > [!div class="mx-imgBorder"]
  > ![Facetas de fecha y hora para búsqueda por relevancia](media/relevance-search-date-time-facets.png "Facetas de fecha y hora para búsqueda por relevancia")  

<a name="BKMK_ConfigureFacets"></a>

## <a name="configure-facets-and-filters"></a>Configuración de facetas y filtros
  
> [!NOTE]
>  Un personalizador del sistema puede establecer la experiencia predeterminada para todas las entidades, pero el usuario puede configurar sus propias facetas y filtros.  
  
1. En la esquina superior derecha, seleccione **Configuración** y después **Configuración de personalización**.  
  
   > [!div class="mx-imgBorder"]
   > ![Configuración de personalización](media/personalization-settings.png "Configuración de personalización")
  
2. En la pestaña **General**, en la sección **Seleccione la experiencia de búsqueda predeterminada**, en el campo **Facetas y filtros**, seleccione **Configurar**.  

   > [!div class="mx-imgBorder"]
   > ![Configuración de facetas y filtros](media/configure-facets-filters.png "Configuración de facetas y filtros")  
  
3. En el cuadro de diálogo **Configurar facetas y filtros**, especifique las facetas que quiere ver para una entidad. El administrador del sistema o el personalizador pueden establecer una experiencia predeterminada para todas las entidades, pero aquí puede establecer una propia.  
  
   - En la lista desplegable **Seleccionar entidad**, seleccione una entidad para la que quiera configurar facetas. Esta lista desplegable contiene solo las entidades que están habilitadas para la búsqueda por relevancia.  
  
   - En la entidad seleccionada, seleccione hasta cuatro campos de faceta. De forma predeterminada, en la lista se seleccionan los cuatro primeros campos a los que se pueden aplicar facetas de la vista **Búsqueda rápida** de la entidad seleccionada. En todo momento solo se pueden tener cuatro campos seleccionados como facetas.  
  
   Puede actualizar varias entidades a la vez. Al seleccionar **Aceptar**, se guardan los cambios de todas las entidades configuradas. Para revertir al comportamiento predeterminado de una entidad que se ha configurado previamente, seleccione **Predeterminado**.  
  
   > [!NOTE]
   > - Si un personalizador del sistema elimina un campo o lo convierte en un campo que no permite búsquedas, y ha guardado una faceta para ese campo, ya no aparece como una faceta.  
   >   -   Solo se ven los campos que existen en la solución predeterminada y que el personalizador del sistema ha configurado como campos que permiten búsquedas.  
