---
title: Personalice los comandos y la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Common Data Service muestra comandos de diferentes maneras en función de la entidad y del cliente. En la mayoría de los lugares en la aplicación web verá una barra de comandos en lugar de una cinta de opciones. Dynamics 365 para tabletas también usa los datos definidos como cintas de opciones para controlar qué comandos están disponibles con una barra de comandos optimizada para tacto.
keywords: ''
ms.date: 03/27/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 926364b0-ede6-00e9-39d4-5aae5e00be0b
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 27b041e7a62b76bab7e920deac9a8933accf4fca
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275948"
---
# <a name="customize-commands-and-the-ribbon"></a>Personalización de comandos y la cinta de opciones

Common Data Service muestra comandos de diferentes maneras en función de la entidad y del cliente. En la mayoría de los lugares en la aplicación web, verá una *barra de comandos* en lugar de una cinta de opciones. 

Dynamics 365 for tablets también usa los datos definidos como cintas de opciones para controlar qué comandos están disponibles con una barra de comandos optimizada para tacto.  
  
La barra de comandos ofrece un mejor rendimiento. La cinta de opciones se sigue mostrando en la aplicación web para determinados formularios de entidad y aún se usa para las vistas de lista en Dynamics 365 for Outlook.  
  
La barra de comandos y la cinta de opciones usan los mismos datos XML subyacentes para definir qué comandos se van a mostrar, cuándo se habilitan y qué función tienen.  
  
Los artículos de esta sección presentan conceptos clave que debe comprender y tareas comunes que realiza al personalizar la barra de comandos o la cinta de opciones.  
  
> [!NOTE]
>  Puesto que el esquema XML subyacente se diseñó para mostrar los comandos como cintas de opciones, el término *cinta de opciones* se seguirá usando en la documentación.  
  
## <a name="troubleshoot-ribbon-issues"></a>Solución de problemas de cinta

Si tiene un problema con un botón de la barra de comandos de la cinta, use esta [guía de solución de problemas](https://support.microsoft.com/help/4552163) para encontrar y resolver el problema.


## <a name="community-tool"></a>Herramienta comunitaria
El SDK describe el proceso de modificación de la cinta de opciones editando el archivo customization.xml directamente. También puedes usar una herramienta comunitaria, [Workbench de cinta](https://www.develop1.net/public/rwb/ribbonworkbench.aspx), para editar visualmente cintas usando la interfaz de usuario. 

> [!NOTE]
> Microsoft no proporciona ayuda o soporte para herramientas comunitarias. Para obtener soporte técnico o ayuda para usar estos programas, póngase en contacto con el editor del programa.  
  
  
## <a name="see-also"></a>Vea también  

 [Esquema central de cinta de opciones](ribbon-core-schema.md)  
 [Esquema de tipos de cinta de opciones](ribbon-types-schema.md)  
 [Esquema WSS de cinta de opciones](ribbon-wss-schema.md)<br/> 
 [Ejemplo: Exportar definiciones de cinta de opciones](sample-export-ribbon-definitions.md)<br/> 
 [Aplicar la lógica de negocios usando scripting de cliente en aplicaciones basadas en modelos](client-scripting.md)
