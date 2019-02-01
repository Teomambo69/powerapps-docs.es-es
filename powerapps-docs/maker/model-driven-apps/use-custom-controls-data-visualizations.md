---
title: Utilizar controles personalizados para visualizaciones de datos de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Aprenda a usar los controles personalizados para los campos
ms.custom: ''
ms.date: 06/07/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 0d6064cd-4d38-4fc2-a564-735cb453a4b2
caps.latest.revision: 8
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-custom-controls-for-model-driven-app-data-visualizations"></a>Usar controles personalizados para visualizaciones de datos de aplicaciones controladas por modelos

En este tema aprenderá a configurar un control personalizado de un campo. 

Los controles personalizados le permiten transformar los componentes de la interfaz de usuario de la aplicación, como un campo o vista que normalmente contienen texto, en visualizaciones. Los controles personalizados se pueden configurar en campos, formularios, paneles, vistas y cuadrículas. Por ejemplo, un control deslizante se puede configurar en un campo de número.

   > [!div class="mx-imgBorder"] 
   > ![Control deslizante personalizado](media/slider-control.PNG "Control deslizante para un campo")

O bien el control de cuadrícula editable se puede configurar en una vista. 

   > [!div class="mx-imgBorder"] 
   > ![Control de cuadrícula editable](media/editable-grid-example.png)

Puede establecer un tipo de control personalizado para que aparezca en el cliente de explorador web y, al mismo tiempo, hacer que en sus aplicaciones móviles de Dynamics 365 para teléfono o tableta aparezca un control personalizado distinto. Por ejemplo, puede usar un control personalizado de entrada de número para un campo en los clientes de explorador web y un control personalizado deslizante para la aplicación de teléfonos. Una vez publicada la personalización, los usuarios pueden interactuar plenamente con el control para cambiar el valor; por ejemplo, deslizando el control, si están usando el control personalizado deslizante lineal. Los cambios se guardan automáticamente cuando se cierra el formulario, al igual que ocurre cuando el usuario cambia un campo tradicional en un formulario.  
  
## <a name="use-a-custom-control-to-add-visualizations-to-a-field"></a>Usar un control personalizado para agregar visualizaciones a un campo  
 Siga los pasos de este procedimiento para cambiar la etiqueta predeterminada y el campo de cuadro de texto del campo **Importe del presupuesto** por un control personalizado deslizante en la entidad Oportunidad. Puede seguir los mismos pasos para sustituir un campo existente por un control personalizado o configurar un control personalizado para un campo personalizado.  
  
1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

     

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.  
  
2.  Abra un formulario como el formulario **Principal** para la entidad Oportunidad. 
  
3.  En el editor de formularios, haga doble clic en el campo en el que desee agregar un control personalizado, como el campo **Importe del presupuesto** en el formulario principal de oportunidad. Como alternativa, puede crear un campo personalizado. 
  
4.  En la página **Propiedades de campo**, seleccione la pestaña **Controles** y, a continuación, seleccione **Agregar control**.  
  
5.  En la página Agregar control, seleccione el control que desee, como el **Control deslizante lineal** que se muestra aquí, y, a continuación, seleccione en **Agregar**.  

   > [!div class="mx-imgBorder"] 
   > ![Agregar control deslizante lineal](media/add-slider.PNG "Agregar control deslizante lineal")  
  
6.  Elija el cliente en el que desee que aparezca el control.  
  
    - **Web**. Para que el control personalizado esté disponible desde cualquier explorador web, seleccione la opción **Web** situada junto al control. Tenga en cuenta que, al establecer la opción **Web**, el control aparece en exploradores web de PC, Mac y dispositivos móviles.  
  
    - **Teléfono**. Para que el control personalizado esté disponible en teléfonos en los que se ejecute Dynamics 365 for phones, seleccione la opción **Teléfono** situada junto al control.  
  
    - **Tableta**. Para que el control personalizado esté disponible en tabletas en las que se ejecute Dynamics 365 for tablets, seleccione la opción **Tableta** situada junto al control.  
  
   > [!div class="mx-imgBorder"] 
   > ![Elegir las aplicaciones de cliente para ver el control personalizado](media/choose-client.png "Elegir las aplicaciones de cliente para ver el control personalizado")  
  
