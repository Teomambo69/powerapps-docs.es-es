---
title: Administrar documentos de SharePoint en un portal | MicrosoftDocs
description: Instrucciones para la administración de documentos de SharePoint en un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d774b3ccd584cdf9872979d2df09eb49cff926df
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977421"
---
# <a name="manage-sharepoint-documents"></a>Administrar documentos de SharePoint

Common Data Service admite la integración de [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] que le habilita a usar las funcionalidades de administración de documentos de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] desde Common Data Service. Los portales de Power Apps ahora admiten cargar y mostrar documentos desde y hacia [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] directamente en un formulario de entidad o formulario web en un portal. Esto permite que los usuarios del portal vean , descarguen, agreguen y eliminen documentos de un portal. Los usuarios del portal también pueden crear subcarpetas para organizar sus documentos.

> [!NOTE]
> - La administración de documentos solo fuinciona con [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)].
> - Se admiten a la administración de documentos con la integración basada en servidor.

Para trabajar con las funcionalidades de la administración de documentos de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] dentro de Common Data Service debe:

1.  [Habilitar la función de administración de documentos en aplicaciones basadas en modelo en Dynamics 365](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [Configurar la integración de SharePoint del centro de administración de portales Power Apps](#step-2-set-up-sharepoint-integration-from-power-apps-portals-admin-center)

3.  [Habilitar la administración de documentos para entidades](#step-3-enable-document-management-for-entities)

4.  [Configurar el formulario correspondiente en documentos de Power Apps](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [Crear el permiso de entidad adecuado y asignarlo al rol web adecuado](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>Paso 1: Habilitar la función de administración de documentos en aplicaciones basadas en modelo en Dynamics 365

Debe habilitar la funcionalidad de administración de documentos en aplicaciones basadas en modelo en Dynamics 365 mediante la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] basada en servidor. La integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] basada en servidor permite a aplicaciones basadas en modelo en Dynamics 365 y [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] realizar una conexión entre servidores. El portal usa el registro del sitio [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] predeterminado. Para obtener información sobre cómo habilitar funcionalidades de administración de documentos en aplicaciones basadas en modelo en Dynamics 365, consulte [Configurar aplicaciones basadas en modelo en Dynamics 365 para usar SharePoint Online](https://docs.microsoft.com/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online).

## <a name="step-2-set-up-sharepoint-integration-from-power-apps-portals-admin-center"></a>Paso 2: Configurar la integración de SharePoint del centro de administración de portales de Power Apps

Para usar las funcionalidades de administración de documentos de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)], debe habilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] desde el centro de administración de portales de Power Apps.

> [!NOTE]
> Debe ser un administrador global para realizar esta acción.

1. Abra [Centro de administración de Portales de Power Apps](admin/admin-overview.md).

2.  Vaya a **Configurar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]** > **Habilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]**.

    > [!div class=mx-imgBorder]
    > ![Habilitar la integración de SharePoint](media/enable-sharepoint-integration.png "Habilitar la integración de SharePoint")

3.  Seleccione **Habilitar** en la ventana de confirmación. Esto permitirá al portal comunicarse con [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]. Mientras la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] está siendo activada, el portal se reiniciará y no estará disponible durante unos minutos. Aparece un mensaje cuando la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] está habilitada.

Cuando la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] se habilita, la acción siguiente está disponible:

- **Deshabilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]**: Le permite deshabilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] con su portal. Mientras la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] está siendo desactivada, el portal se reiniciará y no estará disponible durante unos minutos. Aparece un mensaje cuando la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] está desactivada.

    > [!div class=mx-imgBorder]
    > ![Deshabilitar la integración de SharePoint](media/disable-sharepoint-integration.png "Deshabilitar la integración de SharePoint")

Al habilitar o deshabilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] actualizará la aplicación [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD) para el portal y agregará o quitará los permisos de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] necesarios, respectivamente. También se le redirigirá para dar su consentimiento para que se realicen los cambios en la aplicación [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD. 

> [!div class=mx-imgBorder]
> ![Deshabilitar la integración de SharePoint](media/sharepoint-integration-consent.png "Deshabilitar la integración de SharePoint")

Si no da su consentimiento:

- La habilitar o deshabilitación de la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] no se completará y se mostrará un mensaje de error.

