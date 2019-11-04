---
title: Combinar registros duplicados | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/25/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5a14662d25a7c2dda79f2399b863b959f9f70cc5
ms.sourcegitcommit: 79ac9decef3d5aab40fbf3bc95f8f4ba03f9b3df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/26/2019
ms.locfileid: "72959333"
---
# <a name="merge-duplicate-records"></a>Combinación de registros duplicados 

Los registros duplicados pueden trasentrarse en los datos cuando usted u otros usuarios escriben datos manualmente o importan datos de forma masiva. Common Data Service le ayuda a solucionar posibles duplicados al proporcionar la detección de duplicados para cuentas y contactos. El administrador también puede configurar reglas de detección de duplicados para otras situaciones.  
  
Por ejemplo, supongamos que escribe un registro de contacto, Jim Glynn, junto con un número de teléfono móvil.  La regla de detección de duplicados detecta que ya tiene un registro similar y muestra este cuadro de diálogo.  
  
 > [!div class="mx-imgBorder"] 
 > ![Duplicar registro de contacto detectied](media/duplicates-detected.png "Duplicar registro de contacto detectied")  
  
 No está seguro de si se trata de un nuevo registro (uno que tiene el mismo nombre que un contacto existente) o un duplicado, por lo que selecciona **omitir y guardar**.  
  
 A continuación, vaya a la lista **todos los contactos** y vea que ahora tiene dos registros con el mismo nombre. Después de revisar los registros, determinará que son duplicados que deben combinarse.  
 
 > [!div class="mx-imgBorder"] 
 > ![Duplicar registro de contacto detectied](media/duplicates-detected_1.png "Duplicar registro de contacto detectied")  
 
Common Data Service incluye reglas de detección de duplicados para cuentas y contactos. Estas reglas se activan automáticamente, por lo que no tiene que hacer nada para configurar la detección de duplicados para estos tipos de registro.  
  
> [!NOTE]
>  Si está disponible en el sistema, también puede comprobar si hay duplicados de otros tipos de registros, además de contactos y cuentas. Consulte con el administrador del sistema. [Busque el administrador o el personal de soporte técnico](find-admin.md)  
  
## <a name="merge-duplicate-records"></a>Combinación de registros duplicados  
  
1. Seleccione los registros duplicados y, a continuación, seleccione **combinar**.  
  
   > [!div class="mx-imgBorder"] 
   > ![Duplicar registro de contacto detectied](media/duplicates-detected_2.png "Duplicar registro de contacto detectied")  
  
2. En el cuadro de diálogo **combinar registros** , seleccione el registro maestro (el que desea conservar) y, a continuación, seleccione los campos del nuevo registro que desee fusionar mediante combinación en el registro maestro. Los datos de estos campos pueden invalidar los datos existentes en el registro maestro. Seleccione **Aceptar**.  
  
     
   > [!div class="mx-imgBorder"] 
   > ![Cuadro de diálogo para combinar registros](media/merge-records-dialog.png "Cuadro de diálogo para combinar registros")  
  
> [!NOTE]
>  Existen algunas situaciones en las que se pueden encontrar duplicados:  
> 
> - Cuando se crea o se actualiza un registro.  
>   - Cuando use Dynamics 365 para Outlook y pase de sin conexión a en línea.  
>   - Al importar datos mediante el Asistente para la importación de datos.  
> 
>   No se detectan duplicados al combinar registros, guardar una actividad como completada o cambiar el estado de un registro, como la activación o reactivación de un registro.  
