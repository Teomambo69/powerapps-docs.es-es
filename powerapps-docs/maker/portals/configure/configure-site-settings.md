---
title: Configurar ajustes del sitio para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar la configuración del sitio para un portal y la configuración global para todos los portales de la organización.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6f37959db1296995abe08e85995750796a93da9c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866947"
---
# <a name="configure-site-settings-for-portals"></a>Configurar opciones del sitio para portales

Una configuración del sitio es un valor configurable con nombre que usa el código del sitio web para modificar el comportamiento o el estilo visual del portal. Normalmente cuando un desarrollador crea el código de sitio web, hará referencia a la configuración del sitio para los distintos componentes para permitir a un usuario final modificar los valores de configuración para modificar el sitio web sin tener que cambiar el código, recopilar y volver a implementar el sitio web.

Los portales de ejemplo que se proporcionan con la instalación de portales de Power Apps contienen varias configuraciones ajustables del sitio para diversos estilos usados para editar muchos elementos visuales dentro del sitio, como estilo de fondo, color del texto, y ancho del diseño.
Puede administrar los siguientes tipos de configuraciones de sitio:

- **Configuración de portal global**: Esta configuración se aplica a todos los portales asociados con el entorno Common Data Service donde se agregan.
- **Configuración de sitio de portal**: Esta configuración se aplica a todos los portales específicos (registros de página web) asociados con el entorno Common Data Service donde se agregan.


## <a name="manage-portal-site-settings"></a>Administrar la configuración del sitio de portal

