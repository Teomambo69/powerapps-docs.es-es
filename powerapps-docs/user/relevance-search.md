---
title: Búsqueda de relevancia | MicrosoftDocs
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
ms.openlocfilehash: 25daee9c8dabdbfd39cc1995c6d1e3b28e307da3
ms.sourcegitcommit: 4d858e628c89d245317d6192801d136f3591ea52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76832455"
---
# <a name="using-relevance-search-to-search-for-records"></a>Uso de la búsqueda de relevancia para buscar registros

## <a name="what-is-relevance-search"></a>¿Qué es la búsqueda de relevancia?

La búsqueda de relevancia ofrece resultados rápidos y completos en varias entidades, en una sola lista, ordenadas por relevancia. Utiliza un servicio de búsqueda dedicado externo a Common Data Service (con tecnología [!INCLUDE[pn_Windows_Azure](../includes/pn-windows-azure.md)]) para mejorar el rendimiento de la búsqueda. 
  
La búsqueda de relevancia ofrece las siguientes mejoras y ventajas:  
  
- Mejora el rendimiento con indexación externa y [!INCLUDE[pn_azure_shortest](../includes/pn-azure-shortest.md)] tecnología de búsqueda.  
  
- Busca coincidencias con cualquier palabra del término de búsqueda en cualquier campo de la entidad, en comparación con la búsqueda rápida, donde todas las palabras del término de búsqueda se deben encontrar en un campo. 

- Las coincidencias pueden incluir palabras con inflexión como **Stream**, **streaming**o **streaming**.  
  
- Devuelve los resultados de todas las entidades que se pueden buscar en una única lista ordenada por relevancia, por lo que cuanto mejor sea la coincidencia, más alta aparecerá en los resultados. Una coincidencia tiene una mayor relevancia si se encuentran más palabras del término de búsqueda en estrecha proximidad entre sí. Cuanto menor sea la cantidad de texto donde se encuentren las palabras de búsqueda, mayor será la relevancia. Por ejemplo, si encuentra las palabras de búsqueda en el nombre y la dirección de la empresa, podría ser una mejor coincidencia que las mismas palabras que se encuentran en un artículo grande, separadas entre sí.   
  
- Resalta las coincidencias en la lista de resultados. Cuando un término de búsqueda coincide con un término en un registro, el término aparece como texto en negrita y en cursiva en los resultados de la búsqueda. 

    > [!NOTE]
    > - Ciertas palabras que se usan con mucha frecuencia en un lenguaje ( **como o)** se omiten durante **la** búsqueda, ya que no ayudan a identificar los registros de forma exclusiva. Dado que se omiten durante la búsqueda, estas palabras tampoco se resaltan en los resultados.
    > - Los términos resaltados se devuelven a menudo como parte del valor completo en un campo, ya que solo se resaltan los términos coincidentes.  

- Encontrará los resultados de la búsqueda de texto en un documento que está almacenado en Common Data Service, incluido texto en notas, datos adjuntos de correo electrónico o citas. Los siguientes formatos de archivo son compatibles con la búsqueda: PDF, Microsoft Office documentos, HTML, XML, ZIP, EML, texto sin formato y JSON.  
  
- Puede buscar los registros que se comparten con usted y los registros que posee.  
  
  > [!NOTE]
  >  No se admiten los modelos de seguridad jerárquica.  Incluso si ve una fila en Common Data Service porque tiene acceso a ella a través de la seguridad jerárquica, no verá el resultado en la búsqueda de relevancia.  
  
- También puede buscar conjuntos de opciones y búsquedas. Por ejemplo, supongamos que desea buscar una cuenta de tienda que tenga **farmacéuticos** en el nombre. Al buscar una venta al por **menor**, verá el resultado porque hay una coincidencia con el campo del sector, que es un conjunto de opciones de búsqueda.

  > [!NOTE]
  > - La búsqueda de relevancia está basada en texto y solo puede buscar en campos de tipo una línea de texto, varias líneas de texto, conjuntos de opciones o búsquedas. No admite la búsqueda en campos de tipos de datos numéricos o de fecha. 
  
- Use la sintaxis en el término de búsqueda para obtener los resultados que desee. Por ejemplo, escriba **Car Silver 2-Door** para incluir coincidencias de cualquier palabra en el término de búsqueda en los resultados de la búsqueda. Escriba **Car + Silver +2-Door** para buscar solo coincidencias que incluyan las tres palabras. Escriba **Car&#124;Silver&#124;2-Door** para obtener resultados que contengan **coches** o **Silver** o **de 2 puertas**, o las tres palabras. Más información sobre la sintaxis que puede usar en las consultas de búsqueda: [Sintaxis de consulta simple en Azure Search](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search)
  
  > [!NOTE]
  > La búsqueda de relevancia se configura para requerir coincidencias en cualquier (en lugar de todos) de los criterios de una consulta, lo que puede dar lugar a resultados diferentes de sus expectativas. Esto es especialmente cierto cuando se incluyen operadores booleanos en la consulta.

