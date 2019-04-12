---
title: Examinar los metadatos de la organización (Common Data Service) | Microsoft Docs
description: Use el explorador de metadatos de la entidad para ver las entidades y sus propiedades en Dynamics 365 Customer Engagement. El Explorador de metadatos de la entidad es una solución administrada que puede descargar e instalar en su organización.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="browse-the-metadata-for-your-environment"></a>Examinar los metadatos del entorno

Use el explorador de metadatos de la entidad para ver las entidades y sus propiedades en Common Data Service. El Explorador de metadatos de la entidad es una solución administrada que puede descargar mediante los vínculos siguientes.


|                                                                                               Versión                                                                                                |                                                                                     Download                                                                                      |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Common Data Service | [Descargas de Microsoft: MetadataBrowser_3_0_0_5_managed.zip](http://download.microsoft.com/download/8/E/3/8E3279FE-7915-48FE-A68B-ACAFB86DA69C/MetadataBrowser_3_0_0_5_managed.zip) |

Después de descargar la solución, debe instalarla. Para obtener información sobre cómo instalar una solución administrada, consulte [Importar, actualizar, y exportar soluciones](/dynamics365/customer-engagement/developer/customize/import-update-export-solutions).  

## <a name="open-as-an-app"></a>Abrir como aplicación
Common Data Service se configura como aplicación. Después de instalar la solución **Examinador de metadatos de la entidad**, busque la aplicación **Metadata Tools** y ábralo. **Entidades** es la vista predeterminada. En el área de navegación **Herramientas**, puede seleccionar **Metadatos de la entidad** para inspeccionar las entidades individuales.

## <a name="open-from-the-solution-configuration-page"></a>Abrir desde la página de configuración de la solución
Para versiones anteriores debe usar los siguientes pasos, pero también funcionan para la última versión.  

Después de instalar la solución del **Explorador de metadatos de la entidad**, abra la solución administrada haciendo doble clic en la fila en la lista de soluciones y vea la página **Configuración** para ver información sobre el Explorador de metadatos de la entidad y los botones para iniciar dos vistas distintas.
- **Examinador de metadatos** es equivalente a la vista **Entidades** en la aplicación.
- **Examinador de metadatos de la entidad** es equivalente a la vista **Metadatos de la entidad** en la aplicación.

## <a name="entities-view"></a>Vista de entidades
Puede realizar las siguientes acciones:

- **Ver detalles de la entidad**: Seleccione una entidad para ver mediante la vista **Metadatos de la entidad**.
- **Editar entidad**: Abra el formulario de entidad seleccionada en la organización predeterminada, si la entidad lo permite.
- **Búsqueda de texto**: Realice una búsqueda de texto para filtrar las entidades mostradas mediante las siguientes propiedades de entidad: <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.SchemaName>, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.LogicalName>, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DisplayName>, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ObjectTypeCode> o <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId>.
- **Filtrar entidades**: Defina criterios sencillos para ver un subconjunto de entidades. Todos los criterios evalúan con la lógica AND.
- **Filtrar propiedades**: Filtre las propiedades mostradas para la entidad mostrada. Hay aproximadamente 100 propiedades en la lista. Use esta opción para seleccionar solamente las que le interesan.

## <a name="entity-metadata-view"></a>Vista Metadatos de entidad

Puede realizar las siguientes acciones para una sola entidad:

- **Entidad**: Cambie la entidad que desea ver.
- **Propiedades**: Vea todas las propiedades de la entidad y filtre las propiedades mostradas.

    - **Editar entidad**: Abra el formulario de edición de la entidad seleccionada en la organización predeterminada, si la entidad lo permite.
    - **Filtrar propiedades**: Filtre las propiedades mostradas para la entidad mostrada. Hay aproximadamente 100 propiedades en la lista. Use esta opción para seleccionar solamente las que le interesan.

- **Atributos**: Vea los atributos de la entidad en una vista maestra o detallada. Con esta vista puede:

    - **Editar atributo**: Abra el formulario de atributos seleccionado en la organización predeterminada, si el atributo lo permite.
    - **Búsqueda de texto**: Realice una búsqueda de texto para filtrar los atributos mostrados mediante las siguientes propiedades de atributo: <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName>, <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LogicalName>, <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.DisplayName> o <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId>.
    - **Filtrar atributos**: Filtre los atributos por cualquier valor de propiedades de atributos.
    - **Filtrar propiedades**: Filtre las propiedades mostradas para el atributo seleccionado.

- **Teclas**: Si las teclas alternativas se habilitan para una entidad, puede examinar cómo están configuradas.

- **Relaciones**: Vea los tres tipos de relaciones de entidad: uno a varios, varios a uno y varios a varios. Con estas vistas puede:  
    - **Editar relación**: Abra el formulario de relaciones seleccionado en la organización predeterminada, si la relación lo permite.  
    - **Búsqueda de texto**: Realice una búsqueda de texto para filtrar las relaciones mostradas con valores adecuados para el tipo de relación.  
    - **Filtrar propiedades**: Filtre la relación por cualquier valor de las propiedades de la relación.

- **Privilegios**: Vea los privilegios de la entidad. Con esta vista puede:  
    - Filtrar el privilegio mostrado mediante la propiedad `PrivilegeId`.

> [!NOTE]
> Al ver las propiedades de detalle de la entidad, verá que muchas propiedades complejas se pueden expandir. El valor más útil se muestra con un vínculo que permite cambiar a una vista más detallada. La vista detallada refleja la estructura de los datos tal como se recuperaría mediante programación. La vista detallada también revela otros datos relevantes que se pueden recuperar en la misma área, como por ejemplo, si existe alguna etiqueta localizada para las propiedades **Nombre para mostrar**.

> [!TIP]
> Para copiar texto de la página, simplemente seleccione el texto y use el método abreviado de teclado Ctrl+C o el comando **Copiar** del menú contextual.

## <a name="community-tools"></a>Herramientas de la Comunidad

**Explorador de metadatos** es una herramienta desarrollada por Comunidad XrmToolbox para Common Data Service. Consulte el tema [herramientas para desarrolladores](developer-tools.md) para comunidad de herramientas desarrolladas.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Common Data Service y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Vea también

 [Herramientas para desarrolladores de Common Data Service](developer-tools.md)<br />
 [Personalizar metadatos de entidad](customize-entity-metadata.md)<br />
 