1. Vaya a [configuración de portal](../manage-existing-portals.md#settings) y seleccione **Configuración del sitio**.

2. Para crear un nuevo ajuste, seleccione **Nuevo**.

3. Para editar un ajuste existente, seleccione la **Configuración del sitio** incluida en la cuadrícula.

4. Especifique valores para los campos proporcionados: 

    - **Nombre**: Una etiqueta a la que hace referencia el código del sitio web para recuperar el valor apropiado. El nombre debe ser único para el sitio web asociado, ya que el código que recupera el valor tomará el primer registro que encuentre con el nombre coincidente.
    
    - **Sitio web**: El sitio web asociado. 
    
    - **Valor**: El valor
    
    - **Descripción**: El objetivo del valor o instrucciones especiales.

5. Seleccione **Guardar y cerrar**.

> [!NOTE] 
> La integración de mapas de Bing no se admite en el entorno de la nube soberana alemana. Si intenta crear la configuración de mapas de Bing/credenciales en este entorno, se mostrará un mensaje de error.

## <a name="portal-site-settings"></a>Configuración del sitio del portal

|Nombre|Value|Descripción|
|----|-----|-----------|
|Authentication/Registration/RequiresConfirmation|FALSE |Un valor booleano de True habilita la confirmación por correo electrónico y deshabilita el registro abierto. Valor predeterminado: False |
|Authentication/Registration/RequiresInvitation|FALSE |Un valor booleano de True habilita la característica de código de invitación y deshabilita el registro abierto. Valor predeterminado: False |
|conference-name|Conferencia de portales|El nombre de un registro adx_conference que representa la conferencia para un portal determinado.|
|HelpDesk/CaseEntitlementEnabled|TRUE|Valor booleano que indica si está habilitado el derecho del caso del Servicio de asistencia. Valor predeterminado: false|
|HelpDesk/Deflection/DefaultSelectedProductName| |El nombre de un registro del producto que es el producto predeterminado seleccionado en la lista desplegable mostrada en la desviación de caso del Servicio de asistencia si hay más de un producto donde producttypecode sea igual a 100000001.|
|Profile/ForceSignUp|FALSE|Un valor booleano cuando se establece en “True” forzará al usuario a actualizar la información de su perfil antes de que reciba acceso al contenido de la página web. Valor predeterminado: False|
|Profile/ShowMarketingOptionsPanel|TRUE|Valor booleano que indica si se muestra el panel que enumera los campos para especificar las preferencias de comunicación de marketing en el perfil. Valor predeterminado: False|
|Búsqueda / Habilitado|TRUE|Un valor booleano que indica si la búsqueda está habilitada o no.|
|Filtro de búsqueda|Content:adx_webpage;Events:adx_event,adx_eventschedule;<br>Blogs:adx_blog,adx_blogpost,adx_blogpostcomment;<br>Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;<br>Ideas:adx_ideaforum,adx_idea,adx_ideacomment;<br>Issues:adx_issueforum,adx_issue,adx_issuecomment;Help Desk:incident|Una recopilación de opciones de filtro del nombre lógico de búsqueda. Definir un valor aquí agregará opciones de filtro desplegable a la búsqueda en todo el sitio. Este valor debe tener la forma de pares nombre / valor, con nombre y valor separados por dos puntos, y pares separados por punto y coma.<br>Por ejemplo: “Foros: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment”.|
|Buscar/IndexQueryName|Búsqueda del portal|El nombre de la vista del sistema usada por la consulta de búsqueda del portal. Valor predeterminado: Búsqueda del portal|
|Consulta y búsqueda|+(@Query) _title:(@Query) _logicalname:adx_webpage~0.9^0.2<br> -_logicalname:adx_webfile~0.9 adx_partialurl:(@Query)<br> _logicalname:adx_blogpost~0.9^0.1 -_logicalname:adx_communityforumthread~0.9|Reemplazar consulta para búsqueda del sitio, para aplicar ponderaciones adicionales y filtros. @Query es el texto de consulta escrito por un usuario. Referencia de la sintaxis de consulta Lucene: [https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|Buscar/lematizador|Inglés|El idioma utilizado por el algoritmo de la lematización de búsqueda de portal. Valor predeterminado: Inglés|
|CustomerSupport/DisplayAllUserActivitiesOnTimeline|FALSE| |
|Authentication/[Protocol]/[Provider]/AllowContactMappingWithEmail| |Permitir la asociación automática a un registro de contacto en función de correo electrónico. Para obtener más información, haga clic [aquí](azure-ad-b2c.md#allow-auto-association-to-a-contact-record-based-on-email).|
|||

Para valores del sitio relacionados con las diferentes características del portal, consulte:

- [Identidad de autenticación](set-authentication-identity.md)
- [Proveedor Azure AD B2C](azure-ad-b2c.md)
- [OAuth 2.0](configure-oauth2-settings.md)
- [Open ID Connect](configure-openid-settings.md)
- [WS-Federation](configure-ws-federation-settings.md)
- [SAML 2.0](configure-saml2-settings.md)
- [Migrar proveedores de identidad a Azure AD B2C](migrate-identity-providers.md)
- [Buscar contenido de archivo adjunto](search-file-attachment.md)
- [Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)
- [Agregar ubicación geográfica](add-geolocation.md)
- [Implementar el Reglamento general de protección de datos](https://docs.microsoft.com/dynamics365/customer-engagement/portals/implement-gdpr)
- [Habilitar el almacenamiento en caché de resultados del encabezado y el pie de página](https://docs.microsoft.com/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>Administrar la configuración de portal global

1. Vaya a [configuración de portal](../manage-existing-portals.md#settings) y seleccione **Configuración del sitio**.

2. Vaya a **Configuración** &gt; **Configuración**.

3. Para crear un nuevo ajuste, seleccione **Nuevo**.

4. Para editar un ajuste existente, seleccione la **Configuración del sitio** incluida en la cuadrícula.

5. Especifique valores para los campos proporcionados: 

    - **Nombre**: Un nombre exclusivo a la que hace referencia el código para recuperar el valor apropiado.

    - **Valor**: El valor

    - **Descripción**: El objetivo del valor o instrucciones especiales.

6. Seleccione **Guardar y cerrar**.

> [!NOTE] 
> La integración de mapas de Bing no se admite en el entorno de la nube soberana alemana. Si intenta crear el valor BinMap/Key o Adxstudio/ProductivityPack/BingMap/Key en este entorno, se mostrará un mensaje de error.


