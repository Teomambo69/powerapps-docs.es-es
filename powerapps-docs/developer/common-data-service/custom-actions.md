---
title: Crear acciones propias (Common Data Service para aplicaciones) | Microsoft Docs
description: Las acciones son mensajes personalizados que le ayudan a ampliar la funcionalidad de Dynamics 365 Customer Engagement. Más información sobre cómo crear sus propias acciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-your-own-actions"></a>Crear acciones propias

Para ampliar la funcionalidad de Common Data Service para aplicaciones creando mensajes personalizados denominados *acciones*. Estas acciones tendrán clases de solicitud/de respuesta asociadas y se generará una acción API web. Por lo general, las acciones se utilizan para agregar una nueva funcionalidad específica del dominio al servicio web de la organización o para combinar varias solicitudes de mensaje de servicio web de la organización en una sola solicitud. Por ejemplo, en un centro de atención telefónica de soporte técnico, es posible que desee combinar los mensajes Crear, Asignar y Setstate en un único mensaje nuevo Escalar.  
  
 La lógica de negocios de una acción se implementa mediante un flujo de trabajo. Cuando crea una acción, el flujo de trabajo asociado en tiempo real se registra automáticamente para ejecutarse en la fase 30 (operación principal) de la canalización de ejecuciones. Para obtener más información sobre flujos de trabajo en tiempo real, consulte [Tipos de flujo de trabajo](/dynamics365/customer-engagement/developer/process-categories).  
  
 Si bien las acciones se admiten en CDS for Apps, la creación de una acción en código (mediante XAML) se admite únicamente para las implementaciones locales y con conexión a Internet (IFD). Los clientes de Online deben crear acciones interactivamente en la aplicación web.  
  
<a name="about_actions"></a>   

## <a name="about-action-definitions"></a>Acerca de las definiciones de acción  

 Para definir una acción se utiliza un registro de entidad `Workflow`, similar a un flujo de trabajo en tiempo real. En la lista siguiente se detallan algunos puntos clave acerca de qué es y cómo funciona una acción:  
  
- Se puede asociar con una sola entidad o ser global (no asociada con ninguna entidad determinada).  
  
- Se ejecuta en la fase 30 de la operación principal de la canalización de ejecuciones de eventos.  
  
- Admite la invocación de complementos registrados en las fases de operación previa y posterior de la canalización de ejecuciones de eventos.  
  
- Puede tener complementos registrados en las fases de operación previa y posterior solo cuando el estado de la acción es Activado.  
  
- Está disponible a través de la API web o los extremos `organization.svc` y `organization.svc/web`.  
  
