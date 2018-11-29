---
title: Cuándo editar archivos de personalizaciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Este tema trata de cuándo editar archivos de personalizaciones archivo y distintas formas posibles de hacerlo
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="when-to-edit-the-customizations-file"></a>Cuándo modificar el archivo de personalizaciones

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/when-edit-customization-file -->

El archivo customizations.xml que se exporta como parte de una solución no administrada se puede editar para realizar tareas específicas de personalización. Después de modificar el archivo puede comprimir el archivo editado así como los demás archivos exportados en la solución no administrada. Aplique los cambios importando esa solución modificada no administrada.  
  
 La edición de un archivo XML complejo como el archivo customizations.xml es mucho más fácil y menos propensa a errores si usa un programa diseñado para admitir la validación de esquema. Aunque es posible modificar este archivo con un editor de texto simple como Bloc de notas, no se recomienda a menos que esté muy familiarizado con la edición de este archivo. Para obtener más información, consulte [Editar el archivo de personalizaciones con la validación de esquema](edit-customizations-xml-file-schema-validation.md).  
  
> [!IMPORTANT]
>  Un XML no válido o una definición incorrecta de los componentes de la solución puede causar errores que evitarán la importación de una solución no administrada modificada manualmente.  
  
## <a name="supported-tasks"></a>Tareas compatibles  
 Puede editar el archivo customization.xml para realizar las siguientes tareas.  
  
 **Editar la cinta de opciones**  
 Este documento describe el proceso de editar la cinta de opciones editando el archivo customization.xml directamente. Varias personas han creado editores de cinta de opciones que proporcionan una interfaz de usuario para que sea más sencillo modificar la cinta de opciones. El más conocido hasta el momento es el [Ribbon Workbench](https://www.develop1.net/public/rwb/ribbonworkbench.aspx). Para obtener soporte técnico para usar estos programas, póngase en contacto con el editor del programa.  
  
 Para obtener más información acerca de la edición de la cinta de opciones modificando el archivo customization.xml manualmente, consulte [Personalizar la cinta de opciones](customize-commands-ribbon.md).  
  
 **Editar el SiteMap**  
 El SDK describe el proceso de editar el mapa del sitio editando el archivo customization.xml directamente. Sin embargo, es recomendable usar el diseñador del mapa del sitio en aplicaciones basadas en modelos para crear y actualizar los mapas del sitio. Más información: [Tutorial: Crear un mapa del sitio para una aplicación basada en modelos usando el diseñador de mapas del sitio](../../maker/model-driven-apps/create-site-map-app.md)  
  
 También puede utilizar uno de los editores del mapa del sitio desarrollados por la comunidad, como el [Editor de mapa del sitio XrmToolBox](https://www.xrmtoolbox.com/plugins/MsCrmTools.SiteMapEditor/).   
  
 Para obtener más información, consulte [Cambiar la navegación de la aplicación con el mapa del sitio](/developer/customize-dev/change-application-navigation-using-sitemap.md)  
  
 **Editar FormXml**  
 FormXml se usa para definir formularios de entidad y paneles. El editor de formularios y el diseñador de paneles de la aplicación son las herramientas más utilizadas para este fin. La edición del archivo customizations.xml es un método alternativo. Para obtener más información, consulte [Personalizar los formularios de entidad](customize-entity-forms.md) y [Crear un panel](create-dashboard.md).  
  
 **Editar consultas guardadas**  
 Las definiciones de vistas para entidades se incluyen en el archivo customizations.xml y se pueden editar manualmente. El editor de vistas de la aplicación es la herramienta más utilizada para este fin. La edición del archivo customizations.xml es un método alternativo. Para obtener más información: consulte [Personalizar vistas de entidad](customize-entity-views.md).  
  
 **Editar el archivo ISV.config**  
  En CDS para aplicaciones, la cinta de opciones ofrece la forma de ampliar la aplicación. La única función restante en ISV.Config es personalizar la apariencia del calendario de servicios. Para obtener más información, consulte [Configuración de la apariencia del calendario de servicios](/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration).  
  
## <a name="unsupported-tasks"></a>Tareas no compatibles  
 La definición de otros componentes de la solución editando el archivo customizations.xml exportado no se admite. Esto incluye lo siguiente:  
  
-   Entidades  
  
-   Atributos  
  
-   Relaciones entre entidades  
  
-   Mensajes de la entidad  
  
-   Conjuntos de opciones  
  
-   Recursos web  
  
-   Procesos (flujos de trabajo)  
  
-   Ensamblados de complementos  
  
-   Pasos de procesamiento de mensajes de SDK  
  
-   Extremos del servicio  
  
-   Informes  
  
-   Roles de conexión  
  
-   Plantillas de artículo  
  
-   Plantillas de contrato  
  
-   Plantillas de correo electrónico  
  
-   Plantillas de combinación de correspondencia  
  
-   Roles de seguridad  
  
-   Perfiles de seguridad de campo  
  

### <a name="see-also"></a>Vea también  
 [Referencia de XML de personalización](customization-xml-reference.md)   
 [Esquema de archivo de soluciones de personalización](../common-data-service/customization-solutions-file-schema.md)   
 [Esquema central de cinta de opciones](ribbon-core-schema.md) [Esquema de tipos de cinta de opciones](ribbon-types-schema.md) [Esquema WSS de cinta de opciones](ribbon-wss-schema.md)   
 [Esquema XML de formulario](form-xml-schema.md)   
 [Compatibilidad con el esquema para el archivo de personalización](edit-customizations-xml-file-schema-validation.md)
