---
title: Agregar informes a una aplicación basada en modelos
ms.custom: ''
ms.date: 06/24/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-reporting-to-your-model-driven-app"></a>Agregar informes a una aplicación basada en modelos

Las aplicaciones PowerApps pueden incluir informes que proporcionen información de negocio útil al usuario. Estos informes se basan en SQL Server Reporting Services y proporcionan el mismo conjunto de características que están disponibles para los informes típicos de SQL Server Reporting Services.

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "Informe estándar de progreso en relación con los objetivos")

Los informes del sistema están disponibles para todos los usuarios. Los usuarios que crean o poseen informes pueden compartirlos con equipos o colegas específicos, o pueden ponerlos a disposición de la organización para que todos los usuarios puedan ejecutarlos. Estos informes utilizan consultas FetchXML que son propiedad de aplicaciones de Common Data Service y Dynamics 365 for Customer Engagement y recuperan datos para crear el informe. Los informes que crea en una aplicación de PowerApps son informes basados en Fetch.

> [!NOTE]
> Las características del informe no funcionan con las aplicaciones de lienzo o aplicaciones basadas en modelos que se ejecutan en dispositivos móviles, como tabletas y teléfonos. 

Se pueden generar informes de cualquiera de las maneras siguientes:

- Desde una aplicación basada en modelos mediante el asistente para informes. Más información: [Crear o editar un informe con el Asistente para informes](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
<!-- From a model-driven app using an advanced find query. To do this, you build an advanced find query and then select **Download as FetchXML**. Next, from the reports area select **New**, for **Report Type** select **Existing File**, select **Choose File** open the xml file, fill in the required fields, and save the report. More information: [Add a report](/dynamics365/customer-engagement/basics/add-existing-report) -->
- Crear informes personalizados con SQL Server Data Tools y Extensiones de creación de informes. Más información: [Manual de informes y análisis](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)


## <a name="add-reporting-to-a-unified-interface-app"></a>Agregar informes a una aplicación de la interfaz unificada
Puede agregar funcionalidad de informes basados en Fetch a la aplicación de forma que los usuarios puedan ejecutar, compartir, crear y editar informes. Para ello, agregue la entidad de informe al mapa del sitio de su aplicación. 

1. Inicie sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y abra una aplicación existente para editar. 
2. En el diseñador de aplicaciones, seleccione ![Icono de lápiz para editar el mapa del sitio](media/ccf-pencil-icon.png) junto a **Mapa del sitio**. 
3. En el Diseñador del mapa del sitio, seleccione **Agregar** y después seleccione **Área**. 
4. En el cuadro **Título**, escriba un nombre para el título del área, como *Informes*. 
5. Seleccione el área que nombró en el paso anterior, seleccione **Agregar**, seleccione **Grupo** y, a continuación en el cuadro **Título** del grupo escriba un nombre para el título del grupo, como *Informes*. 
6. Seleccione el grupo que nombró en el paso anterior, seleccione **Agregar**, seleccione **Subárea** y después incluya las propiedades siguientes: 

   - **Tipo**. Seleccione **Entidad**.
   - **Entidad**. En la lista de entidades, seleccione la entidad **Informe**.  
   - **Título**. Escriba un título descriptivo, como *Informes*.

      ![Agregar entidad de informe al mapa del sitio](media/report-entity-sitemap.png)

7. Seleccione **Guardar y cerrar** para cerrar al diseñador de aplicaciones. 


8. En el diseñador de aplicaciones, seleccione **Guardar** y, después, seleccione **Publicar**.


Ahora la aplicación muestra un área **Informes** donde los usuarios pueden ver, ejecutar, asignar, compartir y editar los informes a los que tienen permiso así como crear informes mediante el Asistente para informes. 

> [!div class="mx-imgBorder"] 
> ![](media/report-feature-in-app.png "Ver informe")

### <a name="see-also"></a>Vea también
[Ejecución de informes](/dynamics365/customer-engagement/basics/run-report)
