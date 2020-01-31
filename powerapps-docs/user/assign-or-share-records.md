---
title: Asignar o compartir registros | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/20/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 81a6513f98351f656fdac3fd0ccc24a10061ca85
ms.sourcegitcommit: d0f02fdaa125feaea884932e1ef31b8fea1bd10c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886513"
---
# <a name="assign-or-share-records"></a>Asignar o compartir registros

Si desea que otra persona de su organización controle un registro de cliente, puede asignar el registro a esa persona. También puede asignar un registro a un equipo o a usted mismo.  

Use la opción **compartir** si desea mantener la propiedad del registro pero deje que otra persona trabaje con él. 

1. En el panel de navegación izquierdo, seleccione un tipo de registro. Por ejemplo, **contactos**.

2. En la lista de registros, seleccione el registro que desea reasignar.  
  
3. En la barra de comandos, seleccione **asignar**.

   > [!div class="mx-imgBorder"]
   > ![Reasignar un registro](media/assign1.png "Reasignar un registro")

   > [!NOTE]
   > Si desea mantener la propiedad del registro pero dejar que otra persona trabaje con él, seleccione **compartir**. A continuación, use la información sobre herramientas para guiarle a través de la opción de **uso compartido** . 
   
4. En el cuadro de diálogo asignar, en el área **asignar a** , elija **mí** o **usuario o equipo**.

   > [!div class="mx-imgBorder"]
   > ![Reasignación de un registro a mí o equipo](media/assign2.png "Reasignar un equipo de registro me")
  
   Si selecciona **usuario o equipo**, en el cuadro **buscar registros** , escriba el nombre del usuario o equipo. Si necesita crear un nuevo registro, seleccione **+ nuevo**.
  
5. Cuando haya terminado, seleccione **asignar**.

## <a name="use-advanced-find-to-reassign-records"></a>Usar búsqueda avanzada para reasignar registros

Use la búsqueda avanzada para buscar registros y reasignarlos a otra persona. Para obtener más información sobre la búsqueda avanzada, vea [crear, editar o guardar una búsqueda avanzada](advanced-find.md).


1. En la barra de comandos, seleccione **búsqueda avanzada**.

   > [!div class="mx-imgBorder"]
   > ![Búsqueda avanzada](media/assign3.png "advacned buscar")
   
2. En la lista de registros, seleccione los registros que desea reasignar y, a continuación, seleccione la opción asignar.

   > [!div class="mx-imgBorder"]
   > ![Reasignación de un registro mediante la búsqueda avanzada](media/assign4.png "Reasignación de un registro mediante advacned Find")
   
 
 ## <a name="reassign-all-records-for-admins"></a>Reasignar todos los registros (para administradores)
 
 Un administrador puede reasignar todos los registros de un usuario desde el área de configuración de administrador.
 
 1. Vaya a **Configuración** > **Seguridad**.
 2. Seleccione **usuarios** y seleccione un nombre de usuario para abrir el perfil del usuario.
 3. En la barra de comandos, seleccione **REASIGNAR registros**.
 
   > [!div class="mx-imgBorder"]
   > ![Reasignar todos los registros](media/assign5.png "Reasignar todos los registros")
   
 4. En el cuadro de diálogo **reasignar registros** , elija cómo desea reasignar todos los registros y, después, seleccione **Aceptar**.
 
  > [!NOTE]
   > La opción **reasignar registros** reasignará todos los registros independientemente de su estado. Los registros inactivos y activos se reasignarán al otro usuario o equipo. Esto también desactivará todos los procesos activados, incluidos los flujos de trabajo y las reglas de negocios, cuando se reasigne el registro a otro usuario o equipo. El nuevo propietario debe activar los procesos que se deben usar.
 
   > [!div class="mx-imgBorder"]
   > ![Reasignar todos los registros a un usuario o equipo](media/assign6.png "Reasignar todos los registros a un usuario o equipo")
 

