---
title: Cuándo editar el archivo de personalizaciones (Common Data Service) | Microsoft Docs
description: El archivo customizations.xml que se exporta como parte de una solución no administrada se puede editar para realizar tareas específicas de personalización. Después de modificar el archivo puede comprimir el archivo editado así como los demás archivos exportados en la solución no administrada. Aplique los cambios importando esa solución modificada no administrada.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: cac303a6-70f9-3962-879a-fbf7fdc2364f
author: shmcarth
ms.author: jdaly
manager: ryjones
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e35d21cbb4dd9898ae7b535c052880fe61df647e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154944"
---
# <a name="when-to-edit-the-customizations-file"></a>Cuándo modificar el archivo de personalizaciones

El archivo customizations.xml que se exporta como parte de una solución no administrada se puede editar para realizar tareas específicas de personalización. Después de modificar el archivo puede comprimir el archivo editado así como los demás archivos exportados en la solución no administrada. Aplique los cambios importando esa solución modificada no administrada.  
  
 La edición de un archivo XML complejo como el archivo customizations.xml es mucho más fácil y menos propensa a errores si usa un programa diseñado para admitir la validación de esquema. Aunque es posible modificar este archivo con un editor de texto simple como Bloc de notas, no se recomienda a menos que esté muy familiarizado con la edición de este archivo. Para obtener más información, consulte [Editar el archivo de personalizaciones con la validación de esquema](../model-driven-apps/edit-customizations-xml-file-schema-validation.md). 
  
> [!IMPORTANT]
>  Un XML no válido o una definición incorrecta de los componentes de la solución puede causar errores que evitarán la importación de una solución no administrada modificada manualmente.  
  
## <a name="supported-tasks"></a>Tareas compatibles  
 Puede editar el archivo customization.xml para realizar las siguientes tareas.  
  
 **Editar la cinta de opciones**  
 Este documento describe el proceso de editar la cinta de opciones editando el archivo customization.xml directamente. Varias personas han creado editores de cinta de opciones que proporcionan una interfaz de usuario para que sea más sencillo modificar la cinta de opciones. El más conocido hasta el momento es el [Ribbon Workbench](https://www.develop1.net/public/rwb/ribbonworkbench.aspx). Para obtener soporte técnico para usar estos programas, póngase en contacto con el editor del programa.  
  
 Para obtener más información acerca de la edición de la cinta de opciones modificando el archivo customization.xml manualmente, consulte [Personalizar la cinta de opciones para Microsoft Dynamics 365](../model-driven-apps/customize-commands-ribbon.md).  
  
 **Editar el SiteMap**  
 El SDK describe el proceso de editar el mapa del sitio editando el archivo customization.xml directamente. Sin embargo, es recomendable usar el diseñador del mapa del sitio en Common Data Service para crear y actualizar los mapas del sitio. Más información: [Crear un mapa del sitio para una aplicación mediante el diseñador del mapa del sitio](../../maker/model-driven-apps/create-site-map-app.md)
  
 También puede utilizar uno de los editores del mapa del sitio desarrollados por la comunidad, como el [Editor de mapa del sitio XrmToolBox](https://www.xrmtoolbox.com/plugins/MsCrmTools.SiteMapEditor/).   
  
 Para obtener más información, consulte [Cambiar la navegación de la aplicación con el mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap) 
 
  
 **Editar FormXml**  
 FormXml se usa para definir formularios de entidad y paneles. El editor de formularios y el diseñador de paneles de la aplicación son las herramientas más utilizadas para este fin. La edición del archivo customizations.xml es un método alternativo. Para obtener más información, consulte [Personalizar los formularios de entidad de Microsoft Dynamics 365](../model-driven-apps/customize-entity-forms.md) y [Crear un panel](../model-driven-apps/create-dashboard.md).
  
 **Editar consultas guardadas**  
 Las definiciones de vistas para entidades se incluyen en el archivo customizations.xml y se pueden editar manualmente. El editor de vistas de la aplicación es la herramienta más utilizada para este fin. La edición del archivo customizations.xml es un método alternativo. Para obtener más información: consulte [Personalizar vistas de entidad en Microsoft Dynamics 365](../model-driven-apps/customize-entity-views.md).
  
 **Editar el archivo ISV.config**  
 En versiones anteriores de Dynamics 365 Common Data Service, ISV.Confg era la forma de agregar extensiones a la aplicación cliente así como otras opciones de configuración. En Microsoft Dynamics CRM 2011 y Microsoft Dynamics 365 Online, la cinta de opciones ofrece la forma de ampliar la aplicación. La única función restante en ISV.Config es personalizar la apariencia del calendario de servicios. Para obtener más información, consulte [Configuración de la apariencia del calendario de servicios](/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration)
  
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
 [Personalizar Microsoft Dynamics 365 y Microsoft Dynamics 365 (online)](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)   <!-- TODO Need to find the topic in powerapps repo-->
 [Referencia de XML de personalización](../model-driven-apps/customization-xml-reference.md) [Esquema de archivo de soluciones de personalización](customization-solutions-file-schema.md)  
 [Esquema central de cinta de opciones](../model-driven-apps/ribbon-core-schema.md) [Esquema de tipos de cinta de opciones](../model-driven-apps/ribbon-types-schema.md) [Esquema WSS de cinta de opciones](../model-driven-apps/ribbon-wss-schema.md)   
 [Esquema del mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/sitemap-schema) [Esquema XML de formulario](../model-driven-apps/form-xml-schema.md)   
 [Compatibilidad con el esquema para el archivo de personalización](../model-driven-apps/edit-customizations-xml-file-schema-validation.md)