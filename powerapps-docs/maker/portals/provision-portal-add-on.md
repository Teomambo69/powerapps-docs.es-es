---
title: Aprovisione un portal con el complemento de portal más antiguo | MicrosoftDocs
description: Instrucciones para aprovisionar un portal con el complemento de portal más antiguo.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 8ba1ab497dda3d6e7296c99d868cd6b6726619ac
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981425"
---
# <a name="provision-a-portal-using-the-older-portal-add-on"></a>Aprovisione un portal con el complemento de portal más antiguo

Si ha adquirido un complemento de portal más antiguo, y desea para aprovisionar un portal con el complemento, debe ir a la página **Centro de administración de Dynamics 365** y aprovisione el portal.

> [!NOTE]
> Para aprovisionar un portal, se le debe asignar al rol de administrador del sistema del entorno de Common Data Service seleccionada para el portal. También debe disponer de los [permisos necesarios](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions) para crear y registrar una aplicación en Azure AD. Si no tiene los permisos necesarios, póngase en contacto con el Administrador global para actualizar sus permisos o pida al Administrador global que aprovisione el portal.

Para aprovisionar un portal:

1. Inicie sesión en el [Centro de administración de Microsoft 365](https://admin.microsoft.com).
 
2. En la columna de navegación de la izquierda, seleccione **Mostrar todo**.

3. Si está trabajando con el nuevo centro de administración, seleccione **Todos los centros de administración**. En la lista de todos los centros de administración, seleccione **Dynamics 365**.

    > [!div class="mx-imgBorder"]
    > ![Abrir el Centro de administración de Dynamics 365 desde el nuevo centro de administración](media/from-new-admin-center.png "Abrir el Centro de administración de Dynamics 365 desde el nuevo centro de administración") 

4. Si está trabajando con el antiguo centro de administración, expanda **Centros de administración** en la columna de navegación izquierda y luego seleccione **Dynamics 365**.

    > [!div class="mx-imgBorder"]
    > ![Abrir el Centro de administración de Dynamics 365 desde el antiguo centro de administración](media/from-old-admin-center.png "Abrir el Centro de administración de Dynamics 365 desde el antiguo centro de administración") 

5. En la página **Centro de administración de Dynamics 365**, seleccione la pestaña **Aplicaciones**.

6. Seleccione la fila de la aplicación con el título **Complemento de portal** y, a continuación, haga clic en **Administrar**.

7. En la sección **Configuración general**, escriba un **Nombre** del portal. El **Nombre** ayudará a identificar el portal y se puede cambiar más adelante.

8. El campo **Tipo** representa el tipo de suscripción de portal (prueba o producción). Es un campo del sistema, por lo que no puede modificarlo el usuario. El valor cambia según se trate de una suscripción de prueba o de pago.

9. Opcionalmente, en la lista **Estado de desarrollo del portal**, seleccione uno de los siguientes estados de desarrollo para el portal:

    - Prototipo
    - Desarrollo
    - Probar
    - UAT
    - Live

    > [!NOTE]
    > - Para los portales aprovisionados ya existentes, esta lista desplegable está disponible en la pestaña **Detalles de portal** y ningún estado está seleccionado de forma predeterminada.
    > - Esta lista desplegable solo está disponible para los portales de tipo producción.
    > - Este campo se usa en Microsoft para comprender el patrón de este portal y no afecta a ninguna funcionalidad. Si usa nombres diferentes para el ciclo de vida de desarrollo, seleccione el que está más cerca del propósito. Esto se puede cambiar más tarde una vez el portal esté aprovisionado.

10. En el campo **Dirección URL de portal**, escriba el nombre del subdominio que desee para el portal. Puede usar únicamente caracteres alfanuméricos o guiones (-); otros caracteres no se permiten.

    > [!NOTE]
    > - Para cambiar la dirección URL de un portal después de su aprovisionamiento, vea [Cambiar la dirección URL base de un portal](admin/change-base-url.md).
    > - Para vincular su portal a un dominio personalizado, vea [Vincular el portal a un dominio personalizado](admin/add-custom-domain.md).

11. En la lista desplegable **Instancia Dynamics 365** seleccione la instancia con la que quiera vincular el portal. Esto requiere un rol de administrador del sistema o personalizador del sistema en la instancia que elija para seleccionarlo.

12. Elija el idioma predeterminado de su portal en la lista desplegable **Seleccionar idioma del portal**. Los idiomas disponibles dependerán de los que estén instalados en la instancia. 
    
    > [!NOTE]
    > Los datos de ejemplo se proporcionan únicamente en un idioma, por lo que la selección de un idioma predeterminado también decidirá cómo se traducen los datos de ejemplo. El árabe y el hebreo no se admiten y no aparecerán en la lista.

13. En la lista desplegable **Seleccionar administrador del portal**, seleccione el usuario que configurará, personalizará, y mantendrá el portal. Todos los usuarios que tienen el rol Administrador del sistema en la organización aparecerán como opciones. 

14. En la sección **Público del portal**, seleccione el tipo de público que visitará el portal nuevo. Esto determina qué opciones de portales se le ofrecerán. Puede optar por:

    -   Asociado    
        -   Portal de autoservicio de clientes
        -   Portal personalizado
        -   Portal de asociados
        -   Project Service de asociados (opcional, requiere soluciones instaladas)
        -   Field Service de asociado (opcional, requiere soluciones instaladas)
        -   Portal de la comunidad

    -   Cliente
        -   Portal de autoservicio de clientes
        -   Portal personalizado
        -   Portal de la comunidad

    -   Empleado
        -   Portal de autoservicio de empleados

15. En la sección **Seleccione el portal para implementar**, elija qué tipo de portal desea crear. Las opciones que ve se basan en el público que seleccionó.

    > [!div class="mx-imgBorder"]
    > ![Configurar opciones para el portal](media/configure-settings-portal.png "Configurar opciones para el portal")  

16. Seleccione **Enviar** y acepte las Condiciones de servicio.
    > [!div class="mx-imgBorder"]
    > ![Condiciones de servicio](media/terms-of-service.png "Condiciones de servicio")  

Después de aceptar las condiciones de servicio, el portal iniciará el aprovisionamiento. El aprovisionando tarda normalmente 30 minutos, pero puede tardar unas horas en función de la carga del sistema. El *Nombre* del portal en la pestaña Aplicación cambiará a *Nombre*-Configuración mientras se está aprovisionando. Navegue de vuelta a la página de administración del portal para comprobar si el aprovisionamiento se ha realizado correctamente.

Después de que se aprovisione el portal, se muestra la página **Detalles de portal** con los detalles necesarios.

> [!div class="mx-imgBorder"]
> ![Detalles del portal](media/portal-details-prov.png "Detalles del portal") 


> [!Note]
> Cuando un usuario del portal inicia sesión en el portal por primera vez mediante las credenciales de Azure AD, una página de consentimiento se muestra a todos los usuarios con independencia del tipo de usuario o de portal.

La tabla siguiente resume las características asociadas a cada opción de portal:

| Característica                                | Portal de autoservicio de clientes | Portal de asociados | Portal de autoservicio de empleados | Portal de la comunidad | Portal personalizado |
|----------------------------------------|------------------------------|----------------|------------------------------|------------------|---------------|
| Listo para el mundo                            | •                            | •              | •                            | •                | •             |
| Compatibilidad multilingüe                 | •                            | •              | •                            | •                | •             |
| Administración del portal                  | •                            | •              | •                            | •                | •             |
| Personalización y extensibilidad        | •                            | •              | •                            | •                | •             |
| Temas                                | •                            | •              | •                            | •                | •             |
| Administración de contenido                     | •                            |                | •                            | •                |               |
| Administración del conocimiento                   | •                            | •              | •                            | •                |               |
| Soporte técnico/administración de casos                | •                            |                | •                            | •                |               |
| Foros                                 | •                            |                | •                            | •                |               |
| Búsqueda por facetas                         | •                            |                | •                            |                  |               |
| Administración de perfiles                     | •                            |                | •                            |                  |               |
| Suscribirse a este hilo del foro              | •                            |                | •                            |                  |               |
| Comentarios                               | •                            |                | •                            | •                |               |
| Autenticación AD de [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)]                |                              |                | •                            |                  |               |
| Ideas                                  |                              |                |                              | •                |               |
| Blogs                                  |                              |                |                              | •                |               |
| Integración de Project Service Automation |                              | •              |                              |                  |               |
| Integración de Field Service              |                              | •              |                              |                  |               |
| Incorporación de asociados                     |                              | •              |                              |                  |               |
| Base de portal de                             |  •                           | •              |  •                           | •                | •             |
| Flujos de trabajo de portal                       |  •                           | •              |  •                           | •                | •             |
| Notificaciones web                      |  •                           | •              |  •                           | •                | •             |
| Identidad de [!INCLUDE[cc-microsoft](../../includes/cc-microsoft.md)]                     |     •                         |  •              |     •                         |   •               | •             |
| Flujos de trabajo de identidad                     | •                            |  •             |     •                         |   •               | •             |
| Formularios web                              |  •                            | •               |    •                          | •                 | •             |
| Comentarios                               |   •                           |  •              |  •                            | •                 | •             |
||

