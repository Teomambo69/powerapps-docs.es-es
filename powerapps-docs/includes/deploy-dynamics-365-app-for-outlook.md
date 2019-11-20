---
title: Implementar Dynamics 365 App for Outlook | MicrosoftDocs
ms.custom: ''
ms.date: 2017-04-20
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
ms.assetid: 09736e14-e744-48ca-a755-1b05bb55340e
caps.latest.revision: 39
author: jimholtz
ms.author: jimholtz
manager: brycho
ms.openlocfilehash: 2df69eb2823726116ca08e893acf384afffdd957
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754143"
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>Implementar Dynamics 365 App for Outlook
Los usuarios pueden usar [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] para aprovechar la potencia de [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] mientras usan [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] en el escritorio, la web o tableta. Por ejemplo, vea información sobre los destinatarios de correo electrónico o cita, o vincule un correo electrónico o cita de [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] a un registro de [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] como una oportunidad, una cuenta o un caso. Para obtener más información acerca de qué ofrece [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)], consulte el [Manual del usuario de Dynamics 365 App for Outlook](https://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] no es igual que [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]. [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)], [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] emparejado con [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] es la forma preferida para integrar [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] con [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]. **Tenga en cuenta que el seguimiento de actividades no se admite si un usuario usa [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] y [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] juntos.** Para obtener información acera del complemento [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)], consulta el [Manual del usuario de Dynamics 365 for Outlook](https://go.microsoft.com/fwlink/p/?LinkID=524751).  
>   
>  [Los usuarios delegados](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540) no pueden usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] para realizar el seguimiento de los correos electrónicos. Se recomienda usar [seguimiento de nivel de carpeta o seguimiento automático](https://www.microsoft.com/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx) para los usuarios delegados.  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>Comparación de Dynamics 365 App for Outlook con Dynamics 365 for Outlook  
 La tabla siguiente compara las características de [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] con [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] (también conocido como cliente o complemento de [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]) a partir de [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)].  
  
||||  
|-|-|-|  
|**Característica**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|Seguir y establecer referencia para correo electrónico|Sí|Sí|  
|Seguir y establecer referencia para citas|Sí|Sí|  
|Seguir y establecer referencia para contactos|Sí|Sí|  
|Seguir y establecer referencia para tareas|No|Sí|  
|Establecer referente a en un clic|Sí|No|  
|Muestra resumen de destinatarios|Sí|No|  
|Muestra el resumen de registro Referente a en el correo electrónico/cita|Sí|No|  
|Funciona con [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]|Sí|No|  
|Funciona con el escritorio de [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]|Sí|Sí|  
|Funciona con [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] para Mac|Sí|No|  
|Funciona con teléfonos|Sí|No|  
|Abrir y crear registro de [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] directamente|Sí|Sí|  
|Aplicar formularios personalizados y lógica de negocios|Sí|Sí|  
|Trabajar sin conexión|No|Sí|  
|Aplicar plantillas de correo electrónico|Sí|Sí|  
|Aplicar documentación de ventas|Sí|Sí|  
|Aplicar artículos de conocimientos|Sí|Sí|  
|Capacidad para controlar correos electrónicos después de enviar|Sí|No|  
|Ordenar, filtrar, formatear, agrupar y clasificar vistas|No|Sí|  
|Crear documentos de combinación de correspondencia de Word|No|Sí|  
|Controlar la sincronización de campos|No|Sí|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Se requiere lo siguiente para usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]:  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] o [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   Sincronización de correo electrónico entrante mediante sincronización del lado del servidor. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][Configuración de la sincronización del lado del servidor de correo electrónico, citas, contactos y tareas](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   Privilegios necesarios que se describen a continuación  
  
> [!NOTE]
>  Las configuraciones y los requisitos compatibles para las características de [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] aparecen en toda nuestra documentación. Las configuraciones específicas no documentadas se deberían considerar no compatibles.  
  
### <a name="required-privileges"></a>Privilegios requeridos  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] proporciona acceso a [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] a través del privilegio **Usar Dynamics 365 App for Outlook**. Si un usuario no tiene este privilegio, recibirá el siguiente error:  
  
> "No está autorizado a usar esta aplicación. Consulte con el administrador del sistema para actualizar su configuración."  
  
 Los usuarios deben tener privilegios de lectura y escritura para las siguientes entidades.  
  
 Pestaña Administración de empresas:  
  
-   **Buzón**  
  
 Pestaña Personalización:  
  
-   **Entidad**  
  
-   **Campo**  
  
-   **Relación**  
  
-   **Metadatos de aplicación del sistema**  
  
-   **Formulario del sistema**  
  
-   **Metadatos de aplicación del usuario**  
  
-   **Vista**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>Establezca los privilegios para un rol de seguridad  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  Haga clic en **Roles de seguridad**.  
  
3.  Elija un rol de seguridad y, a continuación, haga clic en la pestaña **Administración de empresas**.  
  
4.  En la sección **Entidad**, revise los valores de los privilegios **Buzón**. El rol de seguridad debe tener una configuración de usuario o superior.  
  
5.  En la sección **Privilegios relacionados con la privacidad**, compruebe que **Usar Dynamics 365 App for Outlook** se ha establecido en **Organización**. De lo contrario, haga clic en **Usar Dynamics 365 App for Outlook**.  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Configuraciones admitidas con Microsoft Exchange  
 En cuanto a [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)], puede usar la aplicación con cualquier combinación de [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] o [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] y [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] o [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises), incluidas las configuraciones híbridas. Esto significa que puede usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] en cualquiera de las configuraciones siguientes:  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (local)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (local)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  Si usa [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)], necesitará autenticarse con autenticación IFD como se describe a continuación.  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>Exploradores admitidos para Outlook en la web  
 Puede usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] con [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] en los exploradores siguientes:  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)] o [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     Se admite la siguiente configuración:  
  
    -   Modo protegido está habilitado para zonas de seguridad de **Internet**. Para habilitar el Modo protegido: en IE 10 o 11, vaya a **Herramientas** > **Opciones de Internet** > **Pestaña de seguridad** > **Internet**.  
  
    -   El modo protegido está habilitado para zonas de seguridad de **Intranet local**. Para habilitar el modo protegido: en IE 10 o 11, vaya a **Herramientas** > **Opciones de Internet** > **Pestaña de seguridad** > **Internet local**.  
  
    -   La dirección URL de [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] está en la lista de zonas de seguridad de **Intranet local** de páginas web de confianza. En IE 10 o 11, vaya a **Herramientas** > **Opciones de Internet** > **Pestaña Seguridad** > **Intranet local** > **Sitios** > **Avanzado**.  
  
-   [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)] (versión más reciente) en [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] (versión más reciente) en [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_Safari](../includes/tn-safari.md)] (versión 9 o versión 10) en Mac o en OSX  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>Sistemas operativos compatibles para Outlook en el escritorio  
 Puede usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] en estas versiones de [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] para el escritorio:  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 y [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016.  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] para Mac*.  
  
     *[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] Se necesita 15.0.847.32 o superior.  
  