## <a name="enable-relevance-search"></a>Habilitar la búsqueda de relevancia

La búsqueda de relevancia está deshabilitada de forma predeterminada. El administrador debe habilitarla para la organización, lo que permite a todos los usuarios de la organización usarla. Después de habilitar la búsqueda de relevancia, es posible que tenga que esperar hasta una hora o más, en función del tamaño de la organización, antes de empezar a ver los resultados de la búsqueda de relevancia para las aplicaciones. Los cambios más pequeños en los datos indizados pueden tardar hasta 15 minutos en aparecer en el sistema.

## <a name="switch-between-relevance-and-categorized-search"></a>Cambiar entre la búsqueda por relevancia y por categorías

Si su organización ha activado ambas opciones de búsqueda (relevancia y búsqueda por categorías), puede cambiar entre las dos.

1. Para cambiar entre los tipos de búsqueda, en la barra de navegación, seleccione el botón **Buscar** .

2. A la izquierda, seleccione el menú desplegable para cambiar entre la búsqueda por **relevancia** o la **búsqueda por categorías**.

   > [!div class="mx-imgBorder"]
   > ![Cambiar entre la búsqueda por relevancia y por categorías](media/switch-global-search.png "Cambiar entre la búsqueda por relevancia y por categorías") 
    
## <a name="set-a-default-search-experience"></a>Establecer una experiencia de búsqueda predeterminada

Si su organización ha activado ambas opciones de búsqueda, puede seleccionar una experiencia de búsqueda predeterminada en su configuración personal.

1. En la esquina superior derecha de la página, seleccione **configuración** y, a continuación, seleccione **configuración de personalización**.  
  
   > [!div class="mx-imgBorder"]
   > ![Configuración de personalización](media/personalization-settings.png "Configuración de personalización")  

2. En la pestaña **General** , en la sección **seleccionar la experiencia de búsqueda predeterminada** , para la **experiencia de búsqueda predeterminada**, seleccione su experiencia predeterminada. 

   > [!div class="mx-imgBorder"]
   > ![Seleccionar experiencia de búsqueda predeterminada](media/default-search-experience.png "Seleccionar experiencia de búsqueda predeterminada")  

## <a name="start-a-search"></a>Iniciar una búsqueda 
 
1.  En la barra de navegación superior, seleccione el botón **Buscar** .  

    > [!div class="mx-imgBorder"]
    > ![Botón de búsqueda global](media/global-search-button.png "Botón de búsqueda global") 
  
2.  Escriba las palabras de búsqueda en el cuadro de búsqueda y, a continuación, seleccione el botón **Buscar** .   

    > [!div class="mx-imgBorder"]
    > ![Cuadro de búsqueda de relevancia](media/relevance-search-box.png "Cuadro de búsqueda de relevancia")   

## <a name="filter-records-with-facets"></a>Filtrar registros con aspectos  
Con Common Data Service, ahora puede refinar los resultados de la búsqueda mediante el uso de aspectos y filtros. Las caras y los filtros permiten profundizar y explorar los resultados de la búsqueda actual sin tener que refinar el término de búsqueda repetidamente. 

Las caras están disponibles en el panel izquierdo. Inmediatamente después de realizar una búsqueda, están disponibles las siguientes caras globales para cuatro campos comunes:  
  
-   Tipo de registro  
  
-   Owner  
  
-   Creado el  
  
-   Modificado el  
  
### <a name="record-type-facets"></a>Aspectos del tipo de registro  
Para restringir los resultados de la búsqueda a una entidad específica, seleccione la entidad en la sección **tipo de registro** .  
 
  > [!div class="mx-imgBorder"]
  > ![Faceta de tipo de registro para restringir los resultados de la búsqueda](media/relevance-search-record-type-facet.png "Faceta de tipo de registro que se usa para restringir los resultados de búsqueda")  
  
Al filtrar por un tipo de registro específico, puede incluir actividades y notas relacionadas con el registro seleccionado en los resultados de la búsqueda. Para ello, active la casilla **notas relacionadas & actividades** . Las actividades y las notas aparecerán en los resultados de nivel superior.
 
  > [!div class="mx-imgBorder"]
  > ![Incluir notas y actividades relacionadas con un tipo de registro en los resultados de la búsqueda](media/relevance-search-record-type-facet-related-notes-activities.png "Incluir notas y actividades relacionadas con un tipo de registro en los resultados de la búsqueda")  
  
