---
title: Seguimiento de las dependencias de los componentes de la solución (Common Data Service) | Microsoft Docs
description: Las dependencias de los componentes de la solución ayudan a garantizar una experiencia confiable cuando trabaja con soluciones. Pueden verse en la aplicación haciendo clic en Mostrar dependencias
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 922dc4affafcd6232857dfd99f8d552812848de3
ms.sourcegitcommit: 94d66a2e1bc7f45f1a8ae97cc5ec4fce89aefdee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2020
ms.locfileid: "3325656"
---
# <a name="dependency-tracking-for-solution-components"></a>Seguimiento de las dependencias de los componentes de la solución

Las soluciones están hechas de componentes de soluciones. Usará el área **Soluciones** en Common Data Service para crear o agregar componentes de la solución. Puede realizar estas acciones mediante programación usando el mensaje de <xref:Microsoft.Crm.Sdk.Messages.AddSolutionComponentRequest> o cualquier mensaje que cree o actualice componentes de la solución que incluyen un parámetro de `SolutionUniqueName`.  
  
 Los componentes de la solución a menudo dependen de otros componentes. No puede eliminar cualquier componente de la solución que tenga dependencia de otro componente de la solución. Por ejemplo, una cinta personalizada requiere normalmente recursos web de imagen o de script para mostrar iconos y realizar acciones mediante scripts. Mientras la cinta personalizada esté en la solución, serán necesarios los recursos web específicos que use. Para poder eliminar los recursos web debe quitar las referencias a ellos en la cinta personalizada. Estas dependencias de componentes de solución se pueden ver en la aplicación haciendo clic en **Mostrar dependencias**.  
  
 Este tema describe los tipos de componentes de la solución que se puede incluir en sus soluciones y cómo dependen unos de otros.  
  
<a name="bkmk_SolutionComponents"></a>   

## <a name="all-solution-components"></a>Todos los componentes de la solución  
 La lista completa de tipos de componentes de soluciones disponibles se encuentra en el conjunto de opciones globales del sistema `componenttype`. El intervalo de valores admitidos para esta propiedad está disponible al incluir el archivo `OptionSets.cs` o `OptionSets.vb` en el proyecto. Sin embargo, muchos de los tipos de componentes de la solución que se muestran aquí son solamente para uso interno y la lista no proporciona información sobre las relaciones entre los componentes de la solución.  
  
<a name="BKMK_SolutionComponentDependencies"></a>   

## <a name="solution-component-dependencies"></a>Dependencias de los componentes de solución  
 Las dependencias de los componentes de la solución ayudan a garantizar una experiencia confiable cuando trabaja con soluciones. Evitan que las acciones que normalmente se realizan incumplan de forma accidental las personalizaciones definidas en una solución. Estas dependencias son las que permiten que una solución administrada se instale y desinstale simplemente importando o eliminando una solución.  
  
 El marco de soluciones realiza un seguimiento automático de las dependencias de los componentes de la solución. Cada función de un componente de la solución calcula automáticamente las dependencias con otros componentes del sistema. La información de dependencia se usa para mantener la integridad del sistema y evitar operaciones que pueden llevar a un estado incoherente.  
  
 Como resultado del seguimiento de la dependencia se aplican los siguientes comportamientos:  
  
- Se evita la eliminación de un componente si otro componente del sistema depende de él.  
  
- La exportación de una solución advierte al usuario si hay componentes que faltan que pueden provocar un error al importar la solución en otro sistema.  
  
   Las advertencias durante la exportación pueden ignorarse si el desarrollador de la solución pretende que esta se instale únicamente en una organización donde se espera que existan componentes dependientes. Por ejemplo, cuando se crea una solución que se ha diseñado para instalarse sobre una solución "base" instalada anteriormente.  
  
