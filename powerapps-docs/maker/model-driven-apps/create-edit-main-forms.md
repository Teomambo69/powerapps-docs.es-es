---
title: Crear o editar formularios principales de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Aprenda a crear o editar un formulario principal.
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: <needs new guid>
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-a-model-driven-app-main-form-for-an-entity"></a>Crear o editar formularios principales de aplicaciones controladas por modelos 

En este tema aprenderá a crear o editar un formulario principal para una entidad.

Al crear un nuevo formulario para una entidad, el tipo de formulario es Principal. Cuando se abre el formulario principal, es idéntico al formulario denominado Información. Puede agregar o editar campos, secciones, pestañas, navegación y propiedades asociadas al formulario y, a continuación, guardar el formulario.

Cada formulario principal se compone de una o varias pestañas. Cada ficha tiene una o varias secciones. Cada sección contiene uno o varios campos o IFRAMES. Si desea basar su nuevo formulario en uno existente, puede clonar un formulario. 

Compruebe que tiene el rol de seguridad de Administrador del sistema o de Personalizador del sistema o permisos equivalentes para realizar esta tarea.

## <a name="how-to-create-or-edit-a-main-form"></a>Cómo crear o editar un formulario principal
  
1.   Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).


> [!IMPORTANT]
> “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment).   
  
2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**. 

3. Para crear un nuevo formulario principal, en la barra de herramientas seleccione **Agregar formulario** > **Formulario principal**.  
    \-O bien - Para editar un formulario principal existente, seleccione cualquiera de los formularios cuyo **Tipo** sea **Principal**.
  
3.  Cambie el diseño del formulario de cualquiera de las siguientes maneras, según corresponda:
    -   Adición de una ficha a un formulario
    -   Adición de secciones a un formulario
    -   Adición de campos a un formulario
    -   Agregar o editar un IFRAME de formulario
    -   Agregar o editar una subcuadrícula en un formulario
    -   Agregar o editar un recurso web de formulario
    -   Adición o edición de la navegación del formulario para las entidades relacionadas
    -   Edición de encabezados y pies de página de formularios
    -   Quitar una pestaña, sección, campo o IFRAME
    -   Habilitar o deshabilitar el Asistente de formulario
    
4.  Edite las propiedades de las partes del formulario según sea necesario:
    -   Edición de propiedades de formularios
    -   Edición de las propiedades de campos de formulario
    -   Edición de las propiedades de ficha
    -   Edición de las propiedades de sección

5.  Agregue los scripts de eventos que sea necesario. 

6.  Determine qué roles de seguridad podrán ver el formulario. Más información: [Asignar roles de seguridad a un formulario](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)

7.  *Muestre una vista previa del aspecto que tendrá el formulario principal y cómo funcionan los eventos:
    - En la ficha **Inicio**, seleccione **Vista previa** y, a continuación, seleccione **Formulario de creación**, **Formulario de actualización** o **Formulario de sólo lectura**.
    - Para cerrar el formulario Vista previa, en el menú **Archivo**, seleccione **Cerrar**.

8.  Cuando haya terminado de editar el formulario, seleccione **Guardar como**. Escriba un nombre para el formulario y, a continuación, seleccione **Aceptar**.

9.  Cuando haya completado las personalizaciones, publíquelas:
    -   Para publicar las personalizaciones únicamente para el componente que está editando actualmente, en **Componentes**, haga clic en la entidad en la que ha estado trabajando, y haga clic en **Publicar**.
    -   Para publicar personalizaciones de todos los componentes no publicados a la vez, en **Componentes**, haga clic en **Entidades** y, en la barra de comandos, haga clic en **Publicar todas las personalizaciones**.
    
 
### <a name="next-steps"></a>Pasos siguientes  
[Información general de la interfaz de usuario del editor de formularios](form-editor-user-interface-legacy.md)
 
