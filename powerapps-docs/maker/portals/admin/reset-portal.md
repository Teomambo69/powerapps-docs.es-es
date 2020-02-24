---
title: Restablecer un portal | MicrosoftDocs
description: Aprenda a restablecer un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 96e661f5774cedff7a3bc2317f02273af7041d13
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978697"
---
# <a name="reset-a-portal"></a>Restablecer un portal

Una vez aprovisionado un portal, es posible que tenga que eliminar recursos del portal en determinadas circunstancias, como si tiene que trasladar su organización a otro inquilino o centro de datos, o si desea quitar el portal de su organización.

Para ello, puede restablecer el portal, que eliminará todos los recursos hospedados asociados a él.. A continuación, puede realizar de nuevo el aprovisionamiento del portal. Una vez que finalice la operación de restablecimiento, no dispondrá de acceso a la dirección URL del portal.

Es importante tener en cuenta que el restablecimiento del portal no quita la configuración del portal o las soluciones presentes en su instancia y seguirán como están.

Puede restaurar un portal configurado completamente o un portal para el que se haya producido un problema al aprovisionar o actualizar una instancia.

Para restaurar un portal configurado:

1.  Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  Vaya a **Acciones del portal** > **Restablecer portal**.

    > [!div class=mx-imgBorder]
    > ![Restablecer un portal](../media/reset-portal.png "Restablecer un portal")

3.  Seleccione **Restablecer** en la ventana de confirmación.

> [!NOTE]
> - Si no dispone de los permisos adecuados en una aplicación asociada de Azure Active Directory, se mostrará un error. Debe ponerse en contacto con el administrador global para obtener los permisos adecuados.
> - Si ha aprovisionado un portal utilizando el complemento de portal anterior y el portal se restablece correctamente, el nombre del portal y su estado en la pestaña **Aplicaciones** en el **Centro de administración de Dynamics 365** no cambia. Por ejemplo, si su nombre de portal y estado eran Portal 1 y Configurado respectivamente, después de restablecer el portal, estos valores no cambian. Si desea cambiar el nombre de portal, puede cambiarlo en la pestaña **Detalles del portal** en el Centro de administración de portales de Power Apps. Sin embargo, el valor del estado no se puede revertir a No configurado.
> - Es importante tener en cuenta que el estado del portal de la pestaña **Aplicaciones** no representa el estado de aprovisionamiento y no afecta al funcionamiento del portal. Simplemente muestra si alguna vez ha obtenido acceso al Centro de administración de portales de Power Apps para ese portal correspondiente o no.

Si su portal no se aprovisiona correcta, aparece un estado de error y se muestra la siguiente pantalla. En este caso, también puede restablecer el portal seleccionando **Restablecer portal** en la pantalla de error.

> [!div class=mx-imgBorder]
> ![Error mientras aprovisiona un portal](../media/provision-portal-error.png "Error mientras aprovisiona un portal")

## <a name="troubleshooting"></a>Solución de problemas

Esta sección proporciona información sobre los problemas de solución de problemas cuando se restablece un portal.

### <a name="reset-request-could-not-be-submitted"></a>Restablecer una solicitud que no se pudo enviar

Si no se pudo enviar una solicitud de restablecimiento del portal, se mostrará un error como el que aparece en la siguiente imagen. En este caso, debe cerrar y volver a abrir el Centro de administración de portales de Power Apps e intentar restablecer el portal de nuevo. Si el problema persiste, póngase en contacto con el soporte técnico de Microsoft.

> [!div class=mx-imgBorder]
> ![Error mientras restablece un portal](../media/reset-portal-request-error.png "Error mientras restablece un portal")

### <a name="reset-portal-job-fails"></a>Error al restablecer un trabajo en el portal

Si se produce un error al restablecer un trabajo en el portal, se mostrará un mensaje de error junto con la acción **Restablecer portal**.

> [!div class=mx-imgBorder]
> ![Error mientras restablece un portal](../media/reset-portal-error.png "Error mientras restablece un portal")

Normalmente, estos son errores transitorios y debe seleccionar **Restablecer portal** para reiniciar el trabajo. Si el problema persiste, póngase en contacto con el soporte técnico de Microsoft.

