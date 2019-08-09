---
title: Agregue un rol de conexión a para vincular registros entre sí | MicrosoftDocs
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
ms.openlocfilehash: c606a7b809f1684cbe60b5e53e4b291f11b1d164
ms.sourcegitcommit: 4e4f7945c3f24faf9bb8a856a5f3892cbfd113be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2019
ms.locfileid: "68786910"
---
# <a name="add-a-connection-role-to-to-link-records-to-each-other"></a>Agregue un rol de conexión a para vincular registros entre sí |

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Las conexiones le permiten asociar fácilmente usuarios, contactos, ofertas, pedidos de ventas y muchos otros registros de entidad entre sí. A los registros de la asociación se les pueden asignar roles concretos que ayuden a definir el propósito de la relación.

Es una forma rápida de crear varias conexiones y roles para un registro determinado. Por ejemplo, un contacto puede tener muchas relaciones con otros contactos, cuentas o contratos. En cada relación, un contacto puede desempeñar un rol diferente.

Los roles de conexión se asocian directamente a una conexión. Para usar un rol de conexión, primero debe agregar una conexión al registro.

Para poder agregar roles de conexión, debe habilitarlo el administrador. Para obtener más información, vea [configurar roles de conexión](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/configure-connection-roles).

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
    > ![Elegir nuevo rol de conexión](media/connection3.png "Elegir nuevo rol de conexión")  

    > [!NOTE]
    > Si ha especificado la información antes de crear un nuevo rol de conexión, se mostrará un cuadro de diálogo de advertencia en el que se le preguntará si desea cancelar y seguir trabajando en la conexión o continuar y salir del registro actual en el que está trabajando.

6. Para crear un nuevo rol de conexión, en la pantalla **nuevo rol de conexión** escriba un nombre y, a continuación, elija una **categoría de rol de conexión**.

    > [!div class="mx-imgBorder"]
    >  ![Agregar categoría de rol de conexión](media/connection4.png "Agregar categoría de rol de conexión") 

7. Cuando haya terminado, seleccione **guardar & cerrar**.

  
## <a name="manage-connection-roles"></a>Administrar roles de conexión

Para administrar un rol de conexión, seleccione el rol de conexión de una entidad de conexión. Se abrirá el registro de entidad del rol de conexión.  Puede editar el nombre, seleccionar una categoría de rol de conexión y agregar una descripción.


   > [!div class="mx-imgBorder"]
   > ![Editar rol de conexión](media/connection7.png "Rol Editconnection") 
  
También puede administrar los tipos de rol de conexión que desea asociar al rol de conexión.

1. Abra el rol de conexión y, a continuación, seleccione **administrar tipo de registro** en el comando. 

    > [!div class="mx-imgBorder"]
    > ![Editar rol de conexión](media/connection5.png "Rol Editconnection") 
  

2. Se abrirá una lista de tipos de roles de conexión que puede Agregar o quitar para este rol de conexión.

    > [!div class="mx-imgBorder"]
    > ![Administrar tipo de registro](media/connection6.png "Administrar tipo de registro") 


