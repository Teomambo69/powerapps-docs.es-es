---
title: Administrar documentos de SharePoint en un portal | MicrosoftDocs
description: Instrucciones para administrar el documento de SharePoint en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ab51a2b1a309921e32949a806adb4a7bf3273ccf
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974699"
---
# <a name="manage-sharepoint-documents"></a>Administración de documentos de SharePoint

Common Data Service admite la integración con [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] que permite usar las funciones de administración de documentos de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] desde Common Data Service. Los portales de PowerApps ahora admiten la carga y visualización de documentos en y desde [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] directamente en un formulario de la entidad o formulario web en un portal. Esto permite a los usuarios del portal ver, descargar, agregar y eliminar documentos desde un portal. Los usuarios del portal también pueden crear subcarpetas para organizar sus documentos.

> [!NOTE]
> - La administración de documentos solo funciona con [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)].
> - La administración de documentos es compatible con la integración basada en servidor.

Para trabajar con las capacidades de administración de documentos de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] dentro de Common Data Service, debe:

1.  [Habilitar la funcionalidad de administración de documentos en aplicaciones controladas por modelos en Dynamics 365](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [Configuración de la integración de SharePoint desde el centro de administración de portales de PowerApps](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)

3.  [Habilitar la administración de documentos para entidades](#step-3-enable-document-management-for-entities)

4.  [Configurar el formulario adecuado en documentos de PowerApps](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [Crear el permiso de entidad adecuado y asignarlo al rol Web adecuado](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>Paso 1: habilitar la funcionalidad de administración de documentos en aplicaciones controladas por modelos en Dynamics 365

Debe habilitar la funcionalidad de administración de documentos en las aplicaciones controladas por modelos en Dynamics 365 mediante la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] basado en servidor. La integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] basado en servidor permite que las aplicaciones controladas por modelos en Dynamics 365 y [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] realicen una conexión de servidor a servidor. El portal utiliza el registro de sitio de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] predeterminado. Para obtener información sobre cómo habilitar la funcionalidad de administración de documentos en las aplicaciones controladas por modelos en Dynamics 365, consulte [configuración de aplicaciones controladas por modelos en dynamics 365 para usar SharePoint Online](https://docs.microsoft.com/en-us/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online).

## <a name="step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center"></a>Paso 2: configurar la integración de SharePoint desde el centro de administración de portales de PowerApps

Para usar las funcionalidades de administración de documentos de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)], debe habilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] desde el centro de administración de portales de PowerApps.

> [!NOTE]
> Debe ser un administrador global para realizar esta acción.

1. Abra el [centro de administración de portales de PowerApps](admin/admin-overview.md).

2.  Vaya a **configuración de la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]**  > **Habilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]** .

    > [!div class=mx-imgBorder]
    > ![Habilitar la integración de SharePoint](media/enable-sharepoint-integration.png "Habilitar la integración de SharePoint")

3.  Seleccione **Habilitar** en la ventana de confirmación. Esto permitirá al portal comunicarse con [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]. Mientras se habilita la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)], el portal se reinicia y no estará disponible durante unos minutos. Aparece un mensaje cuando se habilita la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)].

Cuando se habilita la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)], la siguiente acción está disponible:

- **Deshabilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]** : permite deshabilitar la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] con el portal. Mientras se deshabilita la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)], el portal se reinicia y no estará disponible durante unos minutos. Aparece un mensaje cuando se deshabilita la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)].

    > [!div class=mx-imgBorder]
    > ![Deshabilitar la integración de SharePoint](media/disable-sharepoint-integration.png "deshabilitar la integración de SharePoint")

La habilitación o deshabilitación de la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] actualizará la aplicación [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD) del portal y agregará o quitará los permisos [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] necesarios, respectivamente. También se le redirigirá para proporcionar su consentimiento para que los cambios se realicen en la aplicación [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD. 

> [!div class=mx-imgBorder]
> ![Deshabilitar la integración de SharePoint](media/sharepoint-integration-consent.png "deshabilitar la integración de SharePoint")

Si no proporciona su consentimiento:

- La habilitación o deshabilitación de la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] no se completará y se mostrará un mensaje de error.

- No funcionará el inicio de sesión [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] de AD en el portal. 


## <a name="step-3-enable-document-management-for-entities"></a>Paso 3: habilitar la administración de documentos para entidades
Debe habilitar la administración de documentos para que las entidades almacenen documentos relacionados con registros de entidad en [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]. Para obtener información sobre cómo habilitar la administración de documentos para entidades, vea [Habilitar la administración de documentos de SharePoint para entidades específicas](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities).

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>Paso 4: configurar el formulario adecuado para mostrar documentos

