---
title: Aprovisionamiento de un portal mediante el complemento de portal anterior | MicrosoftDocs
description: Instrucciones para aprovisionar un portal mediante el complemento de portal anterior.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6572a92a46fa308eab6cb46b813a572605327197
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73550988"
---
# <a name="provision-a-portal-using-the-older-portal-add-on"></a>Aprovisionamiento de un portal mediante el complemento de portal anterior

Si ha adquirido un complemento de portal anterior y desea aprovisionar un portal mediante el complemento, debe ir a la página del centro de administración de **Dynamics 365** y aprovisionar el portal.

> [!NOTE]
> Para aprovisionar un portal, debe tener asignado el rol de administrador del sistema o del Personalizador del sistema del Common Data Service entorno seleccionado para el portal. También debe tener los [permisos necesarios](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions) para crear y registrar una aplicación en Azure ad. Si no tiene los permisos necesarios, póngase en contacto con el administrador global para actualizar sus permisos o pida al administrador global que aprovisione el portal.

Para aprovisionar un portal:

1.  Vaya a la página del **centro de administración de Dynamics 365** y, a continuación, seleccione la pestaña **aplicaciones** .

2.  Seleccione la fila de la aplicación titulada **complemento del portal**y, a continuación, seleccione **administrar.**

3.  En la sección **Configuración general** , escriba un **nombre** para el portal. El **nombre** le ayudará a identificar el portal y se puede cambiar más adelante.

4.  El campo **Type** representa el tipo de suscripción de portal (prueba o producción). Se trata de un campo del sistema, por lo que el usuario no puede cambiarlo. El valor cambia en función de si se trata de una suscripción de prueba o de pago.

5. Opcionalmente, en la lista desplegable **Estado de desarrollo del portal** , seleccione uno de los siguientes Estados de desarrollo para el portal:

    - Prototipo
    - DevelopMentor
    - Muestre
    - ACEPTACIÓN
    - Vivo

    > [!NOTE]
    > - En el caso de los portales aprovisionados existentes, esta lista desplegable está disponible en la pestaña **detalles del portal** y no hay ningún estado seleccionado de forma predeterminada.
    > - Esta lista desplegable solo está disponible para los portales de tipo producción.
    > - Microsoft usa este campo para comprender el patrón de uso de este portal y no afecta a ninguna funcionalidad. Si usa nombres diferentes para el ciclo de vida de desarrollo, seleccione el que más se aproxime a su propósito. Se puede cambiar en un momento posterior una vez aprovisionado el portal.

5.  En el campo **dirección URL del portal** , escriba el nombre de subdominio que desee para el portal. Solo puede utilizar caracteres alfanuméricos o guiones (-); no se permiten otros caracteres.

    > [!NOTE]
    > - Para cambiar la dirección URL de un portal una vez aprovisionado, consulte [cambio de la dirección URL base de un portal](admin/change-base-url.md).
    > - Para vincular el portal a un dominio personalizado, consulte [vinculación del portal a un dominio personalizado](admin/add-custom-domain.md).

6.  En la lista desplegable de **instancias de Dynamics 365** , seleccione la instancia a la que desea vincular el portal. Esto requiere el rol de administrador del sistema o del Personalizador del sistema en la instancia que elija para seleccionarlo.

7.  En la lista desplegable **Seleccionar idioma del portal** , seleccione el idioma predeterminado para el portal. Los idiomas disponibles dependerán de los idiomas que estén instalados en la instancia de. 

    > [!NOTE]
    > Los datos de ejemplo solo se proporcionan en un idioma, por lo que al elegir un idioma predeterminado también se decide cómo se traducen los datos de ejemplo. No se admiten los formatos árabe y hebreo, y no aparecerán en la lista.

8. En la lista desplegable **Seleccionar administrador del portal** , seleccione el usuario que va a configurar, personalizar y mantener el portal. Todos los usuarios que tengan el rol de administrador del sistema en la organización aparecerán como opciones. 

9. En la sección **audiencia del portal** , elija el tipo de audiencia que visitará el nuevo portal. Esto determinará las opciones de portales que se proporcionarán. Puede elegir:

    -   Partner    
        -   Portal de autoservicio del cliente
        -   Portal personalizado
        -   Portal de Partners
        -   Servicio de proyecto de asociados (opcional, requiere soluciones instaladas)
        -   Servicio de campo de asociado (opcional, requiere soluciones instaladas)
        -   Portal de la comunidad

    -   Customer
        -   Portal de autoservicio del cliente
        -   Portal personalizado
        -   Portal de la comunidad

    -   Employee
        -   Portal de autoservicio para empleados

10. En la sección **seleccionar el portal que se va a implementar** , elija el tipo de portal que desea crear. Las opciones que ve se basan en la audiencia que ha seleccionado.

    > [!div class="mx-imgBorder"]
    > ![Configurar las opciones del portal](media/configure-settings-portal.png "Configurar las opciones del portal")  

11. Seleccione **submit (enviar**) y acepte los términos de servicio.
    > [!div class="mx-imgBorder"]
    > ![Condiciones del servicio](media/terms-of-service.png "Condiciones del servicio")  

