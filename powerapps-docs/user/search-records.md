---
title: Buscar registros en aplicaciones controladas por modelos | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 26903543232025f43f935a403800ed27170e3123
ms.sourcegitcommit: 7c46e7ce889e2f1c5352ed2e705b0bb8968f2a89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940922"
---
# <a name="search-for-records-in-an-app"></a>Búsqueda de registros en una aplicación

Puede buscar registros en varias entidades mediante la búsqueda por relevancia o la búsqueda por categorías en Common Data Service. 

- La búsqueda de relevancia ofrece resultados rápidos y completos en varias entidades, en una sola lista, ordenadas por relevancia. Utiliza un servicio de búsqueda dedicado externo a Common Data Service (con tecnología [!INCLUDE[pn_Windows_Azure](../includes/pn-windows-azure.md)]) para mejorar el rendimiento de la búsqueda. 
- La búsqueda por categorías devuelve los resultados de la búsqueda agrupados por tipos de entidad, como cuentas, contactos o clientes potenciales.

Normalmente, la búsqueda por categorías es la opción de búsqueda predeterminada. Sin embargo, si la organización habilita la búsqueda de relevancia, se convierte en la experiencia de búsqueda predeterminada.  

Para buscar registros de un solo tipo, puede usar la vista búsqueda rápida de la cuadrícula de la entidad.
  
## <a name="normal-quick-find-categorized-search"></a>Búsqueda rápida normal (búsqueda por categorías) 

Con el uso de categorías, puede buscar registros que comienzan por una palabra específica o usar un carácter comodín.
  
- **Comienza por**: Los resultados incluyen registros que comienzan con una palabra específica. Por ejemplo, si desea buscar "Alpine Ski House", escriba **Alp** en el cuadro de búsqueda; Si escribe **Ski**, el registro no se mostrará.  
  
- **Carácter comodín**: Por ejemplo, * ski o * Ski @ no__t-0. 
  
## <a name="relevance-search"></a>Búsqueda de relevancia
  
  La búsqueda de relevancia está disponible además de otras búsquedas Common Data Service en las que ya está familiarizado. Puede seguir usando la búsqueda rápida de una sola entidad en la cuadrícula de entidades o la búsqueda rápida de varias entidades (denominada búsqueda por categorías, si tiene habilitada la búsqueda de relevancia). Para obtener resultados más detallados y más rápidos, se recomienda usar la búsqueda de relevancia.  

 La búsqueda de relevancia ofrece las siguientes mejoras y ventajas:  
  
- Mejora el rendimiento con indexación externa y tecnología de búsqueda [!INCLUDE[pn_azure_shortest](../includes/pn-azure-shortest.md)].  
  
- Busca coincidencias con cualquier palabra del término de búsqueda en cualquier campo de la entidad. Las coincidencias pueden incluir palabras con inflexión como **Stream**, **streaming**o **streaming**.  
  
- Devuelve los resultados de todas las entidades que se pueden buscar en una única lista ordenada por relevancia, en función de factores como el número de palabras coincidentes o su proximidad entre sí en el texto.  
  
- Resalta las coincidencias en la lista de resultados.  

- Encontrará los resultados de la búsqueda de texto en un documento que está almacenado en Common Data Service, incluido texto en notas, datos adjuntos de correo electrónico o citas. En la búsqueda se admiten los siguientes formatos de archivo: PDF, Microsoft Office documentos, HTML, XML, ZIP, EML, texto sin formato y JSON.  
  
- Puede buscar los registros que se comparten con usted y los registros que posee.  
  
  > [!NOTE]
  >  No se admiten los modelos de seguridad jerárquica.  Incluso si ve una fila en Common Data Service porque tiene acceso a ella a través de la seguridad jerárquica, no verá el resultado en la búsqueda de relevancia.  
  