## <a name="troubleshoot-provisioning"></a>Solución de problemas de aprovisionamiento

A veces se crea un error en el proceso de instalación del paquete o de creación de la dirección URL. En estos casos, se pueden reiniciar los procesos.

Si *Nombre*-Configuración cambia a *Nombre*-Error de aprovisionamiento, deberá reiniciar el proceso de aprovisionamiento.

1. Vaya a la página **Aplicaciones** y seleccione el portal.
2. Seleccione el botón de corregir etiquetado **Administrar**.
3. Seleccione una de las siguientes opciones:

   - **Reiniciar aprovisionamiento**: Reinicia el proceso de instalación con la configuración que se definió anteriormente.

   - **Cambiar configuración y reiniciar aprovisionamiento**: Le permite cambiar algunos de los valores antes de reiniciar el proceso de aprovisionamiento.

Si la instalación de paquetes ha fallado, la página de administrador del portal se abrirá sin ningún problema, pero al navegar a la dirección URL del portal real se mostrará un mensaje Obteniendo configuración. Para confirmar esto:

1. Vaya a la página Administración de soluciones de la página **Centro de administración de Dynamics 365** y compruebe que el estado del paquete es **Error al instalar**. 

2. Si el estado del paquete es **Error al instalar**, vuelva a intentar la instalación desde la página de solución. Además, asegúrese de comprobar que un administrador del sistema está instalando la solución con el idioma predeterminado en Common Data Service establecido como el idioma en el que se debe instalar el portal.

> [!NOTE]
> Algunas soluciones tienen requisitos previos para la instalación, por lo que una instalación generará error si los requisitos previos no se cumplen. Por ejemplo, para instalar Field Service de asociado para un portal de un asociado, las soluciones Portal de asociados y Field Service deben haber sido instaladas. Si intenta instalar Field Service de asociados primero, la instalación producirá un error y mostrará un mensaje de error.
