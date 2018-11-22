Al habilitar [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], acepta permitir el flujo de datos de [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] para determinados servicios [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] a fin de realizar algunos de los procesos de marketing. Estos servicios se denominan colectivamente "servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]".

Para realizar recorridos del cliente, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] necesita enviar definiciones de recorrido del cliente, correo electrónico, formulario de envío y página de marketing a estos servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], que se ejecutan en [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]. Las páginas de marketing se envían a una instancia de capacidades del portal del propio cliente para [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)].

Para personalizar los correos electrónicos enviados, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] tiene que habilitar el flujo de datos desde y hacia [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. Véase a continuación para obtener más información sobre el servicio de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. El flujo de datos a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] incluye la sincronización de contactos y cuentas con [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. Los servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] usan estos datos para personalizar el contenido del correo electrónico. Los datos que se incluyen dependen exclusivamente de la definición del correo electrónico.

Para recalcular modelos de puntuación de clientes potenciales y segmentos de marketing, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] tiene que enviar definiciones de modelos de puntuación de clientes potenciales y definiciones de segmentos a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] y aprovechar los perfiles e interacciones de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] a partir de estos cálculos.

Para proporcionar información en el correo electrónico e interacciones en Internet capturadas por los servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], los flujos de datos recopilados fluyen de los servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] a [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] y [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)].

Además, si se habilita la integración con Administración de eventos de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] sincroniza eventos con [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (directamente a través del conector para [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)]) y registros y entradas de eventos (mediante los servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], como interacciones).

El flujo de datos que involucra a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] es el siguiente:
- Datos de entidad de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] para [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], mediante el conector de entrada regular de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], a fin de proporcionar contenido para la personalización del correo electrónico, la puntuación de clientes potenciales y la segmentación (principalmente contactos y cuentas, finalmente también clientes potenciales y eventos)
- Datos de entidad de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] mediante servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] para [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], a fin de proporcionar identificadores para interacciones e información detallada (recorrido del cliente, correos electrónicos de marketing, páginas de marketing)
- Interacciones de servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (seguimiento de correo electrónico, seguimiento del sitio web, progreso del recorrido del cliente)
- Interacciones de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] mediante servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (registros y entradas de eventos)
- [!INCLUDE[pn-insights](../includes/pn-insights.md)] (interacciones y KPI) de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] mediante servicios de [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] a [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] (principalmente recorrido del cliente y progreso de envío de correo electrónico, y resultados de puntuación de clientes potenciales)
- Aplicaciones de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (segmentación y widgets) de [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] directamente en elementos de la interfaz de usuario dedicados y de espacio aislado en formularios de [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]

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
> Para obtener más información acerca de otras ofertas de servicios de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)], vea [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)] (<https://azure.microsoft.com/support/trust-center/>).

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

Al usar [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], está activando la transferencia de datos de clientes a [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] para su posterior procesamiento. El uso de [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] para [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] puede requerir el cumplimiento de leyes de privacidad específicas. Dirija todas las preguntas al representante adecuado de la organización.

Actualmente, [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] es una versión preliminar pública y no ofrece el mismo nivel de compromisos de privacidad y seguridad que [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] o [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] Customer Engagement. [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] se ha compilado de forma nativa en los servicios de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] y se adhiere a los estándares de cumplimiento y seguridad para cada servicio de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] correspondiente. Para obtener más información, visite el Centro de confianza de [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)]: [https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] utiliza estos servicios de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight (Spark, Phoenix, HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Secret Store
- Centro de eventos de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Redis Cache
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- Supervisión de [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Metrics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Websites
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage
