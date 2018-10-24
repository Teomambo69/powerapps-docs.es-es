---
title: Entornos de versión preliminar | Microsoft Docs
description: Obtenga acceso anticipado a las funcionalidades con el programa de versión preliminar de PowerApps
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 08/29/2018
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: e2c4c735827941b32ce5e019eb8d71e4328e4a7a
ms.sourcegitcommit: b8eee36e680036accb0e7d9fc7a434906af1c4d2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2018
ms.locfileid: "43297916"
---
# <a name="powerapps-preview-program"></a>Programa de versión preliminar de PowerApps
PowerApps actualiza la plataforma y sus funcionalidades cada pocos días o semanas. El programa de versión preliminar de PowerApps es una manera de obtener acceso anticipado a las próximas funcionalidades y actualizaciones antes de su disponibilidad en otras regiones (donde se implementan las aplicaciones de producción del cliente). 

Con el programa de versión preliminar de PowerApps, puede:
- **Probar, aprender y utilizar el software de prueba de las próximas funcionalidades**: muchas funcionalidades se lanzarán primero en versión preliminar durante unos días para obtener comentarios. Al participar en el programa de versión preliminar, puede aprender antes las nuevas funcionalidades y proporcionar comentarios. Además, estará preparado para aprovechar rápidamente las nuevas funcionalidades tan pronto como lleguen a las regiones en las que se crean las aplicaciones de producción.
- **Habilitar la continuidad empresarial asegurándose de que las aplicaciones actuales sigan funcionando** con las próximas actualizaciones (vNext) de PowerApps.

## <a name="what-in-powerapps-is-available-for-preview"></a>¿Qué está disponible en la versión preliminar de PowerApps?
Para tener acceso a las funcionalidades de versión preliminar en PowerApps, tiene que estar en un entorno de versión preliminar. En la sección siguiente se ofrece más información sobre el entorno de versión preliminar.
Actualmente lanzaremos la versión preliminar para los escenarios siguientes en PowerApps:
1. **Creación de aplicaciones**: puede crear aplicaciones de lienzo con la próxima versión de PowerApps. Para ello, han de crearse aplicaciones en un entorno de versión preliminar. Limitaciones actuales: no se pueden compilar aplicaciones controladas por modelos en el programa de versión preliminar; estamos trabajando en ello.
2. **Administración de aplicaciones**: puede administrar y compartir aplicaciones con el [portal web de PowerApps][2]. Para obtener acceso a las funcionalidades de versión preliminar, lo único que necesita es encontrarse en un entorno de versión preliminar; este le llevará a la versión preliminar del [portal web de PowerApps][3].
3. **Reproducción de aplicaciones**: para reproducir las aplicaciones en un entorno de versión preliminar tiene que usar el reproductor web. Al hacerlo, se le dirigirá automáticamente a la [versión preliminar del reproductor web][4]. Las aplicaciones se reproducirán con la versión vNext del reproductor web de PowerApps. Limitaciones actuales: PowerApps Mobile para iOS, Android y Windows no están disponibles actualmente en la versión preliminar. Es posible que la reproducción de las aplicaciones creadas en el entorno de primera versión no funcione; estamos trabajando en ello.
4. **Administración de PowerApps**: hay experiencias de administración disponibles para la versión preliminar con la [versión preliminar del Centro de administración de PowerApps][1]

## <a name="how-to-get-early-access-to-the-upcoming-updates"></a>¿Cómo obtener acceso anticipado a las próximas actualizaciones?
En PowerApps, todas las aplicaciones y los recursos relacionados se almacenan en un entorno. El acceso anticipado a todas las funcionalidades de la versión preliminar también está disponible con un entorno creado en una región donde se implementa vNext (versión preliminar). Por ahora, solo hay una región, **Versión preliminar (Estados Unidos)**, tal y como se muestra en la imagen siguiente:

![](./media/preview-environment/env3-preview.png)

Seleccione **Versión preliminar (Estados Unidos)** como región del entorno y acepte el consentimiento para unirse al programa de versión preliminar para crear el entorno que tenga acceso a la próxima versión (vNext) de PowerApps.
Todas las aplicaciones y los demás recursos creados en este entorno se encuentran en la versión vNext de la plataforma (SAAS).

## <a name="how-to-learn-about-the-latest-updates"></a>¿Cómo obtener información sobre las actualizaciones más recientes?
Puede conocer las nuevas funcionalidades que están disponibles con la versión preliminar en [Novedades de PowerApps][5]. Las funcionalidades que solo están disponibles en la versión preliminar tienen una etiqueta "Versión preliminar".

## <a name="key-scenarios-to-test-with-the-preview-program"></a>Escenarios clave para probar con el programa de versión preliminar
1. **Validación de las aplicaciones de producción con las próximas actualizaciones de PowerApps (vNext)**

   Es posible que quiera comprobar las aplicaciones de producción, para que funcionen bien con las próximas actualizaciones de PowerApps. Puede [copiar][6] las aplicaciones desde un entorno de producción a un entorno de primera versión y reproducir las aplicaciones para probar los escenarios. Tenga en cuenta que también habrá que mover los demás recursos necesarios, como CustomAPI, Flow, etc. Esto solo debería crear otra copia de estas aplicaciones y los recursos necesarios. Puede empezar a probar las actualizaciones más recientes, no solo para reproducir una aplicación, sino también mientras edita y administra las aplicaciones.
   
2. **Prueba de las nuevas funcionalidades disponibles en versión preliminar**

   Inicialmente lanzaremos muchas nuevas funcionalidades en la región **Versión preliminar (Estados Unidos)**. Puede probar las nuevas funcionalidades antes de que estén disponibles en el resto de las regiones (lo que puede afectar a su entorno de producción).

## <a name="how-to-provide-feedback-to-the-product-team"></a>¿Cómo proporcionar comentarios al equipo del producto?
Puede proporcionar comentarios en el [foro de PowerApps][8] y/o ponerse en contacto con [soporte técnico][9].

## <a name="what-are-the-known-issues-and-limitations"></a>¿Cuáles son las limitaciones y los problemas conocidos?
1. **Portales de PowerApps y clientes que no están disponibles en versión preliminar** 

   Hay determinadas funcionalidades, servicios y portales que están disponibles en versión preliminar:
   
   ![](./media/preview-environment/table.png)

2. **Acceso a aplicaciones creadas en el entorno de primera versión desde Desktop Studio en Windows**

   Como se mencionó anteriormente, Desktop Studio en Windows no está disponible en versión preliminar. Por lo tanto, es posible que la creación o edición de las aplicaciones en el entorno de versión preliminar no sea compatible con su instancia de Desktop Studio y muestre el mensaje de error siguiente:
   
   ![](./media/preview-environment/error2.jpg)

   En tal caso, se recomienda usar Web Studio para crear o editar una aplicación en el entorno de versión preliminar.

3. **No se puede crear la base de datos en la región de versión preliminar**

   Actualmente, no se puede crear una base de datos con Common Data Service for Apps en un entorno en la región Versión preliminar (Estados Unidos)de vista previa (Estados Unidos); estamos trabajando en ello.


<!--Reference links in article-->
[1]: https://preview.admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://preview.web.powerapps.com
[4]: https://preview.web.powerapps.com/webplayer
[5]: https://docs.microsoft.com/powerapps/maker/canvas-apps/release-notes
[6]: https://docs.microsoft.com/powerapps/administrator/environment-and-tenant-migration
[7]: https://preview.create.powerapps.com
[8]: https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1
[9]: https://powerapps.microsoft.com/support/

