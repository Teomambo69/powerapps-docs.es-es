---
title: Adición de un rol de conexión para vincular registros entre sí | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2019
ms.locfileid: "72239570"
---
# <a name="add-a-connection-role-to-link-records-to-each-other"></a>Adición de un rol de conexión para vincular registros entre sí

Las conexiones le permiten asociar fácilmente usuarios, contactos, presupuestos, pedidos de ventas y muchos otros registros de entidad entre sí. A los registros de la asociación se les pueden asignar roles concretos que ayuden a definir el propósito de la relación.

Es una forma rápida de crear varias conexiones y roles en un registro determinado. Por ejemplo, un contacto puede tener muchas relaciones con otros contactos, cuentas o contratos. En cada relación, un contacto puede tener un rol diferente.

Los roles de conexión se asocian directamente a una conexión. Para usar un rol de conexión, primero debe agregar una conexión al registro.

Para poder agregar roles de conexión, el administrador debe habilitar esta función. Para obtener más información, vea [Configurar roles de conexión](https://docs.microsoft.com/powerapps/maker/common-data-service/configure-connection-roles).

1. Para agregar o administrar conexiones, seleccione el registro que quiera administrar, como una oportunidad.  
2. Seleccione la pestaña **Relacionados** y después **Conexión**. Se abrirá la cuadrícula de conexión con la lista de conexiones del registro.

    > [!div class="mx-imgBorder"]
    > ![Adición de un nuevo rol de conexión](media/connection1.png "Add a new connection role") 

3. Seleccione **Conectar** y, después, elija **A otro** o **A mí**.

    > [!div class="mx-imgBorder"]
    > ![Selección del tipo de conexión](media/connection2.png "Select connection type") 
  
4. En el campo **Nombre**, escriba o busque el nombre del registro para la conexión.

5. En el campo **Como este rol**, seleccione el icono de búsqueda y después elija **New Connection Role** (Nuevo rol de conexión). También puede usar la búsqueda para encontrar un rol existente que quiera asociar a la conexión y después seleccionar **Guardar**.

    > [!div class="mx-imgBorder"]
    > ![Elección del nuevo rol de conexión](media/connection3.png "Choose new connection role")  

    > [!NOTE]
    > Si ha especificado la información antes de crear un rol de conexión, se mostrará un cuadro de diálogo de advertencia en el que se le preguntará si quiere cancelar y seguir trabajando en la conexión o continuar y salir del registro actual en el que está trabajando.

6. Para crear un rol de conexión, en la pantalla **New Connection Role** (Nuevo rol de conexión) escriba un nombre y después elija una **categoría de rol de conexión**.

    > [!div class="mx-imgBorder"]
    >  ![Adición de la categoría de rol de conexión](media/connection4.png "Add connection role category") 

7. Cuando termine, seleccione **Guardar y cerrar**.

  
## <a name="manage-connection-roles"></a>Administración de los roles de conexión

Para administrar un rol de conexión, seleccione el rol en cuestión de una entidad de conexión. Se abrirá el registro de entidad del rol de conexión.  Puede editar el nombre, seleccionar una categoría de rol de conexión y agregar una descripción.


   > [!div class="mx-imgBorder"]
   > ![Edición del rol de conexión](media/connection7.png "Edit connection role") 
  
También puede administrar los tipos de rol de conexión que quiere asociar al rol de conexión.

1. Abra el rol de conexión y después seleccione **Manage Record Type** (Administrar tipo de registro) en el comando. 

    > [!div class="mx-imgBorder"]
    > ![Edición del rol de conexión](media/connection5.png "Edit connection role") 
  

2. Se abrirá una lista de tipos de roles de conexión que puede agregar o quitar en este rol de conexión.

    > [!div class="mx-imgBorder"]
    > ![Administración del tipo de registro](media/connection6.png "Manage Record Type") 