- Su inicio de sesión de [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD en el portal no funcionará. 


## <a name="step-3-enable-document-management-for-entities"></a>Paso 3: Habilitar la administración de documentos para entidades
Debe permitir que la administración de documentos para entidades almacene documentos relacionados con registros de entidad en [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]. Para obtener información sobre cómo habilitar la administración de documentos para entidades, consulte [Habilitar la administración de documentos de SharePoint para entidades específicas](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities).

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>Paso 4: Configurar el formulario apropiado para mostrar documentos

### <a name="power-apps-customization"></a>Power Apps personalización

Identifique el formulario donde desea usar funcionalidades de administración de documentos. Debe editar el formulario usando el editor de formularios de aplicaciones basadas en formulario y agregarle una subcuadrícula. El subcuadrícula agrega una sección al formulario, lo que le permite trabajar con documentos desde un portal. Debe establecer las siguientes propiedades en la subcuadrícula para que esta característica funcione:

- En **Origen de datos**, seleccione **Ubicaciones de documentos** del lista **Entidad**.

- En **Origen de datos**, seleccione **Ubicaciones de documentos activos** del lista **Vista predeterminada**.

Puede especificar el nombre y la etiqueta según sus necesidades. Guarde y publique el formulario una vez que se haya agregado y configurado la subcuadrícula.

> [!NOTE]
> La administración de documentos debe estar habilitada para la entidad para la que edita el formulario. Más información: [Habilitar la administración de documentos para entidades](#step-3-enable-document-management-for-entities)

### <a name="power-apps-portals-configuration"></a>Configuración de portales de Power Apps

Aparte de la configuración estándar necesaria para el formulario de entidad o el formulario web, debe establecer las siguientes propiedades para habilitar la administración de documentos:

- **Nombre de entidad** y **Nombre del formulario**: Especifique los nombres de la entidad y formulario personalizados en el paso anterior, respectivamente.

- Seleccione la casilla de verificación **Habilitar permiso de entidad** en el formulario para permitir que un usuario lea los documentos.

- Establezca el **Modo** en **Editar** para permitir cargas de documentos.

> [!NOTE]
> La carga de documentos requiere que el registro de la entidad principal exista. Si establece el modo de inserción, la carga del documento no funcionará porque el registro de la entidad principal no se creará hasta que se haya enviado el formulario.

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>Paso 5: Crear el permiso de entidad adecuado y asignarlo al rol web adecuado

Se necesitan dos registros de permiso de entidad para establecer el acceso necesario para ver y para cargar documentos.

- Permisos en la entidad del formulario de entidad o el formulario web: 
    - Cree un registro de **Permiso de entidad** que especifique el **Nombre de entidad** como la entidad del formulario de entidad o el formulario web configurado anteriormente. 
    - Seleccione un **Ámbito** y una relación de ámbito que sea adecuado al comportamiento que desee en el formulario. 
    - Habilite los privilegios **Leer** y **Anexar a** para permitir acceso de lectura de los documentos y habilitar opcionalmente el privilegio de **Escribir** para permitir cargas de documentos. Omita la sección **Permisos de entidad secundaria** por ahora, ya que se rellenará en el paso siguiente.
- Permisos en la **Ubicación de documentos** con el **Ámbito primario** que hace referencia al anterior registro del permiso: 
    - Cree un registro de **Permisos de entidad** que especifique el **Nombre de entidad** como entidad de **Ubicación de documentos** con **Ámbito** establecido como **Primario**. 
    - Seleccione el permiso de entidad primaria para el registro de permiso de entidad creado en el paso anterior. 
    - Privilegios 
        - Los privilegios mínimos para permitir acceso de lectura a los documentos son **Leer**, **Crear** y **Anexar**. 
        - Incluya privilegios de **Escribir** para el acceso a la carga de documentos. 
        - Incluya **Eliminar** para permitir la eliminación de un documento.

> [!NOTE]
> Un permiso de entidad secundaria correspondiente en la entidad **Ubicación de documentos** debe haberse creado para cada instancia de registro de permiso de entidad primaria que exista en la entidad de formulario de entidad o formulario web donde los documentos se deben mostrar.

## <a name="configure-file-upload-size"></a>Configure el tamaño del archivo de carga

De manera predeterminada, el tamaño del archivo se establece en 10 MB. Sin embargo, puede configurar el tamaño del archivo hasta un máximo de 50 MB usando la configuración del sitio `SharePoint/MaxUploadSize`.

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>Configuración de ejemplo para habilitar la administración de documentos en el formulario de entidad Caso

El siguiente ejemplo demuestra la configuración utilizando la entidad Caso que necesita la aplicación Dynamics 365 Customer Service como requisito previo. Aunque este ejemplo usa la entidad Caso, sólo es una ilustración de los pasos mencionados y se puede seguir con cualquier otra entidad personalizada o cualquier entidad de Common Data Service que admita la administración de documentos en SharePoint. 

1.  Siga las instrucciones en [Paso 1](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365) para asegurarse de que la configuración basada en servidor está completa para aplicaciones basadas en modelo en la integración de Dynamics 365 y [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)].

2.  Siga las instrucciones en [Paso 2](#step-2-set-up-sharepoint-integration-from-power-apps-portals-admin-center) para asegurarse de que el portal tiene permisos para integrarse con [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]. 

3.  Siga las instrucciones en [Paso 3](#step-3-enable-document-management-for-entities) para asegurarse de que la administración de documentos está habilitada para la entidad Caso.

4.  Siga las instrucciones en [Paso 4](#step-4-configure-the-appropriate-form-to-display-documents) con las siguientes configuraciones:

    - Aplicaciones basadas en modelo en la personalización de Dynamics 365

        a. Vaya a **Personalizaciones** > **Personalización** > **Personalización del sistema**. 

        b. In la **Solución predeterminada**, vaya a **Caso** entidad > **Formularios**. 
    
        c. Abra **Web – editar Caso** en el editor de formularios.

         > [!div class=mx-imgBorder]
         > ![Web - Editar el formulario de caso](media/web-edit-case-form.png "Web - Editar el formulario de caso")
    
        d. Seleccione el campo **Creado en** en el formulario y, en la pestaña **Insertar** , seleccione **Subcuadrícula**.

         > [!div class=mx-imgBorder]
         > ![Agregar un subcuadrícula a Web - editar el formulario de caso](media/add-sub-grid.png "Agregar un subcuadrícula a Web - editar el formulario de caso")
    
        e. En el cuadro de diálogo **Establecer propiedades**, defina las siguientes propiedades y seleccione **Aceptar**:

         - **Nombre** (Puede ser cualquier nombre): CaseDocuments 
    
         - **Etiqueta** (Puede ser cualquier nombre de etiqueta): Documentos de Caso 
      
         - **Entidad**: Ubicaciones de documentos 
    
         - **Vista predeterminada**: Ubicaciones de documentos activos

         > [!div class=mx-imgBorder]
         > ![Propiedades de subcuadrícula](media/sub-grid-properties.png "Propiedades de subcuadrícula")

        f. En el editor de formularios, seleccione **Guardar** y, después, seleccione **Publicar**.

    - Configuración de portales de Power Apps

        a. Vaya a **Portales** > **Formularios de entidad**.
    
        b. Busque y abra el el formulario de entidad **Servicio al cliente - Editar Caso**.
    
        c. Revise y asegúrese de que están establecidas las siguientes las propiedades:
    
         - **Nombre de entidad**: Caso (incidente)
    
         - **Nombre del formulario**: Web – Editar Caso
    
         - **Modo**: Editar
    
         - **Permisos de entidad**: Habilitados
    
         > [!div class=mx-imgBorder]
         > ![Customer Service: editar formulario de caso](media/customer-service-edit-case-form.png "Customer Service: editar formulario de caso")
    
        d. Si ha realizado algún cambios en el formulario, seleccione **Guardar**.

5. Siga [Paso 5](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
) para asegurarse de que los permisos de entidad se conceden a los usuarios.

   1. Vaya al registro **Rol web** que está asociado al usuario. Para este ejemplo, asumiremos que el usuario tiene un rol web de administrador.

   2. Asegúrese de que existe un registro de permiso de entidad con el nombre de **Servicio al cliente - Casos en los que el contacto es cliente**. 

      > [!NOTE]
      > Asegúrese de que su rol web tenga este permiso de entidad agregado. Si el usuario ya es un administrador, el permiso de entidad anterior no necesita ser asignado explícitamente.

   3. Cree un nuevo permiso de entidad, especifique los siguientes detalles y seleccione **Guardar**:

    - **Nombre** (Puede ser cualquier nombre): Servicio al cliente - Documentos relacionados

    - **Nombre de entidad**: Ubicación de documentos
        
    - **Ámbito**: Primario
        
    - **Permiso de entidad primaria**: Servicio de atención al cliente - casos en los que el contacto es el cliente
        
    - **Relación primaria**: incident_SharePointDocumentLocations
        
    - **Privilegios**: Leer, Crear, Anexar, Escribir, Eliminar

      > [!div class=mx-imgBorder]
      > ![Permiso de entidad de Customer Service](media/customer-service-entity-permission.png "Permiso de entidad de Customer Service")
  
   4. Inicie sesión en el portal para asegurarse de que la administración de documentos esté habilitada para la entidad Caso.

      a. Vaya a la página **Soporte**.

      > [!div class=mx-imgBorder]
      > ![Página de soporte del portal](media/portal-support-page.png "Página de soporte del portal")

      b. Haga clic en un registro de Caso existente de la lista. Vaya a la sección **Documentos de Caso** en la página y vea la lista de documentos agregada.

      > [!div class=mx-imgBorder]
      > ![Documento del caso](media/case-document.png "Documento del caso")

