---
title: Agregar un rol de conexión para vincular registros entre sí | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 8/01/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4552c874ca6be72d37465abd2492a64979aba865
ms.sourcegitcommit: 5ec4cab1dd934446ec57c320a375e577560ac88a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2019
ms.locfileid: "72239570"
---
# <a name="add-a-connection-role-to-link-records-to-each-other"></a>Agregar un rol de conexión para vincular registros entre sí

Las conexiones le permiten asociar fácilmente usuarios, contactos, ofertas, pedidos de ventas y muchos otros registros de entidad entre sí. A los registros de la asociación se les pueden asignar roles concretos que ayuden a definir el propósito de la relación.

Es una forma rápida de crear varias conexiones y roles para un registro determinado. Por ejemplo, un contacto puede tener muchas relaciones con otros contactos, cuentas o contratos. En cada relación, un contacto puede desempeñar un rol diferente.

Los roles de conexión se asocian directamente a una conexión. Para usar un rol de conexión, primero debe agregar una conexión al registro.

Para poder agregar roles de conexión, debe habilitarlo el administrador. Para obtener más información, vea [configurar roles de conexión](https://docs.microsoft.com/powerapps/maker/common-data-service/configure-connection-roles).

1. Para agregar o administrar conexiones, seleccione el registro que desea administrar como una oportunidad.  
2. Seleccione la pestaña **relacionado** y, a continuación, seleccione **conexión**. Se abrirá la cuadrícula de conexión con la lista de conexiones del registro.

    > [!div class="mx-imgBorder"]
    > ![Agregar un nuevo rol de conexión](media/connection1.png "Agregar un nuevo rol de conexión") 

3. Seleccione **conectar** y, luego, elija **otro** o **yo**.

    > [!div class="mx-imgBorder"]
    > ![Seleccionar tipo de conexión](media/connection2.png "Seleccionar tipo de conexión") 
  
4. En el campo **nombre** , escriba o busque el nombre del registro para la conexión.

5. En el campo **como este rol** , seleccione el icono de búsqueda y, a continuación, elija **nuevo rol de conexión**. O bien, use la búsqueda para buscar un rol existente que desee asociar a la conexión y, a continuación, seleccione **Guardar**.

    > [!div class="mx-imgBorder"]
    > ![Elegir nuevo rol de conexión],(media/connection3.png "elegir nuevo rol de conexión")  

    > [!NOTE]
    > Si ha especificado la información antes de crear un nuevo rol de conexión, se mostrará un cuadro de diálogo de advertencia en el que se le preguntará si desea cancelar y seguir trabajando en la conexión o continuar y salir del registro actual en el que está trabajando.

6. Para crear un nuevo rol de conexión, en la pantalla **nuevo rol de conexión** escriba un nombre y, a continuación, elija una **categoría de rol de conexión**.

    > [!div class="mx-imgBorder"]
    >  ![Agregar categoría de rol de conexión](media/connection4.png "Agregar categoría de rol de conexión") 

7. Cuando haya terminado, seleccione **guardar & cerrar**.

  
## <a name="manage-connection-roles"></a>Administrar roles de conexión

Para administrar un rol de conexión, seleccione el rol de conexión de una entidad de conexión. Se abrirá el registro de entidad del rol de conexión.  Puede editar el nombre, seleccionar una categoría de rol de conexión y agregar una descripción.


   > [!div class="mx-imgBorder"]
   > ![Editar]rol de conexión rol de(media/connection7.png "Editconnection") 
  
También puede administrar los tipos de rol de conexión que desea asociar al rol de conexión.

1. Abra el rol de conexión y, a continuación, seleccione **administrar tipo de registro** en el comando. 

    > [!div class="mx-imgBorder"]
    > ![Editar]rol de conexión rol de(media/connection5.png "Editconnection") 
  

2. Se abrirá una lista de tipos de roles de conexión que puede Agregar o quitar para este rol de conexión.

    > [!div class="mx-imgBorder"]
    > ![Administrar tipo]de registro administrar tipo de(media/connection6.png "registro") 