### <a name="powerapps-customization"></a>Personalización de PowerApps

Identifique el formulario en el que desea utilizar las capacidades de administración de documentos. Debe editar el formulario mediante el editor de formulario de aplicación controlada por modelos y agregarle una subcuadrícula. La subcuadrícula agrega una sección al formulario, que le permite trabajar con documentos desde un portal. Debe establecer las siguientes propiedades en la subcuadrícula para que esta característica funcione:

- En **origen de datos**, seleccione **ubicaciones de documento** en la lista de **entidades** .

- En **origen de datos**, seleccione **ubicaciones de documentos activas** en la lista **vista predeterminada** .

Puede especificar el nombre y la etiqueta según sus necesidades. Guarde y publique el formulario una vez que se haya agregado y configurado la subcuadrícula.

> [!NOTE]
> La administración de documentos debe estar habilitada para la entidad para la que se edita el formulario. Más información: [Habilitar la administración de documentos para entidades](#step-3-enable-document-management-for-entities)

### <a name="powerapps-portals-configuration"></a>Configuración de portales de PowerApps

Además de la configuración estándar necesaria para el formulario de la entidad o el formulario Web Forms, debe establecer las siguientes propiedades para habilitar la administración de documentos:

- **Nombre** de la entidad y **nombre del formulario**: escriba los nombres de entidades y formularios personalizados en el paso anterior, respectivamente.

- Active la casilla **Habilitar permiso de entidad** en el formulario para permitir que un usuario Lea los documentos.

- Establezca el **modo** en **Editar** para permitir cargas de documentos.

> [!NOTE]
> La carga de documentos requiere que exista el registro de la entidad primaria. Si establece el modo en Insertar, la carga del documento no funcionará porque el registro de la entidad primaria no se crea hasta que se envía el formulario.

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>Paso 5: crear el permiso de entidad adecuado y asignarlo al rol Web adecuado

Se requieren dos registros de permisos de entidad para establecer el acceso necesario para ver y cargar documentos.

- Permisos en la entidad de la entidad o formulario web: 
    - Cree un registro de **permisos de entidad** que especifique el nombre de la **entidad** como la entidad del formulario de la entidad o del formulario web configurado previamente. 
    - Seleccione una **relación de ámbito y** ámbito que sea adecuada para el comportamiento deseado del formulario. 
    - Habilite los privilegios **leer** y **anexar** a para permitir el acceso de lectura a los documentos y habilitar opcionalmente el privilegio de **escritura** para permitir cargas de documentos. Omita la sección **permisos de entidad secundaria** de ahora, ya que se rellenará con el siguiente paso.
- Permisos en la **Ubicación del documento** con el **ámbito primario** que hace referencia al registro de permisos anterior: 
    - Cree un registro de **permisos de entidad** que especifique el nombre de la **entidad** como entidad de **Ubicación del documento** con el **ámbito** establecido en **principal**. 
    - Seleccione el permiso entidad primaria para el registro de permisos de entidad creado en el paso anterior. 
    - Privilegios 
        - Los privilegios mínimos para permitir el acceso de lectura a los documentos son **leer**, **crear**y **anexar**. 
        - Incluir privilegios de **escritura** para el acceso de carga de documentos. 
        - Incluye **Delete** para permitir la eliminación de un documento.

> [!NOTE]
> Es necesario crear un permiso de entidad secundaria correspondiente en la entidad **Ubicación del documento** para cada instancia del registro de permisos de la entidad primaria que existe en la entidad de la entidad o el formulario web en el que se deben mostrar los documentos.

## <a name="configure-file-upload-size"></a>Configurar el tamaño de carga de archivos

De forma predeterminada, el tamaño del archivo se establece en 10 MB. Sin embargo, puede configurar el tamaño de archivo en un máximo de 50 MB mediante el `SharePoint/MaxUploadSize`de configuración del sitio.

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>Configuración de ejemplo para habilitar la administración de documentos en el formulario de la entidad Case

En el ejemplo siguiente se muestra la configuración mediante la entidad case que necesita la aplicación de servicio de atención al cliente de Dynamics 365 como requisito previo. Aunque en este ejemplo se usa la entidad Case, es solo una ilustración de los pasos mencionados anteriormente y se puede seguir con cualquier otra entidad personalizada o con cualquier entidad Common Data Service que admita la administración de documentos en SharePoint. 

1.  Siga las instrucciones del [paso 1](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365) para asegurarse de que la configuración basada en servidor se ha completado para aplicaciones controladas por modelos en Dynamics 365 y la integración de [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)].

