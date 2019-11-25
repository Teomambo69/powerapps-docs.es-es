---
title: Limitar el acceso a un portal mediante dirección IP | MicrosoftDocs
description: Instrucciones para limitar el acceso al portal mediante la dirección IP.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: da8e6ac6d4e86a12ba196393073706c3705e4a92
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756144"
---
# <a name="restrict-portal-access-by-ip-address"></a>Limitar el acceso al portal mediante la dirección IP

El portal es público cuando está aprovisionado y accesible para cualquier persona desde cualquier equipo. Ahora puede limitar el acceso al su portal desde una lista de direcciones IP. Por ejemplo, una organización gubernamental podría querer hacer visible su contenido solo dentro de su red corporativa. Una organización comercial puede querer mostrar el portal solo cuando ha sido publicado y no mientras se encuentra en el desarrollo para evitar cualquier fuga de datos.

Cuando se genera una solicitud al portal por parte de cualquier usuario, se evalúa su dirección IP con la lista de permitidos. Si la dirección IP no está en la lista, el portal muestra una página web con un código de estado HTTP 403.

Para agregar o quitar direcciones IP, debe tener asignado uno de los roles siguientes:
- Administrador global de Office 365 
-  Administrador de servicios. Más información: [Uso del rol de administrador de servicios para administrar el inquilino](https://technet.microsoft.com/library/mt793847.aspx)  
- Administrador del sistema del entorno de Common Data Service seleccionado para el portal

## <a name="add-an-ip-address"></a>Agregar una dirección IP

Para permitir el acceso a un portal desde una dirección IP o un conjunto de direcciones IP, puede agregar direcciones IP a la lista. Esto permite que se acceda al portal solo desde la lista de direcciones IP agregadas. Si no agrega ninguna dirección IP, el portal será accesiblede desde todas las direcciones IP.

Una vez que agrega una dirección IP a la lista de restricción, el portal será accesible solo para la dirección IP especificada. Si intenta acceder al portal desde cualquier otra dirección IP, el acceso será denegado se y se mostrará una página web con un código de estado HTTP 403. El contenido de esta página web es estático y no se puede modificar.

> [!div class=mx-imgBorder]
> ![Error HTML 403](../media/ip-address-page-error.png "Error HTML 403")  

> [!NOTE]
> Debe especificar una dirección IP pública a la que pueda acceder el portal. El portal no puede acceder a la dirección IP privada.

1.  Abra [Centro de administración de Portales de PowerApps](admin-overview.md).

2.  Vaya a **Configurar restricción de direcciones IP**. Se muestra una lista de direcciones IP y su tipo

    > [!div class=mx-imgBorder]
    > ![Configurar restricción de direcciones IP](../media/set-up-ip-address-restrict.png "Configurar restricción de direcciones IP")

3.  En la página configuración de restricción de direcciones IP, seleccione **Agregar nueva**.

4.  En la ventana Agregar una dirección IP, especifique los valores siguientes:

    - **Seleccionar tipo de dirección IP**: Seleccione si la dirección IP es IPv4 o IPv6.

    - **Especificar la dirección IP en la notación CIDR**: Especifique la dirección IP en la notación CIDR. Más información: [Enrutamiento entre dominios sin clase](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![Agregar una dirección IP](../media/add-ip-address.png "Agregar una dirección IP")    

5.  Seleccione **Configurar**.

## <a name="remove-an-ip-address"></a>Quitar una dirección IP

Para quitar el acceso a un portal de una dirección IP anteriormente permitida, puede quitar la dirección IP de la lista. Si quita todas las direcciones IP, el portal será accesiblede desde todas las direcciones IP.

1.  Abra [Centro de administración de Portales de PowerApps](admin-overview.md).

2.  Vaya a **Configurar restricción de direcciones IP**. Se muestra una lista de direcciones IP y su tipo

    > [!div class=mx-imgBorder]
    > ![Configurar restricción de direcciones IP](../media/set-up-ip-address-restrict.png "Configurar restricción de direcciones IP")

3.  Seleccione **Quitar una dirección IP (x)** junto a la dirección IP que desea quitar.

4.  Seleccione **Quitar** en el mensaje de confirmación.

