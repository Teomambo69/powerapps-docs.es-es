---
title: Implementación de la aplicación Dynamics 365 para Outlook | MicrosoftDocs
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
ms.openlocfilehash: 98a5ec78b0edf607b954d794b3eef95403926a64
ms.sourcegitcommit: baadb67f5cc962b7c3393f9763959eae3a7649dd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57346964"
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>Implementación de la aplicación Dynamics 365 para Outlook
Los usuarios pueden usar [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] para aprovechar la eficacia de [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] mientras se usa [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] en el equipo de escritorio, la web o una tableta. Por ejemplo, vea información sobre los destinatarios de correos electrónicos o citas, o vincule un correo electrónico o una cita de [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] a un registro de [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] como una oportunidad, una cuenta o un caso. Para más información sobre lo que ofrece [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)], consulte el [Manual del usuario de la aplicación de Dynamics 365 para Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] no es lo mismo que [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]. A partir de [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)], el emparejamiento de [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] con [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] es la manera preferida de integrar [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] con [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]. **Tenga en cuenta que no se admiten actividades de seguimiento cuando un mismo usuario no usa juntos [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] y [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)].** Para información sobre el complemento [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)], consulte el [Manual del usuario de Dynamics 365 para Outlook](http://go.microsoft.com/fwlink/p/?LinkID=524751).  
>   
>  Los [usuarios delegados](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540) no pueden usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] para realizar un seguimiento del correo electrónico. Se recomienda usar el [seguimiento de nivel de carpeta o seguimiento automático](https://www.microsoft.com/en-us/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx) para los usuarios delegados.  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>Comparación de la aplicación Dynamics 365 para Outlook con Dynamics 365 para Outlook  
 En la tabla siguiente se comparan las características de [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] con [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] (también conocido como cliente o complemento de [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]) a partir de [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)].  
  
