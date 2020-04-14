---
title: Procedimiento para usar una aplicación basada en modelos en un dispositivo móvil | Microsoft Docs
description: Aprenda a usar una aplicación personalizada basada en modelos en un dispositivo móvil.
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 04/07/2020
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1668b6a10ba651fd7f4986fcd1f83357d83b79bc
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80871467"
---
# <a name="user-guide-for-model-driven-apps-running-on-the-power-apps-mobile-app"></a>Guía del usuario para usar aplicaciones basadas en modelos que se ejecutan en la aplicación móvil de Power Apps

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Use la aplicación móvil de Power Apps para ejecutar aplicaciones basadas en modelos en su dispositivo móvil. Para obtener más información sobre cómo instalar y empezar a usar una aplicación, consulte el artículo sobre cómo [ejecutar aplicaciones de lienzo y aplicaciones basadas en modelos en un dispositivo móvil](run-canvas-and-model-apps-on-mobile.md).

> [!IMPORTANT]
> Las aplicaciones basadas en modelos de Dynamics 365 for Sales, Dynamics 365 for Customer Service y Dynamics 365 for Field Service<!--For sure this list doesn't include Dynamics 365 Marketing, and Dynamics 365 Project Service Automation? That's the list of model-driven apps according to the Dynamics Style Guide.--> no se ejecutan en la aplicación móvil de Power Apps. En su lugar, se usa la aplicación Dynamics 365 para teléfonos y tabletas. Para obtener más información, consulte el artículo [Manual del usuario (Dynamics 365 para teléfonos y tabletas)](https://docs.microsoft.com/dynamics365/mobile-app/dynamics-365-phones-tablets-users-guide).

## <a name="home-screen"></a>Pantalla principal 

Es fácil familiarizarse con la aplicación móvil de Power Apps. En la siguiente ilustración se muestran los elementos de navegación más importantes de la pantalla principal. 

![Controles de navegación, vista expandida](media/home_screen_iphone.png "Controles de navegación, vista expandida")

Leyenda:

1. **Mapa del sitio**: abra el menú y desplácese entre las aplicaciones, consulte sus registros favoritos y los usados recientemente, acceda a la configuración, etc.
2. **Buscar**: busque registros de aplicaciones en Common Data Service.
3. **Creación rápida**: cree un nuevo registro e indique rápidamente casi cualquier tipo de información en el sistema.
4. **Relationship Assistant** (Asistente de relaciones): use el asistente para supervisar y realizar un seguimiento de las acciones y las comunicaciones diarias. El asistente le ayuda a mantenerse al día con las tarjetas de información que se muestran de forma destacada a lo largo de la aplicación para proporcionar información personalizada y práctica.

## <a name="site-map"></a>Mapa del sitio 

En la pantalla principal, seleccione el icono del mapa del sitio ![Icono del mapa del sitio](media/pa_mobile_sitemap_icon.png "Icono del mapa del sitio") para acceder a las entidades, los registros favoritos o más usados, otras aplicaciones y la configuración.

 
   > [!div class="mx-imgBorder"]
   > ![Pantalla del mapa del sitio](media/go_to_sitemap_iphone.gif "En esta imagen se muestra cómo llegar a la pantalla de mapa del sitio.")
   
 *Actualice la página para reiniciar la acción de GIF*.

En la siguiente ilustración se muestran los elementos de navegación principales de la pantalla del mapa del sitio. 

![Pantalla del mapa del sitio](media/site_map_iphone.png "Pantalla del mapa del sitio")

Leyenda

1. **Selector de aplicaciones**: abra este menú para cerrar la aplicación y cambiar a otra.
2. **Pantalla principal**: seleccione esta página para volver a la pantalla principal.
3. **Perfil**: vaya a la pantalla de su perfil para cerrar sesión o volver a configurar la aplicación. 
4. **Registros recientes**: vea una lista de los registros que ha usado recientemente. 
5. **Registros anclados**: vea y abra sus registros favoritos (anclados). 
6. **Navegador de entidades**: en esta área se muestra la entidad disponible en la aplicación.
7. **Ayuda**: acceda al contenido de ayuda para obtener más información sobre cómo usar la aplicación móvil de Power Apps.
8. **Estado sin conexión**: trabaje con los datos en el modo sin conexión, incluso cuando no disponga de acceso a Internet. Más información: [Trabajar sin conexión en su dispositivo móvil](https://docs.microsoft.com/dynamics365/mobile-app/work-in-offline-mode)
9. **Configuración**: acceso a las opciones de configuración

## <a name="pin-favorite-records"></a>Anclaje de registros favoritos

Las listas **Anclados** y **Recientes** proporcionan un acceso rápido a los registros que ha usado o anclado recientemente a sus favoritos. Use la lista **Recientes** para anclar sus registros favoritos.  

1. En el mapa del sitio ![Icono del mapa del sitio](media/pa_mobile_sitemap_icon.png "Icono del mapa del sitio"), seleccione **Recientes** ![Icono de registros recientes](media/pa_mobile_recent_icon.png "Icono de registros recientes").

2. En la pantalla de registros **recientes**, seleccione el icono de chincheta situado junto a uno de los registros para agregarlo a sus favoritos (registros anclados).

3. Para ver los registros recién anclados, seleccione ![Icono de retroceso](media/mobile_go_back_icon.png "Icono de retroceso") y, a continuación, **Anclados** ![Icono de registros favoritos anclados](media/mobile_pinned_favs_icon.png "Icono de registros favoritos anclados").


   > [!div class="mx-imgBorder"]
   > ![Anclaje de un registro a favoritos](media/pin_favs.gif "En esta imagen se muestra cómo anclar los registros favoritos.")
   
*Actualice la página para reiniciar la acción de GIF*.

### <a name="unpin-a-record"></a>Desanclaje de registros

1. En el mapa del sitio ![Icono del mapa del sitio](media/pa_mobile_sitemap_icon.png "Icono del mapa del sitio"), seleccione **Anclados** ![Icono de registros favoritos anclados](media/mobile_pinned_favs_icon.png "Icono de registros favoritos anclados").

2. Seleccione el icono de quitar chincheta ![Icono de quitar chincheta](media/pa_mobile_remove_pin_icon.png "Icono de quitar chincheta") junto a un registro para eliminarlo de los favoritos (registros anclados).


   > [!div class="mx-imgBorder"]
   > ![Desanclaje de registros](media/unpin_favs.gif "En esta imagen se muestra cómo desanclar un registro.")
   
*Actualice la página para reiniciar la acción de GIF*.

## <a name="change-views"></a>Cambio de vista

- En la pantalla principal, seleccione la flecha abajo ![Icono de cambio de vista](media/mobile_view_selector_icon.png "Icono de cambio de vista") junto a la vista actual y, a continuación, seleccione una nueva vista.


   > [!div class="mx-imgBorder"]
   > ![Cambio de vista](media/change_views_iphone.gif "En esta imagen se muestra cómo seleccionar una vista diferente.")

*Actualice la página para reiniciar la acción de GIF*.

## <a name="add-a-record-quickly"></a>Adición de un registro rápidamente

1. En la pantalla principal, seleccione **Nuevo** ![Botón de creación de registros](media/create-record-button.png "Botón Crear registro").
2. Rellene los campos y seleccione **Guardar**.
3. Una vez creado el registro, puede verlo. 

   > [!div class="mx-imgBorder"]
   > ![Crear registros](media/pamobile_add_record.gif "En esta imagen se muestra cómo crear un registro.")

*Actualice la página para reiniciar la acción de GIF*.

-  Para guardar y abrir el registro que ha creado, seleccione **Más** ![Icono de más comandos](media/pa_mobile_more_commands_icon.png "Icono de más comandos") y, a continuación, **Guardar y abrir**.

- Para guardar el registro y crear otro, seleccione **Más** ![Icono de más comandos](media/pa_mobile_more_commands_icon.png "Icono de más comandos") y, después, **Guardar y crear nuevo**.

   > [!div class="mx-imgBorder"]
   > ![Crear registros](media/pa_mobile_save_create_new.gif "En esta imagen se muestra cómo guardar un registro y abrirlo o guardarlo y crear uno nuevo.")

*Actualice la página para reiniciar la acción de GIF*.

## <a name="view-commands-for-a-record-android"></a>Visualización de los comandos de un registro (Android)

1. En la pantalla principal, abra un registro.
2. En el registro abierto, seleccione **Más** ![Icono de más comandos del registro](media/access_record_commands_icon.png "Icono de más comandos del registro") para acceder a más comandos.

   > [!div class="mx-imgBorder"]
   > ![Comandos de un registro](media/pa_mobile_view_record_commands.gif "En esta imagen se muestra cómo acceder a más comandos en un registro.")

*Actualice la página para reiniciar la acción de GIF*.

## <a name="edit-a-record"></a>Editar un registro

1. En la pantalla principal, abra un registro que quiera editar. 
2. Cuando haya terminado de editarlo, seleccione **Guardar**. Para cancelar los cambios, seleccione **Descartar**.

   > [!div class="mx-imgBorder"]
   > ![Edición de un registro](media/save_on_iphone.gif "En esta imagen se muestra cómo editar y, luego, guardar un registro.")

*Actualice la página para reiniciar la acción de GIF*.

## <a name="go-back-to-the-home-screen"></a>Retroceso a la pantalla principal

- Para volver a la pantalla principal cuando se encuentra en un registro, seleccione **Atrás** ![Icono de retroceso](media/pa_mobile_back_icon.png "Icono de retroceso").
- En cualquier momento, mantenga presionado **Atrás** ![Icono de retroceso](media/pa_mobile_back_icon.png "Icono de retroceso") para volver a la pantalla principal. 

   > [!div class="mx-imgBorder"]
   > ![Retroceso a la pantalla principal](media/go_back_home.gif "En esta imagen se muestra cómo volver a la pantalla principal presionando y manteniendo presionado el icono atrás.")

*Actualice la página para reiniciar la acción de GIF*.

## <a name="sign-out"></a>Cerrar sesión

En el mapa del sitio ![Icono del mapa del sitio](media/pa_mobile_sitemap_icon.png "Icono del mapa del sitio"), seleccione el icono del perfil ![Icono del perfil](media/profile_icon.png "Icono del mapa del sitio") y, a continuación, **Cerrar sesión**.