7.  Seleccione en el icono de lápiz ![Icono de editar propiedades del control personalizado](media/ccf-pencil-icon.png "Icono de editar propiedades del control personalizado") situado junto a **Mín.**, **Máx.** y **Paso**, defina la opción de la propiedad tal y como se describe más abajo y, a continuación, seleccione **Aceptar**.  
  
   > [!div class="mx-imgBorder"] 
   > ![Agregar propiedades de controles personalizados](media/ccf-add-properties.png "Agregar propiedades de controles personalizados")
  
   - **Mín.** Establezca el valor mínimo aceptado. Puede enlazar el valor estático que especifique o enlazar el valor a un campo existente. En este ejemplo, **Enlazar a un valor estático** es **Divisa** y el valor mínimo que se puede introducir es *cero*.  
  
       - **Enlazar a un valor estático**. Seleccione el tipo de datos, por ejemplo, un número entero (Whole.None), divisa, coma flotante (FP) o decimales. A continuación, escriba un número que represente el valor mínimo aceptado para el campo.  
  
       - **Enlazar a un valor de un campo**. Seleccione un campo en la lista que se usará como el valor mínimo aceptado.  
  
   - **Máx.** Establezca el valor máximo aceptado del campo. Al igual que ocurre con el valor mínimo, puede enlazar el valor estático que especifique o enlazar el valor a un campo existente, como se ha descrito más arriba. En este ejemplo, **Enlazar a un valor estático** es **Divisa** y el valor máximo que se puede introducir es **1000 millones**.  
  
   - **Paso**. Representa la unidad que debe aumentar o disminuir al sumar o restar del valor actual. Por ejemplo, para el importe del presupuesto, puede seleccionar incrementos/disminuciones de 100 dólares.  
  
   - **Ocultar control predeterminado**. Al seleccionar esta opción, se oculta el control, por lo que ni el control ni los datos se muestran en ninguno de los clientes que no admitan el control personalizado. Tenga en cuenta que el cliente web clásico de Dynamics 365 no admite la mayoría de los controles personalizados. De forma predeterminada, esta opción no está seleccionada y el cliente web clásico de Dynamics 365 muestra el control predeterminado, normalmente basado en texto.  
  
       > [!NOTE]
       >  El control predeterminado se identifica con **(predeterminado)** después del nombre del control.  
       >   
       > > [!div class="mx-imgBorder"] 
       > > ![Control predeterminado](media/default-control.png "Control predeterminado")  
  
8.  Seleccione **Aceptar** para cerrar la página **Propiedades de campo**.  
  
9. Para activar la personalización, en el formulario de entidad, seleccione **Guardar** y, a continuación, seleccione **Publicar**.  
  
10. Seleccione **Guardar y cerrar** para cerrar el editor de formularios.  
  
### <a name="see-the-custom-control-in-action"></a>Ver el control personalizado en acción  
 Abra un registro que incluya el campo con el control personalizado, como el formulario de oportunidad del ejemplo anterior, y observe cómo ha cambiado el campo.  
  
   > [!div class="mx-imgBorder"] 
   > ![Control deslizante mostrado en formulario](media/slider-control.PNG "Control deslizante mostrado en formulario")  
  
 El campo se muestra ahora como un control deslizante en lugar de como un campo de texto. 

## <a name="use-the-editable-grid-control-on-a-view-or-sub-grid"></a>Usar el control de cuadrícula editable en una vista o subcuadrícula

Con las cuadrículas editables, los usuarios pueden editar en línea con gran detalle directamente desde vistas y subcuadrículas tanto si usan una aplicación web, tableta o teléfono. Más información: [Crear cuadrículas (listas) editables mediante el control personalizado Cuadrículas editables](make-grids-lists-editable-custom-control.md) 
  
## <a name="next-steps"></a>Pasos siguientes  
[Crear y editar campos](../common-data-service/create-edit-fields.md)
