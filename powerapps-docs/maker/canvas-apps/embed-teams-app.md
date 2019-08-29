---
title: Insertar una aplicación de PowerApps en Teams | Microsoft Docs
description: Puede insertar una aplicación creada en PowerApps en Microsoft Teams para compartirla.
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
ms.openlocfilehash: ca3430d6b639b7a4c3980f5bbb0ba202220f6d9e
ms.sourcegitcommit: 935470edc7441b76533cc937e6f32229bfd6f11f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70117790"
---
# <a name="embed-a-powerapps-app-in-teams"></a>Inserción de una aplicación de PowerApps en Teams 

Puede compartir un PowerApps que haya creado al incrustarlo directamente en Microsoft Teams. Cuando haya finalizado, los **+** usuarios pueden seleccionar agregar su aplicación a cualquiera de **sus** canales o conversaciones del equipo en el que se encuentre. La aplicación aparece como un icono en **pestañas para el equipo**. 

Un administrador puede cargar la aplicación para que se muestre a **todos los** equipos del inquilino en la **sección todas**las pestañas. Consulte [compartir una aplicación en Microsoft Teams](https://docs.microsoft.com/en-us/power-platform/admin/embed-app-teams).

> [!NOTE]
> Las directivas de aplicación personalizadas del equipo deben estar configuradas para permitir la carga de aplicaciones personalizadas. Si no puede insertar la aplicación en Teams, consulte con el administrador para ver si ha configurado la [Configuración personalizada](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)de la aplicación. 

## <a name="prerequisites"></a>Requisitos previos

- [Tener una licencia de PowerApps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- Se creó una aplicación de lienzo

## <a name="locate-your-powerapps-guid"></a>Busque el GUID de PowerApp

Busque y tome nota del GUID de PowerApp para usarlo en un paso posterior.

1. Inicie sesión en y seleccione aplicaciones en el menú. [https://web.powerapps.com](https://web.powerapps.com)

   > [!div class="mx-imgBorder"] 
   > ![Mostrar lista de aplicaciones](./media/embed-teams-app/file-apps2.png "Mostrar lista de aplicaciones")

2. Seleccione **más comandos** (...) para la aplicación que desea compartir en Teams y, a continuación, seleccione **detalles**.

   > [!div class="mx-imgBorder"] 
   > ![Detalles] de la aplicación (./media/embed-teams-app/app-details.png "Detalles") de la aplicación


3. Registre el **identificador** de la aplicación para su uso posterior.

   > [!div class="mx-imgBorder"] 
   > ![Detalles] de la aplicación (./media/embed-teams-app/app-details2.png "Detalles") de la aplicación

## <a name="install-app-studio"></a>Instalación de App Studio

Puede omitir estos pasos si App Studio ya está instalado. 

1. En equipos, seleccione **aplicaciones** en la parte inferior izquierda del menú equipos (icono![]aplicaciones icono(./media/embed-teams-app/apps-icon.png "aplicaciones")).

2. Busque "App Studio" en el cuadro de búsqueda y, a continuación, selecciónelo.

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. Seleccione **instalar**. 

   > [!div class="mx-imgBorder"] 
   > ![Instalación de App Studio](./media/embed-teams-app/install-app-studio.png "Instalación de App Studio")

4. Seleccione **abrir** para la característica de la aplicación.

   > [!div class="mx-imgBorder"] 
   > ![Abra App Studio](./media/embed-teams-app/open-app-studio.png "Abra App Studio")

## <a name="create-a-teams-app-for-your-powerapp"></a>Creación de una aplicación de Teams para PowerApp

1. En Teams, abra App Studio.

   > [!div class="mx-imgBorder"] 
   > ![Abra App Studio](./media/embed-teams-app/open-app-studio2.png "Abra App Studio")

2. Seleccione la pestaña **Editor de manifiesto** y, después, seleccione **crear una nueva aplicación** en la Página principal.

   > [!div class="mx-imgBorder"] 
   > ![Crear nueva aplicación](./media/embed-teams-app/create-new-app.png "Crear nueva aplicación")

3. Rellene la información sobre la aplicación en la página de detalles de la **aplicación** .  En el caso del identificador GUID de la aplicación, debe usar el GUID del identificador de la aplicación de PowerApp que grabó anteriormente.  Esto evitará la duplicación de aplicaciones de equipos para una PowerApp determinada.
 
   > [!div class="mx-imgBorder"] 
   > ![Información de] rellenado (./media/embed-teams-app/fill-in-info-about-app.png "Información de") rellenado

   |Fields  |DESCRIPCIÓN  |
   |---------|---------|
   |**Nombres de aplicación** |    |
   |Nombre corto     | Necesario. Nombre para mostrar corto de la aplicación. límite de 30 caracteres.        |
   |Nombre largo     | El nombre completo de la aplicación, que se usa si el nombre completo de la aplicación supera los 30 caracteres.       | 
   |**Identificado**     |         |
   |IDENTIFICADOR de la aplicación     | Necesario. Identificador único generado por Microsoft para esta aplicación.        |
   |Nombre del paquete     | Necesario. Un identificador único para esta aplicación. Se recomienda usar la notación de dominio inverso; por ejemplo, com. example. <AppName>.       |
   |`Version`     | Necesario. La versión de la aplicación específica. Si actualiza algo en el manifiesto, la versión también debe incrementarse.     |
   |**Revise**    |     |
   | Descripción breve    | Necesario. Una breve descripción de la experiencia de la aplicación, que se usa cuando el espacio es limitado. límite de 80 caracteres.   |
   | Descripción larga    | Necesario. La descripción completa de la aplicación.     |
   | **Información para desarrolladores**    |     |
   | NOMBRE    | Necesario. El nombre para mostrar de la compañía o el desarrollador.     |
   | Website    | Necesario. La dirección URL de https://al sitio web de la aplicación a través de powerapps.com. Cuando alguien instala la aplicación, aparecerá la página "acerca de la aplicación". Debe vincularse a la versión Web de la aplicación en powerapps.com.   |
   | **Direcciones URL de la aplicación**    | Estos vínculos se mostrarán en la página **About (acerca** de) junto con la dirección URL del sitio Web.     |
   | Declaración de privacidad    | Necesario. La dirección URL de https://a la Directiva de privacidad del desarrollador. [Ejemplo](https://go.microsoft.com/fwlink/p/?LinkID=698505).   |
   | Términos de uso    | Necesario. La dirección URL de https://a los términos de uso del desarrollador.  [Ejemplo](https://go.microsoft.com/fwlink/p/?LinkID=698507).  |
   | **Marca**    |     |
   | Color completo    | Ruta de acceso relativa de un archivo a un icono de 192x192 PNG de color completo.    |
   | Contorno transparente    |Ruta de acceso relativa de un archivo a un icono de esquema PNG de 32 transparente.     |
   | Color de énfasis    | Color que se va a usar junto con y como fondo para los iconos del esquema.     |

Para obtener más información, vea [Editor](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor) de manifiestos y [esquema de manifiesto](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema).

4. Desplácese hacia abajo hasta la sección de personalización de marca y agregue los logotipos y el color de énfasis que quiera para la aplicación.  Estos son los logotipos que aparecerán para la aplicación en Teams. 

   > [!div class="mx-imgBorder"] 
   > ![Personalización de marca y pestañas](./media/embed-teams-app/branding-tabs.png "Personalización de marca y pestañas")

5. En **capacidades**, seleccione **pestañas**.

6. En la **pestaña equipo** , seleccione **Agregar**.

   > [!div class="mx-imgBorder"] 
   > ![Agregar pestaña de equipo](./media/embed-teams-app/team-tab-add.png "Agregar pestaña de equipo")

7. Agregue la dirección URL de configuración de la aplicación en el campo de entrada "URL de configuración" con el siguiente formato:`https://web.powerapps.com/webplayer/teamsapptabsettings?appid=<PowerApp ID>`

   Reemplace `<PowerApp ID>` por el GUID de ID. de aplicación que registró anteriormente.

   Seleccione el [ámbito](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope) en el que aparecerá la aplicación. Asegúrese de que la opción **Actualizar configuración** esté activada y, a continuación, seleccione **Guardar**.

   > [!div class="mx-imgBorder"] 
   > ![URL de configuración](./media/embed-teams-app/configuration-url.png "URL de configuración")

8. En **Finalizar**, seleccione **dominios válidos**. Agregue **apps.powerapps.com** y **apps.preview.powerapps.com** como dominios válidos para la aplicación Teams.

   > [!div class="mx-imgBorder"] 
   > ![Agregar dominios válidos](./media/embed-teams-app/add-valid-domains.png "Agregar dominios válidos")

9. En **Finalizar**, seleccione **probar y distribuir**. En **instalar**, seleccione **instalar**.

   > [!div class="mx-imgBorder"] 
   > ![Seleccionar instalar](./media/embed-teams-app/test-distribute-app.png "Seleccionar instalar")

10. Seleccione el equipo en el que desea que se instale la aplicación y, a continuación, seleccione **instalar**.

    > [!div class="mx-imgBorder"] 
    > ![Agregar a instalación de equipo](./media/embed-teams-app/new-app-add-to-team.png "Agregar a instalación de equipo")
11. Si desea agregar una instancia de esa aplicación a un canal de inmediato, seleccione el canal en el que desea usar la aplicación y seleccione **configurar**.

    > [!div class="mx-imgBorder"] 
    > ![Seleccionar configuración](./media/embed-teams-app/app-now-available.png "Seleccionar configuración")

12. Seleccione **Guardar**.

## <a name="add-the-app-as-a-tab"></a>Agregar la aplicación como una pestaña

Para agregar la aplicación como una pestaña a cualquier canal o conversación, seleccione **+** y, en pestañas del **equipo** , seleccione la aplicación. 

> [!div class="mx-imgBorder"] 
> ![Agregar aplicación como pestaña](./media/embed-teams-app/add-app-as-tab.png "Agregar aplicación como pestaña")

La aplicación aparece ahora como una pestaña.

> [!div class="mx-imgBorder"] 
> ![Aplicación como pestaña](./media/embed-teams-app/app-as-tab.png "Aplicación como pestaña")

### <a name="see-also"></a>Vea también
[Bienvenido a Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[Para administradores: Insertar una aplicación en Microsoft Teams](https://docs.microsoft.com/power-platform/admin/share-app-teams)