- También puede buscar conjuntos de opciones y búsquedas. Por ejemplo, supongamos que desea buscar una cuenta de tienda que tenga **farmacéuticos** en el nombre. Al buscar una venta al por **menor**, verá el resultado porque hay una coincidencia con el campo del sector, que es un conjunto de opciones de búsqueda.  
  
  Dado que los resultados pueden incluir una combinación de entidades, puede restringir los resultados de la búsqueda a una entidad específica seleccionando una entidad en la lista desplegable **filtrar con** . Al filtrar por un tipo de registro específico, puede incluir actividades y notas relacionadas con el registro seleccionado en los resultados de la búsqueda. Para ello, active la casilla **buscar actividades y notas para los registros seleccionados** a la derecha de la lista desplegable **filtrar con** . La casilla se activa después de seleccionar un registro en la lista desplegable **filtrar con** . se desactiva si no seleccionó una entidad en la lista **filtrar con** . Las actividades y las notas se devuelven como resultados de nivel superior.
  
  > [!NOTE]
  > - La búsqueda de relevancia está deshabilitada de forma predeterminada. El administrador debe habilitarla para la organización. Después de habilitar la búsqueda de relevancia, es posible que tenga que esperar hasta una hora o más, en función del tamaño de la organización, antes de empezar a ver los resultados de la búsqueda de relevancia para las aplicaciones. Los cambios más pequeños en los datos indizados pueden tardar hasta 15 minutos en aparecer en el sistema.
  > - La habilitación de la búsqueda de relevancia permite a todos los usuarios de la organización utilizarla.  
  > - La búsqueda de relevancia está basada en texto y solo puede buscar en campos de tipo una línea de texto, varias líneas de texto, conjuntos de opciones o búsquedas. No admite la búsqueda en campos de tipos de datos numéricos o de fecha. 
  
 Aunque la búsqueda de relevancia encuentra coincidencias con cualquier palabra en el término de búsqueda de cualquier campo de una entidad, en una búsqueda rápida @ no__t-0even con la búsqueda de texto completo habilitada @ no__t-1All las palabras del término de búsqueda se deben encontrar en un campo.  
  
 En la búsqueda de relevancia, cuanto mejor sea la coincidencia, más alta aparecerá en los resultados. Una coincidencia tiene una mayor relevancia si se encuentran más palabras del término de búsqueda en estrecha proximidad entre sí. Cuanto menor sea la cantidad de texto donde se encuentren las palabras de búsqueda, mayor será la relevancia. Por ejemplo, si encuentra las palabras de búsqueda en el nombre y la dirección de la empresa, podría ser una mejor coincidencia que las mismas palabras que se encuentran en un artículo grande, separadas entre sí. Dado que los resultados se devuelven en una sola lista, puede ver una combinación de registros mostrados uno después de otro, como cuentas, oportunidades, clientes potenciales, etc. Se resaltan las palabras coincidentes de la lista.  
  
 Use la sintaxis en el término de búsqueda para obtener los resultados que desee. Por ejemplo, escriba **Car Silver 2-Door** para incluir coincidencias de cualquier palabra en el término de búsqueda en los resultados de la búsqueda. Escriba **Car + Silver +2-Door** para buscar solo coincidencias que incluyan las tres palabras. Escriba **Car&#124;Silver&#124;2-Door** para obtener resultados que contengan **coches** o **Silver** o **de 2 puertas**, o las tres palabras. Más información sobre la sintaxis que puede usar en las consultas de búsqueda: [Sintaxis de consulta simple en Azure Search](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search)


> [!NOTE]
> Verá los resaltados de aciertos cuando el término de búsqueda coincide con un término de la aplicación. Los resaltados de aciertos aparecen como texto en negrita y en cursiva en los resultados de la búsqueda. A menudo se devuelven como parte del valor completo en un campo, ya que solo se resaltan los términos coincidentes. 
  
  
<a name=" #BKMK_DefaultOption "></a>
## <a name="switch-between-relevance-and-categorized-search"></a>Cambiar entre la búsqueda por relevancia y por categorías

Si su organización ha activado ambas opciones de búsqueda (relevancia y búsqueda por categorías), puede cambiar entre las dos.

1. Para cambiar entre los tipos de búsqueda, en la barra de navegación, seleccione el botón **Buscar** .

2. A la izquierda, seleccione el menú desplegable para cambiar entre la búsqueda por **relevancia** o la **búsqueda por categorías**.

   > [!div class="mx-imgBorder"]
   > ![Cambiar entre la relevancia y el cambio de búsqueda por categorías](media/switch-search.png "entre la relevancia y la búsqueda por categorías") 
    
### <a name="set-a-default-experience"></a>Establecer una experiencia predeterminada

