---
title: Agregar características de informes a una aplicación basada en modelos
ms.custom: ''
ms.date: 08/16/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 847d132ba3d7ac3e928014fa61b04e0cb8a0ec7b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2885197"
---
# <a name="add-reporting-features-to-your-model-driven-app"></a>Agregar características de informes a una aplicación basada en modelos

Las aplicaciones Power Apps pueden incluir informes que proporcionen información de negocio útil al usuario. Estos informes se basan en SQL Server Reporting Services y proporcionan el mismo conjunto de características que están disponibles para los informes típicos de SQL Server Reporting Services.

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "Progress against goals standard report")

Los informes del sistema están disponibles para todos los usuarios. Los usuarios que crean o poseen informes pueden compartirlos con equipos o colegas específicos, o pueden ponerlos a disposición de la organización para que todos los usuarios puedan ejecutarlos. Estos informes usan consultas FetchXML que pertenecen a Common Data Service y recuperan datos para crear el informe. Los informes que crea en una aplicación de Power Apps son informes basados en Fetch.

> [!NOTE]
> Las características del informe no funcionan con las aplicaciones de lienzo o aplicaciones basadas en modelos que se ejecutan en dispositivos móviles, como tabletas y teléfonos. 

<!-- Reports can be built in either of the following ways.

- From a model-driven app using the report wizard. More information: [Create or edit a report using the Report Wizard](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
- Create custom reports using SQL Server Data Tools and Report Authoring Extensions. More information: [Reporting and Analytics Guide](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)  -->


## <a name="add-reporting-to-a-unified-interface-app"></a>Agregar informes a una aplicación de la interfaz unificada
Puede agregar funcionalidad de informes basados en Fetch a la aplicación de forma que los usuarios puedan ejecutar, compartir, crear y editar informes. Para ello, agregue la entidad de informe al mapa del sitio de su aplicación. 

1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y abra una aplicación existente para editar. 
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
> ![](media/report-feature-in-app.png "Report view")

## <a name="options-for-creating-new-reports"></a>Opciones para crear informes
Puede crear un informe nuevo de dos maneras diferentes:
- Utilice el Asistente para informes. Abra una aplicación basada en modelo que se habilitado para generar informes y ejecutar el Asistente para informes para crear un informe. El Asistente para informes puede crear informes de tablas y gráficos, incluidos los informes detallados e informes N superiores. Más información: [Crear o editar un informe con el Asistente para informes](../../user/create-report-with-wizard.md) 
- Usar la Extensión de creación de informes. Puede escribir nuevos o personalizar informes existentes de Reporting Services basados en Fetch con Visual Studio, SQL Server Data Tools y la Extensión de creación de informes. Más información: [Cree un nuevo informe mediante SQL Server Data Tools](/dynamics365/customer-engagement/analytics/create-a-new-report-using-sql-server-data-tools)

## <a name="report-visibility"></a>Visibilidad del informe
Los informes de entidad estándar, como por ejemplo el Informe de resumen de cuentas para la entidad de cuenta, están disponibles para todos los usuarios de la aplicación. Los usuarios que tengan informes pueden compartirlos con equipos o colegas específicos. Los administradores y personalizadores del sistema pueden poner los informes disponibles con visibilidad para toda la organización, para que todos los usuarios puedan usarlos. Para obtener información acerca de cómo compartir un informe, consulte [Compartir un informe con otros usuarios y equipos](../../user/work-with-reports.md#share-a-report-with-other-users-or-teams). 

## <a name="reports-in-solutions"></a>Informes en soluciones
Los informes son compatibles con las soluciones. Al agregar un informe como componente a una solución hace que esta sea una sola unidad de software que amplía la funcionalidad de Power Apps y la interfaz de usuario. Solo los informes que son visibles para la organización se pueden agregar a las soluciones.

Para saber si un informe puede verse en la organización: En la lista de informes, abra una aplicación basada en modelos, seleccione un informe y luego seleccione **Editar**. En la pestaña **Administración**, vea si **Visible por** está configurado en **Organización**. 

> [!div class="mx-imgBorder"] 
> ![](media/report-scope.png "Organization level report visibility")

Puede agregar, importar o exportar las instantáneas de informes como parte de una solución. En aplicaciones basadas en modelo, los informes, subinformes, categorías de informe, áreas de visualización de informes y tipos de registro relacionados con el informe se consideran como componentes de un conjunto de informes. Cuando se importa la actualización de una solución en modo sin sobrescritura, se omitirán las actualizaciones de la solución a un informe si se ha personalizado algún componente del informe.

## <a name="related-topics"></a>Temas relacionados
[Trabajar con informes](/powerapps/user/work-with-reports)<br/>
[Crear un informe con el Asistente para informes](/powerapps/user/create-report-with-wizard)<br/>
[Agregar un informe desde fuera de Power Apps](/powerapps/user/add-existing-report)<br/>
[Edición del filtro predeterminado de un informe](/powerapps/user/edit-report-filter)<br/>
[Informes de solución de problemas](/powerapps/user/troubleshoot-reports)
