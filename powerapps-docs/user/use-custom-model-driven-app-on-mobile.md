---
title: Procedimiento para usar una aplicación basada en modelos en un dispositivo móvil | Microsoft Docs
description: Aprenda a usar una aplicación personalizada basada en modelos en un dispositivo móvil.
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 03/12/2020
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 84fe0685f9a128fb0cbbeadfbea01aceaa86cb19
ms.sourcegitcommit: 39f6feb699512e9c2bf71ef1a1238b32b639da02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2020
ms.locfileid: "80530432"
---
# <a name="user-guide-for-model-driven-apps-running-on-the-power-apps-mobile-app"></a>Guía del usuario para usar aplicaciones basadas en modelos que se ejecutan en la aplicación móvil de Power Apps

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Use la aplicación móvil de Power Apps para ejecutar aplicaciones basadas en modelos en su dispositivo móvil. Para obtener más información sobre cómo instalar y empezar a usar una aplicación, consulte el artículo sobre cómo [ejecutar aplicaciones de lienzo y aplicaciones basadas en modelos en un dispositivo móvil](run-canvas-and-model-apps-on-mobile.md).

> [!IMPORTANT]
> Las aplicaciones basadas en modelos de Dynamics 365 for Sales, Dynamics 365 for Customer Service y Dynamics 365 for Field Service<!--For sure this list doesn't include Dynamics 365 Marketing, and Dynamics 365 Project Service Automation? That's the list of model-driven apps according to the Dynamics Style Guide.--> no se ejecutan en la aplicación móvil de Power Apps. En su lugar, se usa la aplicación Dynamics 365 para teléfonos y tabletas. Para obtener más información, consulte el artículo [Manual del usuario (Dynamics 365 para teléfonos y tabletas)](https://docs.microsoft.com/dynamics365/mobile-app/dynamics-365-phones-tablets-users-guide).

## <a name="home-screen"></a>Pantalla principal 

Es fácil familiarizarse con la aplicación móvil de Power Apps. En la siguiente ilustración se muestran los elementos de navegación más importantes de la pantalla principal. 

![Controles de navegación, vista expandida](media/pa_mobile_main_nav_android.png "Controles de navegación, vista expandida")

Leyenda:

1. **Mapa del sitio**: abra el menú y desplácese entre las aplicaciones, consulte sus registros favoritos y los usados recientemente, acceda a la configuración, etc.
2. **Buscar**: busque registros de aplicaciones en Common Data Service.
3. **Creación rápida**: cree un nuevo registro e indique rápidamente casi cualquier tipo de información en el sistema.
4. **Comandos globales**: acceda a los comandos globales personalizados por su administrador.
5. **Más**: acceda a más comandos para los registros con los que está trabajando, como ordenar, buscar, eliminar, actualizar, etc.<!--There really are "more"? Or can you end the list at "refresh"?-->
6. **Ordenar registros**: ordene y vea los registros alfabéticamente.

## <a name="site-map"></a>Mapa del sitio 

En la pantalla principal, seleccione el icono del mapa del sitio ![Icono del mapa del sitio](media/pa_mobile_sitemap_icon.png "Icono del mapa del sitio") para acceder a las entidades, los registros favoritos o más usados, otras aplicaciones y la configuración.

   > [!div class="mx-imgBorder"]
   > ![Pantalla del mapa del sitio](media/pa_mobile_site_map.gif "Pantalla del mapa del sitio")

En la siguiente ilustración se muestran los elementos de navegación principales de la pantalla del mapa del sitio. 

![Pantalla del mapa del sitio](media/pa_mobile_sitemap_android.png "Pantalla del mapa del sitio")

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
   > ![Anclaje de un registro a favoritos](media/pin_favs.gif "Anclaje de un registro a favoritos")

### <a name="unpin-a-record"></a>Desanclaje de registros

1. En el mapa del sitio ![Icono del mapa del sitio](media/pa_mobile_sitemap_icon.png "Icono del mapa del sitio"), seleccione **Anclados** ![Icono de registros favoritos anclados](media/mobile_pinned_favs_icon.png "Icono de registros favoritos anclados").

2. Seleccione el icono de quitar chincheta ![Icono de quitar chincheta](media/pa_mobile_remove_pin_icon.png "Icono de quitar chincheta") junto a un registro para eliminarlo de los favoritos (registros anclados).

   > [!div class="mx-imgBorder"]
   > ![Desanclaje de registros](media/unpin_favs.gif "Desanclaje de registros")

## <a name="change-views"></a>Cambio de vista

- En la pantalla principal, seleccione la flecha abajo ![Icono de cambio de vista](media/mobile_view_selector_icon.png "Icono de cambio de vista") junto a la vista actual y, a continuación, seleccione una nueva vista.

   > [!div class="mx-imgBorder"]
   > ![Cambio de vista](media/pa_mobile_change_view.gif "Cambio de vista")

## <a name="add-a-record-quickly"></a>Adición de un registro rápidamente

1. En la pantalla principal, seleccione **Nuevo** ![Botón de creación de registros](media/create-record-button.png "Botón Crear registro").
2. Rellene los campos y seleccione **Guardar**.
3. Una vez creado el registro, puede verlo. 

   > [!div class="mx-imgBorder"]
   > ![Crear registros](media/pamobile_add_record.gif "Creación de un registro")

-  Para guardar y abrir el registro que ha creado, seleccione **Más** ![Icono de más comandos](media/pa_mobile_more_commands_icon.png "Icono de más comandos") y, a continuación, **Guardar y abrir**.

- Para guardar el registro y crear otro, seleccione **Más** ![Icono de más comandos](media/pa_mobile_more_commands_icon.png "Icono de más comandos") y, después, **Guardar y crear nuevo**.

   > [!div class="mx-imgBorder"]
   > ![Crear registros](media/pa_mobile_save_create_new.gif "Creación de un registro")

## <a name="view-commands-for-a-record"></a>Visualización de los comandos de un registro

1. En la pantalla principal, abra un registro.
2. En el registro abierto, seleccione **Más** ![Icono de más comandos del registro](media/access_record_commands_icon.png "Icono de más comandos del registro") para acceder a más comandos.

   > [!div class="mx-imgBorder"]
   > ![Comandos de un registro](media/pa_mobile_view_record_commands.gif "Comandos de un registro")

## <a name="edit-a-record"></a>Editar un registro

1. En la pantalla principal, abra un registro que quiera editar. 
2. Cuando haya terminado de editarlo, seleccione **Guardar**. Para cancelar los cambios, seleccione **Descartar**.

   > [!div class="mx-imgBorder"]
   > ![Edición de un registro](media/pa_mobile_edit_record.gif "Editar un registro")

## <a name="go-back-to-the-home-screen"></a>Retroceso a la pantalla principal

- Para volver a la pantalla principal cuando se encuentra en un registro, seleccione **Atrás** ![Icono de retroceso](media/pa_mobile_back_icon.png "Icono de retroceso").
- En cualquier momento, mantenga presionado **Atrás** ![Icono de retroceso](media/pa_mobile_back_icon.png "Icono de retroceso") para volver a la pantalla principal. 

   > [!div class="mx-imgBorder"]
   > ![Retroceso a la pantalla principal](media/go_back_home.gif "Retroceso a la pantalla principal")

## <a name="sign-out"></a>Cerrar sesión

En el mapa del sitio ![Icono del mapa del sitio](media/pa_mobile_sitemap_icon.png "Icono del mapa del sitio"), seleccione el icono del perfil ![Icono del perfil](media/profile_icon.png "Icono del mapa del sitio") y, a continuación, **Cerrar sesión**.
