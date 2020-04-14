---
title: Ejecución de aplicaciones de lienzo y basadas en modelos en un dispositivo móvil | Microsoft Docs
description: Aprenda a ejecutar una aplicación de lienzo o una aplicación personalizada basada en modelos en un dispositivo móvil.
author: mduelae
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
ms.openlocfilehash: fbd6233eb775fb7f1c48ec6cc05006ac0237f72d
ms.sourcegitcommit: abdc8c609a7a221ce4ca6b051a84b7083bdbe1ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2020
ms.locfileid: "80645574"
---
# <a name="run-canvas-apps-and-model-driven-apps-on-a-mobile-device"></a>Ejecución de aplicaciones de lienzo y basadas en modelos en un dispositivo móvil

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Al crear una aplicación, o cuando alguien comparte una aplicación con usted, &mdash;tanto una aplicación de lienzo como una aplicación basada en modelos&dash;, puede ejecutar dicha aplicación en dispositivos iOS y Android con la aplicación móvil de Power Apps. Si usa un dispositivo Windows, solo puede ejecutar aplicaciones de lienzo; las aplicaciones basadas en modelos no se admiten en la aplicación móvil de Power Apps para dispositivos Windows. En este tema, aprenderá a empezar a usar y ejecutar una aplicación de lienzo y una aplicación basada en modelos en su dispositivo móvil. 

Para obtener información, consulte la [Guía del usuario para usar aplicaciones basadas en modelos que se ejecutan en la aplicación móvil de Power Apps](use-custom-model-driven-app-on-mobile.md).

> [!IMPORTANT]
> Las aplicaciones basadas en modelos de Dynamics 365 for Sales, Dynamics 365 for Customer Service, Dynamics 365 for Field Service, Dynamics 365 for Marketing y Dynamics 365 for Project Service Automation<!--Via Dynamics Style Guide. If this sentence doesn't apply to all these products, maybe only mention Sales, Customer Service, and Field Service as you do in use-custom-model-driven-app-on-mobile.md? "Dynamics verticals" is out of brand.--> no se ejecutan en la aplicación móvil de Power Apps. En su lugar, se usa la aplicación Dynamics 365 para teléfonos y tabletas. Más información: [Manual del usuario (Dynamics 365 para teléfonos y tabletas)](https://docs.microsoft.com/dynamics365/mobile-app/dynamics-365-phones-tablets-users-guide).

![Aplicación móvil de Power Apps](media/powerappsmobile.png "Interfaz de usuario de Power Apps para dispositivos móviles")

Leyenda:

1. **Aplicaciones basadas en modelos**
2. **Aplicaciones de lienzo**

**Para suscribirse a la versión preliminar de Power Apps para dispositivos móviles:**

