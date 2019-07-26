---
ms.openlocfilehash: f331670a2fd6b051c91a7fe2bfa607c54c9ab41a
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225241"
---
Al habilitar [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] acepta permitir el flujo de datos de [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] a determinados servicios [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] para llevar a cabo algunos de los procesos de marketing. Estos servicios se conocen colectivamente como "servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]".

Para realizar recorridos de clientes, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] necesita enviar definiciones de recorridos de clientes, correo electrónico, formulario de envío y páginas de marketing a estos servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], que se ejecutan en [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]. Las páginas de marketing se envían a una instancia propia del cliente de funcionalidades del portal para [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)].

Para personalizar los correos electrónicos enviados, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] debe habilitar el flujo de datos hacia y desde [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. Consulte a continuación para obtener más información sobre el servicio [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. El flujo de datos a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] incluye la sincronización de contactos y cuentas con [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. Los servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] usan estos datos para personalizar el contenido de correo electrónico. Los datos que se incluyen dependen exclusivamente de la definición de correo electrónico.

Para volver a calcular los modelos de puntuación de clientes potenciales y los segmentos de marketing, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] debe enviar las definiciones de modelo de puntuación de clientes potenciales y las definiciones de segmento a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] y aprovechar los perfiles y las interacciones en [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] dentro de estos cálculos.

Para proporcionar información detallada sobre las interacciones por correo electrónico e Internet capturadas por los servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], los datos recopilados fluyen desde los servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] hasta [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] y [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)].

Si, además, la integración de administración de eventos de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] está habilitada, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] sincroniza los eventos con [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (directamente mediante el conector de [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)]) y los registros de eventos y las comprobaciones (mediante los servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], como interacciones).

El flujo de datos que engloba a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] es el siguiente:
- Datos de la entidad de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], mediante el conector de entrada normal de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], con el fin de proporcionar contenido para la personalización de correo electrónico, la puntuación de clientes potenciales y la segmentación (principalmente contactos y cuentas, pero, en ocasiones, también clientes potenciales y eventos)
- Datos de la entidad de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] mediante los servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], con el fin de proporcionar identificadores para las interacciones y la información detallada (recorrido del cliente, correos electrónicos de marketing y páginas de marketing)
- Interacciones de los servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (seguimiento de correo electrónico, seguimiento del sitio web y progreso del recorrido del cliente)
- Interacciones de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] mediante los servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (registros de eventos y comprobaciones)
- [!INCLUDE[pn-insights](../includes/pn-insights.md)] (interacciones y KPI) de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] mediante los servicios [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] a [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] (principalmente el recorrido del cliente y el progreso de envío de correo electrónico y los resultados de puntuación de clientes potenciales)
- Aplicaciones [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (segmentación y widgets) de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] directamente en los elementos de interfaz de usuario en un espacio aislado y dedicados en los formularios de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]

### <a name="marketing-services"></a>Servicios de marketing

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] utiliza estos servicios de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage

> [!NOTE]
> Para obtener más información sobre las ofertas de servicio de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] adicionales, visite el [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)] (<https://azure.microsoft.com/support/trust-center/>).

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

Mediante el uso de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], va a activar la transferencia de datos del cliente a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] para su posterior procesamiento. El uso de [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] para [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] puede requerir el cumplimiento de leyes de privacidad específicas. Plantee las preguntas al representante adecuado de la organización.

En la actualidad, [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] está en versión preliminar pública y no ofrece el mismo nivel de compromisos de privacidad y seguridad que [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] o [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] Customer Engagement. [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] se integra de forma nativa en los servicios [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)], y se aplican los estándares de cumplimiento y seguridad respectivos para cada servicio [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] correspondiente. Para más información, visite el Centro de confianza de [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)]: [https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] utiliza estos servicios de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight (Spark, Phoenix, HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Secret Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Event Hub
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Redis Cache
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Monitoring
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Metrics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Websites
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage
