---
title: Mostrar iconos personalizados junto con los valores en vistas de lista con PowerApps | MicrosoftDocs
description: Obtenga información sobre cómo mostrar gráficos de icono en una vista
ms.custom: ''
ms.date: 02/14/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: af866aed-2586-4b6f-bb1c-3519baae3645
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="display-custom-icons-alongside-values-in-list-views"></a>Mostrar iconos personalizados junto con los valores en vistas de lista

<a name="GridIcons"></a>   

 Los administradores y personalizadores de entornos de PowerApps pueden agregar gráficos a una vista y establecer la lógica usada para seleccionar un gráfico según el valor de la columna con JavaScript. La funcionalidad le permite personalizar las vistas de lista que muestran iconos junto al texto o los valores numéricos. 

> [!div class="mx-imgBorder"] 
> ![](media/icon-in-opportunity-view.png "La vista Todas las oportunidades con la columna Valoración que muestra los iconos y el valor de texto")
  
> [!NOTE]
>  Los iconos de cuadrícula se muestran únicamente en la interfaz web. No se muestran en [!INCLUDE[pn_Outlook_short](../../includes/pn-outlook-short.md)] o la aplicación móvil.  
  
### <a name="add-custom-graphics-and-javascript-as-web-resources"></a>Agregue gráficos personalizados y JavaScript como recursos web  
  
1.  Cree los nuevos archivos de gráficos necesarios para la personalización. Se recomienda un tamaño de icono de 16x16 píxeles (las imágenes más grandes serán reducidas proporcionalmente).  
  
