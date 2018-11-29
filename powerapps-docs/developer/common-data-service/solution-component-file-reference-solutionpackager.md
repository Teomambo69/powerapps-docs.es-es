---
title: Referencia de archivos de componente de la solución (Common Data Service para aplicaciones) | Microsoft Docs
description: Este tema describe la estructura de carpetas y el esquema de nombres de archivos utilizados por la herramienta SolutionPackager. La herramienta se usa para descomponer (desempaquetar) archivos de la solución de Dynamics 365 en archivos XML que puedan administrarse mediante un sistema de control de código fuente.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
---
# <a name="solution-component-file-reference-solutionpackager"></a>Referencia de archivo de componente de la solución (SolutionPackager)

Este tema describe la estructura de carpetas y el esquema de nombres de archivos utilizados por la herramienta SolutionPackager. La herramienta se usa para descomponer (desempaquetar) archivos de la solución de Common Data Service para aplicaciones en archivos XML que puedan administrarse mediante un sistema de control de código fuente. La herramienta también puede compliar (empaquetar) estos archivos XML individuales en un archivo de la solución que pueden importarse en CDS para aplicaciones. Para obtener más información acerca de la herramienta SolutionPackager, consulte [herramienta SolutionPackager](compress-extract-solution-file-solutionpackager.md).  
  
 Las secciones siguientes describen los archivos que se crearán para cada tipo de componente de la solución y cuáles de estos archivos son menos adecuados para incluirlos en el control de código fuente. Las carpetas que se indican en las secciones son todas relativas a la carpeta especificada en el parámetro `/folder` del comando **SolutionPackager**.  
  
<a name="entity_bm"></a>   
## <a name="entity"></a>Entity  
 Difiere en soluciones administradas: Sí  
  
### <a name="notes"></a>Notas  
  
1.  Cada entidad tiene una carpeta diferente.  
  
2.  Cada formulario, vista y visualización tiene su propio archivo en la correspondiente subcarpeta.  
  
3.  Los nombres de archivo de formulario varían según sean de tipos de solución Administrada o No administrada.  
  
4.  Se admite la edición directa de RibbonDiff.xml para personalizar cintas específicas de entidad.  
  
5.  La edición manual de los archivos XML en las carpetas FormXml y SavedQueries es compatible pero opcional.  
  
### <a name="files"></a>Archivos  
 \Entidades\\<Nombre de esquema de entidad\>\  
  
 Entity.Xml  
RibbonDiffXml  
  
 FormXml\Main\  
  
 {guid 1}.xml  
{guid 1_managed}.xml  
{guid n}.xml  
{guid n_managed}.xml  
  
 FormXml\Mobile\  
  
 {guid 1}.xml  
{guid 1_managed}.xml  
{guid n}.xml  
{guid n_managed}.xml  
  
 SavedQueries\  
  
 {guid 1}.xml  
{guid n}.xml  
  
 Visualizaciones\  
  
 {guid 1}.xml  
{guid n}.xml  
  
<a name="optionset_bm"></a>   
## <a name="option-set"></a>Conjunto de opciones  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
 Cada conjunto de opciones se almacena en un archivo independiente.  
  
### <a name="files"></a>Archivos  
 \OptionSets\  
  
 \<nombre de esquema 1>.xml  
\<nombre de esquema n>.xml  
  
<a name="relationship_bm"></a>   
## <a name="entity-relationship"></a>Relación de entidad  
 Difiere en soluciones administradas: Sí  
  
### <a name="notes"></a>Notas  
  
1.  Cada entidad tiene un archivo diferenciado que contiene todas las relaciones para las cuales:  
  
    1.  N:N es la primera entidad enumerada  
  
    2.  1:N es la entidad de referencia  
  
### <a name="files"></a>Archivos  
 \Other\Relationships\  
  
 \<Nombre de esquema de entidad 1>.xml  
\<Nombre de esquema de entidad 1>.xml  
  
<a name="ribbon_bm"></a>   
## <a name="ribbon-customization"></a>Personalización de la cinta de opciones  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
  
1.  Todos los XML de cintas específicas de entidades pueden encontrarse en la carpeta de cada entidad. El resto de XML de cintas estará en este archivo.  
  
2.  Es posible editar directamente RibbonCustomizations.xml para personalizar la banda de opciones global.  
  
### <a name="files"></a>Archivos  
 \Other\RibbonCustomizations.Xml  
  
<a name="sitemap_bm"></a>   
## <a name="site-map"></a>Mapa del sitio  
 Difiere en soluciones administradas: Sí  
  
