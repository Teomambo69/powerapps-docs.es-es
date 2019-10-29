---
title: Restablecer un portal | MicrosoftDocs
description: Obtenga información acerca de cómo restablecer un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7b5bbc05ca7adf7fad9725215f8a7d6c06c035bb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975734"
---
# <a name="reset-a-portal"></a>Restablecimiento de un portal

Una vez que se aprovisiona un portal, es posible que tenga que eliminar recursos del portal en determinadas circunstancias, por ejemplo, si mueve la organización a otro inquilino u otro centro de recursos o si desea quitar el portal de la organización.

Para ello, puede restablecer el portal, con lo que se eliminarán todos los recursos hospedados asociados a él. Después, puede volver a aprovisionar el portal. Una vez finalizada la operación de restablecimiento, ya no será posible acceder a la dirección URL del portal.

Es importante tener en cuenta que el restablecimiento del portal no quita las soluciones o la configuración del portal presentes en la instancia y permanecerán tal cual.

Puede restablecer un portal totalmente configurado o un portal en el que se haya producido un error en el aprovisionamiento o la actualización de una instancia.

Para restablecer un portal configurado:

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **acciones del portal** > **restablecer portal**.

    > [!div class=mx-imgBorder]
    > ![Restablecimiento de]un portal(../media/reset-portal.png "restablecimiento de") un portal

3.  Seleccione **restablecer** en la ventana de confirmación.

> [!NOTE]
> - Si no tiene los permisos adecuados en una aplicación Azure Active Directory asociada, se muestra un error. Debe ponerse en contacto con el administrador global para obtener los permisos adecuados.
> - Si ha aprovisionado un portal mediante el complemento de portal anterior y el portal se ha restablecido correctamente, el nombre del portal y su estado en la pestaña **aplicaciones** del centro de administración de Dynamics 365 no cambian. Por ejemplo, si el nombre y el estado del portal son portal 1 y están configurados respectivamente, después de restablecer el portal, estos valores no cambian. Si desea cambiar el nombre del portal, puede cambiarlo en la pestaña **detalles del portal** del centro de administración de portales de PowerApps. Sin embargo, el valor de estado no se puede revertir a no configurado.
> - Es importante tener en cuenta que el estado del portal en la pestaña **aplicaciones** no representa su estado de aprovisionamiento y no afecta al funcionamiento del portal. Simplemente muestra si alguna vez ha tenido acceso al centro de administración de portales de PowerApps para ese portal correspondiente o no.

Si el portal no se ha aprovisionado correctamente, entra en un estado de error y se muestra la pantalla siguiente. En este caso, también puede restablecer el portal seleccionando **restablecer portal** en la pantalla de error.

> [!div class=mx-imgBorder]
> ![Error al aprovisionar un](../media/provision-portal-error.png "error del portal durante el aprovisionamiento de un portal")

## <a name="troubleshooting"></a>Solución de problemas

En esta sección se proporciona información acerca de la solución de problemas al restablecer un portal.

### <a name="reset-request-could-not-be-submitted"></a>No se pudo enviar la solicitud de restablecimiento

Si no se pudo enviar una solicitud de restablecimiento del portal, se muestra un error como se muestra en la siguiente imagen. En este caso, debe cerrar y volver a abrir el centro de administración de portales de PowerApps y volver a intentar restablecer el portal. Si el problema persiste, póngase en contacto con el soporte técnico de Microsoft.

> [!div class=mx-imgBorder]
> ![Error al restablecer un](../media/reset-portal-request-error.png "error del portal al restablecer un portal")

### <a name="reset-portal-job-fails"></a>Error al restablecer el trabajo del portal

Si se produce un error en un trabajo de restablecimiento del portal, se muestra un mensaje de error junto con la acción **restablecer portal** .

> [!div class=mx-imgBorder]
> ![Error al restablecer un](../media/reset-portal-error.png "error del portal al restablecer un portal")

Normalmente, se trata de errores transitorios y debe seleccionar **restablecer portal** para reiniciar el trabajo. Si el problema persiste, póngase en contacto con el soporte técnico de Microsoft.

