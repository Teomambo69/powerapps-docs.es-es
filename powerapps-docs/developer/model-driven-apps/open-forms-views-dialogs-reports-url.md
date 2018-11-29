---
title: 'Abrir formularios, vistas, diálogos e informes con una dirección URL (aplicaciones basadas en modelos) | Microsoft Docs'
description: 'Obtenga más información acerca de los elementos direccionables de dirección URL, que le permiten incluir vínculos a formularios, vistas, cuadro de diálogo e informes en otras aplicaciones.'
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
# <a name="open-forms-views-dialogs-and-reports-with-a-url"></a>Abrir formularios, vistas, diálogos e informes con una dirección URL

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/open-forms-views-dialogs-reports-url -->

Los elementos direccionables de URL le permiten incluir vínculos a formularios, vistas, diálogos e informes en otras aplicaciones. De esta manera, puede ampliar fácilmente otras aplicaciones, informes o sitios web para que los usuarios puedan ver información y realizar acciones sin cambiar de aplicación.  

> [!NOTE]
> - Los formularios, las vistas, los diálogos y los informes direccionables mediante dirección URL no pueden omitir la seguridad. Solo los usuarios con licencia, en función de sus roles de seguridad, pueden acceder a los datos y los registros que ven.  
>   -   Use `Xrm.Navigation.`[openForm](clientapi/reference/Xrm-Navigation/openForm.md) cuando abra formularios de entidad mediante programación dentro de la aplicación mediante el uso de recursos web. No utilice `window.open`.  
>   -   Fuera de la aplicación, donde las páginas no tienen acceso a la función `Xrm.Navigation.`[openForm](clientapi/reference/Xrm-Navigation/openForm.md), use `window.open` o un vínculo para abrir un registro o formulario determinado para una entidad.  

<a name="BKMK_URLAddressableFormsAndViews"></a>

## <a name="url-addressable-forms-and-views"></a>Formularios y vistas direccionables mediante dirección URL

 Todos los formularios y las vistas de entidad se muestran en la página main.aspx. Los parámetros de cadena de consulta pasados a esta página controlarán lo que se muestra. Por ejemplo:  

<!-- To open a new account entity record form for on-premises [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]:  
 ```  
http://mycrm/myOrg/main.aspx?etn=account&pagetype=entityrecord  
 ```  -->

 Para abrir un formulario de registro de la entidad de cuenta donde el identificador es {91330924-802A-4B0D-A900-34FD9D790829}:  
 ```  
http://myorg.crm.dynamics.com/main.aspx?etn=account&pagetype=entityrecord&id=%7B91330924-802A-4B0D-A900-34FD9D790829%7D  
 ```  

 Para abrir la vista **Oportunidades cerradas** para:  
 ```  
http://myorg.crm.dynamics.com/main.aspx?etn=opportunity&pagetype=entitylist&viewid=%7b00000000-0000-0000-00AA-000010003006%7d&viewtype=1039  
 ```  

 Para abrir la vista **Contactos activos** sin la barra de navegación o la barra de comandos  
 ```  
http://myorg.crm.dynamics.com/main.aspx?etn=contact&pagetype=entitylist&viewid={00000000-0000-0000-00AA-000010001004}&viewtype=1039&navbar=off&cmdbar=false  
 ```  

