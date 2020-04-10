---
title: 'Versión preliminar: Envío de correo electrónico mediante la experiencia de correo electrónico mejorada en aplicaciones basadas en modelos | Microsoft Docs'
description: Use la experiencia de correo electrónico mejorada para redactar un correo electrónico sin abandonar el contexto en el que está trabajando.
ms.date: 04/09/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: shubhadaj
ms.author: shujoshi
manager: annbe
ms.openlocfilehash: bc4b7023e56ae75b34f797089a812ab4ea1f8d84
ms.sourcegitcommit: 2484ebce6563cfd1c849e1e2f66dd2d29fdb7b64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2020
ms.locfileid: "81007948"
---
# <a name="send-email-using-the-enhanced-email-experience"></a>Envío de correo electrónico con la experiencia de correo electrónico mejorada

La experiencia de correo electrónico mejorada en aplicaciones basadas en modelos permite redactar un correo electrónico sin abandonar el registro en el que está trabajando. Con la experiencia de correo electrónico mejorada se puede:

- Ir a diferentes páginas sin perder el contenido del correo electrónico.
- Minimizar la ventana de correo electrónico para volver a los registros en los que se está trabajando.
- Expandir la ventana emergente del editor de correo electrónico para ver más opciones de correo electrónico.
- Abrir simultáneamente tres ventanas emergentes de redacción de correo electrónico.
- Buscar y aplicar una plantilla predefinida a un correo electrónico que se está redactando.
- Insertar datos adjuntos en el correo electrónico.


> [!IMPORTANT]
> - Los administradores del sistema deben habilitar la experiencia de correo electrónico mejorada para que se pueda usar.
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE[cc-preview-features-no-ms-support](../includes/cc-preview-features-no-ms-support.md)]

Redacte un correo electrónico mediante la experiencia de correo electrónico mejorada:

1. En la sección **Escala de tiempo** de registros como Cuenta o Contacto, seleccione **+** y, en **Actividades**, seleccione **Correo electrónico**.

   Se abre una nueva ventana emergente de correo electrónico. 

   > [!div class="mx-imgBorder"]
   > ![Ventana emergente de correo electrónico mejorado](media/enhanced-email-pop-up.png "Ventana emergente de correo electrónico mejorado")

   Los campos **De** y **Para** se rellenan automáticamente en función del usuario y de la cuenta y el contacto del registro original.

2. Escriba el correo electrónico desde cero o seleccione **Insertar plantilla** para buscar y aplicar una plantilla. Para obtener más información sobre cómo insertar una plantilla de correo electrónico, vea [Inserción de una plantilla de correo electrónico](insert-email-template.md).

3. Seleccione **Adjuntar archivo** si quiere agregar datos adjuntos.

4. Seleccione **Insertar firma** para buscar y agregar la firma.

5. Cuando termine, seleccione **Enviar**. 

> [!IMPORTANT]
> - La experiencia de correo electrónico mejorada solo está disponible para las actividades de correo electrónico creadas en la sección **Escala de tiempo** de una aplicación basada en modelo. 
> - La ventana emergente de correo electrónico mejorado solo se abre si el alto y el ancho de la pantalla es de al menos 400 x 650 píxeles o superior. Si es inferior, se le lleva al formulario estándar en lugar de a la experiencia de correo electrónico mejorada. 

### <a name="see-also"></a>Vea también

[Configuración de correo electrónico mejorado](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[Inserción de una plantilla de correo electrónico](insert-email-template.md)
