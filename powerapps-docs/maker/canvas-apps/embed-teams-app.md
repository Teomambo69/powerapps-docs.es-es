---
title: Inserción de una aplicación de PowerApps en Teams | Microsoft Docs
description: Puede insertar una aplicación creada en PowerApps en Microsoft Teams para compartirlo.
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/29/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d17b02cc87bb219474aade955a2910f12fcf7f27
ms.sourcegitcommit: 2376c1f1f3431bca52a8deb9b966ce1fe9f88da0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66381395"
---
# <a name="embed-a-powerapps-app-in-teams"></a>Inserción de una aplicación de PowerApps en los equipos 

Puede compartir un PowerApps ha creado insertando directamente en Microsoft Teams. Cuando haya completado, los usuarios pueden seleccionar **+** para agregar la aplicación a cualquiera de **su** team canales o las conversaciones en el equipo se encuentra en. La aplicación aparece como un icono en **pestañas para su equipo**. 

Un administrador puede cargar la aplicación, por lo que se muestra en **todas** los equipos en el inquilino en el **sección de todas las pestañas**. Consulte [compartir una aplicación en Microsoft Teams](https://review.docs.microsoft.com/en-us/power-platform/admin/embed-app-teams?branch=JimHoltzWorkBranch).

> [!NOTE]
> Directivas de aplicación personalizada de equipo deben establecerse para permitir la carga de aplicaciones personalizadas. Si no se puede insertar la aplicación en los equipos, póngase en contacto con el administrador para comprobar si ha configurado [configuración de aplicación personalizada](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings). 

## <a name="prerequisites"></a>Requisitos previos

- [Tiene una licencia de PowerApps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- Crea una aplicación de lienzo

## <a name="locate-your-powerapps-guid"></a>Busque su PowerApp GUID

Busque y anote su PowerApp GUID para usarlo en un paso posterior.

1. Inicie sesión en [ https://web.powerapps.com ](https://web.powerapps.com)y, a continuación, seleccione **aplicaciones** en el menú.

   > [!div class="mx-imgBorder"] 
   > ![Mostrar lista de aplicaciones](./media/embed-teams-app/file-apps2.png "mostrar la lista de aplicaciones")

2. Seleccione **más comandos** (...) para la aplicación que quiera compartir en los equipos y, a continuación, seleccione **detalles**.

   > [!div class="mx-imgBorder"] 
   > ![Detalles de la aplicación](./media/embed-teams-app/app-details.png "detalles de la aplicación")

3. Registro de la **Id. de aplicación** para su uso posterior.

   > [!div class="mx-imgBorder"] 
   > ![Detalles de la aplicación](./media/embed-teams-app/app-details2.png "detalles de la aplicación")

## <a name="install-app-studio"></a>Instale App Studio

Puede omitir estos pasos si App Studio ya está instalado. 

1. En los equipos, seleccione **aplicaciones** en la parte izquierda inferior del menú de los equipos (![icono aplicaciones](./media/embed-teams-app/apps-icon.png "icono aplicaciones")).

2. Busque "App Studio" en el cuadro de búsqueda y, a continuación, selecciónelo.

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. Seleccione **instalar**. 

   > [!div class="mx-imgBorder"] 
   > ![Instale App Studio](./media/embed-teams-app/install-app-studio.png "instalar App Studio")

4. Seleccione **abierto** para la característica de la aplicación.

   > [!div class="mx-imgBorder"] 
   > ![Abra App Studio](./media/embed-teams-app/open-app-studio.png "abra App Studio")

## <a name="create-a-teams-app-for-your-powerapp"></a>Crear una aplicación de los equipos para su aplicación de Powerapps

1. En los equipos, abra App Studio.

   > [!div class="mx-imgBorder"] 
   > ![Abra App Studio](./media/embed-teams-app/open-app-studio2.png "abra App Studio")

2. Seleccione el **editor de manifiestos** pestaña y, a continuación, seleccione **crear una nueva aplicación** en bienvenida.

   > [!div class="mx-imgBorder"] 
   > ![Crear nueva aplicación](./media/embed-teams-app/create-new-app.png "crear nueva aplicación")

3. Rellene la información acerca de la aplicación en el **detalles de la aplicación** página.  Para el GUID de Id. de aplicación, debe usar GUID del PowerApp de Id. de aplicación que registró anteriormente.  Esto evita la duplicación de las aplicaciones de los equipos para una determinada aplicación de Powerapps.
 
   > [!div class="mx-imgBorder"] 
   > ![Rellene la información](./media/embed-teams-app/fill-in-info-about-app.png "rellene la información")

   |Campos  |Descripción  |
   |---------|---------|
   |**Nombres de aplicación** |    |
   |Nombre corto     | Obligatorio. El nombre para mostrar corto para la aplicación. límite de 30 caracteres.        |
   |Nombre largo     | El nombre completo de la aplicación, se usa si el nombre de la aplicación completa es superior a 30 caracteres.       | 
   |**Identificación**     |         |
   |Id. de aplicación     | Obligatorio. El identificador único de Microsoft generado para esta aplicación.        |
   |Nombre del paquete     | Obligatorio. Un identificador único para esta aplicación. Se recomienda usar la notación de dominio inverso; Por ejemplo, com.example. <AppName>.       |
   |Versión     | Obligatorio. La versión de la aplicación específica. Si actualiza algo en su manifiesto, también debe incrementar la versión.     |
   |**Descripciones**    |     |
   | Descripción breve    | Obligatorio. Una breve descripción de su experiencia de aplicación, que se usa cuando el espacio es limitado. límite de 80 caracteres.   |
   | Descripción larga    | Obligatorio. La descripción completa de la aplicación.     |
   | **Información para desarrolladores**    |     |
   | Nombre    | Obligatorio. El nombre para mostrar de la compañía o el desarrollador.     |
   | Sitio Web    | Obligatorio. Dirección URL https:// al sitio Web de la aplicación a través de powerapps.com. Cuando un usuario instala la aplicación, un "acerca de la aplicación" se mostrará la página. Debe ser un vínculo a la versión web de la aplicación en powerapps.com.   |
   | **Direcciones URL de aplicación**    | Estos vínculos se mostrarán en el **sobre** página junto con la dirección URL del sitio Web.     |
   | Declaración de privacidad    | Obligatorio. La dirección URL https:// política de privacidad del desarrollador. [Ejemplo](https://go.microsoft.com/fwlink/p/?LinkID=698505).   |
   | Términos de uso    | Obligatorio. La dirección URL https:// términos del desarrollador de uso.  [Ejemplo](https://go.microsoft.com/fwlink/p/?LinkID=698507).  |
   | **Personalización de marca**    |     |
   | A todo color    | Una ruta de acceso relativa a un icono de PNG 192 x 192 a todo color.    |
   | Esquema transparente    |Una ruta de acceso relativa a un icono de esquema PNG de 32 x 32 transparente.     |
   | Color de énfasis    | Un color que se usará junto con tal y como un fondo para los iconos del esquema.     |

Para obtener más información, consulte [Editor de manifiestos](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor) y [esquema del manifiesto](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema).

4. Desplácese hacia abajo hasta la sección personalización de marca y agregue los logotipos y el color de énfasis deseado para la aplicación.  Estos son los logotipos que se mostrará para la aplicación en los equipos. 

   > [!div class="mx-imgBorder"] 
   > ![Personalización de marca y pestañas](./media/embed-teams-app/branding-tabs.png "fichas y personalización de marca")

5. En **capacidades**, seleccione **pestañas**.

6. En **pestaña equipo** seleccione **agregar**.

   > [!div class="mx-imgBorder"] 
   > ![Pestaña equipo agregar](./media/embed-teams-app/team-tab-add.png "Agregar pestaña del equipo")

7. Agregue la dirección URL de la configuración de la aplicación en el campo de entrada de "Dirección URL de la configuración", con el formato siguiente: `https://web.powerapps.com/webplayer/teamsapptabsettings?appid=<PowerApp ID>`

   Reemplace `<PowerApp ID>` con el GUID de Id. de aplicación que registró anteriormente.

   Seleccione el [ámbito](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope) aparecen en la aplicación. Asegúrese de **puede actualizar la configuración** está activado y, a continuación, seleccione **guardar**.

   > [!div class="mx-imgBorder"] 
   > ![Dirección URL de configuración](./media/embed-teams-app/configuration-url.png "dirección URL de configuración")

8. En **finalizar**, seleccione **dominios válidos**. Agregar **apps.powerapps.com** y **apps.preview.powerapps.com** como dominios válidos para la aplicación de los equipos.

   > [!div class="mx-imgBorder"] 
   > ![Agregar dominios válidos](./media/embed-teams-app/add-valid-domains.png "agregar dominios válidos")

9. En **finalizar**, seleccione **prueba y distribuir**. En **instalar**, seleccione **instalar**.

   > [!div class="mx-imgBorder"] 
   > ![Seleccione instalar](./media/embed-teams-app/test-distribute-app.png "seleccione instalar")

10. Seleccione el equipo de la aplicación instalada en y, a continuación, seleccione **instalar**.

    > [!div class="mx-imgBorder"] 
    > ![Agregar un equipo de instalación](./media/embed-teams-app/new-app-add-to-team.png "agregar a la instalación de equipo")

11. Si desea agregar una instancia de esa aplicación a un canal inmediatamente, seleccione el canal que desea usar la aplicación en y seleccione **configurar**.

    > [!div class="mx-imgBorder"] 
    > ![Seleccione configurar](./media/embed-teams-app/app-now-available.png "seleccione Configurar")

12. Seleccione **Guardar**.

## <a name="add-the-app-as-a-tab"></a>Agregar la aplicación como una pestaña

Para agregar la aplicación como una pestaña a cualquier conversación o el canal, seleccione **+** y, a continuación, en **pestañas para su equipo** seleccione la aplicación. 

> [!div class="mx-imgBorder"] 
> ![Agregar la aplicación como pestaña](./media/embed-teams-app/add-app-as-tab.png "agregar la aplicación como pestaña")

La aplicación ahora aparece como una pestaña.

> [!div class="mx-imgBorder"] 
> ![La aplicación como pestaña](./media/embed-teams-app/app-as-tab.png "ficha con la aplicación")

### <a name="see-also"></a>Vea también
[Bienvenido a Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[Para que los administradores: Insertar una aplicación en Microsoft Teams](https://docs.microsoft.com/power-platform/admin/share-app-teams)