2.  Escriba una o más funciones JavaScript que establezcan qué iconos se mostrarán para qué valores (normalmente necesitará una función para cada columna que desea personalizar). Cada función debe aceptar un objeto de datos fila y un código de idioma (LCID) como entrada y devolver una matriz que contiene un nombre de imagen y texto de información sobre herramientas. Para ver una función de ejemplo, consulte [Función JavaScript de ejemplo](#SampleJavascript), más adelante en este tema.  
  
3.  Inicie sesión en el entorno como administrador y abra el explorador de soluciones.  
  
4.  Se abre la ventana **Solución predeterminada**. Vaya a **Componentes** > **Recursos web** aquí.  
  
5.  A continuación, cargará los gráficos personalizados, uno cada vez, como recursos web. Seleccione el botón **Nuevo** en la barra de herramientas para crear un nuevo recurso web. Se abre otra ventana emergente para ayudarle a crear el recurso. Haga lo siguiente:  
  
    1.  Dé **Nombre** significativo para el nuevo recurso. Es el nombre que usará para referirse a cada gráfico desde su código JavaScript.  
  
    2.  Establezca el **Tipo** en el formato gráfico que ha usado para guardar el archivo gráfico (PNG, JPEG o GIF).  
  
    3.  Seleccione **Elegir archivo** para abrir una ventana del explorador de archivos. Úsela para buscar y seleccionar el archivo gráfico.  
  
    4.  Agregue el **Nombre para mostrar** y/o la **Descripción** si lo desea.  
  
    5.  Seleccione **Guardar** y luego cierre la ventana **Recurso web**.  
  
6.  Repita el paso anterior para cada archivo gráfico que tiene.  
  
7.  Ahora, agregará JavaScript como recurso web final. Seleccione **Nuevo** en la barra de herramientas para crear un nuevo recurso web. Se abre otra ventana emergente para ayudarle a crear el recurso. Haga lo siguiente:  
  
    1.  Dé **Nombre** significativo para el nuevo recurso.  
  
    2.  Establezca el **Tipo** como **Script (JScript)**.  
  
    3.  Seleccione **Editor de texto** (junto a la configuración **Tipo**) para abrir una ventana del editor de texto. Pegue el código Javascript aquí y seleccione **Aceptar** para guardarlo.  
  
    4.  Agregue el **Nombre para mostrar** y/o la **Descripción** si lo desea.  
  
    5.  Seleccione **Guardar** y luego cierre la ventana **Recurso web**.  
  
8.  Con la ventana emergente **Solución predeterminada** aún abierta, expanda el árbol **Componentes** > **Entidades** y busque la entidad que desea personalizar.  
  
9. Expanda la entidad y seleccione su icono **Vistas**.  
  
10. Ahora verá una lista de vistas para la entidad seleccionada. Seleccione una vista de la lista. A continuación abra la lista desplegable **Más acciones** en la barra de herramientas y seleccione **Editar**.  
  
11. Una ventana emergente se abre con controles para editar la vista seleccionada. Muestra cada columna que forma parte de la vista. Seleccione la columna de destino y seleccione **Cambiar propiedades** en el cuadro **Tareas comunes**. El diálogo **Cambiar propiedades de columna** se abre; establezca los valores siguientes aquí:  
  
    - **Recurso web**: especifique el nombre del recurso web que ha creado para albergar las funciones Javascript (seleccione el botón **Explorar** para elegir de una lista).  
  
    - **Nombre de función**: escriba el nombre de la función que escribió para modificar la columna y la vista seleccionadas.  
  
12. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Cambiar propiedades de la columna**.  
  
13. Seleccione **Guardar y cerrar** para guardar la vista.  
  
14. Repita estos pasos para cada entidad, vista, y columna según sea necesario.  
  
15. Cuando esté listo, seleccione **Publicar todas las personalizaciones** para publicar los cambios. A continuación, cierre la ventana **Solución predeterminada**.  
  
<a name="SampleJavascript"></a>   

### <a name="sample-javascript-function"></a>Función JavaScript de ejemplo  
 La función JavaScript para mostrar iconos personalizados e informaciones sobre herramientas espera los dos argumentos siguientes: el objeto de fila completo especificado en layoutxml y el Id. de configuración regional del usuario que llama (LCID). El parámetro LCID permite especificar el texto de información sobre herramientas en varios idiomas. Para obtener más información sobre los idiomas admitidos por el entorno, consulte [Habilitar idiomas](/dynamics365/customer-engagement/admin/enable-languages) e [Instalar o actualizar paquetes de idioma](/dynamics365/customer-engagement/on-premises/install-or-upgrade-language-packs). Para ver una lista de valores de Id. de configuración regional (LCID) que puede usar en el código, consulte [Id. de configuración regional asignados por Microsoft](https://go.microsoft.com/fwlink/?linkid=829588).

  
 Suponiendo que agregará iconos personalizados para un tipo de conjunto de opciones de atributo, que tiene un conjunto limitado de opciones predefinidas, asegúrese de que usa el valor entero de las opciones en lugar de etiqueta para evitar problemas de localización.  
  
 El siguiente código de ejemplo muestra iconos e informaciones sobre herramientas basándose en uno de tres valores (1: Muy interesado, 2: Algo interesado, 3: No interesado) en el atributo opportunityratingcode (Nivel de interés). El código de ejemplo también muestra cómo mostrar texto de información sobre herramientas localizado. Para que este ejemplo funcione, debe crear tres recursos web de imagen con imágenes 16x16 con los nombres siguientes: new_Hot, new_Warm y new_Cold.  

> [!IMPORTANT]
> Este ejemplo requiere la entidad oportunidad, que está disponible con la aplicación Dynamics 365 Sales.
  
```javascript
function displayIconTooltip(rowData, userLCID) {      
    var str = JSON.parse(rowData);  
    var coldata = str.opportunityratingcode_Value;  
    var imgName = "";  
    var tooltip = "";  
    switch (parseInt(coldata,10)) { 
        case 1:  
            imgName = "new_Hot";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Hot";  
                    break;  
                default:  
                    tooltip = "Opportunity is Hot";  
                    break;  
            }  
            break;  
        case 2:  
            imgName = "new_Warm";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Warm";  
                    break;  
                default:  
                    tooltip = "Opportunity is Warm";  
                    break;  
            }  
            break;  
        case 3:  
            imgName = "new_Cold";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Cold";  
                    break;  
                default:  
                    tooltip = "Opportunity is Cold";  
                    break;  
            }  
            break;  
        default:  
            imgName = "";  
            tooltip = "";  
            break;  
    }  
    var resultarray = [imgName, tooltip];  
    return resultarray;  
}  
```  
  
 <!-- This results in displaying icons with tooltips in the **Rating** column that depend on the value in each row. The result could look like this:  
  
 ![Custom column graphics example](../customize/media/custom-column-graphics-example.png "Custom column graphics example")  -->
 
 ### <a name="see-also"></a>Vea también
[Conocer las vistas de las aplicaciones controladas por modelos](../model-driven-apps/create-edit-views.md)
