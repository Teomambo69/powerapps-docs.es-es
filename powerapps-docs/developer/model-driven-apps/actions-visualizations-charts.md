---
title: Acciones en visualizaciones (gráficos) (aplicaciones basadas en modelos) | Microsoft Docs
description: 'Con los servicios web de Common Data Service para aplicaciones, puede realizar las siguientes acciones en las entidades de la visualización.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: c7eb3bdf-9d6f-9bcc-8114-4c3dc5be2976
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="actions-on-visualizations-charts"></a>Acciones en visualizaciones (gráficos)

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/actions-visualizations-charts -->

Con los servicios web de Common Data Service (CDS) para aplicaciones, puede realizar las siguientes acciones en las entidades de la visualización.  
  
## <a name="actions-on-organization-owned-visualizations"></a>Acciones en visualizaciones que pertenecen a una organización  
 Para realizar acciones sobre una visualización que pertenece a una organización (`SavedQueryVisualization`), debe tener el rol de administrador del sistema o personalizador del sistema. Puede realizar las siguientes acciones sobre una visualización que pertenece a una organización:  
  
- Crear, recuperar, actualizar y eliminar una visualización que pertenece a una organización. Más información: [Crear una visualización](create-visualization-chart.md)  
  
  > [!NOTE]
  >  Después de actualizar una visualización que pertenece a una organización, debe publicar los metadatos para hacerlos visibles en la organización mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest>. Como alternativa, cuando publica una entidad, todas las visualizaciones que pertenecen a una organización asociadas a la entidad se publican automáticamente.  
  
- Consultar y recuperar todas las visualizaciones que pertenecen a la organización asociadas a una entidad usando el atributo `SavedQueryVisualization.PrimaryEntityTypeCode`. Se pueden asociar varias visualizaciones que pertenecen a una organización a una sola entidad. Para obtener una lista de las entidades a las que puede asociar una visualización, consulte [Entidades admitidas para las visualizaciones](view-data-with-visualizations-charts.md#SupportedVisualizationEntities). Para obtener un ejemplo de código que muestra cómo recuperar todas las visualizaciones que pertenecen a la organización asociadas a una entidad, vea [Ejemplo: Recuperar todos los gráficos asociados a una entidad](/dynamics365/customer-engagement/developer/customize-dev/sample-retrieve-all-charts-attached-entity).
  
  > [!NOTE]
  >  No puede cambiar ni actualizar una visualización para asociarla a otra entidad una vez que haya creado la visualización. Esto implica que el atributo `SavedQueryVisualization.PrimaryEntityTypeCode` no es válido para la acción de actualización en la visualización que pertenece a la organización.
  
- Especificar una visualización que pertenece a una organización como visualización predeterminada para la entidad asociada estableciendo el atributo `SavedQueryVisualization.IsDefault` en `true`. Cuando establece una visualización que pertenece a una organización como visualización predeterminada para una entidad, la visualización se muestra de forma predeterminada cuando selecciona ver las visualizaciones de esta entidad en CDS for Apps.
  
  > [!NOTE]
  >  Mediante los servicios web de CDS for Apps, si establece una visualización que pertenece a una organización como predeterminada para una entidad que ya tiene otra visualización establecida como predeterminada, ambas visualizaciones se marcan como visualizaciones predeterminadas para la entidad.  Para establecer una visualización como visualización predeterminada para una entidad, asegúrese de que no se configura ninguna otra visualización como visualización predeterminada para la entidad.  
  
  Para obtener una lista de mensajes admitidos en la entidad de visualización que pertenece a la organización, vea [Entidad SavedQueryVisualization](../common-data-service/reference/entities/savedqueryvisualization.md).
  
## <a name="actions-on-user-owned-visualizations"></a>Acciones sobre visualizaciones que pertenecen a un usuario  
 Puede realizar las siguientes acciones en una visualización que pertenece a un usuario (`UserQueryVisualization`):  
  
- Crear, recuperar, actualizar y eliminar una visualización que pertenece a un usuario. Más información: [Crear una visualización](create-visualization-chart.md)  
  
- Consultar y recuperar todas las visualizaciones que pertenecen al usuario asociadas a una entidad usando el atributo `UserQueryVisualization.PrimaryEntityTypeCode`. Se pueden asociar varias visualizaciones que pertenecen a un usuario a una entidad. Para obtener una lista de las entidades a las que puede asociar una visualización, consulte [Entidades admitidas para las visualizaciones](view-data-with-visualizations-charts.md#SupportedVisualizationEntities).  
  
  > [!NOTE]
  >  No puede cambiar ni actualizar una visualización para asociarla a otra entidad una vez que haya creado la visualización. Esto implica que el atributo `UserQueryVisualization.PrimaryEntityTypeCode` no es válido para la acción de actualización en la visualización que pertenece al usuario.
  
- Cambiar la propiedad de una visualización que pertenece a un usuario asignándola a otro usuario o equipo mediante <xref:Microsoft.Crm.Sdk.Messages.AssignRequest>.  
  
- Recuperar el acceso que la entidad de seguridad especificada (usuario o equipo) tiene a una visualización que pertenece a un usuario mediante <xref:Microsoft.Crm.Sdk.Messages.RetrievePrincipalAccessRequest>. También puede recuperar todas las entidades de seguridad (usuarios o equipos) con acceso a una visualización que pertenece a un usuario, junto con sus derechos de acceso a la visualización que pertenece al usuario mediante <xref:Microsoft.Crm.Sdk.Messages.RetrieveSharedPrincipalsAndAccessRequest>.  
  
- Colaborar con otros usuarios y equipos en áreas específicas compartiendo con ellos una visualización que pertenece a un usuario mediante <xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>, <xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest> y <xref:Microsoft.Crm.Sdk.Messages.RevokeAccessRequest>.  
  
  Para obtener una lista de mensajes admitidos en la entidad de visualización que pertenece al usuario, vea [Entidad UserQueryVisualization](../common-data-service/reference/entities/userqueryvisualization.md).

### <a name="see-also"></a>Vea también  
 [Gráficos](view-data-with-visualizations-charts.md)   
 [Descripción de los gráficos: representación de datos y gráficos subyacentes](understand-charts-underlying-data-chart-representation.md)   
 [Crear un gráfico](create-visualization-chart.md)   
 [Gráficos de muestra](sample-charts.md)   
 [Ejemplo: Crear, recuperar, actualizar y eliminar (CRUD) un gráfico](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-chart)  <!--TODO: Need to find the topic in Powerapps repo to link --> [Ejemplo: recuperar todos los gráficos asociados a una entidad](/dynamics365/customer-engagement/developer/customize-dev/sample-retrieve-all-charts-attached-entity)   <!--TODO: Need to find the topic in Powerapps repo to link --> [Ejemplo: Asignar un gráfico a otro usuario](/dynamics365/customer-engagement/developer/customize-dev/sample-assign-chart-another-user)   <!--TODO: Need to find the topic in Powerapps repo to link --> [Entidad SavedQueryVisualization](../common-data-service/reference/entities/savedqueryvisualization.md)   
 [Entidad UserQueryVisualization](../common-data-service/reference/entities/userqueryvisualization.md)