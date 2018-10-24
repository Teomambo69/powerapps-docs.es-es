---
title: Configuración de controladores de eventos para formularios principales de aplicaciones controladas por modelos en PowerApps | Microsoft Docs
description: Aprenda a configurar los controladores de eventos en Dynamics 365 for Customer Engagement.
Keywords: Main form; Configure event handlers; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.assetid: dc0ebb3f-0c00-413a-968f-9cfd107055c0
ms.openlocfilehash: e05e9d840a2b3ad7d8d5c74e8e3b670504f739b0
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39702925"
---
# <a name="configure-model-driven-app-form-event-handlers"></a>Configuración de controladores de eventos de formularios de aplicaciones controladas por modelos

 Los controladores de eventos de formulario para formularios PowerApps pueden configurarse para las siguientes áreas de un formulario:  
  
|Elemento|Evento|Descripción|  
|-------------|-----------|-----------------|  
|Formulario|`OnLoad`|Se produce cuando se carga el formulario.|  
||`OnSave`|Se produce cuando se guardan los datos.|  
|Pestaña|`TabStateChange`|Se produce cuando la pestaña se expande o se contrae.|  
|Campo|`OnChange`|Se produce cuando los datos del campo cambian y el control pierde el foco.|  
|IFRAME|`OnReadyStateComplete`|Se produce cuando se carga el contenido de un IFRAME.|  
  
 Un controlador de eventos consta de una referencia a un recurso web JavaScript y una función definida dentro de ese recurso web que se ejecutará cuando tenga el lugar el evento. Cada elemento puede tener hasta 50 controladores de eventos configurados independientes.  
  
> [!IMPORTANT]
>  Configurar un controlador de eventos de forma incorrecta puede dar lugar a errores de script que pueden hacer que el formulario no se cargue o no funcione correctamente. Si no es el desarrollador del script, asegúrese de entender exactamente qué opciones de configuración requiere el script.  
>   
>  No configure un controlador de eventos de scripts mediante una biblioteca que no provenga de un origen en el que confíe. Los scripts se pueden utilizar para llevar a cabo cualquier acción que un usuario pueda realizar y un script mal escrito puede dañar significativamente el rendimiento de un formulario.  
>   
>  Después de configurar un controlador de eventos, pruébelo siempre para comprobar que funciona correctamente.  
  
### <a name="to-configure-an-event-handler"></a>Para configurar un controlador de eventos 
  
1.  En el editor de formulario, seleccione el elemento con el evento para el que desea configurar un controlador.  
  
2.  En la [pestaña Inicio](form-editor-user-interface-legacy.md#home-tab), en el grupo **Editar**, seleccione **Cambiar propiedades** o simplemente haga doble clic en el elemento.  
  
3.  En el cuadro de diálogo de propiedades del elemento, seleccione la pestaña **Eventos**.  
  
4.  Expanda el área **Bibliotecas de formularios**. Si la biblioteca que contiene la función que desea establecer como controlador de eventos no está ya en la lista, agregue la biblioteca.  
  
5.  Para agregar una biblioteca de formularios a un controlador de eventos:  
    1.  En la sección **Bibliotecas de formularios** de la **lista de eventos**, seleccione **Agregar**.  
  
    2.  Busque el recurso web de JavaScript en la lista de recursos web disponibles. Selecciónelo y, después, seleccione **Agregar**.  
  
         Si el recurso web de JavaScript que necesita no existe, seleccione **Nuevo** para abrir un nuevo formulario de recurso web y crear uno.  
  
    3.  Para crear un recurso web de JavaScript:  
        1.  En el formulario de recursos web establezca las propiedades siguientes:  
  
            |Propiedad|Valor|  
            |--------------|-----------|  
            |Nombre|**Requerido**. Escriba el nombre del recurso web.|  
            |Nombre para mostrar|**Requerido**. Escriba el nombre que se mostrará en la lista de recursos web.|  
            |Descripción|Opcional. Escriba una descripción del recurso web.|  
            |Tipo|**Requerido**. Seleccione **Script (JScript)**.|  
            |Lenguaje|Opcional. Elija uno de los idiomas disponibles para la organización.|  
  
        2.  Si se le ha proporcionado un script, le recomendamos encarecidamente que utilice el botón **Examinar** para localizar el archivo y cargarlo.  
  
             También puede seleccionar el botón **Editor de texto** y pegar o escribir el contenido del script en el cuadro de diálogo **Editar contenido**.  
  
            > [!NOTE]
            >  Debido a que este sencillo editor de texto no proporciona ninguna característica para comprobar la corrección del script, por lo general siempre debería intentar utilizar una aplicación independiente como Visual Studio para editar scripts y después cargarlos.  
  
        3.  Seleccione **Guardar** y cierre el cuadro de diálogo del recurso web.  
  
        4.  El recurso web que creó ahora está seleccionado en el cuadro de diálogo **Buscar registro**. Seleccione **Agregar** para cerrar el cuadro de diálogo.  
6.  En la sección **Controladores de eventos**, seleccione el evento para el que desea configurar un controlador de eventos.  
  
7.  Seleccione **Agregar** para abrir el cuadro de diálogo **Propiedades del controlador**.  
  
8. En la pestaña **Detalles**, seleccione la biblioteca adecuada y escriba el nombre de la función que debe ejecutarse para el evento.  
  
9. De forma predeterminada, el controlador de eventos está habilitado. Desactive la casilla **Habilitado** si no desea habilitar este evento.  
  
     Algunas funciones requieren que se pase un contexto de ejecución a la función. Seleccione **Pasar el contexto de ejecución como primer parámetro** si es necesario.  
  
     Algunas funciones pueden aceptar un conjunto de parámetros para controlar el comportamiento de una función. Si son necesarios, escríbalos en la **lista de parámetros separados por comas que se pasarán a la función**.  
  
10. En la pestaña **Dependencias**, agregue los campos de los que dependa el script en el área **Campos dependientes**.  
  
11. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Propiedades del controlador**.  
  
12. Cuando se introduce el controlador de eventos, puede ajustar el orden en el que se ejecutará la función en relación con cualquier otra función mediante las flechas verdes para moverla hacia arriba o hacia abajo.  
  
13. Seleccione **Aceptar** para cerrar el cuadro de diálogo de propiedades del elemento.  
  
14. Seleccione **Guardar** para guardar los cambios. Seleccione **Publicar** para publicar el formulario.  
  
> [!NOTE]
>  Mientras que la interfaz de usuario le permite ajustar el orden en el que se cargan los scripts mediante las flechas verdes arriba y abajo, los scripts en realidad no se cargan secuencialmente.   

## <a name="next-steps"></a>Pasos siguientes

[Use el formulario principal y sus componentes](use-main-form-and-components.md)