> [!NOTE]
>  La apertura de formularios de entidad en una ventana de diálogo mediante [showModalDialog](https://msdn.microsoft.com/library/ie/ms536759.aspx) o [showModelessDialog](https://msdn.microsoft.com/library/ie/ms536761.aspx) no se admite.  
>   
>  No se puede mostrar un formulario de entidad en un iFrame incrustado en otro formulario de entidad.  

 Normalmente usará el método [getClientUrl](clientapi/reference/Xrm-Utility/getGlobalContext/getClientUrl.md) para recuperar la dirección URL raíz de la organización para aplicaciones basadas en modelos.  

<a name="BKMK_QueryStringParametersForMainForm"></a>   
### <a name="query-string-parameters-for-the-mainaspx-page"></a>Parámetros de cadena de consulta para la página Main.aspx  

> [!TIP]
>  Para obtener el valor del identificador de cualquier registro, use el botón **Enviar un vínculo** de la barra de comandos. A continuación tiene un ejemplo de lo que se abrirá en la aplicación de correo electrónico:  
>   
>  `<http://mycrm/myOrg/main.aspx?etc=4&id=%7b899D4FCF-F4D3-E011-9D26-00155DBA3819%7d&pagetype=entityrecord>`.  
>   
>  El parámetro de identificador pasado a la dirección URL es el valor de identificador codificado del registro. En este ejemplo, el valor de identificador es `{899D4FCF-F4D3-E011-9D26-00155DBA3819}`. La versión codificada del GUID sustituirá las llaves de apertura y cierre “{” y “}” por “%7B” y “%7D”, respectivamente,  

 A continuación se indican los parámetros de cadena de consulta que se usan con la página main.aspx para abrir formularios o vistas de entidad:  


|  Parámetro   |                                                                                                                                                                                                                                                                                                                                            Descripción                                                                                                                                                                                                                                                                                                                                            |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **etn**    |                                                                                                                                                                                                                                    El nombre lógico de la entidad. **Importante:** no use el parámetro **etc** (código de tipo de entidad) que contiene un código entero para la entidad. El código entero varía para las entidades personalizadas de distintas organizaciones.                                                                                                                                                                                                                                     |
| **extraqs**  |     Opcional para formularios. Este parámetro contiene parámetros codificados en este parámetro.<br /><br /> Use este parámetro para transferir valores a un formulario. Para obtener más información, consulte [Establecer los valores de campo mediante parámetros que se pasan a un formulario](set-field-values-using-parameters-passed-form.md).<br /><br /> Cuando una entidad tiene más de un formulario definido, puede usar este parámetro para especificar qué formulario se debe abrir pasando el parámetro codificado `formid` con el valor igual al valor del identificador del formulario. Por ejemplo, para abrir un formulario con el identificado ‘6009c1fe-ae99-4a41-a59f-a6f1cf8b9daf’, incluya este valor en el parámetro `extraqs`: `formid%3D6009c1fe-ae99-4a41-a59f-a6f1cf8b9daf%0D%0A`.     |
| **pagetype** |                                                                                                                                                                                                                                                        El tipo de página. Hay dos valores posibles:<br /><br /> - **entityrecord**<br />     Muestra un formulario de registro de la entidad.<br />- **entitylist**<br />     Muestra una vista de entidad.                                                                                                                                                                                                                                                         |
|    **id**    |                                                                                                                                                                      Opcional para formularios. Utilícelo cuando abra un registro de entidad específico. Pase el identificador GUID codificado de la entidad. La versión codificada del GUID sustituirá las llaves de apertura y cierre “{” y “}” por “%7B” y “%7D”, respectivamente, por ejemplo `{91330924-802A-4B0D-A900-34FD9D790829}` is `%7B91330924-802A-4B0D-A900-34FD9D790829%7D`.                                                                                                                                                                      |
|  **viewid**  |                                                                                                                                                                                                        Necesario para vistas. Este es el identificador del registro de entidad `savedquery` o `userquery` que define la vista. La forma más fácil de obtener la dirección URL de una vista es copiarla. Para obtener más información, consulte [Copiar la dirección URL de una vista](open-forms-views-dialogs-reports-url.md#BKMK_CopyViewURL).                                                                                                                                                                                                         |
| **viewtype** |                                                                                                                                                                                                        Define el tipo de vista. Los valores posibles son los siguientes:<br /><br /> - **1039**<br />     Úselo para una vista de sistema. El parámetro `viewid` representa el identificador de un registro `savedquery`.<br />- **4230**<br />     Úselo para una vista personal. El parámetro `viewid` representa el identificador de un registro `userquery`.                                                                                                                                                                                                         |
|   `navbar`   | Controla si la barra de navegación se muestra y si la navegación por la aplicación está disponible mediante las áreas y subáreas definidas en el mapa del sitio.<br /><br /> -   `on`<br />     Se muestra la barra de navegación. Este es el comportamiento predeterminado si el parámetro `navbar` no se usa.<br />-   `off`<br />     No se muestra la barra de navegación. Los usuarios pueden navegar usando otros elementos de la interfaz de usuario o los botones adelante y atrás.<br />-   `entity`<br />     En un formulario de entidad, solo las opciones de navegación de entidades relacionadas están disponibles. Después de navegar a una entidad relacionada, se muestra un botón atrás en la barra de navegación para permitir volver al registro original. |
|   `cmdbar`   |                                                                                                                Controla si se muestra la barra de comandos. **Nota**: esta función admite los requisitos de la aplicación de Unified Service Desk. No se admite su uso para mostrar un formulario de entidad en un IFrame incrustado en otro formulario de entidad. <br /><br /> -   `true`<br />     Se muestra la barra de comandos. Esta es la configuración predeterminada.<br />-   `false`<br />     Se oculta la barra de comandos.                                                                                                                |

<a name="BKMK_CopyViewURL"></a>   
### <a name="copy-the-url-for-a-view"></a>Copia de la dirección URL para una vista  
 Muchas vistas de aplicaciones basadas en modelos permiten a un usuario copiar la dirección URL de una vista determinada o enviar un correo electrónico con la dirección URL de una vista determinada incrustada en el mensaje. Esta característica facilita la comunicación entre usuarios, y expone una forma de obtener acceso a una dirección URL para una vista que los usuarios pueden incluir en otra aplicación, como un sitio de SharePoint.  

> [!NOTE]
>  No use esta dirección URL para incluir la vista en la navegación de la aplicación mediante el mapa del sitio. Para obtener más información, consulte [Mostrar una vista en la navegación de la aplicación con el mapa del sitio](open-forms-views-dialogs-reports-url.md#BKMK_DisplayViewInApplicationUsingSiteMap).  

 La página mostrada por la dirección URL incluye la vista completa. Esto incluye la cinta de opciones, pero no la navegación de la aplicación.  

##### <a name="get-the-url-for-a-view"></a>Obtención de la dirección URL para una vista  

1. Abra la vista que desea usar.  

2. En la barra de comandos, haga clic en **Enviar un vínculo** y, a continuación, en **De la vista actual**.  

3. Péguelo en el Bloc de notas y edítelo para extraer solo la parte de la dirección URL del texto que desee.  

> [!NOTE]
> - Las vistas que usan el contexto del usuario como un parámetro, como **Mis cuentas**, no se pueden copiar.  
>   - El GUID que representa vistas del sistema para las entidades del sistema será igual para todas las instalaciones. El GUID para las entidades y vistas personalizadas será único para cada instalación de .  

<a name="BKMK_DisplayViewInApplicationUsingSiteMap"></a>   
### <a name="display-a-view-in-the-application-navigation-using-the-site-map"></a>Visualización de una vista en la navegación de la aplicación mediante el mapa del sitio  
 Al personalizar la navegación por la aplicación mediante el mapa del sitio, no use la dirección URL de la vista que copió de la aplicación con los pasos descritos en [Copiar la dirección URL de una vista](open-forms-views-dialogs-reports-url.md#BKMK_CopyViewURL) para establecerla como dirección URL. Esta dirección URL muestra una página que incluye la cinta de opciones y genera resultados indeseables si se usa en un atributo de URL `<SubArea>`.  

 Para mostrar una lista de registros de entidades dentro de la aplicación para una subárea, establezca el valor del atributo Entity. Esto muestra la vista predeterminada para esa entidad y proporciona el título y el icono correctos.  

 Sin embargo, si desea tener un elemento SubArea que use una vista determinada predeterminada inicial específica, use el patrón de URL siguiente.  

```xml  
Url=“/_root/homepage.aspx?etn=<entity logical name >&amp;viewid=%7b<GUID value of view id>%7d”  
```  

 Al usar esta dirección a URL, también debe especificar los valores adecuados para `<Titles>` y `<Descriptions>`, y especificar un icono para la entidad.  

> [!NOTE]
>  Si especifica la vista mediante la página `/_root/homepage.aspx`, el selector de vista seguirá mostrándose. Si el usuario cambia la vista, la aplicación basada en modelos recuerda la selección más reciente y muestra la vista predeterminada inicial una vez que cierre y reinicie de nuevo el explorador.  

<a name="BKMK_OpenADialogProcess"></a>   
## <a name="opening-a-dialog-process-by-using-a-url"></a>Apertura de un proceso de diálogo mediante una dirección URL  
 Una personalización común es permitir que un usuario abra un determinado proceso de diálogo en el contexto de un registro específico. Por ejemplo, es posible que desee agregar un botón personalizado a la cinta de opciones para una entidad específica usando el valor del identificador del registro actual como un parámetro de entrada del proceso de diálogo.  

 Para abrir un diálogo necesita lo siguiente:  

-   El identificador único del diálogo.  

-   El nombre lógico de la entidad para la que se crea el diálogo.  

-   El identificador único del registro en el que desea que se ejecute el diálogo.  

> [!TIP]
>  Para obtener el identificador único del diálogo, vaya a **Configuración**, en la solución predeterminada seleccione **Procesos**. Seleccione un proceso y en las opciones **Acciones** de la barra de comandos, haga clic en **Copiar un enlace**. Esto copiará un vínculo para modificar el diálogo en el portapapeles, por ejemplo, *[[URL de la organización]]*`/sfa/workflow/edit.aspx?id=%7b6A6E93C9-1FE6-4C07-91A9-E0E2A7C70976%7d`.  

 El siguiente ejemplo muestra los parámetros de la dirección URL y la cadena de consulta para abrir un diálogo:  

```
[organization url]/cs/dialog/rundialog.aspx?DialogId=[dialog unique identifier]&EntityName=[entity logical name]&ObjectId=[unique identifier for the record]  
```  

 Por ejemplo, para abrir el diálogo con identificador ={6A6E93C9-1FE6-4C07-91A9-E0E2A7C70976} con el identificador de registro de cuenta = {40C9ADFD-90A8-DF11-840E-00155DBA380F}, utilice la dirección URL del siguiente ejemplo.  

```
[organization url]/cs/dialog/rundialog.aspx?DialogId=%7b6A6E93C9-1FE6-4C07-91A9-E0E2A7C70976%7d&EntityName=account&ObjectId=%7b40C9ADFD-90A8-DF11-840E-00155DBA380F%7d  
```  

> [!TIP]
>  En los exploradores que no sean Internet Explorer, si un proceso de diálogo se abre desde un vínculo, es posible que el botón **Finalizar** no funcione. Los datos se guardarán, pero el usuario deberá hacer clic en el botón **Cerrar** en la ventana para cerrarla. Esto se debe a que otros exploradores no proporcionan un método `window.close` si la ventana no se abre usando JavaScript desde otra ventana. Siempre que sea posible, use JavaScript y el método `window.open` para abrir procesos de diálogo en lugar de simplemente proporcionar vínculos.  

 Puede crear una función de JavaScript para abrir el diálogo como se muestra en el siguiente ejemplo:  

```javascript  
function openDialogProcess(dialogId, entityName, objectId)  
{  
 var url = Xrm.Page.context.getClientUrl() +  
  "/cs/dialog/rundialog.aspx?DialogId=" +  
  dialogId + "&EntityName=" +  
  entityName + "&ObjectId=" +  
  objectId;  
 window.open(url);  
}  
```  

<a name="BKMK_OpenReportWithURL"></a>   
## <a name="opening-a-report-by-using-a-url"></a>Apertura de un informe mediante una dirección URL  
 Puede abrir un informe pasando valores de parámetros apropiados la siguiente dirección URL: `[organization url]/crmreports/viewer/viewer.aspx`.  

 Esta dirección URL acepta los siguientes parámetros:  

 **acción**  
 Dos valores posibles para este parámetro son `run` o `filter`. Si se utiliza `run`, el informe se mostrará usando los filtros predeterminados. Cuando se usa, `filter` el informe muestra un filtro que el usuario puede modificar antes de elegir el botón **Ejecutar informe** para ver el informe.  

 **helpID**  
 Este parámetro es opcional. Para los informes incluidos en las aplicaciones basadas en modelos el valor de este parámetro permite que el botón **Ayuda** muestre contenido apropiado sobre este informe cuando se selecciona **Ayuda de esta página**. El valor debe corresponder al valor de atributo `FileName` del informe.  

 **id**  
 Este parámetro es el valor del atributo `ReportId` del informe.  

 Los siguientes ejemplos muestran las direcciones URL que se pueden usar para abrir informes en MDA.  

 Abra el informe **Casos sin atender** mediante el filtro predeterminado:  
 ```  
 [organization url]/crmreports/viewer/viewer.aspx?action=run&helpID=Neglected%20Cases.rdl&id=%7b8c9f3e6f-7839-e211-831e-00155db7d98f%7d  
 ```  

 Abra el informe **Mejores artículos de Knowledge Base** e indique al usuario que establezca valores de filtro:  
 ```  
 [organization url]/crmreports/viewer/viewer.aspx?action=filter&helpID=Top%20Knowledge%20Base%20Articles.rdl&id=%7bd84ec390-7839-e211-831e-00155db7d98f%7d  
 ```  

 La función siguiente muestra cómo codificar valores correctamente en la dirección URL:  

```javascript  
function getReportURL(action,fileName,id) {  
 var orgUrl = GetGlobalContext().getClientUrl();  
 var reportUrl = orgUrl +   
  "/crmreports/viewer/viewer.aspx?action=" +  
  encodeURIComponent(action) +  
  "&helpID=" +  
  encodeURIComponent(fileName) +  
  "&id=%7b" +  
  encodeURIComponent(id) +  
  "%7d";  
 return reportUrl;  
}  
```  

### <a name="see-also"></a>Vea también   
 [Establecer valores de campo usando parámetros pasados a un formulario](set-field-values-using-parameters-passed-form.md)   
 [Configurar un formulario para aceptar parámetros querystring personalizados](configure-form-accept-custom-querystring-parameters.md)    
 [Personalizar la cinta de opciones](customize-commands-ribbon.md)<br/>
 [Scripting del cliente con JavaScript](client-scripting.md)<br/>
 [Recursos web](web-resources.md)<br/> 
 [Ampliar el cliente](/dynamics365/customer-engagement/developer/extend-client)<br/> 
 [Cambiar navegación de la aplicación con el mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap)<br/> 
 [Iniciar un diálogo mediante una dirección URL](/dynamics365/customer-engagement/developer/actions-dialogs#StartDialog)
