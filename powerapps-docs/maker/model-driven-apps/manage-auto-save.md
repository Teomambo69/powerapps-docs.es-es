---
title: Deshabilitar el guardado automático en una aplicación controlada por modelos con PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: 2e7f75dd-7a3f-4716-b995-b626929c0501
caps.latest.revision: 14
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="disable-auto-save-in-a-model-driven-app"></a>Deshabilitar el guardado automático en una aplicación controlada por modelos

El guardado automático ayuda a los usuarios de la aplicación a centrarse en el trabajo sin tener que administrar el almacenamiento de datos en el formulario. La mayoría de las personas apreciará no tener que guardar datos de forma explícita que cada vez actualice un registro, pero algunas organizaciones pueden tener personalizaciones que fueron diseñadas para guardarse de forma explícita. Para estas organizaciones existen opciones para administrar la forma de aplicar el autoguardado.  
  
<a name="BKMK_HowAutoSaveWorks"></a>   

## <a name="how-auto-save-works"></a>Autoguardado de trabajos  
 De forma predeterminada, todos los formularios de las [entidades actualizadas y clásicas](create-design-forms.md#updated-versus-classic-entities) tendrán el autoguardado habilitado. Una vez creado un registro (guardado en un principio), los cambios realizados en un formulario se guardarán automáticamente treinta segundos después del cambio. Si no se realiza ningún cambio en el formulario, el guardado automático no se producirá mientras el formulario esté abierto. Después de realizar un cambio, el período de 30 segundos antes del autoguardado vuelve a empezar. El campo que alguien está editando actualmente no se incluye en un autoguardado. Si otra persona ha actualizado el mismo registro mientras lo editaba, esos cambios se recuperarán y mostrarán en el formulario al realizar el autoguardado.  
  
 Con el autoguardado habilitado, el botón de guardar solo aparece al guardar inicialmente el registro. Una vez creado el registro, el botón de guardar en la barra de comandos no aparece, pero puede verse un botón ![Botón Guardado automático](media/auto-save-icon.png "Botón Guardado automático") en la esquina inferior derecha, que aparecerá si existen cambios sin guardar. Este control también se muestra si el autoguardado está deshabilitado.  
  
 Puede seleccionar este botón para guardar el registro y actualizar datos en el formulario de forma inmediata. Cuando el autoguardado está habilitado, el registro se guardará cada vez que navegue fuera de un registro o cierre la ventana independiente que muestra un registro. No es necesario para el botón **Guardar y cerrar** que aparece en los formularios de entidades que no se actualizan.  
  
<a name="BKMK_AutoSave"></a>   
## <a name="should-you-disable-auto-save"></a>¿Debe deshabilitar el autoguardado?  
 Si tiene complementos, flujos de trabajo o scripts de formularios que se ejecuten al guardar un registro, se ejecutarán que vez que se realice el autoguardado. Esto puede llevar a comportamientos indeseables si estas extensiones no fueron diseñadas para funcionar con el autoguardado. Independientemente de si el autoguardado está habilitado, los complementos, flujos de trabajo y scripts de formularios se deben diseñar para buscar cambios específicos, y no deben ejecutarse indistintamente para cada evento de guardar.  
  
 Si tiene la auditoría configurada para una entidad, cada operación de guardar se trata como una actualización independiente. Si alguien se queda en un formulario con cambios sin guardar durante más de treinta segundos, verá una entrada adicional solo si se agregan más datos tras realizar el autoguardado. Si tiene informes que dependen de datos de auditoría y trata cada guardado como "toque" individual de un registro, es posible que se produzca un aumento de la periodicidad de los toques. Si usa este método, debe tener en cuenta que los comportamientos de un usuario individual lo convierten en una métrica no fiable con o sin el autoguardado habilitado.  
  
<a name="BKMK_DisableAutoSaveOrg"></a>   
## <a name="disable-auto-save-for-the-organization"></a>Deshabilitar el autoguardado para la organización  
 Si determina que el autoguardado ocasionará problemas con las extensiones que está usando, puede deshabilitarlo para la organización. No hay ningún valor para deshabilitar el autoguardado para entidades o formularios individuales.  
  
1. Vaya a **[Configuración](advanced-navigation.md#settings)** > **Administración**.  
  
2.  Elija **Configuración del sistema**.  
  
3.  Para la opción **Habilitar autoguardado para todos los formularios**, seleccione **No**.  
  
<a name="BKMK_DisalbleAutoSaveForm"></a>   
## <a name="disable-auto-save-for-a-form"></a>Deshabilitar el autoguardado para un formulario  
 Si desea deshabilitar el autoguardado para formularios específicos de entidad, puede agregar código al evento `OnSave` de una entidad.  
  
> [!NOTE]
>  El guardado automático se deshabilitará para el formulario, pero los datos se guardarán al seleccionar el botón ![Botón Guardado automático](media/auto-save-icon.png "Botón guardado automático") de la esquina inferior derecha. Si intenta desplazarse fuera de un formulario o cerrar un formulario donde se han cambiado los datos, se les pedirá que guarden los cambios para poder salir o cerrar el formulario.  
  
1.  En el sitio de [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) seleccione **Controlado por modelos** (parte inferior izquierda del panel de navegación).  

    ![Modo de diseño controlado por modelos](../model-driven-apps/media/model-driven-switch.png)

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.  
  
3.  Abra el formulario que desee editar.  
  
4.  Cree un recurso web de JavaScript y agréguelo al formulario:  
  
    1.  En el editor de formularios, en el grupo **Formulario** elija **Propiedades de formulario**.  
  
    2.  En la ficha **Eventos**, debajo de **Bibliotecas de formularios**, elija **Agregar**.  
  
    3.  En el cuadro de diálogo **Buscar registro**, elija **Nuevo**.  
  
    4.  En el formulario de recursos web, especifique la siguiente información:  
  
        |||  
        |-|-|  
        |**Nombre**|preventAutoSave|  
        |**Nombre para mostrar**|Impedir el autoguardado|  
        |**Tipo**|Script (JScript)|  
  
    5.  Junto al campo **Tipo**, elija **Editor de texto**.  
  
    6.  En el campo **Origen**, pegue el siguiente código:  
  
        ```javascript  
        function preventAutoSave(econtext) {  
            var eventArgs = econtext.getEventArgs();  
            if (eventArgs.getSaveMode() == 70 || eventArgs.getSaveMode() == 2) {  
                eventArgs.preventDefault();  
            }  
        }  
  
        ```  
  
    7.  Seleccione **Aceptar** para cerrar el editor de texto.  
  
    8.  Elija **Guardar** para guardar el recurso web y cierre la ventana del recurso web.  
  
    9. En el diálogo **Buscar registro**, el nuevo recurso web que ha creado estará seleccionado. Elija **Agregar** para cerrar el cuadro diálogo.  
  
5.  Configurar el evento OnSave:  
  
    1.  En la ventana **Propiedades de formulario**, en la sección **Controladores de eventos**, defina **Evento** en **OnSave**.  
  
    2.  Seleccione **Agregar**.  
  
    3.  En la ventana **Propiedades del controlador**, establezca **Biblioteca** en el recurso web que agregó en el paso anterior.  
  
    4.  Escriba ‘`preventAutoSave`’ en el campo **Función**. Distingue mayúsculas de minúsculas. No incluya las comillas.  
  
    5.  Asegúrese de que la opción **Habilitado** se encuentre activada.  
  
    6.  Active **Pasar el contexto de ejecución como primer parámetro**.  
  
        > [!IMPORTANT]
        >  Si no realiza este paso, el script no funcionará.  
  
         El diálogo **Propiedades del controlador** debe verse así. El prefijo de personalización "new_" puede variar según el prefijo de personalización definido para el editor predeterminado para la organización.  
  
 ![Controlador del evento OnSave para evitar el guardado automático en Dynamics 365](media/prevent-auto-save-script.png "Controlador del evento OnSave para evitar el guardado automático en Dynamics 365")  
  
    7.  Seleccione **Aceptar** para cerrar el cuadro de diálogo **Propiedades del controlador**.  
  
    8.  Si hay otros controladores de eventos para el evento `OnSave`, use las flechas verdes para moverlo a la parte superior.  
  
6. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Propiedades del formulario**.  
  
7. Seleccione **Guardar y cerrar** para cerrar el formulario.  
  
8. En el explorador de soluciones, seleccione **Publicar todas las personalizaciones**.  
  
 Después de aplicar este script al evento `OnSave`, cuando los usuarios editen un registro mediante este formulario, el mensaje **cambios no guardados** aparecerá en la esquina inferior derecha de formulario como si el autoguardado no estuviese deshabilitado. Pero este mensaje no desaparecerá hasta que los usuarios seleccionen el botón ![Botón Guardado automático](media/auto-save-icon.png "Botón guardado automático") situado al lado.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear y diseñar formularios](create-design-forms.md)      

 
