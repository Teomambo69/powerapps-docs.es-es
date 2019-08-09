---
title: Personalice los comandos y la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Common Data Service muestra comandos de diferentes maneras en función de la entidad y del cliente. En la mayoría de los lugares en la aplicación web verá una barra de comandos en lugar de una cinta de opciones. Dynamics 365 for tablets también usa los datos definidos como cintas de opciones para controlar qué comandos están disponibles con una barra de comandos optimizada para tacto.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 926364b0-ede6-00e9-39d4-5aae5e00be0b
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="customize-commands-and-the-ribbon"></a>Personalización de comandos y la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/customize-commands-ribbon -->

 Common Data Service muestra comandos de diferentes maneras en función de la entidad y del cliente. En la mayoría de los lugares en la aplicación web verá una *barra de comandos* en lugar de una cinta de opciones. Dynamics 365 for tablets también usa los datos definidos como cintas de opciones para controlar qué comandos están disponibles con una barra de comandos optimizada para tacto.  
  
 La barra de comandos ofrece un mejor rendimiento. La cinta de opciones se sigue mostrando en la aplicación web para determinados formularios de entidad y aún se usa para las vistas de lista en Dynamics 365 for Outlook.  
  
 La barra de comandos y la cinta de opciones usan los mismos datos XML subyacentes para definir qué comandos se van a mostrar, cuándo se habilitan y qué función tienen.  
  
 Los temas de esta sección presentan conceptos clave que debe comprender y tareas comunes que realiza al personalizar la barra de comandos o la cinta de opciones.  
  
> [!NOTE]
>  Puesto que el esquema XML subyacente se diseñó para mostrar los comandos como cintas de opciones, el término *cinta de opciones* se seguirá usando en la documentación.  
  
 El SDK describe el proceso de modificación de la cinta de opciones editando el archivo customization.xml directamente. Varias personas han creado editores de cinta de opciones que proporcionan una interfaz de usuario para que sea más sencillo modificar la cinta de opciones. Actualmente están disponibles los siguientes proyectos en Codeplex y en otras ubicaciones:  
  
- [Ribbon Workbench](http://www.develop1.net/public/rwb/ribbonworkbench.aspx)  
  
- [MS CRM 2011 : Pragma Toolkit : Ribbon, Site Map Editor](http://pragmatoolkit.codeplex.com/)  
  
- [CRM 2011 Visual Ribbon Editor](http://crmvisualribbonedit.codeplex.com/)  
  
  Para obtener soporte técnico o ayuda para usar estos programas, póngase en contacto con el editor del programa.  
  
  
## <a name="see-also"></a>Vea también  

 [Esquema central de cinta de opciones](ribbon-core-schema.md)  
 [Esquema de tipos de cinta de opciones](ribbon-types-schema.md)  
 [Esquema WSS de cinta de opciones](ribbon-wss-schema.md)<br/> 
 [Ejemplo: Exportar definiciones de cinta de opciones](sample-export-ribbon-definitions.md)<br/> 
 [Aplicar la lógica de negocios usando scripting de cliente en aplicaciones basadas en modelos](client-scripting.md)
