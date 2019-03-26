---
title: 'Tutorial: Configurar seguridad de ensamblados para complemento sin conexión (Common Data Service para aplicaciones) | Microsoft Docs'
description: El tema proporciona un tutorial sobre la configuración de la seguridad de ensamblado para un complemento sin conexión.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="walkthrough-configure-assembly-security-for-an-offline-plug-in"></a>Tutorial: configurar la seguridad de ensamblado para un complemento sin conexión

La plataforma Common Data Service para aplicaciones aplica una restricción adicional de seguridad a los ensamblados de complementos sin conexión registrados. Cuando Dynamics 365 for Microsoft Office Outlook con acceso sin conexión está instalado, una clave AllowList se agrega al registro del sistema en el equipo cliente. Por cada ensamblado que contenga un complemento sin conexión que registre, debe agregar una subclave de registro a la clave AllowList con el nombre de clave derivado del token de clave pública del ensamblado. Si no lo hace, la plataforma no ejecutará el complemento sin conexión aunque el complemento esté registrado. Este recorrido describe cómo agregar esta subclave a un ensamblado de complementos.  
  
### <a name="get-the-public-key-token"></a>Obtener el token de clave pública  
  
1.  Cargue el ensamblado que contiene el complemento sin conexión en la herramienta de registro de complementos. Para obtener más información sobre cómo usar la herramienta, consulte [Registrar un complemento](../register-plug-in.md).  
  
2.  Seleccione el ensamblado de complementos en la vista de árbol de la herramienta.  
  
3.  Copie (Ctrl+C) el valor en el campo **Token de clave pública** en el búfer de pegado.  
  
### <a name="add-an-allowlist-key"></a>Agregue una clave AllowList  
  
1.  Ejecute el editor del registro seleccionando **Inicio** y luego **Ejecutar**. Escriba `regedit.exe`.  
  
2.  En el panel de vista de árbol, vaya a la clave **AllowList**. La ruta completa de la clave es `HKEY_CURRENT_USER\Software\Microsoft\MSCRMClient\AllowList`.  
  
3.  Seleccione la clave **AllowList** y pulse con el botón secundario para mostrar el menú contextual.  
  
4.  Seleccione **Nueva** y luego **Clave** para crear una nueva subclave.  
  
5.  Pegue el valor del token de clave pública en el nombre de la nueva subclave.  
  
6.  Cierre el editor del registro.  
  
### <a name="see-also"></a>Vea también  
 [Desarrollo de complementos](/dynamics365/customer-engagement/developer/plugin-development)   
 [Ejemplo: Crear un complemento básico](../org-service/samples/basic-followup-plugin.md)   
 [Registrar e implementar complementos](/dynamics365/customer-engagement/developer/register-deploy-plugins)