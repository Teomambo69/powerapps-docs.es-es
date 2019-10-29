---
title: Restringir el acceso a un portal mediante la dirección IP | MicrosoftDocs
description: Instrucciones para restringir el acceso al portal por dirección IP.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ba3315ed9ba6f2a0c89b6710debc55c4be00a427
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975941"
---
# <a name="restrict-portal-access-by-ip-address"></a>Restringir el acceso al portal por dirección IP

El portal es público cuando lo aprovisiona cualquier usuario desde cualquier equipo. Ahora puede restringir el acceso a su portal desde una lista de direcciones IP. Por ejemplo, es posible que una organización gubernamental quiera mostrar su contenido solo dentro de la red corporativa. Es posible que una organización comercial quiera mostrar el portal solo cuando esté publicado y no mientras esté en desarrollo para evitar cualquier pérdida de datos.

Cuando se genera una solicitud al portal desde cualquier usuario, su dirección IP se evalúa con respecto a la lista de permitidos. Si la dirección IP no está en la lista, el portal muestra una página web con un código de Estado HTTP 403.

Para agregar o quitar direcciones IP, debe tener asignado uno de los siguientes roles:
- Administrador global de Office 365 
- Administrador de servicios. Más información: [usar el rol de administrador de servicios para administrar el inquilino](https://technet.microsoft.com/en-us/library/mt793847.aspx)  
- Administrador del sistema del entorno de Common Data Service seleccionado para el portal

## <a name="add-an-ip-address"></a>Agregar una dirección IP

Para permitir el acceso a un portal desde una dirección IP o un conjunto de direcciones IP, puede Agregar las direcciones IP a la lista. Esto permite tener acceso al portal únicamente desde la lista de direcciones IP agregadas. Si no agrega ninguna dirección IP, se podrá acceder al portal desde todas las direcciones IP.

Una vez que agregue una dirección IP a la lista de restricciones, solo se podrá acceder al portal a la dirección IP especificada. Si intenta obtener acceso al portal desde cualquier otra dirección IP, se denegará el acceso y se mostrará una página web con un código de Estado HTTP 403. El contenido de esta página web es estático y no se puede modificar.

> [!div class=mx-imgBorder]
> ![Html 403 error](../media/ip-address-page-error.png "HTML 403") error  

> [!NOTE]
> Debe especificar una dirección IP pública a la que se pueda acceder desde el portal. No se puede tener acceso a la dirección IP privada en el portal.

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **configuración de la restricción de direcciones IP**. Se muestra una lista de direcciones IP y su tipo.

    > [!div class=mx-imgBorder]
    > ![Configurar restricción de dirección IP](../media/set-up-ip-address-restrict.png "configurar restricción de dirección IP")

3.  En la página configurar restricción de direcciones IP, seleccione **Agregar nuevo**.

4.  En la ventana Agregar una dirección IP, escriba los valores siguientes:

    - **Seleccionar tipo de dirección IP**: Seleccione si la dirección IP es IPv4 o IPv6.

    - **Especifique la dirección IP en la notación CIDR**: especifique la dirección IP en la notación CIDR. Más información: [enrutamiento entre dominios con clases](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![Agregar una dirección IP](../media/add-ip-address.png "Agregar una dirección IP")    

5.  Seleccione **configurar**.

## <a name="remove-an-ip-address"></a>Quitar una dirección IP

Para quitar el acceso a un portal de una dirección IP permitida previamente, puede quitar la dirección IP de la lista. Si quita todas las direcciones IP, se podrá acceder al portal desde todas las direcciones IP.

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **configuración de la restricción de direcciones IP**. Se muestra una lista de direcciones IP y su tipo.

    > [!div class=mx-imgBorder]
    > ![Configurar restricción de dirección IP](../media/set-up-ip-address-restrict.png "configurar restricción de dirección IP")

3.  Seleccione **quitar una dirección IP (x)** junto a la dirección IP que se va a quitar.

4.  Seleccione **quitar** en el mensaje de confirmación.

