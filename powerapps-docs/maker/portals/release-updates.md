---
title: Publicar actualizaciones en los portales de Power Apps | MicrosoftDocs
description: Obtenga información sobre las actualizaciones de las versiones de los portales de Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d775b383116f28df8a584a4943e64989e9ca0f76
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981381"
---
# <a name="release-updates"></a>Lanzamiento de actualizaciones

Este tema proporciona recursos donde podrá obtener información sobre las nuevas funciones que se han lanzado recientemente y las nuevas características que se lanzarán en los próximos meses.

## <a name="power-apps-portals-updates"></a>Actualizaciones de los portales de Power Apps

Para obtener información sobre las nuevas características que se publiquen en los próximos meses que puede usar para planear, consulte:

- [Plan de versión de 2019, oleada 2](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-powerapps/planned-features#portal-capabilities-for-power-apps)

## <a name="previous-portal-updates"></a>Actualizaciones del portal anterior

A continuación, se ofrece una lista de las características agregadas a los portales de Dynamics 365. Para obtener más información acerca de las actualizaciones de los portales de Dynamics 365 hasta la fecha, consulte [Versiones de Microsoft Dynamics 365](https://support.microsoft.com/help/3181191).

> [!NOTE]
> Los portales de Power Apps se conocían anteriormente como portales de Dynamics 365.

### <a name="dynamics-365-portals-version-914-for-the-model-driven-apps-in-dynamics-365"></a>La versión 9.1.4 de los portales de Dynamics 365 para las aplicaciones basadas en modelo en Dynamics 365

La versión 9.1.4 de los portales de Dynamics 365 para aplicaciones basadas en modelo en Dynamics 365 muestra estas nuevas actualizaciones y características:

- **Modo de mantenimiento para portal**: Como administrador del portal, ahora puede configurar el portal para mostrar un mensaje adecuado a los clientes cada vez que una actividad de mantenimiento se produzca. Por ejemplo, se actualizan paquetes de la solución. Más información: [Modo de mantenimiento para un portal](admin/enable-maintenance-mode.md)

- **Habilitar servicio Power BI Embedded**: Como administrador del portal, ahora puede insertar paneles e informes creados en el nuevo espacio de trabajo de Power BI habilitando el servicio Power BI Embedded. Los paneles e informes se insertan en las páginas web en un portal utilizando la etiqueta powerbi Liquid. Más información: [Configurar integración de Power BI](admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)

- **Habilitar moderación de contenido en ideas**: Como administrador de portal, ahora puede crear una política de moderación de contenido para moderar las ideas que se envían en el portal.

- **Flujo de concesión implícito de OAuth 2.0**: Como programador del portal, ahora puede hacer llamadas API del lado del cliente a API externas y protegerlas mediante el flujo de concesión implícito de OAuth 2.0. Más información: [Flujo de concesión implícito de OAuth 2.0](oauth-implicit-grant-flow.md)

- **Portal de inicio de Common Data Service (vista previa)**: Como administrador del portal, ahora puede configurar el portal para conectarse al entorno de Common Data Service y para permitir que los usuarios interactúen con él. Esta característica permite conectar un portal a un entorno de Common Data Service que no tiene ninguna aplicaciones basadas en modelo en Dynamics 365 (Dynamics 365 Sales, Dynamics 365 Service, Dynamics 365 Marketing) preinstaladas.

### <a name="dynamics-365-portals-version-911-for-the-model-driven-apps-in-dynamics-365"></a>La versión 9.1.1 de los portales de Dynamics 365 para las aplicaciones basadas en modelo en Dynamics 365

La versión 9.1.1 de los portales de Dynamics 365 para aplicaciones basadas en modelo en Dynamics 365 muestra estas nuevas actualizaciones y características:

- El **comprobador del portal**: ahora puede usar el comprobador de portal para identificar problemas con el portal viendo diferentes parámetros de configuración y proporcionando sugerencias sobre cómo corregirlos. Más información: [comprobador del portal](admin/portal-checker.md)

### <a name="dynamics-365-portals-version-9010-for-the-model-driven-apps-in-dynamics-365"></a>La versión 9.0.10 de los portales de Dynamics 365 para las aplicaciones basadas en modelo en Dynamics 365

La versión 9.0.10 de los portales de Dynamics 365 para aplicaciones basadas en modelo en Dynamics 365 muestra estas nuevas actualizaciones y características:

- **Migrar la configuración del Portal de Dynamics 365**: ahora puede migrar la configuración de los portales de Dynamics 365 desde el entorno de desarrollo a pruebas o a los entornos de producción. La migración implica la exportación de los datos de configuración existentes desde la instancia de Dynamics 365 de origen y, a continuación, importarlos en la instancia de Dynamics 365 de destino. Para migrar los datos de configuración, tiene que usar la herramienta Migración de la configuración y un archivo de esquema de configuración específico del portal. Más información: [Migrar la configuración de los portales de Dynamics 365](admin/migrate-portal-configuration.md)

- **Agregar visualización de Power BI**: como administrador del portal, ahora puede insertar las visualizaciones de Power BI (panel, informes y ventanas) en las páginas web de un portal mediante la etiqueta powerbi de Liquid. Más información: [Configurar integración de Power BI](admin/set-up-power-bi-integration.md)

- **Limitar el acceso al portal mediante la dirección IP**: como administrador del portal, ahora puede definir una lista de direcciones IP con permiso para acceder al portal. Cuando se genera una solicitud al portal por parte de cualquier usuario, se evalúa su dirección IP con la lista de permitidos. Si la dirección IP no está en la lista, el portal muestra una página web con un código de estado HTTP 403. Más información: [Limitar el acceso al portal mediante la dirección IP](admin/ip-address-restrict.md)

- **Administrar documentos de SharePoint**: los portales de Dynamics 365 permite ahora cargar y mostrar documentos desde y hacia SharePoint directamente en un formulario de entidad o un formulario web en un portal. Esto permite que los usuarios del portal vean , descarguen, agreguen y eliminen documentos de un portal. Los usuarios del portal también pueden crear carpetas para organizar sus documentos. Más información: [Administrar correos electrónicos de SharePoint](manage-sharepoint-documents.md)

- **Nuevo editor de contenido de portal (vista previa)**: en este vista previa está disponible un nuevo editor de portal simplificado para quienes quieran personalizar los portales de Dynamics 365, a fin de rebajar la curva de aprendizaje de la personalización de los portales de Dynamics 365 y de aumentar la productividad de quien realice la personalización.

- **Habilitar la votación por razones de estado**: de forma predeterminada, una idea se habilita para la votación únicamente cuando Razón para el estado se establece en Nueva. Ahora puede habilitar la votación sobre una idea por distintas razones de estado. Para habilitar la votación de una idea por distintas razones de estado, debe crear el valor de sitio Ideas/EnableVotingForStatusReasons y establecer como valor uno de los valores requeridos de razón para el estado. 

### <a name="dynamics-365-portals-version-906-for-the-model-driven-apps-in-dynamics-365"></a>La versión 9.0.6 de los portales de Dynamics 365 para las aplicaciones basadas en modelo en Dynamics 365

La versión 9.0.6 de los portales de Dynamics 365 para aplicaciones basadas en modelo en Dynamics 365 trae consigo las siguientes nuevas actualizaciones y características:

- **Aplicación del portal de Dynamics 365**: la aplicación de los portales de Dynamics 365 proporciona una nueva experiencia para configurar y administrar su plataforma en línea para comunicarse con los clientes y colaborar con ellos. Al instalar los portales de Dynamics 365, versión 9.0 y superior, la aplicación de los portales de Dynamics 365, que se basa en el marco de trabajo de la interfaz unificada, se crea de forma inmediata.

- **Restaurar un portal**: ahora puede restaurar un portal si piensa trasladarse a otra geolocalización o a otro inquilino, y no desea seguir usando el portal. Cuando restablezca un portal, se eliminan los recursos hospedados del portal y no se podrá obtener acceso a la dirección URL del portal. Más información: [Restaurar un portal](admin/reset-portal.md)

- **Cambiar la dirección URL base de un portal**: ahora puede cambiar la dirección URL base de un portal una vez aprovisionado. Por ejemplo, si elige contosocommunity.microsoftcrmportals.com como la dirección URL de base cuando aprovisiona el portal, puede cambiarlo después a contosocommunityportal.microsoftcrmportals.com si así lo desea. Más información: [Cambiar dirección URL de base](admin/change-base-url.md)


### <a name="dynamics-365-portals-version-841-for-the-model-driven-apps-in-dynamics-365"></a>La versión 8.4.1 de los portales de Dynamics 365 para las aplicaciones basadas en modelo en Dynamics 365

La versión 8.4.1 de los portales de Dynamics 365 para aplicaciones basadas en modelo en Dynamics 365 incorpora varias correcciones de errores y mejoras de rendimiento, así como las características siguientes:

- **Buscar en el contenido de los datos adjuntos de los artículos de conocimientos y de los archivos de web**: el contenido de los datos adjuntos de los artículos de conocimientos y los archivos web se puede buscar ahora para aumentar la probabilidad de resultados de la búsqueda relevantes. Más información: [Buscar en el contenido de los archivos adjuntos](configure/search-file-attachment.md)
- **Accesibilidad**: los portales listos para usar (portal de la comunidad, portal de asociados, portal de clientes, portal de autoservicio de empleados) están accesibles ahora. Sin embargo, el personalizador debe asegurarse de que el portal permanezca accesible después de cualquier personalización o cambio.


### <a name="dynamics-365-portals-version-84-for-the-model-driven-apps-in-dynamics-365"></a>La versión 8.4 de los portales de Dynamics 365 para las aplicaciones basadas en modelo en Dynamics 365

La versión 8.4 de los portales de Dynamics 365 para aplicaciones basadas en modelo en Dynamics 365 incorpora varias correcciones de errores y mejoras de rendimiento, así como las características siguientes:

- **Registros de error del portal de acceso**: como desarrollador de portales, ahora puede tener acceso a registros de errores detallados para todos los problemas de su portal. Esto le ayuda a depurar los problemas durante el desarrollo del portal. Cuando el portal esté en marcha, puede configurar el portal para enviar todos los errores de aplicación a una cuenta de Azure Blob Storage de su propiedad. Esto le ayudará a depurar los problemas detectados por los clientes. Más información: [acceso a registros de error del portal](admin/view-portal-error-log.md)
- **Renovación de la clave de autenticación**: un portal se conecta a un entorno de Common Data Service con una aplicación de Azure Active Directory. Para ello, se requiere una clave de autenticación conectada a la aplicación de Azure Active Directory. Esta clave se agrega al aprovisionar su portal y debe renovarse cada dos años. Esta versión del portal aporta la capacidad para que los administradores reciban una notificación sobre la expiración de la clave y renueven esta clave en el centro de administración de Portales de Power Apps. Más información: [Renovación de la clave de autenticación del portal](admin/manage-auth-key.md)
- **Aplicación del Reglamento general de protección de datos en los portales**: como administrador de portal, ahora puede configurar su portal para que cumpla los estándares GDPR. También puede proporcionar determinados términos y condiciones que deben ser aceptados por los usuarios del portal para utilizar el portal. También puede configurar comprobaciones como, por ejemplo, si un usuario menor de edad tiene acceso a un portal, este usuario debe tener consentimiento de sus padres para acceder al portal. Aplicar el GDPR le permite obtener el consentimiento de los usuarios del portal en relación con el uso de sus datos personales, identificar a los usuarios menores y obtener el consentimiento parental para menores. Más información: [Implementar GDPR en portales](configure/implement-gdpr.md)

### <a name="dynamics-365-portals-version-83-for-the-model-driven-apps-in-dynamics-365"></a>La versión 8.3 de los portales de Dynamics 365 para las aplicaciones basadas en modelo en Dynamics 365

La versión 8.3 de los portales de Dynamics 365 para aplicaciones basadas en modelo en Dynamics 365 tiene muchas actualizaciones y características nuevas:

- **Capacidad de incluir los datos adjuntos en los artículos de conocimientos**: esta característica permite mostrar los datos adjuntos de las notas junto con el artículo de conocimientos. Para habilitar esta característica, debe crear la configuración de sitio KnowledgeManagement/DisplayNotes y establecer el valor en **true**. Los usuarios del portal también pueden buscar dichos datos adjuntos. Más información: Mostrar los archivos adjuntos con los artículos de conocimientos

  > [!Note]
  > La búsqueda de datos adjuntos es posible solo con la descripción de la nota y con el nombre del archivo adjunto. El contenido del archivo adjunto no se puede buscar.
  
- **Asistente administrativo agregar una entidad al portal**: Esta característica introduce un nuevo asistente administrativo para exponer fácilmente los datos en el portal. La entidad creada en el asistente toma los datos de la organización y facilita un subconjunto de estos que está disponible para los clientes del portal según el modelo de seguridad y permisos que elija.

- **Importar traducción de metadatos**: use esta característica para importar la traducción de los metadatos en otros idiomas recién activados, una vez haya instalado un portal. Más información: [importar traducción de metadatos](admin/import-metadata-translation.md)

- **Disponibilidad de código fuente para los portales**: una única versión del código de los portales de Dynamics 365 se publica en el Centro de descarga de Microsoft en licencia MIT para que la descarguen los desarrolladores. Esta característica habilita los portales para que se implementen en Dynamics 365 (on-premises) en los entornos locales o en línea, y permite que los desarrolladores personalicen el código para adaptarlo a las necesidades específicas del negocio.

  > [!NOTE]
  > El código fuente se proporciona como una muestra de operación y según sea necesario. No se proporciona ningún soporte directo para ninguna modificación del código.

- **Mejoras de configuración de inicio de sesión único (SSO) y soporte para Azure Active Directory B2C (Azure AD B2C)**: para los portales que requieren un inicio de sesión basado en cliente, esta característica ahora admite la posibilidad de:
  - Configurar la autenticación de portal para usar SSO. 
  - Admitir Azure AD B2C para la autenticación del cliente.
  - Administrar la seguridad del portal en Azure.

  Más información: [Configuración del proveedor Azure AD B2C para portales](configure/azure-ad-b2c.md)

- **Compatibilidad con los formatos de fecha independientes de zona horaria en los formularios de los portales**: esta característica permite la compatibilidad con **Solo fecha** e **Independiente de la zona horaria** en los campos de fecha y hora de los portales. Más información: [Comportamiento y formato del campo de fecha y hora](configure/behavior-format-date-time-field.md)

- **Permitir que los administradores no globales aprovisionen el portal**: ahora puede aprovisionar un portal si tiene asignado el rol de administrador del sistema de la organización CRM seleccionada para el portal. Ahora puede también administrar un portal existente, si tiene cualquiera de los roles:
  - Administrador de servicio de Dynamics 365
  - Administrador del sistema de la organización de CRM seleccionada para el portal

- **Nombre de dominio personalizado de almacén para el portal**: esta característica almacena el nombre del dominio principal de un portal en el registro de la página web. Si el nombre de dominio se cambia posteriormente, se almacena el último nombre de dominio principal.

- **Cookie de seguimiento para portales**: una cookie persistente Dynamics365PortalAnalytics se establecerá siempre que un usuario vaya a un portal. Esta cookie tiene una expiración de 90 días. Esta cookie no almacena datos personales del usuario y la usa Microsoft para recopilar datos analíticos del servicio de portal. Puede obtener más información sobre la declaración de privacidad de servicios en línea de Microsoft [aquí](https://go.microsoft.com/fwlink/p/?linkid=856855).

- **Mejora del rendimiento de encabezado y el pie de página en un portal**: dos nuevos valores del sitio, Header/OutputCache/Enabled y Footer/OutputCache/Enabled, se agregan para permitir que el encabezado o pie de página se almacenen en la caché cuando estos valores se establecen en "true". Para los nuevos usuarios, esta configuración de sitio se establece de forma predeterminada en verdadero, habilitando el almacenamiento en caché de resultados del encabezado y el pie de página. Para los usuarios existentes que se actualicen a una versión más reciente de los portales de Dynamics 365, el almacenamiento de resultados en caché está deshabilitado de forma predeterminada. Significa que las plantillas web de encabezado y de pie de página se analizan y representan cada vez que una página se carga. Para habilitar almacenamiento de resultados en caché, deben actualizar las plantillas web adecuadas y crear los valores necesarios del sitio. Más información: [Habilitar el almacenamiento en caché de resultados del encabezado y el pie de página](configure/enable-header-footer-output-caching.md)

### <a name="december-2016-updates"></a>Actualizaciones de diciembre de 2016

La actualización de diciembre de 2016 ha traído muchas características nuevas a las capacidades de los portales de Dynamics 365. Estas actualizaciones permiten mejores interacciones entre compañías, asociados y clientes y hacen que la experiencia de navegar por el portal sea más rápida y fácil. Algunas de las actualizaciones principales:

- **Compatibilidad con varios idiomas:** Ayuda a los clientes varias regiones utilizando un único portal. Más información: [habilitar la compatibilidad con varios idiomas](configure/enable-multiple-language-support.md)
- **Compatibilidad con idiomas asiáticos orientales:** idiomas de varios bytes como japonés, chino y coreano ahora se admiten.
- **Búsqueda por facetas:** Nuevos filtros mejoran la rapidez con la que los clientes pueden encontrar el contenido que están buscando mientras conceden mayor control sobre la visibilidad del contenido. Más información: [Búsqueda en facetas](configure/improve-portal-search-faceted-search.md)
- **Filtrado de productos:** Los usuarios del portal pueden recortar el acceso a artículos de conocimientos relacionados con la propiedad de sus productos para evitar la sobrecarga de información.
- **Niveles de acceso a contenido:** un nuevo nivel de propiedad asociado a un contacto de portal, una cuenta, o un rol web se puede usar para controlar el acceso a los artículos de conocimientos, para ayudarle a dirigir el artículo correcto al el público correcto y evitar que los artículos inútiles emerjan. Más información: [Niveles de acceso de contenido](https://docs.microsoft.com/dynamics365/portals/manage-knowledge-articles-content-levels)
- **Mejora de los informes de artículos de conocimientos:** El portal realiza un seguimiento de dónde se usa un artículo de conocimientos en el portal.
- **Integración de Project Service Automation**: Proporcione acceso y visibilidad para proyectos activos y cerrados en todas las fases de un ciclo de vida del proyecto a asociados y clientes. Los integrantes del equipo, los revisores, y los clientes pueden ver el estado del proyecto, citas, foros del pedido, y recursos reservables en el portal con esta solución. Más información: [integrar Project Service Automation](https://docs.microsoft.com/dynamics365/portals/integrate-project-service-automation)
- **Integración de Field Service**: Exponga información acerca de contratos activos, activos, órdenes de trabajo, facturas, y casos de soporte a asociados y clientes en el portal con esta solución. Más información: [integrar Field Service](https://docs.microsoft.com/dynamics365/portals/integrate-field-service)
- **Incorporación de asociados**: Contrate nuevos partners para mejorar las experiencias de atención y servicio al cliente. Los partners potenciales pueden solicitar el estado de asociado a través del portal.

### <a name="privacy-notice"></a>Aviso de privacidad

[!INCLUDE[cc-privacy-crm-portals-data-exposed](../../includes/cc-privacy-crm-portals-data-exposed.md)]

Para obtener más información acerca de otras ofertas de servicios de [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)], vea [[!INCLUDE[cc_privacy_note_azure_trust_center](../../includes/cc_privacy_note_azure_trust_center.md)]](https://azure.microsoft.com/support/trust-center/).  