Si su organización ha activado ambas opciones de búsqueda, puede seleccionar una experiencia de búsqueda predeterminada en su configuración personal.

1. En la esquina superior derecha de la página, seleccione **configuración** y, a continuación, seleccione **configuración de personalización**.  
  
   > [!div class="mx-imgBorder"]
   > ![Seleccionar experiencia de búsqueda predeterminada](media/relevance-search-personal-settings.png "seleccionar experiencia de búsqueda predeterminada")  

2. En la pestaña **General** , en la sección **seleccionar la experiencia de búsqueda predeterminada** , para la **experiencia de búsqueda predeterminada**, seleccione su experiencia predeterminada. 

   > [!div class="mx-imgBorder"]
   > ![Seleccionar experiencia de búsqueda predeterminada](media/default.png "seleccionar experiencia de búsqueda predeterminada")  
 


## <a name="start-a-search"></a>Iniciar una búsqueda 
 
1.  En la barra de navegación superior, seleccione el botón **Buscar** .  
  
2.  Escriba las palabras de búsqueda en el cuadro de búsqueda y, a continuación, seleccione el botón **Buscar** .   

    > [!div class="mx-imgBorder"]
    > Opción de(media/search-option.png "búsqueda") ![opción de búsqueda]  
  
## <a name="filter-categorized-search-results"></a>Filtrar los resultados de la búsqueda por categorías 
  
-   Para filtrar los resultados por un tipo de registro, en la pantalla de búsqueda, elija un tipo de registro en el cuadro desplegable **filtrar con:** .  
  
-   Para buscar en todos los tipos de registro, elija **ninguno** en el cuadro desplegable **filtrar con:** .  

    > [!div class="mx-imgBorder"]
    > ![](media/filter-search.png "Búsqueda") de filtro de búsqueda de filtros  

## <a name="filter-records-with-facets-works-with-relevance-search"></a>Filtrar registros con aspectos (funciona con la búsqueda de relevancia)  
 Con Common Data Service, ahora puede refinar los resultados de la búsqueda mediante el uso de aspectos y filtros. Las caras están disponibles en el panel izquierdo. Inmediatamente después de realizar una búsqueda, están disponibles las siguientes caras globales para cuatro campos comunes:  
  
-   Tipo de registro  
  
-   Owner  
  
-   Creado el  
  
-   Modificado el  
  
