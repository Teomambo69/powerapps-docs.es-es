---
title: Mostrar iconos personalizados en lugar de valores en las vistas de lista con PowerApps | Microsoft Docs
description: Obtenga información sobre cómo mostrar gráficos de iconos personalizados en una vista.
ms.custom: ''
ms.date: 06/21/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 592d2ad73b192d7f03c552563c4f91d52f3d201d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699421"
---
# <a name="display-custom-icons-instead-of-values-in-list-views"></a>Mostrar iconos personalizados en lugar de valores en las vistas de lista

<a name="GridIcons"></a>   

 Los personalizadores y administradores de entornos de PowerApps pueden agregar gráficos a una vista y establecer la lógica utilizada para seleccionar el gráfico según los valores de una columna con JavaScript. La funcionalidad de mostrar las vistas de lista que muestren iconos en lugar de texto o valores numéricos en algunas columnas se introdujo en la información detallada sobre relaciones. 
  
> [!NOTE]
>  Los iconos de cuadrícula solo se muestran en la interfaz web. No se muestran en [!INCLUDE[pn_Outlook_short](../../includes/pn-outlook-short.md)] ni en la aplicación móvil.  
  
### <a name="add-custom-graphics-and-javascript-as-web-resources"></a>Incorporación de gráficos personalizados y JavaScript como recursos web  
  
1.  Cree los archivos de gráficos necesarios para su personalización. Se recomienda un tamaño de icono de 16 x 16 píxeles (las imágenes más grandes se reducirán verticalmente).  
  
2.  Escriba una o varias funciones de JavaScript que establezcan qué iconos mostrar para qué valores (normalmente, necesitará una función para cada columna que desee personalizar). Cada función debe aceptar un objeto de datos de fila y un código de idioma (LCID) como entrada y devolver una matriz que contiene texto de información sobre herramientas y un nombre de imagen. Para una función de ejemplo, vea [Función de ejemplo de JavaScript](#SampleJavascript) más adelante en este tema.  
  
3.  Inicie sesión en su entorno como administrador y abra el [Explorador de soluciones](../model-driven-apps/advanced-navigation.md#solution-explorer).  
  
4.  Se abre la ventana emergente **Solución predeterminada**. Vaya a **Componentes** > **Recursos web** aquí.  
  
5.  Ahora, podrá cargar los gráficos personalizados, uno a uno, como recursos web. Seleccione el botón **Nuevo** en la barra de herramientas para crear un recurso web. Se abre otra ventana emergente para ayudarle a crear el recurso. Haga lo siguiente:  
  
    1.  Asigne al nuevo recurso un **nombre** significativo. Este es el nombre que va a usar para hacer referencia a cada gráfico desde el código de JavaScript.  
  
    2.  Establezca el **Tipo** en el formato de gráfico usado para guardar el archivo de gráfico (GIF, JPEG o PNG).  
  
    3.  Seleccione **Elegir archivo** para abrir una ventana del explorador de archivos. Úsela para buscar y seleccionar el archivo de gráfico.  
  
    4.  Agregue un **nombre para mostrar** o una **descripción** si lo desea.  
  
    5.  Seleccione **Guardar** y cierre la ventana **Recurso web**.  
  
6.  Repita el paso anterior para cada archivo de gráfico que tenga.  
  
7.  Ahora, agregará el código de JavaScript como el recurso web final. Seleccione **Nuevo** en la barra de herramientas para crear un recurso web. Se abre otra ventana emergente para ayudarle a crear el recurso. Haga lo siguiente:  
  
    1.  Asigne al nuevo recurso un **nombre** significativo.  
  
    2.  Establezca el **Tipo** en **Script (JScript)**.  
  
    3.  Seleccione **Editor de texto** (junto a la configuración **Tipo**) para abrir una ventana del editor de texto. Pegue el código de JavaScript aquí y seleccione **Aceptar** para guardarlo.  
  
    4.  Agregue un **nombre para mostrar** o una **descripción** si lo desea.  
  
    5.  Seleccione **Guardar** y cierre la ventana **Recurso web**.  
  
8.  Con la ventana emergente **Solución predeterminada** todavía abierta, expanda el árbol **Componentes** > **Entidades** y busque la entidad que desea personalizar.  
  
9. Expanda la entidad y seleccione su icono **Vistas**.  
  
10. Ahora verá una lista de vistas para la entidad seleccionada. Seleccione una vista en la lista. A continuación, abra la lista desplegable **Más acciones** en la barra de herramientas y seleccione **Editar**.  
  
11. Se abre una ventana emergente con los controles para editar la vista seleccionada. Muestra cada columna que forma parte de la vista. Seleccione la columna de destino y después seleccione **Cambiar propiedades** en el cuadro **Tareas comunes**. Se abre el cuadro de diálogo **Cambiar propiedades de columna**; realice la siguiente configuración aquí:  
  
    - **Recurso web**: especifique el nombre del recurso web que creó para contener las funciones de Javascript (seleccione **Examinar** para elegir en una lista).  
  
    - **Nombre de la función**: escriba el nombre de la función que se escribió para modificar la columna y la vista seleccionadas.  
  
12. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Cambiar propiedades de columna**.  
  
13. Seleccione **Guardar y cerrar** para guardar la vista.  
  
14. Repita estos pasos para cada entidad, vista y columna según sea necesario.  
  
15. Cuando haya terminado, seleccione **Publicar todas las personalizaciones** para publicar los cambios. A continuación, cierre la ventana **Solución predeterminada**.  
  
<a name="SampleJavascript"></a>   

### <a name="sample-javascript-function"></a>Función de ejemplo de JavaScript  
 La función de JavaScript para mostrar iconos personalizados e información sobre herramientas espera los dos siguientes argumentos: el objeto de toda la fila especificado en layoutxml y el Id. de configuración regional (LCID) del usuario que realiza la llamada. El parámetro LCID permite especificar el texto de información sobre herramientas en varios idiomas. Para más información sobre los idiomas admitidos en el entorno, vea [Habilitar idiomas](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages) e [Instalar o actualizar paquetes de idioma para Dynamics 365](https://technet.microsoft.com/library/hh699674.aspx). Para obtener una lista de valores de Id. de configuración regional (LCID) que puede usar en el código, vea los [identificadores de configuración regional asignados por Microsoft](https://go.microsoft.com/fwlink/?linkid=829588).

  
 Suponiendo que va a agregar iconos personalizados para un tipo de conjunto de opciones de atributo, que tiene un limitado conjunto de opciones predefinidas, asegúrese de que utiliza el valor de entero de las opciones en lugar de la etiqueta para evitar problemas de localización.  
  
 El ejemplo de código siguiente muestra los iconos e información sobre herramientas basados en uno de estos tres valores (1: Hot, 2: Warm, 3: Cold) en el atributo opportunityratingcode (clasificación). El código de ejemplo también muestra cómo mostrar el texto de información sobre herramientas localizada. Para que este ejemplo funcione, debe crear tres recursos web de imagen con imágenes de 16 x 16 con los siguientes nombres: new_Hot, new_Warm y new_Cold.  
  
```  
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
  
 Esto da como resultado mostrar iconos con información sobre herramientas en la columna **Clasificación** que dependen del valor de cada fila. El resultado podría tener este aspecto:  
  
 ![Ejemplo de gráficos de columna personalizada](media/custom-column-graphics-example.png "Ejemplo de gráficos de columna personalizada")  
 
 ### <a name="see-also"></a>Vea también
 [Comprender las vistas](../model-driven-apps/create-edit-views.md)