Los resultados de la búsqueda que se encuentran en datos adjuntos de correo electrónico o entidades de cita se muestran en los resultados de búsqueda bajo su registro primario, ya sea correo electrónico o cita.  
  
Al refinar por tipo de registro, el ámbito de la faceta cambia a la entidad seleccionada y se muestran hasta cuatro facetas que son específicas de la entidad. Por ejemplo, si selecciona la entidad cuenta, verá la faceta **contacto principal** además de las facetas globales.  
  
En el cuadro de diálogo **establecer opciones personales** , también puede elegir otras caras de las que el administrador del sistema o el cliente han puesto a su disposición. La configuración de usuario invalida la configuración predeterminada. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [configurar las caras y los filtros de la búsqueda](#BKMK_ConfigureFacets)  
  
### <a name="text-based-facets"></a>Aspectos basados en texto  
Todas las búsquedas, los conjuntos de opciones y los tipos de registro son aspectos basados en texto. Por ejemplo, el propietario de la faceta basada en texto se compone de una lista de valores de campo y sus recuentos correspondientes.  
 
  > [!div class="mx-imgBorder"]
  > ![Faceta basada en texto en la búsqueda de relevancia](media/relevance-search-text-based-facets.png "Faceta basada en texto en la búsqueda de relevancia")  
  
Los filtros de estas caras se ordenan en orden descendente por recuento. De forma predeterminada, se muestran los cuatro valores principales de faceta. Cuando haya más de cuatro valores de faceta, verá un vínculo **Mostrar más** que puede seleccionar para expandir la lista y ver hasta quince valores de faceta superior. Seleccione cada valor para filtrar los resultados de la búsqueda y mostrar solo los registros en los que el campo tenga el valor seleccionado. Por ejemplo, si selecciona **Jim Glynn**, los resultados de la búsqueda mostrarán todos los registros en los que el propietario es Jim Glynn. Al seleccionar un valor de faceta búsqueda o conjunto de opciones, los resultados de la búsqueda se filtran para incluir solo los registros con el valor especificado.  
  
### <a name="date-and-time-facets"></a>Aspectos de fecha y hora  
Al igual que otras caras, puede usar las caras de fecha y hora para filtrar y ver los resultados de la búsqueda para un momento concreto. Para seleccionar un intervalo de valores, arrastre el control deslizante o seleccione una de las columnas verticales.  
 
  > [!div class="mx-imgBorder"]
  > ![Aspectos de fecha y hora para la búsqueda de relevancia](media/relevance-search-date-time-facets.png "Aspectos de fecha y hora para la búsqueda de relevancia")  

<a name="BKMK_ConfigureFacets"></a>

## <a name="configure-facets-and-filters"></a>Configurar aspectos y filtros    
  
> [!NOTE]
>  Un Personalizador del sistema puede establecer la experiencia predeterminada para todas las entidades, pero puede configurar sus propias caras y filtros.  
  
1. En la parte superior derecha, seleccione **configuración** y, a continuación, seleccione **configuración de personalización**.  
  
   > [!div class="mx-imgBorder"]
   > ![Configuración de personalización](media/personalization-settings.png "Configuración de personalización")    
  
2. En la pestaña **General** , en la sección **seleccionar la experiencia de búsqueda predeterminada** , en el campo **aspectos y filtros** , seleccione **configurar**.  

   > [!div class="mx-imgBorder"]
   > ![Configurar aspectos y filtros](media/configure-facets-filters.png "Configurar aspectos y filtros")  
  
3. En el cuadro de diálogo **configurar aspectos y filtros** , especifique las caras que le gustaría ver para una entidad. El administrador del sistema o el personalizador pueden establecer una experiencia predeterminada para todas las entidades, pero aquí puede establecer las suyas propias.  
  
   - En la lista desplegable **seleccionar entidad** , seleccione una entidad para la que desee configurar las caras. Esta lista desplegable contiene solo las entidades que están habilitadas para la búsqueda de relevancia.  
  
   - En la entidad seleccionada, seleccione hasta cuatro campos de faceta. De forma predeterminada, los cuatro primeros campos con facetas de la vista **búsqueda rápida** de la entidad seleccionada se seleccionan en la lista. En cualquier momento, solo puede tener cuatro campos seleccionados como aspectos.  
  
   Puede actualizar varias entidades al mismo tiempo. Al seleccionar **Aceptar**, se guardan los cambios de todas las entidades que ha configurado. Para revertir al comportamiento predeterminado de una entidad que configuró anteriormente, seleccione **predeterminado**.  
  
   > [!NOTE]
   > - Si un Personalizador del sistema elimina un campo o hace que ya no se puede buscar y ha guardado una faceta para ese campo, ya no aparecerá como una faceta.  
   >   -   Solo verá los campos que existen en la solución predeterminada y que están configurados como que el personalizador del sistema puede buscar.  
