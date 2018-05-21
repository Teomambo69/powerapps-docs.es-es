---
title: Administración de licencias de la organización | Microsoft Docs
description: Preguntas y respuestas frecuentes acerca de las licencias, la administración y el registro de usuarios a PowerApps en su inquilino de Office 365
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: jamesol
ms.openlocfilehash: 8a734ef57a3820e38d52ad2bd87a2ab8979c0348
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2018
---
# <a name="manage-powerapps-licenses-in-your-organization"></a>Administración de licencias de PowerApps de la organización
En este artículo se describe la forma en que los usuarios de la organización pueden obtener acceso para usar PowerApps y cómo controlar el servicio de PowerApps.

## <a name="sign-up-for-powerapps"></a>Suscribirse a PowerApps
### <a name="what-is-powerapps"></a>¿Qué es PowerApps?
Microsoft PowerApps permite a los usuarios crear aplicaciones para dispositivos móviles con Windows, iOS y Android. Mediante estas aplicaciones se pueden crear conexiones a servicios de SaaS comunes, como Twitter, Office 365, Dropbox y Excel.

### <a name="how-do-users-sign-up-for-powerapps"></a>¿Cómo se suscriben los usuarios a PowerApps?
La única opción de suscripción para los usuarios individuales de su organización es la versión de evaluación del plan 2 de PowerApps, a la que pueden suscribirse a través del sitio web de PowerApps:

##### <a name="option-1"></a>Opción 1
Para suscribirse, los usuarios pueden ir a [powerapps.microsoft.com](https://powerapps.microsoft.com); para ello, deben seleccionar la opción **Suscribirse gratis** y, después, completar el proceso de suscripción a PowerApps mediante [portal.office.com](https://portal.office.com/Start?sku=powerapps).

##### <a name="option-2"></a>Opción 2
Para suscribirse, los usuarios pueden ir a [powerapps.microsoft.com](https://powerapps.microsoft.com), seleccionar **Iniciar sesión**, iniciar sesión con sus cuentas profesionales o educativas, y suscríbase a la versión de evaluación del plan 2 de PowerApps aceptando los términos de uso de PowerApps.    

Si un usuario de su organización se suscribe a PowerApps, se le asigna automáticamente una licencia de PowerApps.

> [!NOTE]
> Los usuarios que se suscriben a una evaluación gratuita desde dentro de PowerApps no aparecen en el Portal de administración de Office 365 como usuarios de la versión de evaluación gratuita del Plan 2 de PowerApps (a menos que tengan otra licencia de Office 365, Dynamics 365 o PowerApps).

Para más información, consulte [Suscripción de autoservicio para PowerApps](../maker/signup-for-powerapps.md).

### <a name="how-can-users-in-my-organization-gain-access-to-powerapps"></a>¿Cómo pueden obtener acceso a PowerApps los usuarios de mi organización?
Los usuarios de su organización pueden obtener acceso a PowerApps de tres maneras diferentes:

* Pueden suscribirse individualmente a una versión de evaluación del plan 2 de PowerApps, como se describe en la sección [¿Cómo se suscriben los usuarios a PowerApps?](#how-do-users-sign-up-for-powerapps)
* Puede asignarles una licencia de PowerApps en el portal de administración de Office 365.
* Se ha asignado al usuario planes de Office 365 y Dynamics 365 que incluyen el acceso al servicio PowerApps. Consulte la [página de precios de PowerApps](https://powerapps.microsoft.com/pricing) para ver la lista de planes de Office 365 y Dynamics 365 que incluyen las funcionalidades de PowerApps.

### <a name="can-i-block-users-in-my-organization-from-signing-up-for-powerapps"></a>¿Puedo bloquear en mi organización que los usuarios suscriban a PowerApps?
Cualquier usuario puede probar las características del Plan 2 de Microsoft PowerApps durante 30 días sin costo alguno, como se describe en la sección [¿Cómo se suscriben los usuarios a PowerApps?](#how-do-users-sign-up-for-powerapps).  Esta opción está disponible para cualquier usuario de un inquilino y no puede deshabilitarla un administrador.  Después de que la versión de evaluación del usuario expire, este perderá el acceso a las funcionalidades del plan 2 de PowerApps.  

Si un usuario se suscribe a una versión de evaluación de 30 días del Plan 2 de Microsoft PowerApps y decide no admitirlo en la organización, no supondrá ningún costo para la empresa. Si una persona se suscribe a Microsoft PowerApps, que es una relación directa entre dicha persona y Microsoft, al igual que otros muchos servicios en la nube públicos de Microsoft, como Bing, Wunderlist, OneDrive o Outlook.com y no implica que la organización proporcione el servicio.

Por último, si su empresa desea restringir el uso de datos exclusivos de la organización en Microsoft PowerApps, se puede hacer mediante las directivas de prevención de pérdida de datos (DLP). Para más información, consulte [Data loss prevention (DLP) policies](prevent-data-loss.md) [Directivas de prevención de pérdida de datos (DLP)].

## <a name="administration-of-powerapps"></a>Administración de PowerApps
### <a name="why-has-the-powerapps-icon-appeared-in-the-office-365-app-launcher"></a>¿Por qué ha aparecido el icono de PowerApps en el iniciador de aplicaciones de Office 365?
Microsoft PowerApps es una parte fundamental del conjunto de aplicaciones de Office 365 y está habilitado como un servicio que forma parte de la SKU de Office 365. Puesto que ahora los usuarios de todo el mundo pueden usar Microsoft PowerApps, este se muestra en la sección "Todas las aplicaciones" de la pantalla del iniciador de aplicaciones. Para saber qué SKU de Office 365 incluyen PowerApps, consulte [Licensing overview](pricing-billing-skus.md) (Introducción a las licencias).

Si quiere que el icono de PowerApps no se muestre en la sección "Todas las aplicaciones" de forma predeterminada, consulte la sección siguiente.

### <a name="how-do-i-remove-powerapps-from-existing-users"></a>¿Cómo se quita PowerApps de los usuarios existentes?
Si se ha asignado una licencia del plan 1 de PowerApps o del plan 2 de PowerApps a un usuario, puede realizar los pasos siguientes para quitar la licencia de PowerApps a dicho usuario:

1. Vaya al [Portal de administración de Office 365](https://portal.microsoftonline.com/).

2. En la barra de navegación izquierda, seleccione **Usuarios** y, después, **Usuarios activos**.

3. Busque el usuario cuya licencia desea quitar y seleccione su nombre.

4. En el panel de detalles del usuario, en la sección de **Product licenses** (Licencias de productos), seleccione **Edit** (Editar).

5. Busque la licencia **Microsoft PowerApps Plan 1** o **Microsoft PowerApps Plan 2**, establezca el control de alternancia en **Desactivado** y seleccione **Guardar**.

    ![](./media/signup-question-and-answer/remove-license.png)

Si un usuario tiene acceso a PowerApps a través de su licencia de planes de Office 365 y Dynamics 365, puede deshabilitar su acceso al servicio PowerApps realizando los pasos siguientes:

1. Vaya al [Portal de administración de Office 365](https://portal.microsoftonline.com/).

2. En la barra de navegación izquierda, seleccione **Usuarios** y, después, **Usuarios activos**.

3. Busque el usuario al que desea quitar el acceso y seleccione su nombre.

4. En el panel de detalles del usuario, en la sección de **Product licenses** (Licencias de productos), seleccione **Edit** (Editar).

5. Expanda la licencia de Office 365 o Dynamics 365 del usuario, deshabilite el acceso para el servicio **PowerApps for Office 365** (PowerApps para Office 365) o **PowerApps for Dynamics 365** (PowerApps para Dynamics 365) y seleccione **Guardar**.

    ![](./media/signup-question-and-answer/remove-service-plan.png)

También es posible la eliminación masiva de licencias mediante PowerShell. Para ver un ejemplo detallado, Consulte [Eliminar licencias de cuentas de usuario con PowerShell de Office 365](https://technet.microsoft.com/library/dn771774.aspx).   Por último, puede ver más instrucciones acerca de la eliminación masiva de los servicios de una licencia en [Deshabilitar el acceso a servicios con PowerShell de Office 365](https://technet.microsoft.com/library/dn771769.aspx).

La eliminación del servicio o de la licencia de PowerApps para un usuario de una organización también se eliminarán los iconos de PowerApps y Dynamics 365 de las siguientes ubicaciones de dicho usuario:

* [Office.com](https://office.com)

    ![](./media/signup-question-and-answer/office-home.png)
* Office 365 AppLauncher “waffle”

    ![](./media/signup-question-and-answer/office-waffle.png)

### <a name="how-can-i-restrict-my-users-ability-to-access-my-organizations-business-data-using-powerapps"></a>¿Cómo puedo restringir la capacidad que tienen los usuarios para acceder a los datos empresariales de una organización mediante PowerApps?
PowerApps permite crear zonas de datos para datos empresariales y no empresariales, como se muestra a continuación.  Una vez que se implementan estas directivas de prevención de pérdida de datos, se impide que los usuarios diseñen o ejecuten instancias de PowerApps que combinen datos empresariales y no empresariales. Para más información, consulte [Data loss prevention (DLP) policies](prevent-data-loss.md) [Directivas de prevención de pérdida de datos (DLP)].

![](./media/signup-question-and-answer/data-loss-prevention-policy.png)

### <a name="why-did-10000-licenses-for-microsoft-powerapps-show-up-in-my-office-365-tenant"></a>¿Por qué han aparecido 10 000 licencias de Microsoft PowerApps en mi inquilino de Office 365?
En las organizaciones aptas, los usuarios de la organización pueden probar el Plan 2 de Microsoft PowerApps durante 30 días y estas licencias de evaluación representan la capacidad disponible para nuevos usuarios de PowerApps en el inquilino. Estas licencias no tienen costo alguno. En concreto, hay dos posibles motivos por los que puede que aparezca una capacidad de 10 000 licencias (evaluación) para PowerApps en el portal de administración de Office 365:

* Si al menos un usuario del inquilino ha participado en la versión preliminar pública de PowerApps que estuvo activa de abril a octubre de 2016, verá 10 000 licencias con la etiqueta "Microsoft PowerApps and Logic flows" (Flujos de Microsoft PowerApps y Logic)

    ![](./media/signup-question-and-answer/licenses_2.png)
* Si al menos un usuario del inquilino se ha suscrito a la versión de evaluación del plan 2 de PowerApps a través de la **opción 1** de la suscripción de evaluación que se describe en la sección [¿Cómo se suscriben los usuarios a PowerApps?](#how-do-users-sign-up-for-powerapps), verá 10 000 licencias con la etiqueta "Microsoft PowerApps & Flow" (Flujos de Microsoft PowerApps y Logic)

    ![](./media/signup-question-and-answer/licenses_1.png)

Se pueden asignar licencias adicionales a los usuarios a través del Portal de administración de Office 365, pero tenga en cuenta que se trata de licencias de evaluación del Plan 2 de Microsoft PowerApps y que expirarán 30 días después de la asignación.

### <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>¿Es gratuito? ¿Se me cobrará por estas licencias?
Estas son licencias de evaluación gratuitas para que los usuarios prueben el Plan 2 de Microsoft PowerApps durante 30 días.

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>¿Cómo cambiará esto la forma de administrar las identidades los usuarios de una organización?
Si una organización ya tiene un entorno de Office 365 existente y todos los usuarios tienen cuentas de Office 365, la administración de identidades no cambiará.

Si la organización ya tiene un entorno de Office 365 existente, pero no todos los usuarios tienen cuentas de Office 365, crearemos un usuario en el inquilino y asignaremos licencias en función de las direcciones de correo electrónico laborales o académicas del usuario. Esto significa que el número de usuarios que administra en cualquier momento determinado crecerá a medida que los usuarios de la organización se suscriben en el servicio.

Si la organización no tiene un entorno de Office 365 conectado al dominio de correo electrónico, no se producirá ningún cambio en la forma de administrar las identidades. Los usuarios se agregarán a un nuevo directorio de usuario solo en la nube y tendrá la opción de tomar el control como administrador de inquilinos y administrarlos.

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>¿Cuál es el proceso para administrar un inquilino creado por Microsoft para mis usuarios?
Si Microsoft ha creado un inquilino, puede reclamarlo y administrarlo mediante estos pasos:

1. Para unir el inquilino, suscríbase a PowerApps mediante un dominio de correo electrónico que coincida con el dominio del inquilino que desea administrar. Por ejemplo, si Microsoft creó el inquilino de contoso.com, únase a él con una dirección de correo electrónico que termine en @contoso.com.
2. Para reclamar el control de la administración, compruebe la propiedad del dominio: una vez que se encuentre en el inquilino, puede promocionarse al rol de administrador comprobando la propiedad del dominio. Para ello, siga estos pasos:
3. Vaya a [https://portal.office.com](https://portal.office.com/Start?sku=powerapps).
4. Seleccione el icono del iniciador de aplicaciones en la esquina superior izquierda y luego elija Administrador.
5. Lea las instrucciones de la página **Become the admin** (Convertirse en el administrador) y, después, elija **Yes, I want to be the admin** (Sí, deseo ser el administrador).  

> [!NOTE]
> Si esta opción no aparece, se deberá a que ya hay un administrador de Office 365.

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>Si dispongo de varios dominios, ¿puedo controlar el inquilino de Office 365 al que se agregan los usuarios?
Si no hace nada, se creará un inquilino para cada dominio y subdominio de correo electrónico del usuario.

Si desea que todos los usuarios estén en el mismo inquilino, independientemente de sus extensiones de correo electrónico:  

* Cree de antemano un inquilino de destino o use un inquilino existente. Agregue todos los dominios y subdominios existentes que desee que se consoliden en dicho inquilino. A partir de ese momento, todos los usuarios cuyas direcciones de correo electrónico terminen en esos dominios y subdominios se unirán automáticamente al inquilino de destino al suscribirse.

> [!IMPORTANT]
> No hay ningún mecanismo automático que permita mover usuarios entre inquilinos una vez que se han creado. Para obtener información acerca de cómo agregar dominios a un solo inquilino de Office 365, consulte [Agregar usuarios y un dominio con el asistente de configuración](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-ffdb2216-330d-4d73-832b-3e31bcb5b2a7).