1. [Instale Power Apps para iOS](https://go.microsoft.com/fwlink/?linkid=2125171) o [Power Apps para Android](https://go.microsoft.com/fwlink/?linkid=2125172).
2. Si ya ha instalado la aplicación, esta se reemplazará por la versión preliminar de la aplicación.
3. Asegúrese de actualizar manualmente a la versión más reciente disponible para beneficiarse de las últimas mejoras. 
3. Después de instalar la aplicación, puede empezar las pruebas. Si tiene algún comentario, póngase en contacto con nosotros en [pamobsup@microsoft.com](mailto:pamobsup@microsoft.com). 

## <a name="open-power-apps-and-sign-in"></a>Apertura de Power Apps e inicio de sesión

Abra Power Apps en el dispositivo móvil e inicie sesión con sus credenciales de Azure Active Directory.

![Inicio de sesión en Power Apps](media/powerapps_mobile_app_signin_screen.png "Iniciar sesión en Power Apps")

Si tiene la aplicación Microsoft Authenticator instalada en el dispositivo móvil, simplemente escriba el nombre de usuario cuando se le solicite y, después, apruebe la notificación enviada al dispositivo.


## <a name="find-the-app"></a>Buscar la aplicación

Al iniciar sesión en la aplicación, el filtro está establecido en **Mis aplicaciones** de forma predeterminada. Si no encuentra la aplicación que está buscando, puede abrir el menú de **Power Apps** y seleccionar otro filtro. 


![Filtros de aplicación](media/filter-menu.png "Filtros de aplicación")

Los siguientes filtros están disponibles:

* **Todas las aplicaciones**: muestra todas las aplicaciones de lienzo y basadas en modelos a las que tiene acceso, incluidas las aplicaciones que ha creado y las que otros han compartido con usted.

* **Mis aplicaciones**: en el caso de las aplicaciones de lienzo, se muestran las aplicaciones de lienzo que ha abierto, aquellas de las que es propietario y las que puede editar. En el caso de las aplicaciones basadas en modelos, se muestran todas las aplicaciones de este tipo a las que tiene acceso. 

* **Aplicaciones de ejemplo** (solo aplicaciones de lienzo): muestra las aplicaciones de lienzo de ejemplo de Microsoft que presentan escenarios de aplicaciones reales con datos ficticios para ayudar a explorar las posibilidades de diseño.

* **Favoritos** (solo aplicaciones de lienzo): muestra las aplicaciones de lienzo que ha marcado seleccionando los puntos suspensivos (…) en el icono de la aplicación y, después, seleccionando **Favoritos**. Para quitar una aplicación de esta lista, seleccione los puntos suspensivos (…) en el icono de la aplicación y, después, seleccione **Quitar de Favoritos**.

    ![Marcado como favorito](media/add_favorite_app.png "Marcar como favorito")

* **Aplicaciones destacadas** (solo aplicaciones de lienzo): muestra las aplicaciones de lienzo que el administrador ha marcado como aplicaciones destacadas.

### <a name="sort-apps"></a>Ordenación de las aplicaciones

Después de filtrar las aplicaciones, puede ordenar la lista filtrada por la fecha de la última vez que se abrieron o modificaron, o bien alfabéticamente por nombre. Estas preferencias se conservan cuando cierra y vuelve a abrir las aplicaciones. Puede ordenar tanto las aplicaciones de lienzo como las aplicaciones basadas en modelos.

![Menú de ordenación](media/sort_apps.png "Menú Ordenar")

### <a name="search-apps"></a>Buscar aplicaciones

Si conoce el nombre de la aplicación que quiere ejecutar, seleccione el icono de búsqueda en la parte superior y, después, escriba parte del nombre en el cuadro de búsqueda. Puede buscar aplicaciones de lienzo y aplicaciones basadas en modelos.

![Búsqueda de aplicaciones](media/search_apps.png "Búsqueda de aplicaciones")

Si ha filtrado las aplicaciones, la búsqueda se realizará en la lista filtrada.

### <a name="refresh-the-list-of-apps"></a>Actualización de la lista de aplicaciones

Seleccione el icono de actualización ![Icono Actualizar](media/refresh_icon.png) para actualizar la lista de aplicaciones. De esta manera, se actualizarán las listas de aplicaciones de lienzo y aplicaciones basadas en modelos. 

## <a name="pin-an-app-to-the-home-screen"></a>Anclar una aplicación a la pantalla de inicio

Puede anclar aplicaciones de lienzo y aplicaciones basadas en modelos a la pantalla principal de su dispositivo para tener un acceso rápido. Seleccione los puntos suspensivos (…) del icono de la aplicación, seleccione **Anclar a página principal** y, luego, siga las instrucciones que aparecen.

![Anclaje de una aplicación](media/pin_to_home.png "Anclaje de una aplicación")

## <a name="see-non-production-apps"></a>Visualización de las aplicaciones que no son de producción

De forma predeterminada, solo las aplicaciones basadas en modelos de producción se muestran en la lista de aplicaciones.

Para ver las aplicaciones basadas en modelos de entornos que no son de producción, seleccione el menú **Configuración** ![Icono de Configuración](media/settings_icon.png) y, a continuación, active la opción **Mostrar aplicaciones que no son de producción**. Siga las instrucciones que aparecen.

![Conmutador de alternancia para aplicaciones que no son de producción](media/non_prod_toggle.png "Conmutador de alternancia para aplicaciones que no son de producción")

## <a name="run-an-app"></a>Ejecutar una aplicación

Para ejecutar una aplicación en un dispositivo móvil, seleccione el icono de la aplicación. Si otro usuario creó una aplicación y la compartió con usted en un correo electrónico, puede ejecutarla seleccionando el vínculo del correo electrónico.

### <a name="run-a-canvas-app"></a>Ejecución de una aplicación de lienzo

Si es la primera vez que ejecuta una aplicación de lienzo mediante la aplicación móvil de Power Apps, aparecerá una pantalla que le mostrará los gestos de deslizamiento.

#### <a name="close-a-canvas-app"></a>Cierre de una aplicación de lienzo

Deslice su dedo desde el borde izquierdo de la aplicación al borde derecho para cerrarla. En los dispositivos Android, también puede presionar el botón Atrás y luego confirmar que quiere cerrar la aplicación.

![Cierre de una aplicación](media/swipe.gif "Cerrar una aplicación")

#### <a name="pinch-and-zoom-in-on-a-canvas-app"></a>Gesto de reducir o ampliar en una aplicación de lienzo

![Gesto de reducir o ampliar](media/pinchtozoom.jpg "Gesto de reducir o ampliar")

#### <a name="give-consent-to-a-canvas-app"></a>Concesión de permisos a una aplicación de lienzo

Si una aplicación requiere una conexión a un origen de datos o permiso para usar las funcionalidades del dispositivo (como la cámara o los servicios de ubicación), debe dar su consentimiento antes de usar la aplicación. Normalmente, solo se le pedirá la primera vez que ejecute la aplicación.

![Concesión de permisos](media/give_consent_canvas.jpg "Dar consentimiento")

### <a name="run-a-model-driven-app"></a>Ejecutar una aplicación controlada por modelos 

La siguiente imagen muestra un ejemplo de la pantalla de una aplicación basada en modelos después de haber iniciado sesión. Para obtener información, consulte la [Guía del usuario para usar aplicaciones basadas en modelos que se ejecutan en la aplicación móvil de Power Apps](use-custom-model-driven-app-on-mobile.md). 

![Página principal de la aplicación basada en modelos](media/model-driven-app-opened.png "Página principal de la aplicación basada en modelos")

#### <a name="give-consent-to-a-model-driven-app"></a>Concesión de permisos a una aplicación basada en modelos

Si una aplicación requiere una conexión a un origen de datos o permiso para usar las funcionalidades del dispositivo (como la cámara o los servicios de ubicación), debe dar su consentimiento antes de usar la aplicación. Normalmente, solo se le pedirá la primera vez que use la aplicación.

![Concesión de permisos](media/give_consent.png "Dar consentimiento")

#### <a name="close-a-model-drive-app"></a>Cierre de una aplicación basada en modelos

Seleccione el icono del mapa del sitio ![Icono del mapa del sitio](media/pa_mobile_sitemap_icon.png "Icono del mapa del sitio") y, después, **Aplicaciones**.

![Cierre de una aplicación basada en modelos](media/pa_mobile_close_app.png "Cierre de una aplicación basada en modelos")

## <a name="known-issues"></a>Problemas conocidos

Todavía estamos trabajando en algunos problemas conocidos y publicaremos correcciones con el tiempo. Asegúrese de actualizar de forma manual a la versión preliminar más reciente en cuanto esté disponible. 

Problemas conocidos

- A veces desaparecen los iconos de las aplicaciones basadas en modelos.

