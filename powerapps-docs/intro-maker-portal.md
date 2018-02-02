---
title: "Introducción a powerapps.com | Microsoft Docs"
description: Un nuevo lugar de encuentro para todos los creadores de aplicaciones.
services: 
suite: powerapps
documentationcenter: na
author: linhtranms
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/28/2016
ms.author: litran
ms.openlocfilehash: a6ec814d057f85b39f794bd7c0c100c5a28f652f
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="introduction-to-powerappscom"></a>Introducción a powerapps.com
El equipo de PowerApps va a volver a presentar [powerapps.com](http://web.powerapps.com) como el nuevo lugar de encuentro para los creadores de aplicaciones. Se ha rediseñado la página como el principal sitio donde los creadores puedan empezar a crear aplicaciones, usar Microsoft Common Data Service y administrar sus aplicaciones, todo en una sola ubicación. En este artículo, se le guiará por los siguientes elementos:

* el encabezado
* la página principal
* la página **Aplicaciones**

## <a name="header"></a>Encabezado
Cuando se registra e inicia sesión por primera vez en powerapps.com, observará el nuevo encabezado del sitio. Cerca del borde izquierdo del encabezado está el botón cuadrado de Office. Se trata de un lugar rápido desde donde acceder a todos los demás productos de Office, como PowerPoint, OneNote y Word, así como a Microsoft Flow y Dynamics 365.

![Encabezado: botón cuadrado](./media/intro-maker-portal/waffle.png)

Cerca del borde derecho del encabezado, en primer lugar verá una lista desplegable de entornos, donde puede cambiar rápidamente entre ellos. Probablemente, **Entorno predeterminado** está seleccionado de forma predeterminada. [Aprenda más acerca de los entornos](environments-overview.md).

![Encabezado: entorno](./media/intro-maker-portal/environment.png)

Junto al menú desplegable de entornos, verá un icono de descarga. Haga clic o pulse en este icono para mostrar un cuadro de diálogo con vínculos para descargar PowerApps Mobile (para iOS o Android) o PowerApps Studio para Windows.

![Encabezado: descarga](./media/intro-maker-portal/downloads2.png)

Junto al icono de descarga, verá un icono de engranaje para la configuración. Haga clic o pulse en este icono para mostrar vínculos para conexiones, puertas de enlace y el centro de administración.

![Encabezado: configuración](./media/intro-maker-portal/settings_items2.png)

Junto al de configuración, verá un icono de signo de interrogación para obtener ayuda. Haga clic o pulse en este icono para mostrar vínculos a Aprendizaje guiado, Documentación, Soporte técnico, Comunidad, Blogs, Legal y Privacidad.

![Encabezado: ayuda](./media/intro-maker-portal/help_items2.png)

## <a name="homepage"></a>Página principal
Después de iniciar sesión en [powerapps.com](http://web.powerapps.com), llegará a la página principal de forma predeterminada. Se ha cambiado el diseño de esta página principal para ayudarle a empezar a trabajar rápidamente, tanto si crea aplicaciones como si quiere explorar Common Data Service.

Si ha iniciado sesión en PowerApps antes y ha ejecutado o creado algunas aplicaciones, la primera sección que verá en la página principal es una lista de **aplicaciones recientes**. Están ordenadas según la fecha en que se abrieron más recientemente.

![Aplicaciones recientes](./media/intro-maker-portal/recentapps2.png)

Cerca de la esquina superior derecha, aparece una flecha llamada **Aplicaciones** y vínculos directos a la página **Aplicaciones** para que pueda ver todas las aplicaciones.

Si nunca ha iniciado sesión, creado una aplicación ni ejecutado una aplicación antes, no verá la sección **Aplicaciones recientes**. En su lugar verá el titular **Crear una aplicación**.

![Crear una aplicación](./media/intro-maker-portal/createapp.png)

Haga clic o pulse en **Introducción** en este titular para mostrar opciones para crear una aplicación con **PowerApps Studio para Windows** o **PowerApps Studio para web**.

![Modo Crear una aplicación](./media/intro-maker-portal/createmodal2.png)

Junto a **Introducción**, aparecen vínculos a nuestros vídeos de tutoriales sobre cómo crear rápidamente una aplicación a partir de datos (en SharePoint o PowerApps) y compartirla. El vínculo de la flecha **Más información** le llevará a un tema sobre cómo crear una aplicación a partir de datos existentes.

Debajo del titular **Crear una aplicación**, se ve el titular **Usar Microsoft Common Data Service**.

![Microsoft Common Data Service](./media/intro-maker-portal/cds2.png)

En **Common Data Service**, aparecerá un botón diferente en función de su licencia o permiso.

* Si aparece el botón **Iniciar período de prueba**, carece de licencia de P2 de PowerApps, que es necesaria para Common Data Service. Haga clic o pulse en este botón para abrir la página donde puede registrarse en una prueba gratuita de 90 días de esta licencia. [Más información sobre las licencias de PowerApps](signup-for-powerapps.md).
* Si aparece el botón **Introducción**, se encuentra en un entorno que carece de base de datos de Common Data Service o no tiene acceso a ella. Haga clic o pulse en este botón para crear un entorno y una base de datos a la vez, para que pueda empezar a usar Common Data Service para las aplicaciones. [Más información acerca de cómo crear entornos](environments-administration.md).
  
    ![Crear un entorno y una base de datos](./media/intro-maker-portal/createenvanddb2.png)
  
    Si no desea crear un entorno, siempre puede cambiar a uno al que tenga acceso.
* Si aparece el botón **Crear base de datos**, se encuentra en un entorno que carece de base de datos de Common Data Service, pero tiene permiso para crear una.
  
    ![Crear una base de datos](./media/intro-maker-portal/cds-createdb2.png)
  
    Si hace clic o pulsa en este botón, aprovisionará una base de datos para este entorno.
  
    ![Crear una base de datos](./media/intro-maker-portal/cds_createdb22.png)
* Si aparece el botón **Explorar entidades**, se encuentra en un entorno con una base de datos de Common Data Service ya aprovisionada y tiene acceso a ella. Haga clic o pulse en este botón para abrir la página **Entidades**.
  
    ![Crear una base de datos](./media/intro-maker-portal/cds_browseentities2.png)

Debajo del titular **Usar Microsoft Common Data Service**, verá un conjunto de aplicaciones de ejemplo y aplicaciones de ejemplo conectadas ya creadas para que las use.

* **Aplicaciones de ejemplo**: las aplicaciones de ejemplo se han creado para diferentes escenarios empresariales con un diseño de teléfono o tableta. Puede hacer clic en una aplicación para ver rápidamente una descripción de lo que hace, el diseño con que se creó y qué funcionalidades demuestra, como cámara, GPS o botones de radio. Es una forma rápida de que los nuevos usuarios aprendan sobre las funcionalidades de PowerApps, y puede usar una plantilla para crear una aplicación idéntica en PowerApps Studio para Windows.
  
    ![Aplicaciones de ejemplo](./media/intro-maker-portal/sampleapps2.png)
* **Aplicaciones de ejemplo conectadas**: estas aplicaciones se conectan a los datos a través de una conexión de datos como Office 365, Salesforce, Trello y Wunderlist. Este conjunto de aplicaciones es diferente de las aplicaciones de ejemplo anteriores. Al hacer clic o pulsar en una aplicación de ejemplo conectada, realmente está aprovisionando una nueva instancia de la aplicación (considérela una plantilla). Se le pedirá que escriba sus credenciales para conectarse a los datos. Lo que resulta muy útil con una aplicación de ejemplo conectada es que se aprovisiona una instancia automáticamente y luego puede abrirla en PowerApps Studio para aprender cómo se creó la aplicación correspondiente. El inconveniente es que puede tardar bastante tiempo (hasta un minuto) en crearse. Así que sea paciente y deje el explorador abierto cuando haga clic o pulse en una aplicación de ejemplo conectada.
  
    ![Aplicaciones de ejemplo conectadas](./media/intro-maker-portal/connectedsampleapps2.png)

## <a name="new-apps-page"></a>Página de nuevas aplicaciones
Puede acceder a la página **Aplicaciones** por medio de la barra de navegación izquierda en [powerapps.com](http://web.powerapps.com).

![Navegación izquierda](./media/intro-maker-portal/leftnav2.png)

Antes, la página **Aplicaciones** permitía cambiar entre la vista de iconos y la vista de lista. A partir del 26 de octubre de 2016, solo admite la vista de lista.

![Vista de lista de aplicaciones](./media/intro-maker-portal/listview2.png)

Tenga en cuenta que la vista de lista solo muestra las aplicaciones en el entorno seleccionado. Para ver aplicaciones de un entorno diferente, cambie a él mediante el selector de entorno en el encabezado. [Más información sobre cómo cambiar de entorno](working-with-environments.md).

## <a name="whats-new"></a>Novedades

* Si hace clic o pulsa en una aplicación, ahora se abre en PowerApps Studio para web en una nueva pestaña.
* De forma predeterminada, la página **Aplicaciones** muestra todas las aplicaciones para las que tenga permiso de edición. Para ver **Todas las aplicaciones** (incluidas las que solo puede utilizar), seleccione el filtro **Todas las aplicaciones**.
  
   ![Filtro de aplicaciones](./media/intro-maker-portal/allapps_filter.png)

También existen:

* **Apps I can use** (Aplicaciones que puedo usar), donde aparecen todas las aplicaciones que se han compartido con usted con permiso Usuario (solo puede ejecutar la aplicación). Tenga en cuenta que también puede adquirir estas aplicaciones en [Dynamics 365](http://home.dynamics.com).
* **Aplicaciones que me pertenecen**, con todas las aplicaciones que ha creado.
* **Aplicaciones con las que colaboro**, que contiene todas las aplicaciones que se han compartido con usted con permiso Colaborador.
* **Aplicaciones de ejemplo**, que incluye todas las aplicaciones de ejemplo (no conectadas).

Si hace clic o pulsa en el círculo de información, se abre la página de detalles de la aplicación.

![Detalles de la aplicación](./media/intro-maker-portal/ibubble.png)

Si hace clic en el botón de puntos suspensivos de una aplicación, aparecen opciones como Reproducir, Editar, Compartir y Detalles.

![Opciones de la aplicación](./media/intro-maker-portal/ellipsis.png)

Básicamente, estas son las novedades en powerapps.com, que están destinadas a los creadores de aplicaciones. Esperamos que le resulten útiles. Deje sus comentarios sobre lo que le ha gustado y lo que le gustaría ver. Nos encantaría recibir sus comentarios.