||||  
|-|-|-|  
|**Característica**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|Seguir y establecer referente para correo electrónico|Sí|Sí|  
|Seguir y establecer referente para citas|Sí|Sí|  
|Seguir y establecer referente para contactos|Sí|Sí|  
|Seguir y establecer referente para tareas|No|Sí|  
|Establecer referente con un clic|Sí|No|  
|Muestra el resumen de los destinatarios|Sí|No|  
|Muestra el resumen de registros referentes en el correo electrónico o la cita|Sí|No|  
|Funciona con [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]|Sí|No|  
|Funciona con [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] para escritorio|Sí|Sí|  
|Funciona con [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] para Mac|Sí|No|  
|Funciona con teléfonos|Sí|No|  
|Abrir y crear registros de [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] directamente|Sí|Sí|  
|Aplicar formularios personalizados y lógica de negocios|Sí|Sí|  
|Trabajar sin conexión|No|Sí|  
|Aplicar plantillas de correo electrónico|Sí|Sí|  
|Aplicar documentación de ventas|Sí|Sí|  
|Aplicar artículos de conocimiento|Sí|Sí|  
|Posibilidad de supervisar los mensajes de correo electrónico después de enviarlos|Sí|No|  
|Ordenar, filtrar, formatear, agrupar y clasificar vistas|No|Sí|  
|Crear documentos de combinación de correspondencia de Word|No|Sí|  
|Controlar la sincronización de los campos|No|Sí|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Son necesarios los siguientes para usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]:  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] o [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   Sincronización del correo electrónico entrante mediante la sincronización del lado servidor. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][Configuración de la sincronización del lado del servidor de correo electrónico, citas, contactos y tareas](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   Los privilegios necesarios descritos a continuación  
  
> [!NOTE]
>  Las configuraciones admitidas y los requisitos de [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] se enumeran a lo largo de nuestra documentación. Las configuraciones específicas no documentadas se deben considerar no admitidas.  
  
### <a name="required-privileges"></a>Privilegios necesarios  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] proporciona acceso a [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] mediante el privilegio **Usar aplicación Dynamics 365 para Outlook**. Si un usuario no tiene este privilegio, recibirá el siguiente error:  
  
> "No tiene autorización para usar esta aplicación. Póngase en contacto con el administrador del sistema para actualizar la configuración".  
  
 Los usuarios también deben tener privilegios de lectura y escritura para las siguientes entidades.  
  
 Pestaña Administración de empresas:  
  
-   **Buzón**  
  
 Pestaña Personalización:  
  
-   **Entidad**  
  
-   **Campo**  
  
-   **Relación**  
  
-   **Metadatos de aplicación del sistema**  
  
-   **Formulario del sistema**  
  
-   **Metadatos de aplicación del usuario**  
  
-   **Ver**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>Establecimiento de los privilegios de un rol de seguridad  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  Haga clic en **Roles de seguridad**.  
  
3.  Elija un rol de seguridad y, a continuación, haga clic en la pestaña **Administración de empresas**.  
  
4.  En la sección **Entidad**, revise la configuración de privilegios de **Buzón**. El rol de seguridad debe tener configuración de usuario o superior.  
  
5.  En la sección **Privilegios relacionados con la privacidad**, compruebe que **Usar aplicación Dynamics 365 para Outlook** está establecida en **Organización**. En caso contrario, haga clic en **Usar aplicación Dynamics 365 para Outlook**.  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Configuraciones compatibles con Microsoft Exchange  
 A partir de [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)], puede usar la aplicación con cualquier combinación de [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] o [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] y [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] o [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (entorno local), incluidas las configuraciones híbridas. Esto significa que puede usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] en cualquiera de las siguientes configuraciones:  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (entorno local)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (entorno local)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  Si usa [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)], tendrá que autenticarse con la autenticación de IFD, como se describe a continuación.  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>Exploradores compatibles con Outlook en la web  
 Puede usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] con [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] con los siguientes exploradores:  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)] o [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     Se admite la siguiente configuración:  
  
    -   El modo protegido está habilitado para la zona de seguridad **Internet**. Para habilitar el modo protegido: en Internet Explorer 10 u 11, vaya a **Herramientas** > **Opciones de Internet** > **pestaña Seguridad** > **Internet**.  
  
    -   El modo protegido está habilitado para la zona de seguridad **Intranet Local**. Para habilitar el modo protegido: en Internet Explorer 10 u 11, vaya a **Herramientas** > **Opciones de Internet** > **pestaña Seguridad** > **Internet local**.  
  
    -   Su dirección URL [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] está en la lista de sitios web de confianza de la zona de seguridad **Intranet local**. En Internet Explorer 10 u 11, vaya a **Herramientas** > **Opciones de Internet** > **pestaña Seguridad** > **Intranet Local** >  **Sitios** > **Avanzadas**.  
  
-   [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)] (última versión) en [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] (última versión) en [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_Safari](../includes/tn-safari.md)] (versión 9 o versión 10) en Mac o en OSX  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>Sistemas operativos compatibles con Outlook en el escritorio  
 Puede usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] en estas versiones de [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] para el escritorio:  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 y [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016.  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] para Mac *.  
  
     Se requiere la versión 15.0.847.32 o superior de *[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)].  
  
### <a name="supported-mobile-devices"></a>Dispositivos móviles compatibles  
 Puede usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] con [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] en el explorador móvil en cualquiera de los teléfonos y sistemas operativos siguientes:  
  
-   Dispositivos [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_iphone](../includes/tn-iphone.md)] que ejecutan la versión 8, 9 o 10 de iOS.  
  
-   Teléfonos [!INCLUDE[tn_android](../includes/tn-android.md)] que ejecutan [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4 (KitKat) o 5.0 (Lollipop), 6 (Marshmallow) o 7 (Nougat).  
  
-   Dispositivos [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] que ejecutan [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] o [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)].  
  
