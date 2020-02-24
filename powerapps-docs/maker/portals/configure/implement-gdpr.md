---
title: Implementar Reglamentos generales de protección de datos en portales de Power Apps | MicrosoftDocs
description: Aprenda a aplicar Reglamentos generales de protección de datos en portales de Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 80a60ae7b1dd8810ee3509dfe9fcd108dffceb5d
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980070"
---
# <a name="implementing-general-data-protection-regulations-in-your-power-apps-portals"></a>Aplicar Reglamentos generales de protección de datos en portales de Power Apps

El Reglamento General de protección de datos (GDPR) es una ley de la Unión Europea (UE), que protege los datos para todas las personas dentro de la Unión Europea. Con GDPR, la gente puede controlar el uso de sus datos personales en Common Data Service.

Como administrador, puede configurar su portal para cumplir los estándares GDPR. Por ejemplo, los menores deben tener consentimiento parental para usar el portal. También puede establecer los términos y condiciones para los usuarios de su portal. Los usuarios deben aceptar los términos y condiciones de uso del portal.

GDPR le permite obtener consentimiento de los usuarios del portal para usar sus datos personales, identificar a los usuarios menores y obtener el consentimiento parental para menores.

## <a name="audit-logging"></a>Registro de auditoría

El campo **último inicio de sesión correcto** del registro de contacto del portal muestra cuando un usuario del portal ha iniciado sesión. Esta fecha se elige mediante una auditoría del registro de contacto y pone la información a disposición de la secuencia de auditoría estándar. Esto permite al administrador ver los miembros de la Comunidad inactivos y eliminar los registros.

> [!NOTE]
> La característica de seguimiento de inicio de sesión está obsoleta. Se recomienda usar una tecnología de análisis como Azure Application Insights para capturar este tipo de información. Para ver una lista de características obsoletas, haga clic [aquí](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/).

## <a name="identifying-minor-portal-users-and-obtaining-parental-consent"></a>Identificar a los usuarios de portal menores y obtención del consentimiento parental

Las normativas para identificar a los menores varían según el país/región. Puesto que un menor solo puede acceder al portal con consentimiento paterno, puede configurar el portal de para identificar a los menores con estos campos del registro de contacto del portal:
- **Es menor**: indica que el contacto se considera menor en su jurisdicción. De forma predeterminada, se selecciona **No**.
- **Es menor con consentimiento parental**: indica que se considera al contacto menor en su jurisdicción y tiene consentimiento parental. De forma predeterminada, se selecciona **No**.

    ![Identificar a los usuarios de portal menores y obtener el consentimiento parental](../media/identify-minor-in-portal.png "Identificar a los usuarios de portal menores y obtener el consentimiento parental")

La siguiente configuración del sitio controla el uso de portales por menores y menores sin consentimiento de los padres:

| Nombre  | Descripción   |
|-----------------------|------------------------------------------|
| Authentication/Registration/DenyMinors  | Niega el uso del portal a menores. De forma predeterminada, se establece como falso.                          |
| Authentication/Registration/DenyMinorsWithoutParentalConsent | Rechaza el uso de este portal por menores sin consentimiento de sus padres. De forma predeterminada, se establece como falso. |
|||

Si se determina que un usuario del portal es menor y el portal está configurado para bloquear a los menores, aparecerá un mensaje adecuado y no se muestra el contenido.

![Mensajes de requisitos de edad](../media/gdpr-age-req.png "Mensajes de requisitos de edad")

Si se determina que un usuario del portal es menor y no tiene consentimiento parental, y el portal está configurado para bloquear a los menores sin consentimiento parental, aparecerá un mensaje adecuado y no se muestra el contenido.

![Mensaje de autorización parental](../media/gdpr-parental-consent.png "Mensaje de autorización parental")

Los siguientes fragmentos de contenido controlan los mensajes que aparecen cuando usan el portal menores y menores sin consentimiento de los padres. Puede cambiar el mensaje de acuerdo con sus necesidades.

