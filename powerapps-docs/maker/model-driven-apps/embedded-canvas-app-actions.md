---
title: Realice acciones en el formulario de host desde una aplicación de lienzo insertada | MicrosoftDocs
ms.custom: ''
ms.date: 03/29/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="perform-predefined-actions-on-the-host-form-from-within-an-embedded-canvas-app"></a>Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada
Las aplicaciones de lienzo incrustadas permiten realizar acciones predefinidas en el formulario de host. Estas acciones permiten a creadores navegar, actualizar y guardar el formulario de host. Con estas acciones, una aplicación de lienzo incrustada puede actuar como parte más integral del formulario y de la aplicación basada en modelos.  

> [!NOTE]
> Esta característica está actualmente en vista previa. <br />
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)] 

El objeto **ModelDrivenFormIntegration** ahora incluye los siguientes nuevos métodos para permitir a los creadores realizar acciones en el formulario de host.  
  
### <a name="navigatetomainformentityname-mainformname-recordid"></a>NavigateToMainForm(entityName, mainFormName, recordId)
Navega el formulario de host a un formulario principal y muestra el registro especificado.  
* **entityName** - Parámetro de cadena requerido que especifica la entidad principal del formulario principal.  
* **formName** - Parámetro de cadena requerido que especifica el nombre del formulario principal al que navegar.  
* **recordId** - Parámetro de cadena requerido que especifica el identificador del registro para mostrar en el formulario principal.  
 
Al llamar al método NavigateToMainForm se pueden mostrar los siguientes mensajes de error.
  
| Mensaje de error | Instrucciones para la resolución de problemas |
|:--------------|:-------------------------|
|**No se encuentra la entidad: *[EntityName]*** | Compruebe el valor del parámetro *entityName* y asegúrese de que es un nombre de entidad válido y que el usuario tiene acceso a él. |
|**No se encuentra el formulario: *[FormName]*** | Compruebe el valor del parámetro *mainFormName* y asegúrese de que es un nombre de formulario principal y que el usuario tiene acceso a él. |
|**Se produjo un problema al cargar el registro.** | Compruebe el valor del parámetro *recordId* y asegúrese de que es un identificador de registro válido y que el usuario tiene acceso a él. |
  
  
### <a name="navigatetoviewentityname-viewname"></a>NavigateToView(entityName, viewName)
Navega el formulario de host a una vista.  
* **entityName** - Parámetro de cadena requerido que especifica la entidad principal de la vista.  
* **viewName** - Parámetro de cadena requerido que especifica el nombre del formulario principal al que navegar.  
 
Al llamar al método NavigateToView se pueden mostrar los siguientes mensajes de error.
  
| Mensaje de error | Instrucciones para la resolución de problemas |
|:--------------|:-------------------------|
|**No se encuentra la entidad: *[EntityName]*** | Compruebe el valor del parámetro *entityName* y asegúrese de que es un nombre de entidad válido y que el usuario tiene acceso a él. |
|**No se encuentra la vista: *[ViewName]*** | Compruebe el valor del parámetro *viewName* y asegúrese de que es un nombre de vista válido y que el usuario tiene acceso a él. |
  
  
### <a name="openquickcreateformentityname"></a>OpenQuickCreateForm(entityName)  
Abre el formulario de creación rápida predeterminado para una entidad.  
* **entityName** - Parámetro de cadena requerido que especifica la entidad principal del formulario de creación rápida.  
 
Al llamar al método OpenQuickCreateForm se pueden mostrar los siguientes mensajes de error.
  
| Mensaje de error | Instrucciones para la resolución de problemas |
|:--------------|:-------------------------|
|**No se encuentra la entidad: *[EntityName]*** | Compruebe el valor del parámetro *entityName* y asegúrese de que es un nombre de entidad válido y que el usuario tiene acceso a él. |
  
  
### <a name="refreshformshowprompt"></a>RefreshForm(showPrompt)  
Actualiza los datos en el formulario de host.  
* **showPrompt** - Parámetro booleano requerido que indica si un mensaje de confirmación se debe mostrar al usuario antes de guardar los datos sin guardar en el formulario de host. Los valores de deben ser “True “o “False”.
 
Al llamar al método RefreshForm se pueden mostrar los siguientes mensajes de error.
  
| Mensaje de error | Instrucciones para la resolución de problemas |
|:--------------|:-------------------------|
|**Utilice "true" o "false" como valor del parámetro.** | Compruebe el valor del parámetro *showPrompt* y asegúrese que es ”True” o ”False”. |
  
  
### <a name="saveform"></a>SaveForm()  
Guarda los datos en el formulario de host.  


> [!NOTE]
> Si no ve IntelliSense en los métodos para realizar acciones predefinidas en las aplicaciones de lienzo incrustadas que se crearon antes de que la funcionalidad estuviera disponible; guarde, cierre y vuelva a abrir la aplicación. 

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Pasar el registro actual como contexto de datos a una aplicación incrustada de lienzo](pass-current-embedded-canvas-app.md) <br />
[Pasar una lista de registros relacionados como contexto de datos a una aplicación incrustada de lienzo](pass-related-embedded-canvas-app.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md)