### <a name="supported-clients-per-feature"></a>Clientes admitidos por característica  
 Las características de [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] admitidas dependen del cliente que ejecute. En la tabla siguiente se resumen las características que se admiten para cada configuración o cliente de [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] y [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)].  
  
 ![Clientes admitidos con cada característica de la Aplicación Dynamics 365 para Outlook](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "Clients supported for each Dynamics 365 App for Outlook feature")  
  
 (1) [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] admite [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)], [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)], [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9, [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10, [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] y [!INCLUDE[tn_chrome](../includes/tn-chrome.md)].  
  
 (2) Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] admite [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)], [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)], [!INCLUDE[tn_ios](../includes/tn-ios.md)] 8, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 9, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 10, [!INCLUDE[tn_android](../includes/tn-android.md)] KitKat (4.4), [!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop, [!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow y [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat.  
  
 (3) El seguimiento del correo electrónico en modo de redacción y el seguimiento de citas requieren[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 CU14 o [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016.  
  
 (4) El seguimiento de contactos solo se admite en [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]2016 CU3 y [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 y versiones posteriores.  
  
 (5) Agregar plantillas de correo electrónico, artículos de administración del conocimiento y documentación de ventas no se admite en Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)].  
  
 (6) Solo se admite en [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 y versiones posteriores.  
  
 (7) Solo se admite en 16.0.6741.1000 y versiones posteriores.  
  
> [!NOTE]
>  En este momento no se admiten tabletas (próximamente).  
  
 [Obtenga más información sobre los clientes admitidos en este blog: Dynamics 365 App for Outlook Support Matrix](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/) (Aplicación Dynamics 365 para la matriz de compatibilidad de Outlook)  
  
### <a name="supported-servers"></a>Servidores admitidos  
 Los [requisitos de servidor para usar complementos de Office](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins) son [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)], [!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)] o [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)].  
  
### <a name="supported-languages"></a>Idiomas admitidos  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] admite los siguientes idiomas:  
  
||||  
|-|-|-|  
|Búlgaro (Bulgaria): 1026|Hindi (India): 1081|Portugués (Portugal): 2070|  
|Chino (República Popular China): 2052|Húngaro: 1038|Rumano: 1048|  
|Chino (Taiwán): 1028|Indonesio: 1057|Ruso: 1049|  
|Croata (Croacia): 1050|Italiano: 1040|Serbio: 2074|  
|Checo (República Checa): 1029|Japonés: 1041|Eslovaco: 1051|  
|Danés: 1030|Kazajo: 1087|Esloveno: 1060|  
|Neerlandés: 1043|Coreano: 1042|Español: 3082|  
|Inglés: 1033|Letón: 1062|Sueco: 1053|  
|Estonio: 1061|Lituano: 1063|Tailandés: 1054|  
|Finés: 1035|Malasio: 1086|Turco: 1055|  
|Francés: 1036|Noruego: 1044|Ucraniano: 1058|  
|Alemán: 1031|Polaco: 1045|Vietnamita: 1066|  
|Griego: 1032|Portugués (Brasil): 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>Implementación de la aplicación Dynamics 365 para Outlook  
 Después de configurar [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] y establecer los privilegios necesarios, puede insertar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] en algunos o todos los usuarios, o bien puede hacer que los usuarios lo instalen por su cuenta según sea necesario.  
  
> [!NOTE]
>  Si se encuentra en [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)], consulte la sección siguiente:  [Implementación en usuarios locales de Dynamics 365](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>Inserción de la aplicación en los usuarios  
  
1.  Vaya a **Configuración** >  **Aplicación Dynamics 365 para Outlook**.  
  
2.  En la pantalla **Getting Started with Dynamics 365 App for Outlook** (Introducción a la aplicación Dynamics 365 para Outlook), en **Agregar para usuarios aptos** (puede tener que hacer clic en **Configuración** si abre esta pantalla por segunda o consecutiva vez), active la casilla **Automatically add the app to [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]** (Agregar automáticamente la aplicación a) si quiere que los usuarios obtengan la aplicación automáticamente. Si un usuario tiene los privilegios necesarios y el correo electrónico está sincronizado mediante [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)], no tendrá que hacer nada más para insertar la aplicación en dicho usuario. Por ejemplo, si agrega los privilegios necesarios al rol de vendedor y luego asigna este rol a un nuevo usuario, dicho usuario obtendrá automáticamente la aplicación.  
  