### <a name="notes"></a>Notas  
 El formato XML de mapa del sitio es diferente para las soluciones administradas y no administradas. Se espera que el archivo se nombre como se indica aquí. Al extraer ambos tipos de paquetes, los dos archivos están presentes.  
  
### <a name="files"></a>Archivos  
 \Otras\  
  
 SiteMap.xml  
SiteMap_managed.xml  
  
<a name="resource_bm"></a>   
## <a name="web-resources"></a>Recursos web  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
  
1.  Los recursos web sin procesar se almacenan como un archivo independiente. Los caracteres de barra (/) se usan para crear carpetas.  
  
2.  Los metadatos de recursos de web se almacenan con una extensión de archivo similar .data.xml.  
  
3.  Se recomienda que el nombre de un recursos web contenga la extensión de archivo natural.  
  
4.  La adición de los archivos sin procesar para controlar el código fuente puede provocar duplicados.  
  
### <a name="files"></a>Archivos  
 \WebResources\  
  
 \<nombre 1>  
\<nombre 1>.data.xml  
\<nombre n>  
\<nombre n>.data.xml  
  
<a name="role_bm"></a>   
## <a name="role"></a>Rol  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
 Cada rol se almacena en un archivo independiente.  
  
### <a name="files"></a>Archivos  
 \Roles\  
  
 \<nombre de esquema>.xml  
  
<a name="connectionrole_bm"></a>   
## <a name="connection-role"></a>Rol de conexión  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
 Todos los roles de conexión se almacenan en conjunto en un archivo.  
  
### <a name="files"></a>Archivos  
 \Other\ConnectionRoles.xml  
  
<a name="dashboard_bm"></a>   
## <a name="dashboard"></a>Panel  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
 Cada panel se almacena en un archivo independiente.  
  
### <a name="files"></a>Archivos  
 \Paneles\  
  
 {guid 1}.xml  
{guid n}.xml  
  
<a name="workflow_bm"></a>   
## <a name="workflow"></a>Flujo de trabajo  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
  
1.  El XAML para cada flujo de trabajo se almacena en un archivo independiente.  
  
2.  Los metadatos para cada flujo de trabajo se encuentran en un archivo de nombre similar terminado en .data.xml.  
  
### <a name="files"></a>Archivos  
 \Workflows\  
  
 \<XamlFileName 1 > .xaml  
\<XamlFileName 1>.xaml.data.xml  
\<XamlFileName n>.xaml  
\<XamlFileName n>.xaml.data.xml  
  
<a name="emailtemplate_bm"></a>   
## <a name="email-template"></a>Plantilla de correo electrónico  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
  
1.  Todos los metadatos de plantilla de correo electrónico se almacenan en un único archivo.  
  
2.  Cada plantilla de correo electrónico utiliza cuatro archivos diferenciados por idioma.  
  
### <a name="files"></a>Archivos  
 \Templates\  
  
 EmailTemplates.xml  
  
 EmailDocuments\  
  
 \<LCID 1>\\{guid 1}\  
  
 Body.xsl  
Presentation.xml  
Subject.xsl  
Subjectpresentation.xml  
  
 \<LCID 1>\\{guid n}\  
  
 Body.xsl  
Presentation.xml  
Subject.xsl  
Subjectpresentation.xml  
  
 \<LCID n>\\{guid 1}\  
  
 Body.xsl  
Presentation.xml  
Subject.xsl  
Subjectpresentation.xml  
  
 \<LCID n>\\{guid n}\  
  
 Body.xsl  
Presentation.xml  
Subject.xsl  
Subjectpresentation.xml  
  
<a name="contracttemplate_bm"></a>   
## <a name="contract-template"></a>Plantilla de contrato  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
 Todos los metadatos de plantillas de contrato se almacenan en un único archivo.  
  
### <a name="files"></a>Archivos  
 \Templates\ContractTemplates.xml  
  
<a name="kbarticle_bm"></a>   
## <a name="kb-article-template"></a>Plantilla de artículo de KB  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
  
1.  Todos los metadatos de plantillas de contrato se almacenan en un único archivo.  
  
2.  Cada plantilla de contrato utiliza dos archivos diferenciados por idioma.  
  
### <a name="files"></a>Archivos  
 \Templates\  
  
 KBArticleTemplates.xml  
  
 KBArticleTemplates\  
  
 \<LCID 1>\\{guid 1}\  
  
 formatxml.xsl  
Structurexml.xml  
  
 \<LCID 1>\\{guid n}\  
  
 formatxml.xsl  
Structurexml.xml  
  
 \<LCID n>\\{guid 1}\  
  
 formatxml.xsl  
Structurexml.xml  
  
 \<LCID n>\\{guid n}\  
  
 formatxml.xsl  
Structurexml.xml  
  
<a name="mailmerge_bm"></a>   
## <a name="mail-merge-template"></a>Plantilla de combinación de correspondencia  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
  
1.  Todos los metadatos de plantillas de combinación de correspondencia se almacenan en un único archivo.  
  
2.  Cada plantilla de combinación de correspondencia utiliza dos archivos diferenciados por idioma.  
  
3.  Los documentos que se comparten entre varias plantillas se almacenarán en un único archivo diferenciado.  
  
### <a name="files"></a>Archivos  
 \Templates\  
  
 MailMergeTemplates.xml  
  
 MailMergeDocuments\  
  
 \<LCID 1>\\{guid 1}\\<nombre de documento 1>.xml  
\<LCID 1>\\{guid n}\\<nombre de documento n\>.xml  
\<LCID n>\\{guid 1}\\<nombre de documento 1>.xml  
\<LCID n>\\{guid n}\\<nombre de documento n\>.xml  
  
<a name="pluginassembly_bm"></a>   
## <a name="pluginassembly"></a>PluginAssembly  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
  
1.  Cada ensamblado de complemento tendrá un archivo diferenciado para los bytes de ensamblado sin procesar.  
  
2.  Los metadatos de ensamblados de complementos se almacenan en un archivo de nombre similar terminado en .data.xml.  
  
3.  No se recomienda incluir el ensamblado sin procesar en control de código fuente.  
  
### <a name="files"></a>Archivos  
 \PluginAssemblies\  
  
 \<Nombre del ensamblado 1>-{guid 1}\  
  
 \<Nombre del ensamblado 1>.dll  
\<Nombre del ensamblado 1 >. dll.data.xml  
  
 \<Nombre del ensamblado n>-{guid n}\  
  
 \<Nombre del ensamblado n>.dll  
\<Nombre del ensamblado n>.dll.data.xml  
  
<a name="step_bm"></a>   
## <a name="sdkmessageprocessingstep"></a>SdkMessageProcessingStep  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
 Cada paso de procesamiento del mensaje de SDK se almacena en un archivo independiente.  
  
### <a name="files"></a>Archivos  
 \SdkMessageProcessingSteps\  
  
 {guid 1}.xml  
{guid n}.xml  
  
<a name="serviceendpoint_bm"></a>   
## <a name="serviceendpoint"></a>Extremo de servicio  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
 Todos los metadatos de extremo de servicio se almacenan juntos en un archivo.  
  
### <a name="files"></a>Archivos  
 \PluginAssemblies\ServiceEndpoints.xml  
  
<a name="reports_bm"></a>   
## <a name="reports"></a>Informes  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
  
1.  Los informes se almacenan en una subcarpeta distinta por idioma.  
  
2.  Cada informe tiene un archivo diferenciado dentro de esa carpeta.  
  
3.  Los metadatos de cada informe se almacenan en un archivo de nombre similar terminado en .data.xml.  
  
### <a name="files"></a>Archivos  
 \Reports\  
  
 ReportSignatureIdMappings.xml  
  
 ReportLinks.xml  
  
 \<LCID 1>\\{guid 1}\  
  
 \<Nombre del informe 1>.rdl  
\<Nombre del informe 1>.rdl.data.xml  
  
 \<LCID 1>\\{guid n}\  
  
 \<Nombre del informe n>.rdl  
\<Nombre del informe n>.rdl.data.xml  
  
 \<LCID n>\\{guid 1}\  
  
 \<Nombre del informe 1>.rdl  
\<Nombre del informe 1>.rdl.data.xml  
  
 \<LCID n>\\{guid n}\  
  
 \<Nombre del informe n>.rdl  
\<Nombre del informe n>.rdl.data.xml  
  
<a name="entitymap_bm"></a>   
## <a name="entitymap"></a>EntityMap  
 Difiere en soluciones administradas: No  
  
### <a name="notes"></a>Notas  
 Todos los mapas de entidad se almacenan en un único archivo.  
  
### <a name="files"></a>Archivos  
 \Other\EntityMaps.xml  
  
### <a name="see-also"></a>Vea también  
 [Use la herramienta SolutionPackager para comprimir y extraer un archivo de solución](compress-extract-solution-file-solutionpackager.md)   
