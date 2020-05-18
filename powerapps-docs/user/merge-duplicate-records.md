---
title: Combinación de registros duplicados| Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c0811645429c9f1e7570ceeaf316a5217e440ae4
ms.sourcegitcommit: bee698ca0d11524377b67813a65e1a022d08c05e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "3302642"
---
# <a name="merge-duplicate-records"></a>Combinación de registros duplicados 

Es posible que se incorporen registros duplicados a los datos cuando uno mismo u otros usuarios especifiquen datos de forma manual o los importen en bloque. Common Data Service ayuda a abordar los duplicados potenciales mediante la detección de duplicados para registros activos como cuentas y contactos. Al combinar un registro, también lo hacen los registros relacionados o secundarios. El administrador también puede configurar reglas de detección de duplicados para otras situaciones.  
  
Por ejemplo, supongamos que introduce un registro de contacto, Jim Glynn, junto con un número de teléfono móvil.  La regla de detección de duplicados detecta que ya tiene un registro similar y muestra este cuadro de diálogo.  
  
 > [!div class="mx-imgBorder"] 
 > ![Registro de contacto duplicado detectado](media/duplicates-detected.png "Registro de contacto duplicado detectado")  
  
 Como no está seguro de si se trata de un registro nuevo (uno con el mismo nombre que un contacto existente) o de un duplicado, seleccione **Omitir y guardar**.  
  
 Luego vaya a la lista **Todos los contactos** y vea que ahora tiene dos registros con el mismo nombre. Después de revisar los registros, determina que son duplicados que deben combinarse.  
 
 > [!div class="mx-imgBorder"] 
 > ![Registro de contacto duplicado detectado](media/duplicates-detected_1.png "Registro de contacto duplicado detectado")  
 
Common Data Service incluye reglas de detección de duplicados para cuentas y contactos. Estas reglas se activan automáticamente, por lo que no tiene que hacer nada para configurar la detección de duplicados para estos tipos de registros.  
  
> [!NOTE]
>  Si la característica está disponible en el sistema, es posible que pueda buscar duplicados de otros tipos de registros, además de contactos y cuentas. Pregunte al administrador del sistema. [Búsqueda de un administrador o una persona de soporte técnico](find-admin.md)  
  
## <a name="merge-duplicate-records"></a>Combinación de registros duplicados  
  
1. Seleccione los registros duplicados y luego **Combinar**.  
  
   > [!div class="mx-imgBorder"] 
   > ![Registro de contacto duplicado detectado](media/duplicates-detected_2.png "Registro de contacto duplicado detectado")  
  
2. En el cuadro de diálogo **Combinar registros**, seleccione el registro maestro (el que desea mantener,) y seleccione cualquier campo en el nuevo registro que desea combinar en el registro maestro. Los datos de estos campos pueden reemplazar los datos existentes en el registro maestro. Seleccione **Aceptar**.  
  
     
   > [!div class="mx-imgBorder"] 
   > ![Cuadro de diálogo Combinar registros](media/merge-records-dialog.png "Cuadro de diálogo Combinar registros")  
  
> [!NOTE]
>  Hay algunas situaciones en las que se pueden detectar duplicados:  
> 
> - Cuando se crea o se actualiza un registro.  
>   - Cuando utiliza Dynamics 365 for Outlook y pasa del modo desconectado al modo conectado.  
>   - Al importar datos mediante el Asistente para la importación de datos.  
> 
>   No se detectan duplicados al combinar registros, guardar una actividad como completada ni cambiar el estado de un registro, por ejemplo, al activarlo o reactivarlo.  
