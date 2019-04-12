---
title: 'Apéndice: Lista de comprobación de certificación de aplicaciones (PowerApps) | Microsoft Docs'
description: 'La lista de comprobación de certificación de aplicaciones le proporciona información acerca de las comprobación que deben pasar las aplicaciones basadas en modelos, de lienzo y los flujos antes de poder publicarse en AppSource.'
ms.custom: ''
ms.date: 03/20/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: omarcdoc
ms.author: omarc
manager: AnnBe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="appendix-app-certification-checklist"></a>Apéndice: Lista de comprobación de certificación de aplicaciones

La lista de comprobación siguiente proporciona la lista de comprobaciones realizadas por Microsoft durante el proceso de la certificación después de que usted [envíe](next-steps-submit-app-cloud-partner-portal.md) su aplicación. 

<table>
<tbody>
<tr>
<th>Aplicaciones</th>
<th>Tipo de validación</th>
<th>Lista de comprobación de certificación</th>
</tr>
<tr>
<td rowspan=5><a href="https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview">Aplicaciones basadas en modelos</a>, <a href="https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started">aplicaciones de lienzo</a> y <a href="https://docs.microsoft.com/flow/getting-started">flujos</a> que se conectan a Common Data Service<br/><br/><strong>NOTA</strong>: Las aplicaciones de Dynamics 365 for Customer Engagement son aplicaciones basadas en modelos</td>
<td>Comprobación de estado</td>
<td><ul>
<li>Buscar el tipo de registro de la aplicación: gratuita, prueba o contacto. Si se ha registrado en Contacto , el editor debe habilitar la prueba.</li>
<li>Compruebe que el <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/create-package-app-appsource"> paquete</a> enviado contiene todos los artefactos necesarios para publicar en AppSource.</li>
<li>Descargue el documento funcional de extremo a extremo (E2E) del portal de Socio en la nube y valide si el documento se actualiza con escenarios funcionales y viaje usuario/administrador.</li>
</ul>
</td>
</tr>
<tr>
<td>Validación de código</td>
<td>
<ul>
<li>La validación de código para las aplicaciones de lienzo se efectuará a través de la <a href="https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/accessibility-checker">herramienta Accessibility Checker</a> en PowerApps para comprobar lo siguiente:
<ul>
<li>Errores y advertencias estáticos de fórmula: Si se encuentran problemas, el equipo de la certificación compartirá los comentarios para resolver y reenviar a AppSource.</li>
<li>Errores en tiempo de ejecución: Pueden producirse cuando la aplicación se abre en modo de ejecución para ver. Los problemas que se encuentren se comunicarán por correo electrónico.</li>
<li>Errores y advertencias de accesibilidad: Todos los errores de accesibilidad se deben resolver siguiendo las instrucciones del Comprobador de soluciones.</li>
</ul></li>
<li>La validación de código para la solución de Common Data Service se efectuará a través de la herramienta <a href="https://experienceisv.microsoftcrmportals.com/precertification/#/">de la análisis del código de OnDemand (ODCA)</a>.</li>
<li>Los problemas comunicados desde ODCA serán validados manualmente para su corrección y se reducirán los problemas de falsos positivos para bajar la gravedad.</li>
<li>El informe generado se comparte con el editor a través del correo electrónico.</li>
</ul>
</td>
</tr>
<tr>
<td>Validación de la implementación</td>
<td>
<ul>
<li>La solución se instalará en PowerApps Studio mediante <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/package-deployer/create-packages-package-deployer">Package Deployer</a>. Las aplicaciones de lienzo instaladas se localizarán manualmente en la solución y también en la sección de aplicaciones después de la instalación y garantizarán que la aplicación está abierta en modo de edición y ejecución. La aplicación de lienzo se eliminará manualmente de PowerApps Studio para validar la desinstalación correcta</li>
<li>Compruebe que la aplicación de lienzo se conecta correctamente a través de conectores proporcionados por los editores. Por ejemplo, Common Data Service o cualquier otra conexión.</li>
<li>Compruebe todos los componentes de Common Data Service (entidades, recursos web, complementos y otros componentes) están disponibles en la solución.</li>
<li>Desinstale manualmente la solución y compruebe si todos los componentes asociados con la solución administrada se han quitado.</li>
</ul>
</td>
</tr>
<tr>
<td>Funcionalidad de la funcionalidad</td>
<td>
<ul>
<li>Valide la funcionalidad de la aplicación basándose en el documento funcional compartido por el editor. Todas las características que se implementan en la aplicación deben pasar.</li>
<li>El editor debe enviar el documento funcional E2E a través del portal de Socio en la nube o puede compartir vínculos de vídeo a través de correo electrónico.</li>
<li>Si la aplicación requiere configuración de licencia, el equipo de certificación compartirá los detalles de la instancia para que el editor actualice la licencia necesaria.</li>
</ul></td>
</tr>
<tr>
<td>Validación de la seguridad</td>
<td>
<ul>
<li>La comprobación si la aplicación de lienzo se conecta a cualquier origen de datos externo o conexiones que necesiten acceso, y se comparten los detalles de conexión del documento E2E.</li>
<li>Compruebe que la aplicación de lienzo se conecta a cualquier conexión externa desde los conectores PowerApps.</li>
<li>Compruebe el código personalizado proporcionado en Package Deployer. Valide el código antes de aprobar la aplicación a AppSource.</li>
<li>Valide manualmente el código para ver si el código personalizado está recuperando datos del cliente del entorno de destino.</li>
</ul>
</td>
</tr>
<tr>
<td rowspan=5><a href="https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started">Aplicaciones de lienzo</a>, y <a href="https://docs.microsoft.com/flow/getting-started">flujos</a> y que se conectan a orígenes de datos <i>distintos</i> de Common Data Service
</td>
<td>Comprobación de estado</td>
<td><ul>
<li>Compruebe que la aplicación de lienzo contiene un archivo .msapp válido.</li>
<li>Compruebe que la carpeta de paquete tiene todos los componentes necesarios como manifiesto, Jason y otros componentes de imagen.</li>
</ul>
</td>
</tr>
<tr>
<td>Validación de código</td>
<td><ul>
<li>Igual que se explicó antes para las aplicaciones basadas en modelos, aplicaciones de lienzo y flujos que se conectan a Common Data Service</li></ul>
</td>
</tr>
<tr>
<td>Validación de la implementación</td>
<td>
<ul>
<li>La aplicación de lienzo se instalará manualmente en PowerApps Studio mediante la característica de importación de aplicaciones. Las aplicaciones de lienzo instaladas se localizarán manualmente en la sección de aplicaciones después de la instalación y garantizarán que la aplicación está abierta en modo de edición y ejecución. La aplicación de lienzo se eliminará manualmente de PowerApps Studio para validar la desinstalación correcta.</li>
<li>Compruebe que la aplicación de lienzo se conecta correctamente a conectores proporcionados por los editores.</li>
</ul>
</td>
</tr>
<tr>
<td>Funcionalidad de la funcionalidad</td>
<td>
<ul>
<li>Igual que se explicó antes para las aplicaciones basadas en modelos, aplicaciones de lienzo y flujos que se conectan a Common Data Service</li></ul></td>
</tr>
<tr>
<td>Validación de la seguridad</td>
<td>
<ul>
<li>Igual que se explicó antes para las aplicaciones basadas en modelos, aplicaciones de lienzo y flujos que se conectan a Common Data Service</li></ul>
</td>
</tr>
</tbody>
</table>

Para obtener más información acerca de las prácticas recomendadas para crear:
- Aplicaciones de lienzo, vea [Estándar e instrucciones de codificación de aplicaciones de lienzo](https://aka.ms/powerappscanvasguidelines)
- Aplicaciones basadas en modelos, consulte [Comprender los componentes de aplicaciones basadas en modelos](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-components)

  




  