| Nombre                                                        | Tipo | Value                                                                    |
|-------------------------------------------------------------|------|--------------------------------------------------------------------------|
| Account/Signin/MinorNotAllowedHeading                       | Texto | Requisitos de edad                                                         |
| Account/Signin/MinorNotAllowedCopy                          | HTML | El uso de este portal no es adecuado para su uso por menores y no está permitido. |
| Account/Signin/MinorWithoutParentalConsentNotAllowedHeading | Texto | Consentimiento jerárquico                                                         |
| Account/Signin/MinorWithoutParentalConsentNotAllowedCopy    | HTML | El uso de este portal por secundarios requiere el consentimiento jerárquico.              |
|||

Cuando alguien se registra mediante un proveedor externo y el portal está configurado para bloquear a menores o menores sin consentimiento parental, no se crea el registro de contacto y no se autentica al usuario.

## <a name="agreeing-to-terms-and-conditions"></a>Aceptación de los términos y condiciones

Según la GDPR, los usuarios del portal deben está de acuerdo con los términos y condiciones para permitir marketing, elaboración de perfiles o acceso a información privada. Como administrador, puede publicar sus propios términos y condiciones para obtener el consentimiento del usuario del portal antes de que se autentiquen en el sitio.

![Términos y condiciones del portal](../media/gdpr-terms-agreement.png "Términos y condiciones del portal")

Los siguientes fragmentos de contenido controlan la visualización de los términos y condiciones en la pantalla. Puede cambiar el texto de acuerdo con sus necesidades.

| Nombre                                           | Tipo | Value                                 |
|------------------------------------------------|------|---------------------------------------|
| Account/Signin/TermsAndConditionsHeading       | Texto | Términos y condiciones                  |
| Account/Signin/TermsAndConditionsCopy          | HTML |                                       |
| Account/Signin/TermsAndConditionsAgreementText | Texto | Acepto estos términos y condiciones |
| Account/Signin/TermsAndConditionsButtonText    | Texto | Continuar                              |
|||

El fragmento de contenido `Account/Signin/TermsAndConditionsCopy` está vacío de forma predeterminada. Un administrador del portal debe escribir los términos y condiciones de este fragmento de contenido.

La siguiente configuración de sitio controla la fecha de publicación de los términos y si estos deberían mostrarse en el portal:

| Nombre  | Descripción |
|------------|---------------|
| Authentication/Registration/TermsPublicationDate  | Un valor de fecha y hora en formato GMT para representar la fecha efectiva de los términos y condiciones publicados actualmente. Si el acuerdo de términos está habilitado, se pedirá a los usuarios del portal que no han admitido los términos después de esta fecha que los acepten la siguiente vez que inicien sesión. Si no se proporciona la fecha y el acuerdo de términos está habilitado, los términos aparecerán cada vez que los usuarios del portal inicien sesión. <br> **Nota**: si quiere que un usuario del portal está de acuerdo con los términos y condiciones cada vez que inicie sesión, no proporcione un valor para esta configuración de sitio.|
| Authentication/Registration/TermsAgreementEnabled | Un valor verdadero o falso. Si se establece en verdadero, el portal mostrará los términos y condiciones del sitio. Los usuarios deben estar de acuerdo con los términos y condiciones antes de que se considere que están autenticados y puedan usar el sitio. De forma predeterminada, se establece como falso.        |
|||

El campo siguiente se agrega al registro de contacto del portal para almacenar la fecha y hora en la que un usuario del portal aceptó los términos y condiciones:
- **Fecha de acuerdo de términos del portal**: Indica la fecha y la hora en que la persona aceptó los términos y condiciones del portal.

    ![Fecha de acuerdo de términos del portal](../media/portal-terms-agreement.png "Fecha de acuerdo de términos del portal")

### <a name="see-also"></a>Vea también

[Migrar proveedores de identidad a Azure AD B2C](migrate-identity-providers.md)
