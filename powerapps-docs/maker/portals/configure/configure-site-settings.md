---
title: Configuración del sitio para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar el sitio para un portal y la configuración global de todos los portales de la organización.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 339a8b221474bd9d98ed8e425f730bab1dbb1e0a
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978333"
---
# <a name="configure-site-settings-for-portals"></a>Configuración del sitio para portales

Una configuración de sitio es un valor con nombre configurable que se usa en el código del sitio web para modificar el comportamiento o el estilo visual del portal. Normalmente, cuando un desarrollador crea el código del sitio web, hará referencia a la configuración del sitio para varios componentes a fin de permitir que un usuario final modifique los valores de configuración para modificar el sitio web sin tener que cambiar el código, volver a compilar y volver a implementar el sitio Web.

Los portales de ejemplo que se proporcionan con la instalación de portales de PowerApps contienen varias configuraciones de sitio configurables para varios estilos utilizados para modificar muchos elementos visuales dentro del sitio, como el estilo de fondo, el color del texto y el ancho del diseño.
Puede administrar los siguientes tipos de configuración del sitio:

- **Configuración del portal global**: esta configuración se aplica a todos los portales asociados al entorno de Common Data Service en el que se van a agregar.
- **Configuración del sitio de portal**: esta configuración se aplica a portales específicos (registros de sitios web) que están asociados con el Common Data Service entorno en el que se van a agregar.


## <a name="manage-portal-site-settings"></a>Administrar la configuración del sitio de portal