- La importación de una solución es incorrecta si todos los componentes necesarios no se incluyen en la solución y tampoco existen en el sistema de destino.  
  
  -   Además, al importar una solución administrada todos los componentes requeridos deben coincidir con el tipo de paquete de la solución. Un componente de una solución administrada puede depender solo de otro componente administrado.  
  
  Existen tres tipos de dependencias de componentes de solución:  
  
  **Elemento interno de la solución**  
  Las dependencias internas las administra Common Data Service. Existen cuando un componente de la solución en particular no puede existir sin otro componente de la solución.  
  
  **Publicado**  
  Las dependencias públicas se crean cuando dos componentes de la solución se relacionan mutuamente y luego se publican. Para eliminar este tipo de dependencia, debe eliminarse la asociación y, a continuación, se deben volver a publicar las entidades.  
  
  **Sin publicar**  
  Las dependencias sin publicar se aplican a la versión sin publicar de un componente de la solución publicable se va a actualizar. Una vez que se publique el componente de la solución, se convierte en una dependencia publicada.  
  
  Las dependencias internas de la solución son dependencias en las que las acciones con un componente de la solución necesitan una acción para otro componente de la solución. Por ejemplo, si se elimina una entidad, se espera que se eliminen con ella todos sus atributos. También se eliminarán todas las relaciones con otras entidades.  
  
  Sin embargo, una dependencia interna puede llevar a una dependencia publicada y seguir necesitando intervención manual. Por ejemplo, si incluye un campo de búsqueda en un formulario de entidad y luego elimina la entidad primaria de la relación, no podrá completar esa eliminación hasta que quite el campo de búsqueda del formulario de entidad relacionado y luego publique el formulario.  
  
  Cuando realiza acciones mediante programación con soluciones, puede usar los mensajes relacionados con la entidad `Dependency`. Consulte [Entidad de dependencia](/reference/entities/dependency.md) para ver los mensajes que puede usar para identificar las dependencias que pueden existir antes de eliminar un componente o desinstalar una solución.  
  
<a name="BKMK_CheckForSolutionComponentDependencies"></a>   
## <a name="check-for-solution-component-dependencies"></a>Buscar dependencias de los componentes de la solución  
 Cuando edite soluciones es posible que descubra que no puede eliminar un componente de la solución porque tiene una dependencia publicada con otro. O bien, es posible que no pueda desinstalar una solución administrada porque uno de los componentes de la solución administrada se ha utilizado en una personalización de otra solución no administrada.  
  
 La siguiente tabla muestra los mensajes que puede usar para recuperar datos de dependencias de componentes de la solución.  
  
|Mensaje|Descripción|  
|-------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveDependentComponentsRequest>|Devuelve una lista de las dependencias de los componentes de la solución que dependen directamente de un componente de la solución.<br /><br /> Por ejemplo, cuando se usa este mensaje para un componente de la solución global de conjunto de opciones, los registros de dependencia para los componentes de la solución que representan cualquier atributo de conjunto de opciones que hace referencia al componente de la solución global de conjunto de opciones se devuelven.<br /><br /> Cuando se usa este mensaje para el registro de componentes de la solución para la entidad de cuenta, los registros de dependencia para todos los componentes de la solución que representan atributos, vistas y formularios usados para esa entidad se devuelven.|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveRequiredComponentsRequest>|Devuelve una lista de las dependencias para los componentes de la solución de las que depende directamente otro componente de la solución. Este mensaje proporciona el reverso del mensaje de `RetrieveDependentComponentsRequest`.|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveDependenciesForDeleteRequest>|Devuelve una lista de todas las dependencias para los componentes de la solución que podrían evitar la eliminación de un componente de la solución.|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveDependenciesForUninstallRequest>|Devuelve una lista de todas las dependencias para los componentes de la solución que podrían evitar la desinstalación de una solución administrada.|  
  
<a name="BKMK_RootSolutionComponents"></a>   
## <a name="common-solution-components"></a>Componentes comunes de la solución  
 Estos son los componentes de la solución que se muestran en la aplicación y los componentes con lo que trabajará directamente al agregar o quitar componentes de la solución con la página de la solución. Cada uno de los demás tipos de componentes de la solución dependerán de uno o más de estos componentes de la solución para existir.  
  
