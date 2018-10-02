---
title: Configurar controladores de eventos para formularios principales de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Conocer cómo configurar controladores de eventos en Dynamics 365 for Customer Engagement
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-model-driven-app-form-event-handlers"></a>Configurar controladores de eventos para formularios de aplicaciones controladas por modelos

 Los controladores de eventos de formularios para formularios de PowerApps pueden configurarse para las siguientes áreas en un formulario:  
  
|Elemento|Evento|Descripción|  
|-------------|-----------|-----------------|  
|Formulario|`OnLoad`|Se produce cuando el formulario se carga.|  
||`OnSave`|Se produce cuando se guardan los datos.|  
|Pestaña|`TabStateChange`|Se produce cuando se expande o contrae la ficha.|  
|Campo|`OnChange`|Se produce cuando los datos del campo cambian y el control pierde el foco.|  
|IFRAME|`OnReadyStateComplete`|Se produce cuando se carga el contenido de un IFRAME.|  
  
 Un controlador de eventos se compone de una referencia a un recurso web de JavaScript y a una función definida dentro de ese recurso web que se ejecutará cuando se produzca el evento. Cada elemento puede tener hasta 50 controladores de eventos independientes configurados.  
  
> [!IMPORTANT]
>  La configuración de un controlador de eventos puede provocar errores de script que pueden causar que el formulario no se cargue o no funcione correctamente. Si no es el desarrollador del script, asegúrese de comprender exactamente qué opciones de configuración requiere el script.  
>   
>  No configure un controlador de eventos de script mediante una biblioteca que no proceda de un origen de confianza. Los scripts se pueden usar para realizar las acciones que un usuario podría realizar y un script mal redactado puede afectar considerablemente al rendimiento de un formulario.  
>   
>  Después de configurar un controlador de eventos, pruébelo siempre para comprobar que funciona correctamente.  
  
### <a name="to-configure-an-event-handler"></a>Para configurar un controlador de eventos 
  
1.  En el editor de formularios, seleccione el elemento con el evento para el que desea configurar un controlador.  
  
2.  En la [pestaña Inicio](form-editor-user-interface-legacy.md#home-tab), en el grupo **Editar**, seleccione **Cambiar propiedades** o simplemente haga doble clic en el elemento.  
  
3.  En el cuadro de diálogo de propiedades del elemento, seleccione la ficha **Eventos**.  
  
4.  Expanda el área **Bibliotecas de formularios**. Si la biblioteca que contiene la función que desea establecer como el controlador de eventos no se muestra en la lista, agréguela.  
  
5.  Para agregar una biblioteca de formularios a un controlador de eventos:  
    1.  En la sección **Bibliotecas de formularios** de la **Lista de eventos**, seleccione **Agregar**.  
  
    2.  Busque el recurso web de JavaScript en la lista de recursos web disponibles. Selecciónelo y después **Agregar**.  
  
         Si el recurso web de JavaScript que necesita no existe, seleccione **Nuevo** para abrir un formulario de recurso web nuevo y cree uno.  
  
    3.  Para crear un recurso web de JavaScript:  
        1.  En el formulario de recurso web, establezca las propiedades siguientes:  
  
            |Propiedad|Valor|  
            |--------------|-----------|  
            |Nombre|**Requerido**. Especifique el nombre del recurso web.|  
            |Nombre para mostrar|**Requerido**. Escriba el nombre para mostrar en la lista de recursos web.|  
            |Descripción|Opcional. Escriba una descripción del recurso web.|  
            |Tipo|**Requerido**. Seleccione **Script (JScript)**.|  
            |Idioma|Opcional. Seleccione uno de los idiomas disponibles para su organización.|  
  
        2.  Si se le ha proporcionado un script, se recomienda encarecidamente utilizar el botón **Examinar** para buscar el archivo y cargarlo.  
  
             O bien, puede seleccionar el botón **Editor de texto** y pegar o escribir el contenido del script en el diálogo **Editar contenido**.  
  
            > [!NOTE]
            >  Dado que este editor de texto simple no ofrece ninguna característica para comprobar si el script es correcto, debe intentar usar una aplicación independiente como Visual Studio para editar scripts y cargarlos a continuación.  
  
        3.  Seleccione **Guardar** y cierre el cuadro de diálogo de recursos web.  
  
        4.  El recurso web que ha creado aparece ahora seleccionado en el diálogo **Buscar registro**. Seleccione **Agregar** para cerrar el cuadro diálogo.  
6.  En la sección **Controladores de eventos**, seleccione el evento para el que desee establecer un controlador de eventos.  
  
7.  Seleccione **Agregar** para abrir el cuadro de diálogo **Propiedades del controlador**.  
  
8. En la ficha **Detalles** elija la biblioteca adecuada y escriba el nombre de la función que debe ejecutarse para el evento.  
  
9. De forma predeterminada, el controlador de eventos está habilitado. Desactive la casilla de verificación **Habilitado** si no desea habilitar este evento.  
  
     Algunas funciones requieren que se pase un contexto de ejecución a la función. Seleccione **Pasar el contexto de ejecución como primer parámetro** si es necesario.  
  
     Algunas funciones pueden aceptar un conjunto de parámetros para controlar el comportamiento de una función. Si es necesario, introdúzcalos en **Lista de parámetros separados por coma que se transmitirá a la función**.  
  
10. En la ficha **Dependencias**, agregue los campos de los que depende el script en el área **Campos dependientes**.  
  
11. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Propiedades del controlador**.  
  
12. Cuando el controlador de eventos esté introducido, podrá cambiar el orden en el que la función se ejecutará en relación con cualquier otra función mediante las flechas verdes para moverla arriba o abajo.  
  
13. Seleccione **Aceptar** para cerrar el cuadro de diálogo de propiedades del elemento.  
  
14. Seleccione **Guardar** para guardar los cambios. Seleccione **Publicar** para publicar el formulario.  
  
> [!NOTE]
>  Aunque la interfaz de usuario (UI) le permite cambiar el orden en que los scripts se cargan utilizando las flechas verdes arriba y abajo, los scripts no se cargan en realidad de forma secuencial.   

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