1. Vaya a [configuración del portal](../manage-existing-portals.md#settings) y seleccione **configuración del sitio**.

2. Para crear una nueva configuración, seleccione **nuevo**.

3. Para editar una configuración existente, seleccione la **configuración del sitio** que aparece en la cuadrícula.

4. Especifique los valores para los campos proporcionados: 

    - **Nombre**: una etiqueta a la que hace referencia el código del sitio web para recuperar la configuración adecuada. El nombre debe ser único para el sitio web asociado, ya que el código que recupera la configuración tomará el primer registro que se encuentre con el nombre coincidente.
    
    - **Sitio web**: el sitio web asociado. 
    
    - **Valor**: configuración
    
    - **Descripción**: el propósito de la configuración o las instrucciones especiales.

5. Seleccione **Guardar y cerrar**.

> [!NOTE] 
> La integración de mapas de Bing no se admite en la nube independiente de alemán. Si intenta crear el valor de la opción Bingmaps/Credentials en este entorno, se mostrará un mensaje de error.

## <a name="portal-site-settings"></a>Configuración del sitio de portal

|Nombre|Value|Descripción|
|----|-----|-----------|
|Autenticación/registro/RequiresConfirmation|ES |Un valor booleano de true habilita la confirmación de correo electrónico y deshabilita el registro abierto. Valor predeterminado: false |
|Autenticación/registro/RequiresInvitation|ES |Un valor booleano de true habilita la característica de código de invitación y deshabilita el registro abierto. Valor predeterminado: false |
|nombre de conferencia|Congreso de portales|Nombre de un registro adx_conference que representa la Conferencia de un portal determinado.|
|Departamento de soporte técnico/CaseEntitlementEnabled|REALES|Un valor booleano que indica si está habilitado el derecho del Departamento de soporte técnico. Valor predeterminado: false|
|Departamento de soporte técnico/desvío/DefaultSelectedProductName| |El nombre de un registro de producto que es el producto seleccionado predeterminado en la lista desplegable que se muestra en la desviación de casos del Departamento de soporte técnico si hay más de un producto en el que producttypecode es igual a 100000001.|
|Perfil/ForceSignUp|ES|Un valor booleano cuando se establece en "true" obligará al usuario a actualizar su información de perfil antes de que se les concedido acceso al contenido del sitio Web. Valor predeterminado: false|
|Perfil/ShowMarketingOptionsPanel|REALES|Valor booleano que indica si se va a mostrar el panel que muestra los campos para especificar las preferencias de comunicación de marketing en el perfil. Valor predeterminado: false|
|Búsqueda/habilitado|REALES|Valor booleano que indica si la búsqueda está habilitada o no.|
|búsqueda/filtros|Contenido: adx_webpage; Eventos: adx_event, adx_eventschedule;<br>Blogs: adx_blog, adx_blogpost, adx_blogpostcomment;<br>Foros: adx_communityforum, adx_communityforumthread, adx_communityforumpost;<br>Ideas: adx_ideaforum, adx_idea, adx_ideacomment;<br>Problemas: adx_issueforum, adx_issue, adx_issuecomment; Departamento de soporte técnico: incidente|Colección de opciones de filtro de nombre lógico de búsqueda. La definición de un valor aquí agregará opciones de filtro desplegable a la búsqueda en todo el sitio. Este valor debe tener el formato de pares nombre-valor, con el nombre y el valor separados por dos puntos, y los pares separados por un punto y coma.<br>Por ejemplo: "forums: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment ".|
|Buscar/IndexQueryName|Búsqueda en el portal|El nombre de la vista del sistema utilizada por la consulta de búsqueda en el portal. Valor predeterminado: búsqueda en el portal|
|búsqueda/consulta|\+ (@Query) _title:(@Query) _logicalname: adx_webpage ~ 0.9 ^ 0,2<br> -_logicalname: adx_webfile ~ 0.9 adx_partialurl:(@Query)<br> _logicalname: adx_blogpost ~ 0.9 ^ 0.1-_logicalname: adx_communityforumthread ~ 0.9|Invalide la consulta para la búsqueda de sitios para aplicar pesos y filtros adicionales. @Query es el texto de la consulta escrito por un usuario. Referencia de sintaxis de consulta de Lucene: [http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|Búsqueda/analizador lingüístico|Inglés|El lenguaje utilizado por el algoritmo de lematización de la búsqueda del portal. Valor predeterminado: Inglés|
|CustomerSupport/DisplayAllUserActivitiesOnTimeline|ES| |
|Autenticación/[Protocolo]/[proveedor]/AllowContactMappingWithEmail| |Permitir Asociación automática a un registro de contacto basado en el correo electrónico. Para obtener más información, haga clic [aquí](https://docs.microsoft.com/en-us/dynamics365/portals/azure-ad-b2c#allow-auto-association-to-a-contact-record-based-on-email).|
|||

Para ver la configuración del sitio relacionada con varias características del portal, consulte:

- [Identidad de autenticación](set-authentication-identity.md)
- [Proveedor de Azure AD B2C](azure-ad-b2c.md)
- [OAuth 2,0](configure-oauth2-settings.md)
- [Open ID Connect](configure-openid-settings.md)
- [WS-Federation](configure-ws-federation-settings.md)
- [SAML 2,0](configure-saml2-settings.md)
- [Migrar proveedores de identidades a Azure AD B2C](migrate-identity-providers.md)
- [Buscar en el contenido de los archivos adjuntos](https://docs.microsoft.com/dynamics365/customer-engagement/portals/search-file-attachment)
- [Comportamiento y formato del campo de fecha y hora](https://docs.microsoft.com/dynamics365/customer-engagement/portals/behavior-format-date-time-field)
- [Agregar ubicación geográfica](https://docs.microsoft.com/dynamics365/customer-engagement/portals/add-geolocation)
- [Integrar servicio de campo](https://docs.microsoft.com/dynamics365/customer-engagement/portals/integrate-field-service)
- [Implementación de normativas generales de protección de datos](https://docs.microsoft.com/dynamics365/customer-engagement/portals/implement-gdpr)
- [Habilitar almacenamiento en caché de resultados de encabezado y pie de página](https://docs.microsoft.com/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>Administrar la configuración global del portal

1. Vaya a [configuración del portal](../manage-existing-portals.md#settings) y seleccione **configuración del sitio**.

2. Vaya a **configuración** &gt; **configuración**.

3. Para crear una nueva configuración, seleccione **nuevo**.

4. Para editar una configuración existente, seleccione la **configuración del sitio** que aparece en la cuadrícula.

5. Especifique los valores para los campos proporcionados: 

    - **Nombre**: un nombre único al que hace referencia el código para recuperar la configuración adecuada.

    - **Valor**: configuración

    - **Descripción**: el propósito de la configuración o las instrucciones especiales.

6. Seleccione **Guardar y cerrar**.

> [!NOTE] 
> La integración de mapas de Bing no se admite en la nube independiente de alemán. Si intenta crear la configuración BinMap/Key o Adxstudio/ProductivityPack/BingMap/Key en este entorno, se mostrará un mensaje de error.