2.  Siga las instrucciones del [paso 2](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center) para asegurarse de que el portal tiene permisos para la integración con [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]. 

3.  Siga las instrucciones del [paso 3](#step-3-enable-document-management-for-entities) para asegurarse de que la administración de documentos está habilitada para la entidad Case.

4.  Siga las instrucciones del [paso 4](#step-4-configure-the-appropriate-form-to-display-documents) con las siguientes configuraciones:

    - Aplicaciones controladas por modelos en la personalización de Dynamics 365

        a. Vaya a **configuración** > **Personalización** > **personalizar el sistema**. 

        b. En la **solución predeterminada**, vaya a la entidad **Case** > **Forms**. 
    
        c. Abra el **Web: editar caso** en el editor de formularios.

         > [!div class=mx-imgBorder]
         > ![Web: formulario de edición de casos](media/web-edit-case-form.png "Web: formulario de edición web")
    
        d. Seleccione el campo **creado en** del formulario y, en la pestaña **Insertar** , seleccione **subcuadrícula**.

         > [!div class=mx-imgBorder]
         > ![Agregar una subcuadrícula al formulario de casos de edición web](media/add-sub-grid.png "Agregar una subcuadrícula al formulario de edición web")
    
        e. En el cuadro de diálogo **establecer propiedades** , establezca las siguientes propiedades y seleccione **Aceptar**:

         - **Nombre** (puede ser cualquier nombre): CaseDocuments 
    
         - **Etiqueta** (puede ser cualquier nombre de etiqueta): documentos de caso 
      
         - **Entidad**: ubicaciones del documento 
    
         - **Vista predeterminada**: ubicaciones de documentos activos

         > [!div class=mx-imgBorder]
         > Propiedades de ![subcuadrícula]propiedades de(media/sub-grid-properties.png "subcuadrícula")

        formato. En el editor de formularios, seleccione **Guardar** y, a continuación, seleccione **publicar**.

    - Configuración de portales de PowerApps

        a. Vaya a **portales** > **formularios de entidad**.
    
        b. Busque y Abra **Customer Service-Edit Case** Entity Form.
    
        c. Revise y asegúrese de que se establecen las siguientes propiedades:
    
         - **Nombre de entidad**: caso (incidente)
    
         - **Nombre del formulario**: Web: editar caso
    
         - **Modo**: editar
    
         - **Permiso de entidad**: habilitado
    
         > [!div class=mx-imgBorder]
         > ![Servicio de atención al cliente: Editar formulario de caso](media/customer-service-edit-case-form.png "de cliente: Editar formulario de caso")
    
        d. Si ha realizado algún cambio en el formulario, seleccione **Guardar**.

5. Siga el [paso 5](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
) para asegurarse de que los permisos de entidad se conceden a los usuarios.

   1. Vaya al registro de **rol Web** que está asociado al usuario. En este ejemplo, supondremos que el usuario tiene un rol Web de administrador.

   2. Asegúrese de que existe un registro de permisos de entidad por el nombre del **servicio de atención al cliente: casos en los que Contact es Customer**. 

      > [!NOTE]
      > Asegúrese de que el rol Web tiene agregado este permiso de entidad. Si el usuario ya es un administrador, no es necesario asignar explícitamente el permiso de entidad anterior.

   3. Cree un nuevo permiso de entidad, escriba los detalles siguientes y seleccione **Guardar**:

    - **Nombre** (puede ser cualquier nombre): documentos relacionados con el servicio de atención al cliente

    - **Nombre de entidad**: Ubicación del documento
        
    - **Ámbito**: principal
        
    - **Permisos de entidad primaria**: servicio de atención al cliente: casos en los que el contacto es cliente
        
    - **Relación primaria**: incident_SharePointDocumentLocations
        
    - **Privilegios**: leer, crear, anexar, escribir, eliminar

      > [!div class=mx-imgBorder]
      > Permiso de entidad del ![servicio de atención al cliente](media/customer-service-entity-permission.png "permiso de entidad de servicio")
  
   4. Inicie sesión en el portal para asegurarse de que la administración de documentos está habilitada para la entidad Case.

      a. Vaya a la página de **soporte técnico** .

      > [!div class=mx-imgBorder]
      > ![](media/portal-support-page.png "Página") de soporte técnico del portal página de soporte

      b. Haga clic en un registro de caso existente en la lista. Vaya a la sección **documentos de casos** en la página y vea la lista de documentos agregada.

      > [!div class=mx-imgBorder]
      > ![](media/case-document.png "Documento de caso") de documento de caso