### <a name="supported-mobile-devices"></a>Dispositivos móviles compatibles  
 Puede usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]con [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] en el explorador móvil en cualquiera de los siguientes teléfonos y sistemas operativos:  
  
-   Dispositivos [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_iphone](../includes/tn-iphone.md)] que ejecutan iOS versión 8, 9 o 10.  
  
-   Teléfonos [!INCLUDE[tn_android](../includes/tn-android.md)] que ejecutan [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4 (KitKat) o 5.0 (Lollipop), 6 (Marshmallow) o 7 (Nougat).  
  
-   Dispositivos [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] que ejecutan [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] o [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)].  
  
### <a name="supported-clients-per-feature"></a>Clientes compatibles por característica  
 Las características admitidas de [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] dependen del cliente que se está ejecutando. En la siguiente tabla se resumen las características que admite cada cliente o configuración de [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] y [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)].  
  
 ![Clientes compatibles con cada característica de Dynamics 365 App for Outlook](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "Clientes compatibles con cada característica de Dynamics 365 App for Outlook")  
  
 (1)  [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] admite [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)], [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)], [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9, [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10, [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] y [!INCLUDE[tn_chrome](../includes/tn-chrome.md)].  
  
 (2)  Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] admite [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)], [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)], [!INCLUDE[tn_ios](../includes/tn-ios.md)] 8, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 9, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 10, [!INCLUDE[tn_android](../includes/tn-android.md)] KitKat (4.4), [!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop, [!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow y [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat.  
  
 (3)  El seguimiento de correo electrónico en modo de redacción y el seguimiento de citas requiere [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 CU14 o [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016.  
  
 (4)  El seguimiento de contactos solo se admite en [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]2016 CU3 y [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 y posteriores.  
  
 (5)  La adicción de plantillas de correo electrónico, los artículos de administración del conocimiento y la documentación de ventas no se admiten en Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)].  
  
 (6)  Solo se admite en [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 y posteriores.  
  
 (7)  Solo se admite en 16.0.6741.1000 y posteriores.  
  
> [!NOTE]
>  Las tabletas no se admiten en este momento (llegará en CY2017).  
  
 [Obtenga más detalles sobre clientes admitidos en este blog: Matriz de compatibilidad de la Dynamics 365 App for Outlook](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>Servidores compatibles  
 Los [requisitos del servidor para usar complementos de Office ](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins) son [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)], [!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)] o [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)].  
  
### <a name="supported-languages"></a>Idiomas compatibles  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]admite los siguientes idiomas:  
  
||||  
|-|-|-|  
|Búlgaro (Bulgaria) - 1026|Hindi (India) - 1081|Portugués (Portugal) - 2070|  
|Chino (República Popular China) - 2052|Húngaro - 1038|Rumano - 1048|  
|Chino (Taiwán) - 1028|Indonesio - 1057|Ruso - 1049|  
|Croata (Croacia) - 1050|Italiano - 1040|Serbio - 2074|  
|Checo (República Checa) - 1029|Japonés - 1041|Eslovaco - 1051|  
|Danés - 1030|Kazajo - 1087|Esloveno - 1060|  
|Neerlandés - 1043|Coreano - 1042|Español - 3082|  
|Inglés - 1033|Letón - 1062|Sueco - 1053|  
|Estonio - 1061|Lituano - 1063|Tailandés - 1054|  
|Finés - 1035|Malayo - 1086|Turco - 1055|  
|Francés - 1036|Noruego - 1044|Ucraniano - 1058|  
|Alemán - 1031|Polaco - 1045|Vietnamita - 1066|  
|Griego - 1032|Portugués (Brasil) - 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>Implementar Dynamics 365 App for Outlook  
 Después de configurar [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] y establecer los privilegios necesarios, puede insertar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] en algunos o todos los usuarios o bien los usuarios pueden instalarlo ellos mismos según sea necesario.  
  
> [!NOTE]
>  Si se encuentra en [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)], consulte la siguiente sección: [Para implementar en usuarios de Dynamics 365 locales](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>Para insertar la aplicación en los usuarios  
  
1.  Vaya a **Configuración** >  **Dynamics 365 App for Outlook**.  
  
2.  En la pantalla **Introducción a la Dynamics 365 App for Outlook**, en **Agregar para usuarios aptos** (es posible que tenga que hacer clic en **Configuración** si va a abrir esta pantalla por segunda o más veces), active la casilla **Agregue la aplicación a [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] automáticamente** si desea que los usuarios obtengan la aplicación automáticamente. Si un usuario tiene los privilegios necesarios y el correo electrónico se sincroniza a través de [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)], no tendrá que hacer nada más que insertar la aplicación. Por ejemplo, si agrega los privilegios necesarios al rol Comercial y luego asigna este rol a un usuario nuevo, recibirán automáticamente la aplicación.  
  
3.  Realice una de las acciones siguientes:  
  
    -   Para insertar la aplicación en todos los usuarios aptos, haga clic en **Agregar aplicación para todos los usuarios aptos**.  
  
    -   Para insertar la aplicación en ciertos usuarios, seleccione esos usuarios en la lista y, a continuación, haga clic en **Agregar aplicación a Outlook**.  
  
    > [!TIP]
    >  Si la lista muestra que un usuario está pendiente o no se ha agregado, puede hacer clic en el vínculo **Más información** junto al usuario para obtener más información sobre el estado.  
  
4.  Cuando acabe, haga clic en **Guardar**.  
  
#### <a name="to-have-users-install-the-app-themselves"></a>Para hacer que los usuarios instalen la aplicación por sí mismos  
  
1.  Los usuarios hacen clic en el botón **Configuración** ![botón Configuración](media/mp-ua-r16-settings.png "Botón Configuración") y, a continuación, hacen clic en **Aplicaciones para Dynamics 365**.  
  
2.  En la pantalla **Aplicaciones para Dynamics 365**, en **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**, los usuarios hacen clic en **Agregar aplicación a [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]**.  
  
> [!NOTE]
>  Los usuarios también pueden deshabilitar o quitar el complemento por sí mismos, si es necesario. Para obtener más información, consulte el [Manual del usuario de Dynamics 365 App for Outlook"](https://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>Para implementar en usuarios de Dynamics 365 local  
 Siga estos pasos si usa las Dynamics 365 on-premises.  
  
-   Configure Dynamics 365 Server para una implementación con conexión a Internet. Consulte [Configurar IFD para Microsoft Dynamics 365](https://technet.microsoft.com/library/dn609803.aspx).  
  
-   Si va a conectarse a Exchange on-premises, configure el proveedor OAuth y registre aplicaciones cliente. Vea [Configurar Windows Server 2012 R2 para aplicaciones Dynamics 365 que usan OAuth](https://technet.microsoft.com/library/hh699726.aspx).  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>Solución de problemas de instalación  
 Si usted o sus usuarios tiene problemas para instalar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)], puede ser debido a que el buzón de [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] está vinculado actualmente a otra organización de [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)]. Un buzón de [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] (dirección de correo electrónico) puede sincronizar solo citas, contactos y tareas con una organización, y un usuario perteneciente a esa organización puede sincronizar solo citas, contactos, y tareas con un buzón de [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)].  Puede sobrescribir la opción almacenada en [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] si desea cambiar la organización de sincronización principal. Para obtener más información, consulte [este artículo KB.](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook)  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>Explorar el Manual de usuario y entrenar a los usuarios  
 Para aprender a usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)], [consulta el Manual del usuario de Dynamics 365 App for Outlook](https://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
 ![Página de Manual del usuario de Dynamics 365 App for Outlook](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Página de Manual del usuario de Dynamics 365 App for Outlook")  
  
## <a name="see-also"></a>Vea también  
 [Manual del usuario de Dynamics 365 App for Outlook](https://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [Obtenga más detalles sobre clientes admitidos en este blog: Matriz de compatibilidad de Dynamics 365 App for Outlook](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [Configuración de la sincronización del lado del servidor de correo electrónico, citas, contactos y tareas](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [Adición de usuarios, licencias y roles de seguridad](https://msdn.microsoft.com/23612155-f92d-4871-a109-186419d5c19d)   
 [Adición de características de interoperación a Microsoft Dynamics 365 (online)](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)