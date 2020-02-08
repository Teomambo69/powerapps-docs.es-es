---
title: Vista previa del envío de correo electrónico con la experiencia de correo electrónico mejorada en las aplicaciones controladas por modelos | MicrosoftDocs
description: Utilice la experiencia de correo electrónico mejorada para crear un correo electrónico sin tener que mantener el contexto del trabajo en el que está trabajando.
ms.date: 02/03/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: shubhadaj
ms.author: shujoshi
manager: annbe
ms.openlocfilehash: 6f3c603284e5f5d53380f5caa932cafac11e2d7a
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051945"
---
# <a name="preview-send-email-using-the-enhanced-email-experience"></a>Vista previa: enviar correo electrónico con la experiencia de correo electrónico mejorada

Enviar correo electrónico con la experiencia de correo electrónico mejorada es una característica de acceso temprano. Puede participar pronto para habilitar estas características en su entorno. Esto le permitirá probar estas características y después adoptarlas en sus entornos. Para obtener información sobre cómo habilitar estas características, consulte [participación en las actualizaciones de la versión 1 de 2020](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).

La experiencia de correo electrónico mejorada en las aplicaciones controladas por modelos permite crear un correo electrónico sin tener que cerrar el registro en el que están trabajando. Con la experiencia de correo electrónico mejorada, puede:

- Navegue a diferentes páginas sin perder el contenido de correo electrónico.
- Minimice la ventana de correo electrónico para volver a los registros en los que estaba trabajando.
- Expanda la ventana emergente editor de correo electrónico para ver más opciones de correo electrónico.
- Abra simultáneamente tres ventanas emergentes de redacción de correo electrónico.
- Busque y aplique una plantilla predefinida a un correo electrónico que esté creando.
- Insertar datos adjuntos en el correo electrónico.


> [!IMPORTANT]
> - Los administradores del sistema deben habilitar la experiencia de correo electrónico mejorada antes de poder usarla.
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE[cc-preview-features-no-ms-support](../includes/cc-preview-features-no-ms-support.md)]

Redacte un correo electrónico con la experiencia mejorada:

1. En la sección de la **escala de tiempo** de registros como cuenta o contacto, seleccione **+** y, en **actividades**, seleccione **correo electrónico**.

   Se abre una nueva ventana emergente de correo electrónico. 

   > [!div class="mx-imgBorder"]
   > ![Ventana emergente de correo electrónico mejorado](media/enhanced-email-pop-up.png "Ventana emergente de correo electrónico mejorado")

   Los campos **desde** y **hasta** se rellenan automáticamente según el usuario y la cuenta y el contacto del registro original.

2. Escriba el correo electrónico desde cero o seleccione **Insertar plantilla** para buscar y aplicar una plantilla. Para obtener más información sobre la inserción de una plantilla de correo electrónico, consulte [inserción de una plantilla de correo electrónico](insert-email-template.md).

3. Seleccione **adjuntar archivo** si desea agregar datos adjuntos.

4. Seleccione **Insertar firma** para buscar y agregar la firma.

5. Cuando haya terminado, seleccione **Enviar**. 

> [!IMPORTANT]
> - La experiencia de correo electrónico mejorada solo está disponible para las actividades de correo electrónico creadas a partir de la sección **escala de tiempo** de una aplicación controlada por modelos. 
> - La ventana emergente correo electrónico mejorado solo se abre cuando el alto y el ancho del tamaño de pantalla es de al menos 400 x 650 píxeles o superior. Si es inferior, se le dirigirá al formulario estándar en lugar de a la experiencia de correo electrónico mejorada. 

### <a name="see-also"></a>Vea también

[Configuración del correo electrónico mejorado](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[Insertar una plantilla de correo electrónico](insert-email-template.md)