3.  Lleve a cabo una de las siguientes acciones:  
  
    -   Para insertar la aplicación en todos los usuarios aptos, haga clic en **Agregar aplicación para todos los usuarios aptos**.  
  
    -   Para insertar la aplicación en determinados usuarios, seleccione los usuarios de la lista y, a continuación, haga clic en **Agregar aplicación a Outlook**.  
  
    > [!TIP]
    >  Si la lista muestra que un usuario está pendiente o no se ha agregado, puede hacer clic en el vínculo **Más información** junto al usuario para encontrar más información sobre el estado.  
  
4.  Cuando termine, haga clic en **Guardar**.  
  
#### <a name="to-have-users-install-the-app-themselves"></a>Instalación de la aplicación por los usuarios  
  
1.  Los usuarios deben hacer clic en el botón **Configuración** ![botón Configuración](media/mp-ua-r16-settings.png "botón Configuración") y, luego, en **Aplicaciones para Dynamics 365**.  
  
2.  En la pantalla **Aplicaciones para Dynamics 365**, en **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**, los usuarios hacen clic en **Add app to [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]** (Agregar aplicación a).  
  
> [!NOTE]
>  Si es necesario, los usuarios también pueden deshabilitar o quitar el complemento ellos mismos. Para más información, consulte el [Manual del usuario de Dynamics 365 para Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>Implementación en usuarios locales de Dynamics 365  
 Si usa Dynamics 365 en el entorno local, siga estos pasos.  
  
-   Configure el servidor de Dynamics 365 para la implementación accesible desde Internet. Consulte [Configurar IFD para Microsoft Dynamics 365](https://technet.microsoft.com/library/dn609803.aspx).  
  
-   Si se conecta a Exchange local, configure el proveedor de OAuth y registre las aplicaciones cliente. Consulte [Configurar Windows Server 2012 R2 para aplicaciones Dynamics 365 que usan OAuth](https://technet.microsoft.com/library/hh699726.aspx).  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>Solución de problemas de instalación  
 Si usted o sus usuarios tienen problemas para instalar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)], puede ser debido a que su buzón [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] está vinculado actualmente a otra organización de [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)]. Un buzón de [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] (dirección de correo electrónico) solo puede sincronizarse citas, contactos y tareas con una organización, y un usuario que pertenezca a esa organización solo puede sincronizar citas, contactos y tareas con un buzón de [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)].  Si quiere cambiar la organización de sincronización principal, puede sobrescribir el valor almacenado en [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)]. Para más información, consulte [este artículo de KB](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook).  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>Explorar el Manual de usuario y entrenar a los usuarios  
 Para aprender a usar [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)], [consulte el Manual del usuario de Dynamics 365 para Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
 ![Página del Manual del usuario de la aplicación de Dynamics 365 para Outlook](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Dynamics 365 App for Outlook User's Guide page")  
  
## <a name="see-also"></a>Consulte también  
 [Manual del usuario de la aplicación de Dynamics 365 para Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [Obtenga más información sobre los clientes admitidos en este blog: Dynamics 365 App for Outlook Support Matrix](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  (Aplicación Dynamics 365 para la matriz de compatibilidad de Outlook)  
 [Configuración de la sincronización del lado del servidor de correo electrónico, citas, contactos y tareas](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [Agregar usuarios, licencias y roles de seguridad](http://msdn.microsoft.com/en-us/23612155-f92d-4871-a109-186419d5c19d)   
 [Agregar características de interoperación a Microsoft Dynamics 365 (en línea)](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)