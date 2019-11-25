---
title: Uso de Power BI con aplicaciones basadas en modelo | MicrosoftDocs
ms.custom: ''
ms.date: 10/14/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- admin
search.app:
- D365CE
- Powerplatform
ms.openlocfilehash: a05a163e8f946f35f0b3b52d8978b1bf9be4fe8b
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755968"
---
# <a name="use-power-bi"></a>Uso de Power BI

El servicio de nube de Power BI funciona con aplicaciones Common Data Service para proporcionar una solución de análisis de autoservicio. Power BI actualiza automáticamente los datos de aplicaciones que se muestran. Con Power BI Desktop o Microsoft Excel, Power Query para crear informes y Power BI para compartir panales y actualizar datos de aplicaciones basadas en modelo, los usuarios tienen una manera eficaz de trabajar con los datos de aplicaciones.  
  
<a name="PowerBIGetstarted"></a>   
## <a name="get-started-using-power-bi-with-model-driven-apps"></a>Introducción al uso de Power BI con aplicaciones basadas en modelo  
 
Los paquetes de contenidos de aplicaciones de Dynamics 365 para Power BI permiten acceder fácilmente y analizar los datos en aplicaciones basadas en modelo en Dynamics 365 (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 Field Service, Dynamics 365 Marketing, Dynamics 365 Project Service Automation).  
  
 Para crear un panel de Power BI con un paquete de contenido, siga estas instrucciones.  
  