- Se puede ejecutar mediante un recurso web de JavaScript. Más información: [Ejecutar una acción con un recurso web de JavaScript](/dynamics365/customer-engagement/developer/create-own-actions#BKMK_JavaScript)  
  
- Siempre se ejecuta en el contexto de seguridad del usuario que llama.  
  
- El registro no se puede eliminar mientras hay pasos de complementos registrados en la acción.  
  
- De manera opcional, mediante una opción de configuración, puede participar en la transacción de la base de datos actual.  
  
- No admite un ámbito cuando la ejecución está limitada a un usuario, una unidad de negocio o una organización. Las acciones siempre se ejecutan en el ámbito de la organización.  
  
- Admite argumentos de entrada y salida.  
  
- Admite la auditoría de cambios de datos.  
  
- No es compatible con clientes sin conexión.  
  
- Puede ser invocado por una llamada a un método de servicio web.  
  
- Puede ser invocado directamente desde un flujo de trabajo.  
  
<a name="bkmk_permissions"></a> 
  
## <a name="required-permissions"></a>Permisos requeridos
  
 Se requiere un privilegio de seguridad denominado Activar procesos en tiempo real (`prvActivateSynchronousWorkflow`) para activar el flujo de trabajo en tiempo real de una acción para que pueda ejecutarse. Esto es además de los privilegios necesarios para crear un flujo de trabajo.  

<!-- Removed much content about creating a custom action using code-->
  
<a name="bkmk_package"></a>   

## <a name="package-an-action-for-distribution"></a>Empaquetar una acción para la distribución

 Para distribuir la acción de modo que se pueda importar a una organización de CDS for Apps, agregue la acción a una solución de CDS for Apps. Esto se realiza fácilmente usando la aplicación web y desplazándose a **Configuración** > **Personalizaciones** > **Soluciones**. También puede escribir código para crear la solución. Para obtener más información sobre cómo usar soluciones, consulte [Empaquetar y distribuir las extensiones](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).  
  
<a name="bkmk_gentypes"></a>

## <a name="generate-early-bound-types-for-an-action"></a>Generar tipos de enlace en tiempo de compilación para una acción

 Con la herramienta CrmSvcUtil puede generar clases de solicitud y respuesta para la acción para incluirlas en el código de aplicación. Sin embargo, antes de generar estas clases, asegúrese de activar la acción.  
  
Para descargar el CrmSvcUtil.exe, consulte [Descargar herramientas de NuGet](download-tools-NuGet.md).
  
 El siguiente ejemplo muestra el formato para ejecutar la herramienta desde la línea de comandos para una instalación local de CDS for Apps. Se suministran los valores de los parámetros para la instalación.  
  
```ms-dos  
CrmSvcUtil.exe /url:http://<serverName>/<organizationName>/XRMServices/2011/Organization.svc /out:<outputFilename>.cs /username:<username> /password:<password> /domain:<domainName> /namespace:<outputNamespace> /serviceContextName:<serviceContextName> /generateActions  
```  
  
 El siguiente ejemplo muestra el formato para ejecutar la herramienta desde la línea de comandos con CDS for Apps. Se suministran los valores de los parámetros adecuados para su cuenta y servidor.  
  
```ms-dos  
CrmSvcUtil.exe /url:https://<organizationUrlName>.api.crm.dynamics.com/XRMServices/2011/Organization.svc /out:<outputFilename>.cs /username:<username> /password:<password> /namespace:<outputNamespace> /serviceContextName:<serviceContextName> /generateActions  
```  
  
 Tenga en cuenta el uso del parámetro `/generateActions`. Más información: [Crear clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool).  
  
 Puede usar tipos de enlace en tiempo de compilación y en tiempo de ejecución con las clases generadas de solicitud y respuesta para la acción.  
  
<a name="bkmk_executeWebAPI"></a>

## <a name="execute-an-action-using-the-web-api"></a>Ejecutar una acción con la API web

Una nueva acción se crea en la API web cuando se crea. Si la acción se crea en el contexto de una entidad, está enlazada a esa entidad. Si no, es una acción sin enlazar. Más infomación: [Usar acciones web API](/dynamics365/customer-engagement/developer/webapi/use-web-api-actions).  
  
<a name="bkmk_execute"></a>

## <a name="execute-an-action-using-the-organization-service"></a>Ejecutar una acción con el servicio de organización

Para ejecutar una acción con el servicio web de la organización por medio de código administrado, siga estos pasos.  
  
1. Incluya el archivo de tipos de enlace en tiempo de compilación que generó con la herramienta CrmSvcUtil en el proyecto de la aplicación.  
  
2. En el código de aplicación, cree una instancia de la solicitud de la acción y complete las propiedades necesarias.  
  
3. Invoque <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>, pasando la solicitud como un argumento.  
  
   Antes de ejecutar el código de aplicación, asegúrese de que la acción esté activada. De lo contrario, recibirá un error de tiempo de ejecución.  
  
<a name="BKMK_JavaScript"></a>   

### <a name="execute-an-action-using-a-javascript-web-resource"></a>Ejecutar una acción con un recurso web de JavaScript

Una acción puede ejecutarse con la API web igual que cualquier acción del sistema. Más infomación: [Usar acciones web API](/dynamics365/customer-enagagement/developer/webapi/use-web-api-actions).  

La biblioteca de ejemplo [Sdk.Soap.js](http://code.msdn.microsoft.com/SdkSoapjs-9b51b99a) muestra cómo se pueden usar los mensajes con los recursos web de JavaScript y el servicio de organización (organization.svc/web). Use el ejemplo complementario [Generador de mensaje de acción de Sdk.Soap.js](http://code.msdn.microsoft.com/SdkSoapjs-Action-Message-971be943) para generar bibliotecas de JavaScript que se pueden usar con Sdk.Soap.js de la misma forma en que puede usar las bibliotecas para los mensajes del sistema proporcionados en dicho ejemplo. Los archivos generados con el Generador de mensaje de acción de `Sdk.Soap.js` son bibliotecas de JavaScript independientes para cada acción. Cada biblioteca contiene una clase de solicitud y respuesta que se corresponde con las clases generadas por la herramienta CrmSvcUtil.  
  
<a name="bkmk_execute-process"></a>

## <a name="execute-an-action-using-a-process"></a>Ejecute una acción mediante un proceso

Puede ejecutar una acción desde flujos de trabajo, diálogos u otras acciones del proceso. Hay acciones personalizadas activadas disponibles para los procesos seleccionando el elemento **Realizar acción** en el desplegable **Agregar paso** del formulario del proceso de aplicación web. Cuando el paso se agrega al proceso, puede seleccionar la nueva acción personalizada (o cualquier acción) desde la lista **Acción** proporcionado en el paso. Elija **Establecer propiedades** en el paso para especificar parámetros de entrada que la acción personalizada requiera.  
  
> [!NOTE]
>  Si una acción personalizada tiene tipos de parámetros no compatibles, por ejemplo, Lista desplegable, Entidad o Colección de entidades, la acción personalizada no se muestra en la lista **Acción**.  
  
Las plataforma de <xref:Microsoft.Xrm.Sdk.IExecutionContext.Depth> existentes comprueba para asegurarse que no se produce un bucle infinito. Para obtener más información sobre límites de profundidad, vea <xref:Microsoft.Xrm.Sdk.Deployment.WorkflowSettings.MaxDepth>.  
  
<a name="bkmk_longrunning"></a>

## <a name="watch-out-for-long-running-actions"></a>Observar las acciones de ejecución prolongada

Si uno de los pasos del flujo de trabajo en tiempo real de la acción es una actividad de flujo de trabajo personalizada, dicha actividad de flujo de trabajo personalizada se ejecuta dentro del entorno aislado de tiempo de ejecución en el espacio aislado y estará sujeta al límite de tiempo de espera de dos minutos, similar al modo en que se administran los complementos en el espacio aislado. Sin embargo, no hay restricciones en cuanto a la cantidad de tiempo total que la acción en sí puede tardar. Además, si la acción participa en una transacción en la que está habilitada la reversión, se aplicarán los tiempos de espera de SQL Server.  

> [!TIP]
>  Una de las prácticas recomendadas consiste en ejecutar las operaciones de ejecución prolongadas fuera de CDS for Apps con procesos asincrónicos .NET o en segundo plano.  
  
### <a name="see-also"></a>Vea también  
 [Crear flujos de trabajo en tiempo real](/dynamics365/customer-engagement/developer/create-real-time-workflows)   
 [Usar diálogos para procesos guiados](/dynamics365/customer-engagement/developer/use-dialogs-guided-processes)   
 [Canalización de ejecución del evento](event-framework.md#event-execution-pipeline)   
 [Escribir flujos de trabajo para automatizar los procesos de negocio](/dynamics365/customer-engagement/developer/automate-business-processes-customer-engagement)   
 [Personalizar el sistema](https://technet.microsoft.com/library/dn531158.aspx)