### <a name="record-type-facets"></a>Aspectos del tipo de registro  
 Para restringir los resultados de la búsqueda a una entidad específica, seleccione la entidad en la sección **tipo de registro** .  
 
  > [!div class="mx-imgBorder"]
  > ![Faceta de tipo de registro para restringir la faceta de]tipo de registro de resultados de búsqueda(media/relevance-search-record-type-facet.png "que se usa para restringir los resultados de búsqueda")  
  
 Al filtrar por un tipo de registro específico, puede incluir actividades y notas relacionadas con el registro seleccionado en los resultados de la búsqueda. Para ello, active la casilla **notas relacionadas & actividades** . Las actividades y las notas aparecerán en los resultados de nivel superior.  
  
 
  > [!div class="mx-imgBorder"]
  > ![Incluir notas y actividades relacionadas con un tipo de registro en los resultados de la búsqueda](media/relevance-search-record-type-facet-related-notes-activities.png "incluyen notas y actividades relacionadas con un tipo de registro en los resultados de la búsqueda") .  
  
 Los resultados de la búsqueda que se encuentran en datos adjuntos de correo electrónico o entidades de cita se muestran en los resultados de búsqueda bajo su registro primario, ya sea correo electrónico o cita.  
  
 Al refinar por tipo de registro, el ámbito de la faceta cambia a la entidad seleccionada y se muestran hasta cuatro facetas que son específicas de la entidad. Por ejemplo, si selecciona la entidad cuenta, verá la faceta **contacto principal** además de las facetas globales.  
  
 En el cuadro de diálogo **establecer opciones personales** , también puede elegir otras caras de las que el administrador del sistema o el cliente han puesto a su disposición. La configuración de usuario invalida la configuración predeterminada. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [configurar las caras y los filtros de la búsqueda](#BKMK_ConfigureFacets)  
  
### <a name="text-based-facets"></a>Aspectos basados en texto  
 Todas las búsquedas, los conjuntos de opciones y los tipos de registro son aspectos basados en texto. Por ejemplo, el propietario de la faceta basada en texto se compone de una lista de valores de campo y sus recuentos correspondientes.  
 
  > [!div class="mx-imgBorder"]
  > ![Faceta basada en texto en la faceta búsqueda de relevancia](media/relevance-search-text-based-facets.png "basada en texto en la búsqueda de relevancia")  
  
 Los filtros de estas caras se ordenan en orden descendente por recuento. De forma predeterminada, se muestran los cuatro valores principales de faceta. Cuando haya más de cuatro valores de faceta, verá un vínculo **Mostrar más** que puede seleccionar para expandir la lista y ver hasta 15 valores de faceta superior. Seleccione cada valor para filtrar los resultados de la búsqueda y mostrar solo los registros en los que el campo tenga el valor seleccionado. Por ejemplo, si selecciona **Kim Alberti**, los resultados de la búsqueda mostrarán todos los registros en los que el propietario es Kim Alberti. Al seleccionar un valor de faceta búsqueda o conjunto de opciones, los resultados de la búsqueda se filtran para incluir solo los registros con el valor especificado.  
  
### <a name="date-and-time-facets"></a>Aspectos de fecha y hora  
 Al igual que otras caras, puede usar las caras de fecha y hora para filtrar y ver los resultados de la búsqueda para un momento concreto. Para seleccionar un intervalo de valores, arrastre el control deslizante o seleccione una de las columnas verticales.  
 
  > [!div class="mx-imgBorder"]
  > ![Aspectos de fecha y hora para]las(media/relevance-search-date-time-facets.png "caras de fecha y hora de búsqueda de relevancia para la búsqueda de relevancia")  
  
<a name="BKMK_ConfigureFacets"></a>   
### <a name="configure-facets-and-filters-for-the-search"></a>Configurar las caras y los filtros de la búsqueda  
 Las caras y los filtros permiten profundizar y explorar los resultados de la búsqueda actual sin tener que refinar el término de búsqueda repetidamente. Configure las caras y los filtros que desee en el cuadro de diálogo **establecer opciones personales** .  
  
> [!NOTE]
>  El personalizador del sistema puede establecer la experiencia predeterminada para todas las entidades, pero puede configurar sus propias caras y filtros.  
  
#### <a name="to-configure-facets-for-yourself"></a>Para configurar las caras para sí mismo  
  
1. En la esquina superior derecha de la página, seleccione **configuración** y, a continuación, seleccione **configuración de personalización**.  
  
   > [!div class="mx-imgBorder"]
   > ![Seleccionar experiencia de búsqueda predeterminada](media/relevance-search-personal-settings.png "seleccionar experiencia de búsqueda predeterminada")  
  
2. En la pestaña **General** , en la sección **seleccionar la experiencia de búsqueda predeterminada** , en el campo **aspectos y filtros** , seleccione **configurar**.  
  
3. En el cuadro de diálogo **configurar aspectos y filtros** , especifique las caras que le gustaría ver para una entidad. El administrador del sistema o el personalizador pueden establecer una experiencia predeterminada para todas las entidades, pero aquí puede establecer las suyas propias.  
  
   - En la lista desplegable **seleccionar entidad** , seleccione una entidad para la que desee configurar las caras. Esta lista desplegable contiene solo las entidades que están habilitadas para la búsqueda de relevancia.  
  
   - En la entidad seleccionada, seleccione hasta cuatro campos de faceta. De forma predeterminada, los cuatro primeros campos con facetas de la vista **búsqueda rápida** de la entidad seleccionada se seleccionan en la lista. En cualquier momento, solo puede tener cuatro campos seleccionados como aspectos.  
  
     Puede actualizar varias entidades al mismo tiempo. Al seleccionar **Aceptar**, se guardan los cambios de todas las entidades que ha configurado. Para revertir al comportamiento predeterminado de una entidad que configuró anteriormente, seleccione **predeterminado**.  
  
   > [!NOTE]
   > - Si un Personalizador del sistema elimina un campo o hace que ya no se puede buscar y ha guardado una faceta para ese campo, ya no aparecerá como una faceta.  
   >   -   Solo verá los campos que existen en la solución predeterminada y que están configurados como que el personalizador del sistema puede buscar.  
  
 