1. Si aún no lo ha hecho, [regístrese en Power BI](https://powerbi.com/).  
  
2. Una vez que haya iniciado sesión en Power BI, en el área **Conjuntos de datos** seleccione **Obtener datos**, en **Servicios** seleccione **Obtener** y, a continuación, seleccione uno de los siguientes paquetes de contenido.  
  
   - **Análisis de ventas para Dynamics 365**  
  
   - **Análisis de servicio al cliente for Dynamics 365**  
  
   - **Microsoft Dynamics 365 - Social Engagement**  
  
3. Para los paquetes de contenido de análisis de ventas y de análisis del servicio, escriba la dirección URL de la instancia, como *<https://OrganizationName.crm.dynamics.com>*, donde *OrganizationName* es el nombre de la organización de su instancia, y seleccione **Siguiente**.  
  
   > [!NOTE]
   >  Si el centro de datos se encuentra fuera de Norteamérica el nombre del dominio de crm.dynamics.com puede ser distinto, como crm2.dynamics.com, crm3.dynamics.com, crm4.dynamics.com, etc. Para buscar el nombre de dominio, en la aplicación web aplicaciones vaya a **Configuración** > **Personalizacones** > **Recursos de desarrollador**. Las direcciones URL enumeradas indicarán el nombre de dominio correcto.  
  
    Para el paquete de contenido de marketing, especifique la dirección URL como *<https://OrganizationName.marketing.dynamics.com/analytics>*, donde *OrganizationName* es el nombre de la organización de su instancia de Dynamics 365 y seleccione **Siguiente**.  
  
4. En **Método de autenticación**, seleccione **oAuth2**.  
  
5. Se importan los datos de la instancia y varias visualizaciones pasan a estar disponibles.  
  
> [!TIP]
>  Si el paquete de contenido que selecciona no se abre en el explorador web, en el panel izquierdo de su espacio de trabajo de Power BI, haga clic en el paquete de contenido en **Paneles**.  
  
### <a name="content-packs-available-for-download"></a>Contenido del paquete disponible para descarga.  
 Los paquetes de contenido de Dynamics 365 admiten las entidades predefinidas predeterminadas de la aplicación. Sin embargo, puede personalizar los siguientes paquetes de contenido descargando el archivo .PBIX y usando después Power BI Desktop para personalizar el paquete de contenido antes de cargarlo al servicio de Power BI.  
  
- [Descargar el .PBIX de Dynamics CRM Online Sales Manager](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
- [Descargar el analizador de procesos .PBIX del administrador del servicio de aplicaciones Microsoft Dynamics 365 for Customer Engagement (onlie)](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  La Power BI Report Template para Connected Field Service permite que los usuarios publiquen el informe de Power BI que muestra el latido activo de los dispositivos conectados.  
  
- [Descargar Power BI Report Template Connected Field Service for Dynamics 365 for Customer Engagement](https://download.microsoft.com/download/E/B/5/EB5ED97A-A36A-4CAE-8C04-333A1E463B4F/PowerBI%20Report%20Template%20for%20Connected%20Field%20Service%20for%20Microsoft%20Dynamics%20365.pbix)  
  
 Para obtener información acerca de cómo personalizar los paquetes de contenido, consulte [Personalizar agrupaciones de contenido de Power BI](customize-power-bi-content-packs.md). 
  
<a name="BPI_embed"></a>   
## <a name="embed-power-bi-visualizations-on-personal-dashboards"></a>Insertar visualizaciones de Power BI en paneles personales  
 Para que los usuarios puedan insertar visualizaciones de Power BI en paneles personales, debe habilitarse la configuración para toda la organización.  
  
> [!NOTE]
>  De forma predeterminada, insertar visualizaciones de Power BI está deshabilitado y debe habilitarse para que los usuarios puedan insertarlas en paneles personales.  
  
### <a name="enable-power-bi-visualizations-in-the-organization"></a>Habilite visualizaciones Power BI en la organización  
  
1. Inicie sesión en las aplicaciones Dynamics 365 como un usuario con el rol de seguridad de administrador del sistema.  
  
2. Vaya a **Configuración** > **Administración** > **Configuración del sistema**.  
  
3. En la pestaña **Informes** en la opción **Permitir la inserción de ventanas de Power BI**, seleccione **Sí** para habilitarla o **No** para deshabilitarla.  
  
4. Seleccione **Aceptar**.  
  
Para obtener más información sobre cómo agregar iconos de Power BI a paneles personales en aplicaciones, consulte [Insertar iconos de Power BI en el panel personal](/powerapps/user/add-powerbi-dashboards#embed--power-bi-tiles-on-your-personal-dashboard).  
  
Para obtener más información sobre cómo agregar paneles de Power BI a paneles personales en aplicaciones, consulte [Agregar o editar visualizaciones de Power BI en el personal](/powerapps/user/add-powerbi-dashboards).  
  
<a name="CRMOnline_PBIDesktop"></a>   
## <a name="use-power-bi-desktop-to-connect-directly-to-your-instance"></a>Use Power BI Desktop para conectarse directamente a su instancia.  
 Puede conectarse a su instancia con Power BI Desktop para crear informes y paneles de aplicaciones personalizados para usarlos con el servicio de Power BI.  
  
### <a name="requirements"></a>Requisitos  
  
- Registro del servicio de Power BI  
  
- Power BI Desktop  
  
- Instancia de Dynamics 365  
  
### <a name="connect"></a>Conectar  
  
1. Iniciar Power BI Desktop.  
  
2. En la pestaña Inicio, seleccione **Obtener datos**y, a continuación, seleccione **Más**.  
  
3. En la lista Obtener datos, seleccione **Dynamics 365 Online**.  
  
4. Escriba la dirección URL del extremo OData de Dynamics 365. Debe ser similar a esta dirección URL, donde *nombreDeOrganización* es el nombre de la organización de **v9.0** es la versión. Seleccione **Aceptar**.  
  
    https://<em>Nombredeorganización</em>.api.crm.dynamics.com/api/data/*v9.0*  
  
> [!IMPORTANT]
> Para obtener más información sobre las versiones del extremo, consulte [Dirección URL de API de web y versiones](/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors#web-api-url-and-versions).
 
> [!TIP]
>  Puede encontrar la dirección URL del extremo de OData. Vaya a **Configuración** > **Personalizaciones** > **Recursos de desarrollador** y busque la dirección URL en la **API web de la instancia**.  
  
5. En el cuadro de diálogo Acceso a una fuente OData, seleccione **Cuenta profesional** y, a continuación, seleccione **Conectar**.  
  
   > [!NOTE]
   >  Si no ha iniciado sesión en su instancia, seleccione **Iniciar sesión** en el cuadro de diálogo Acceso a una fuente OData antes de hacer seleccionar Conectar.  
  
6. Las tablas de entidad de base de datos de la organización aparecen en la ventana del navegador de Power BI Desktop. Puede seleccionar entidades predeterminadas y personalizadas. Para obtener más información acerca de la creación de informes con Power BI Desktop, consulte [Compatibilidad con Power BI: vista de informe en Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-report-view/).  
  
   ![Seleccionar tabla de entidades](media/pbi-select-entity-table.PNG "Seleccionar tabla de entidades")  
  
   > [!TIP]
   >  Puede usar pasos similares para conectarse a Dynamics 365 con Excel Power Query seleccionando **De otras fuentes** en la pestaña **Power Query** de Excel.  
  

