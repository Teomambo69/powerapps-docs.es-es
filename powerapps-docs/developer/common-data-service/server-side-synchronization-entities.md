---
title: Entidades de sincronización del lado del servidor (Common Data Service para aplicaciones) | Microsoft Docs
description: 'La sincronización del lado del servidor proporciona una interfaz entre Common Data Service para aplicaciones y uno o más servidores Exchange o servidores POP3 para correo electrónico entrante, y uno o más servidores SMTP o Exchange para el correo electrónico saliente.'
ms.custom: ''
ms.date: 02/21/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: mayadu
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="server-side-synchronization-entities"></a>Entidades de sincronización del lado del servidor

En PowerApps, la sincronización del lado del servidor proporciona una interfaz entre Common Data Service para aplicaciones y uno o más servidores Exchange o servidores POP3 para correo electrónico entrante, y uno o más servidores SMTP o Exchange para el correo electrónico saliente. Recupera y evalúa los correos electrónicos para ver su importancia para Common Data Service para aplicaciones y crea en consecuencia las actividades de correo electrónico correspondientes en Common Data Service para aplicaciones. También recoge los mensajes de correo electrónico de Common Data Service para aplicaciones y los envía a través del servidor de correo electrónico configurado para los usuarios y las colas de . También permite la sincronización de citas, contactos y tareas con Exchange Server 2010 y Exchange Server 2013.  
  
 Gracias a la configuración de correo electrónico centralizada, el modelo de entidad de Common Data Service para aplicaciones permite tener una configuración común de la interfaz de usuario (UI) (como nombre de usuario, contraseña, dirección de correo electrónico y métodos de sincronización) para los usuarios, las colas y los buzones de enrutamiento. Cada usuario o las colas pueden tener buzones, que se pueden supervisar mediante la sincronización del lado del servidor o Microsoft Dynamics 365 for Outlook. La entidad [EmailServerProfile](/powerapps/developer/common-data-service/reference/entities/emailserverprofile) representa el perfil de servidor de correo electrónico de una organización. La entidad [Buzón](/powerapps/developer/common-data-service/reference/entities/mailbox) representa el método de entrega de citas, contactos y tareas del buzón. Actualmente, la entidad de usuario está limitada a tener un solo registro de buzón por usuario y la entidad de colas a tener un solo registro de buzón por cola, como se muestra en la ilustración siguiente.  
  
 ![Modelo de entidad de conector de correo electrónico](media/email-connector-entity-model.png "Modelo de entidad de conector de correo electrónico")  
  
 La sincronización del lado del servidor proporciona las siguientes capacidades:  
  
- Procesar los mensajes de correo electrónico de un usuario y una cola con la dirección de correo electrónico, el método de entrega de correo electrónico y las credenciales del registro de buzón relacionado.  
  
- Procesar citas, contactos y tareas.  
  
- Usar los registros de buzón para procesar mensajes de correo electrónico para usuarios y colas que tienen el método de entrega entrante establecido en buzón de enrutamiento.  
  
- Usar la información de un registro de perfil de correo electrónico relacionado para procesar los mensajes de correo electrónico de todos los buzones.  
  
- Evitar el procesamiento de correo electrónico de buzones inactivos o buzones que no tienen un perfil de correo electrónico asociado.  
  
- Relacionar automáticamente un buzón asociado con el perfil de correo electrónico predeterminado cuando se crea un usuario o una cola con el método de entrega de correo electrónico establecido en sincronización del lado del servidor.  
  
- Realice un seguimiento automático de los mensajes de Microsoft Exchange en PowerApps para un usuario según las reglas de seguimiento de nivel de carpeta.  
  
### <a name="related-topics"></a>Temas relacionados  
 [Configurar reglas de seguimiento de nivel de carpeta](configure-exchange-folder-level-tracking-rules.md) 