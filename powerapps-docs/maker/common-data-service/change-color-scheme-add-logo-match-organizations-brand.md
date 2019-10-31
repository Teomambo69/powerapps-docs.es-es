---
title: Cambiar la combinación de colores o agregar un logotipo para que coincida con la marca de la organización | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: 21a166a0-d25e-4260-a1e4-2ddc528787c2
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-theme"></a>Crear un tema

Puede crear una vista y una sensación personalizadas (un tema) para su aplicación al realizar cambios en los colores predeterminados y los elementos visuales proporcionados en el sistema personalizado. Por ejemplo, puede crear su marca de producto personal agregando un logotipo de compañía y proporcionando colores específicos de la entidad. Un tema se crea mediante las herramientas de personalización de la interfaz de usuario, sin necesidad de que un programador escriba código. Puede crear, cambiar o eliminar temas que se usen en su organización. La personalización del tema se admite en los formularios web de Dynamics 365 for Outlook. Puede definir varios temas, pero solo puede establecer y publicar uno como tema predeterminado.  
  
<a name="UseThemes"></a>   
## <a name="use-themes-to-enhance-the-user-interface-and-create-your-product-branding"></a>Use temas para mejorar la interfaz de usuario y crear su marca de producto  
 Los temas se usan para mejorar la interfaz de usuario de la aplicación, no para modificarla por completo. Los colores del tema se aplican globalmente en toda la aplicación. Por ejemplo, puede mejorar los siguientes elementos visuales en la interfaz de usuario:  
  
-   Cambie logotipos de productos y colores de navegación para crear una marca de producto  
  
-   Ajustar colores de énfasis, como los colores de selección o del puntero  
  
-   Proporcionar colores específicos de la entidad  
    
-   Logotipo  
  
-   Información sobre herramientas del logotipo  
  
-   Color de barra de navegación  
  
-   Color de área de barra de navegación

-   Color de barra de comandos principal en la Interfaz unificada
  
-   Color de encabezado  
  
-   Color de vínculo global  
  
-   Efecto de vínculo seleccionado  
  
-   Efecto de pasar el puntero sobre el vínculo  
  
-   Color de control de proceso  
  
-   Color predeterminado de entidad  
  
-   Color predeterminado de entidad personalizada  
  
-   Tono de control  
  
-   Borde de control  
  
<a name="Solution"></a>   
## <a name="solution-awareness"></a>Conocimiento de la solución  
 El tema no tiene conocimiento de la solución. Los cambios realizados en el tema de una organización no están incluidos en soluciones exportadas desde la organización. Los datos se almacenan en la entidad del tema que se puede exportar y reimportar a otro entorno. Los temas importados se deben publicar para que surtan efecto.  
  
<a name="CloneAlter"></a>   
## <a name="copy-and-alter-the-existing-theme"></a>Copie y edite el tema existente  
 La forma más sencilla y rápida de crear un tema nuevo es clonar uno existente y modificarlo. Después, debe guardarlo, mostrar una vista previa y publicarlo. 
 
1.  Inicie sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Seleccione **Controlado por modelo** (parte inferior izquierda). 

3.  Seleccione ![Icono Configuración](../model-driven-apps/media/powerapps-gear.png) (parte superior derecha) > **Personalizaciones avanzadas**. 

4. En **Temas** seleccione **Todos los temas**. 

5. Seleccione **Tema predeterminado de CRM**. 

La captura de pantalla siguiente muestra una parte de la configuración predeterminada del tema.  

> [!div class="mx-imgBorder"] 
> ![Tema predeterminado](media/default-theme.png) 
  
 Hemos clonado el tema predeterminado y cambiado los colores. Las siguientes capturas de pantalla muestran los nuevos colores para desplazamiento y resaltado. También puede elegir un nuevo logotipo del producto.  
  
 La captura de pantalla siguiente muestra el nuevo color de navegación.  
 
 > [!div class="mx-imgBorder"] 
 > ![Colores del tema en verde claro](media/theme-gentle-green.png "Colores del tema en verde claro")  
  
 La captura de pantalla siguiente muestra la cuadrícula de entidad de cuenta con el nuevo color del resalte.  
 
 > [!div class="mx-imgBorder"] 
 > ![Cuadrícula de la cuenta con el tema en verde claro](media/themes-gentle-green-account-grid.png "Cuadrícula de la cuenta con el tema en verde claro")  
  
<a name="Publish"></a>   
## <a name="preview-and-publish-a-theme"></a>Obtener una vista previa y publicar un tema  
 Para obtener una vista previa y publicar un tema, siga estos pasos:  
  
-   Cree un nuevo tema desde cero o clone uno existente.  
  
-   Para mostrar una vista previa del tema nuevo, elija **Vista previa** en la barra de comandos. Para salir del modo de vista previa, elija **Salir de vista previa** en la barra de comandos, junto a **Vista previa**.  
  
-   Publique un tema. Elija **Publicar tema** en la barra de comandos.  
  
 La captura de pantalla siguiente muestra los botones de la barra de comandos para vista previa y publicación.  
  
 ![Usar los botones de vista previa para entras al modo de vista previa o salir de él](media/themes-preview-buttons.PNG "Usar los botones de vista previa para entras al modo de vista previa o salir de él")  
  
<a name="BestPracticies"></a>   
## <a name="best-practices"></a>Prácticas recomendadas  
 A continuación se ofrecen recomendaciones para diseñar contrastes de tema y elegir colores.  
  
### <a name="theme-contrast"></a>Contraste de temas  
 Se recomienda el siguiente método para proporcionar colores de contraste:  
  
-   Elija cuidadosamente los colores de contraste. El tema predeterminado predefinido de Common Data Service tiene los coeficientes de contraste correctos para asegurar una facilidad de uso óptima. Use coeficientes similares para los nuevos temas.  
  
-   Para el modo de contraste alto, use la configuración predeterminada de colores.  
  
### <a name="theme-colors"></a>Colores de temas  
 Recomendamos no usar un gran número de diferentes colores. Aunque puede establecer un color diferente para cada entidad, se recomienda uno de dos patrones:  
  
-   Cree todas las entidades en colores neutrales y resalte las entidades clave.  
  
-   Use el mismo color para entidades similares o entidades relacionadas, como elemento de cola y cola, o entidades del catálogo de productos. Mantenga bajo el número total de grupos.  
  
<a name="Considerations"></a>   
## <a name="custom-theme-considerations"></a>Consideraciones sobre temas personalizados  
 Deberá tener en cuenta lo siguiente al planificar el uso de temas personalizados:  
  
-   La mayoría de las áreas de la interfaz de usuario (UI) actualizadas se mostrarán en los colores del tema personalizado.  
  
-   Aunque los colores de tema se aplican globalmente en toda la aplicación, algunas áreas heredadas de la interfaz de usuario, como los botones del degradado, mantendrán los colores predeterminados.  
  
-   Ciertas áreas deben usar colores oscuros o claros con los colores predeterminados de icono. El color del icono no se puede personalizar.  
  
-   Una entidad no se puede mostrar en diferentes colores en diferentes nodos del mapa del sitio.  
  
-   Los colores de los nodos del mapa del sitio no se pueden personalizar.  
  
## <a name="see-also"></a>Vea también  
         
 [Vídeo: Temas](http://go.microsoft.com/fwlink/p/?LinkId=529568) [Consultar y editar un tema de organización](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/query-and-edit-an-organization-theme)