||||  
|-|-|-|  
|[Cintas de opciones de la aplicación (RibbonCustomization)](dependency-tracking-solution-components.md#BKMK_RibbonCustomization)|[Entidad (Entity)](dependency-tracking-solution-components.md#BKMK_Entity)|[Informe (Report)](dependency-tracking-solution-components.md#BKMK_Report)|  
|[Plantilla de artículo (KBArticleTemplate)](dependency-tracking-solution-components.md#BKMK_KBArticleTemplate)|[Perfil de seguridad de campo (FieldSecurityProfile)](dependency-tracking-solution-components.md#BKMK_FieldSecurityProfile)|[Paso de procesamiento del mensaje del SDK (SDKMessageProcessingStep)](dependency-tracking-solution-components.md#BKMK_SDKMessageProcessingStep)|  
|[Rol de conexión (ConnectionRole)](dependency-tracking-solution-components.md#BKMK_ConnectionRole)|[Plantilla de combinación de correspondencia (MailMergeTemplate)](dependency-tracking-solution-components.md#BKMK_MailMergeTemplate)|[Rol de seguridad (rol)](dependency-tracking-solution-components.md#BKMK_Role)|  
|[Plantilla de contrato (ContractTemplate)](dependency-tracking-solution-components.md#BKMK_ContractTemplate)|[Conjunto de opciones (OptionSet)](dependency-tracking-solution-components.md#BKMK_OptionSet)|[Extremo de servicio (ServiceEndpoint)](dependency-tracking-solution-components.md#BKMK_ServiceEndpoint)|  
|[Panel o formulario de entidad (SystemForm)](dependency-tracking-solution-components.md#BKMK_SystemForm)|[Ensamblado de complemento (PluginAssembly)](dependency-tracking-solution-components.md#BKMK_PluginAssembly)|[Mapa del sitio (SiteMap)](dependency-tracking-solution-components.md#BKMK_SiteMap)|  
|[Plantilla de correo electrónico (EmailTemplate)](dependency-tracking-solution-components.md#BKMK_EmailTemplate)|[Proceso (flujo de trabajo)](dependency-tracking-solution-components.md#BKMK_Workflow)|[Recurso web (WebResource)](dependency-tracking-solution-components.md#BKMK_WebResource)|  
  
<a name="BKMK_RibbonCustomization"></a>   
### <a name="application-ribbons-ribboncustomization"></a>Cintas de opciones de la aplicación (RibbonCustomization)  
 Personalizaciones de cinta de opciones para las plantillas de la cinta de opciones de la entidad y la cinta de opciones de la aplicación. Las cintas de opciones de la aplicación no incluyen definiciones de cintas en el nivel de la entidad o del formulario.  
  
 Las cintas de opciones de la aplicación personalizadas con frecuencia tienen publicadas dependencias de recursos web. Los recursos web se usan para definir iconos botón y funciones JavaScript para controlar cuándo se muestran los elementos de la cinta de opciones o qué acciones se realizan cuando se usa un determinado control de la cinta de opciones. Las dependencias se crean únicamente cuando las definiciones de la cinta usan la directiva de `$webresource:` para asociar el recurso web a la cinta de opciones. Más información: [Directiva $webresource](/dynamics365/customer-engagement/developer/web-resources#BKMK_WebResourceDirective).  
  
<a name="BKMK_KBArticleTemplate"></a>   
### <a name="article-template-kbarticletemplate"></a>Plantilla de artículo (KBArticleTemplate)  
 La plantilla que contiene los atributos estándar de un artículo. Siempre existe una dependencia interna entre la plantilla de artículo y la entidad KbArticle.  
  
<a name="BKMK_ConnectionRole"></a>   
### <a name="connection-role-connectionrole"></a>Rol de conexión (ConnectionRole)  
 Rol que describe una relación entre dos registros. Cada rol de conexión define qué tipos de registros de la entidad se pueden vincular con el rol de conexión. Se crea una dependencia publicada entre el rol de conexión y la entidad.  
  
<a name="BKMK_ContractTemplate"></a>   
### <a name="contract-template-contracttemplate"></a>Plantilla de contrato (ContractTemplate)  
 La plantilla que contiene los atributos estándar de un contrato. Siempre existe una dependencia interna entre la plantilla de contrato y la entidad de contrato.  
  
<a name="BKMK_SystemForm"></a>   
### <a name="dashboard-or-entity-form-systemform"></a>Panel o formulario de entidad (SystemForm)  
 Los registros de la entidad del formulario del sistema se usan para definir los paneles y formularios de entidad. Cuando se usa un SystemForm como formulario de entidad hay una dependencia interna en la entidad. Cuando se usa un SystemForm como panel, no hay ninguna dependencia interna. Los paneles y los formularios de entidad habitualmente tienen dependencias publicadas relacionadas con su contenido. Un formulario de entidad puede tener campos de búsqueda que dependen de una relación de entidad. Los paneles y formularios de entidad pueden contener gráficos o subcuadrículas que crearán una dependencia publicada en una vista, que tiene una dependencia interna de una entidad. Una dependencia publicada de recursos web se puede crear debido al contenido que aparece en el panel o el formulario o cuando un formulario contiene las bibliotecas de JavaScript. Los formularios de entidad tienen dependencias publicadas de cualquier atributo que se muestre como campo del formulario.  
  
<a name="BKMK_EmailTemplate"></a>   

### <a name="email-template-emailtemplate"></a>Plantilla de correo electrónico (EmailTemplate)  
 Plantilla que contiene los atributos estándar de un mensaje de correo electrónico. Una plantilla de correo electrónico normalmente incluye los campos que insertan datos de atributos de entidad especificados. Una plantilla de correo electrónico se puede vincular a una entidad específica cuando se crea de forma que puede haber una dependencia interna en la entidad. Una plantilla de correo electrónico global no está asociada con una entidad específica, pero puede tener dependencias publicadas en los atributos de entidad usados para proporcionar datos. Con frecuencia se configura un proceso (flujo de trabajo) para enviar un correo electrónico usando una plantilla de correo electrónico que crea una dependencia publicada con el flujo de trabajo.  
  
<a name="BKMK_Entity"></a>   

### <a name="entity-entity"></a>Entidad (Entity)  
 La estructura primaria usada para modelar y administrar datos en Common Data Service. Los gráficos, los formularios, las relaciones de entidad, las vistas y los atributos asociados a una entidad se eliminan automáticamente cuando se elimina la entidad debido a las dependencias internas entre ellos. Las entidades con frecuencia tienen publicadas dependencias con procesos, paneles y plantillas de correo electrónico.  
  
<a name="BKMK_FieldSecurityProfile"></a>   
### <a name="field-security-profile-fieldsecurityprofile"></a>Perfil de seguridad de campo (FieldSecurityProfile)  
 Perfil que define el nivel de acceso para los atributos protegidos.  
  
<a name="BKMK_MailMergeTemplate"></a>   
### <a name="mail-merge-template-mailmergetemplate"></a>Plantilla de combinación de correspondencia (MailMergeTemplate)  
 Plantilla que contiene los atributos estándar de un documento de combinación de correspondencia. Una plantilla de combinación de correspondencia tiene una dependencia publicada de la entidad con la que está asociada.  
  
<a name="BKMK_OptionSet"></a>   
### <a name="option-set-optionset"></a>Conjuntos de opciones (OptionSet)  
 Un conjunto de opciones define un conjunto de opciones. Un atributo de lista desplegable usa un conjunto de opciones para definir las opciones que proporciona. Varios atributos de lista desplegable pueden usar un solo conjunto de opciones global de modo que las opciones que proporcionen sean siempre las mismas y pueden mantenerse en un solo lugar. Una dependencia publicada se produce cuando un atributo de lista desplegable hace referencia a un conjunto de opciones globales. No puede eliminar un conjunto de opciones globales que esté usando un atributo de lista desplegable.  
  
<a name="BKMK_PluginAssembly"></a>   
### <a name="plug-in-assembly-pluginassembly"></a>Ensamblado de complemento (PluginAssembly)  
 Ensamblado que contiene uno o más tipos de complementos. Los complementos se registran en los eventos asociados normalmente con una entidad. Esto crea una dependencia publicada.  
  
<a name="BKMK_Workflow"></a>   
### <a name="process-workflow"></a>Proceso (flujo de trabajo)  
 Conjunto de reglas lógicas que define los pasos necesarios para automatizar un proceso, una tarea o un conjunto de acciones empresariales específicos que se deben realizar. Los procesos proporcionan una amplia gama de acciones que crean dependencias publicadas en cualquier otro componente de la solución al que hace referencia el proceso. Cada proceso tiene también una dependencia publicada de la entidad con la que está asociada.  
  
<a name="BKMK_Report"></a>   
### <a name="report-report"></a>Informe (Report)  
 Resumen de datos en un diseño fácil de leer. Un informe publicó dependencias de los datos de la entidad o del atributo incluidos en el informe. Cada informe también debe asociarse con una categoría de informes que cree una dependencia interna de un componente de la solución llamado categoría relacionada del informe (ReportCategory). Los informes se pueden configurar para ser subinformes que crean una dependencia publicada con el informe primario.  
  
<a name="BKMK_SDKMessageProcessingStep"></a>   
### <a name="sdk-message-processing-step-sdkmessageprocessingstep"></a>Paso de procesamiento del mensaje de SDK (SDKMessageProcessingStep)  
 Fase de la canalización de ejecuciones que debe ejecutar un complemento.  
  
<a name="BKMK_Role"></a>   
### <a name="security-role-role"></a>Rol de seguridad (rol)  
 Agrupación de privilegios de seguridad. Se asignan a los usuarios roles que autorizan su acceso al sistema Common Data Service. Los formularios de entidad se pueden asociar con roles de seguridad específicos para controlar quién puede ver el formulario. Esto crea una dependencia publicada entre el rol de seguridad y el formulario.  
  
> [!NOTE]
>  Solo los roles de seguridad de la unidad de negocio de la organización se pueden agregar a una solución. Solo un usuario con acceso de lectura a estos roles de seguridad puede agregarlos a una solución.  
  
<a name="BKMK_ServiceEndpoint"></a>   
### <a name="service-endpoint-serviceendpoint"></a>Extremo de servicio (ServiceEndpoint)  
 Extremo de servicio que puede contactarse.  
  
<a name="BKMK_SiteMap"></a>   
### <a name="site-map-sitemap"></a>Mapa del sitio (SiteMap)  
 Datos de XML usados para controlar el panel de navegación de la aplicación. El mapa del sitio se puede vincular para mostrar un recurso web HTML o un icono del mapa del sitio puede usar un recurso web de imagen. Cuando la directiva de `$webresource:` se usa para establecer estas asociaciones se crea una dependencia publicada. Más información: [Directiva $webresource](/dynamics365/customer-engagement/developer/web-resources#BKMK_WebResourceDirective).  
  
<a name="BKMK_WebResource"></a>   
### <a name="web-resource-webresource"></a>Recurso web (WebResource)  
 Datos equivalentes a los archivos que se usan en el desarrollo web. Los recursos web proporcionan los componentes de cliente que se usan para proporcionar elementos de la interfaz de usuario personalizados. Los recursos web pueden haber publicado dependencias con formularios de entidad, cintas y el mapa del sitio. Cuando la directiva de `$webresource:` se usa para establecer asociaciones en una cinta o el mapa del sitio, se crea una dependencia publicada. Para obtener más información, consulte [Directiva $webresource](/dynamics365/customer-engagement/developer/web-resources#BKMK_WebResourceDirective).  
  
> [!NOTE]
>  Los recursos web pueden depender de otros recursos web basándose en los vínculos relativos. Por ejemplo, un recurso web HTML puede usar un recurso web de CSS o de script. Un recurso web de Silverlight mostrado fuera de un gráfico o formulario de entidad debe tener un recurso web HTML para alojarlo. Estas dependencias no se siguen como dependencias de solución.  
  
### <a name="see-also"></a>Vea también  
 [Eliminar dependencias](removing-dependencies.md)   
 [Empaquetar y distribuir extensiones con soluciones de Dynamics 365](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Introducción a las soluciones](introduction-solutions.md)   
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Crear, exportar o importar una solución no administrada](create-export-import-unmanaged-solution.md)   
 [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)   
 [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)   
 [Desinstalar o eliminar una solución](uninstall-delete-solution.md)   
 [Entidades de solución](/dynamics365/customer-engagement/developer/solution-entities)