Después de aceptar los términos de servicio, el portal comenzará el aprovisionamiento. El aprovisionamiento normalmente tarda 30 minutos, pero puede tardar unas horas en función de la carga del sistema. El *nombre* del portal en la pestaña aplicación cambiará a *nombre*-configurando mientras se aprovisiona. Vuelva a la página de administración del portal para comprobar si el aprovisionamiento se ha realizado correctamente.

Una vez aprovisionado el portal, se muestra la página **detalles del portal** con los detalles necesarios.

> [!div class="mx-imgBorder"]
> ![Detalles del portal](media/portal-details-prov.png "Detalles del portal") 


> [!Note]
> Cuando un usuario del portal inicia sesión en el portal por primera vez mediante el uso de una credencial de Azure AD, se muestra una página de consentimiento a todos los usuarios, independientemente del tipo de usuario o de portal.

En la tabla siguiente se resumen las características asociadas a cada opción del portal:

| Ofrecen                                | Portal de autoservicio del cliente | Portal de Partners | Portal de autoservicio de empleado | Portal de la comunidad | Portal personalizado |
|----------------------------------------|------------------------------|----------------|------------------------------|------------------|---------------|
| Preparado para todo el mundo                            | •                            | •              | •                            | •                | •             |
| Compatibilidad con varios idiomas                 | •                            | •              | •                            | •                | •             |
| Administración del portal                  | •                            | •              | •                            | •                | •             |
| Personalización y extensibilidad        | •                            | •              | •                            | •                | •             |
| Temas                                | •                            | •              | •                            | •                | •             |
| Administración de contenido                     | •                            |                | •                            | •                |               |
| Administración del conocimiento                   | •                            | •              | •                            | •                |               |
| Compatibilidad y administración de casos                | •                            |                | •                            | •                |               |
| Foros                                 | •                            |                | •                            | •                |               |
| Búsqueda por facetas                         | •                            |                | •                            |                  |               |
| Administración de perfiles                     | •                            |                | •                            |                  |               |
| Subproceso de suscripción a foros              | •                            |                | •                            |                  |               |
| Opiniones                               | •                            |                | •                            | •                |               |
| Autenticación de [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD                |                              |                | •                            |                  |               |
| Pone                                  |                              |                |                              | •                |               |
| Blogs                                  |                              |                |                              | •                |               |
| Integración de automatización del servicio de proyecto |                              | •              |                              |                  |               |
| Integración del servicio de campo              |                              | •              |                              |                  |               |
| Incorporación de asociados                     |                              | •              |                              |                  |               |
| Base del portal                            |  •                           | •              |  •                           | •                | •             |
| Flujos de trabajo del portal                       |  •                           | •              |  •                           | •                | •             |
| Notificaciones Web                      |  •                           | •              |  •                           | •                | •             |
| Identidad de [!INCLUDE[cc-microsoft](../../includes/cc-microsoft.md)]                     |     •                         |  •              |     •                         |   •               | •             |
| Flujos de trabajo de identidad                     | •                            |  •             |     •                         |   •               | •             |
| Formularios Web Forms                              |  •                            | •               |    •                          | •                 | •             |
| Los                               |   •                           |  •              |  •                            | •                 | •             |
||

## <a name="troubleshoot-provisioning"></a>Solución de problemas de aprovisionamiento

En ocasiones, el proceso de instalación de paquetes o el proceso de creación de direcciones URL pueden tener errores. En estos casos, se pueden reiniciar los procesos.

Si *Name*-configure los cambios en el aprovisionamiento de *nombre*, deberá reiniciar el proceso de aprovisionamiento.

1. Vaya a la página **aplicaciones** y seleccione el portal.
2. Seleccione el botón de lápiz azul con la etiqueta **administrar**.
3. Elija una de las siguientes opciones:

   - **Reiniciar el aprovisionamiento**: reinicia el proceso de instalación con la configuración que se definió previamente.

   - **Cambiar valores y reiniciar el aprovisionamiento**: permite cambiar algunos de los valores antes de reiniciar el proceso de aprovisionamiento.

Si se ha producido un error en la instalación del paquete, se abrirá la página Administrador del portal sin ningún problema, pero al ir a la dirección URL del portal real se mostrará un mensaje de configuración. Para confirmarlo:

1. Vaya a la página Administración de soluciones de la página del **centro de administración de Dynamics 365** y compruebe que el estado del paquete es **error de instalación**. 

2. Si el estado del paquete es **error de instalación**, intente volver a intentar la instalación desde la página de la solución. Además, asegúrese de comprobar que un administrador del sistema está instalando la solución con el idioma predeterminado en Common Data Service establecido en el idioma en el que se debe instalar el portal.

> [!NOTE]
> Algunas soluciones tienen requisitos previos para su instalación, por lo que se producirá un error en la instalación si no se cumplen los requisitos previos. Por ejemplo, para instalar el servicio de campo de asociado para un portal de Partners, las soluciones del portal de Partners y del servicio de campo ya deben estar instaladas. Si intenta instalar el servicio de campo de asociado en primer lugar, se producirá un error en la instalación y se le mostrará un mensaje de error.
