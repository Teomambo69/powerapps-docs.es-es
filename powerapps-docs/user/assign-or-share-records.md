---
title: Asignación o uso compartido de registros | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886513"
---
# <a name="assign-or-share-records"></a>Asignar o compartir registros

Si quiere que otra persona de la organización use un registro de cliente, puede asignar el registro a esa persona. También puede asignar un registro a un equipo o a sí mismo.  

Use la opción **Compartir** si quiere mantener la propiedad del registro, pero dejar que otra persona trabaje en él. 

1. En el panel de navegación izquierdo, seleccione un tipo de registro. Por ejemplo, **Contactos**.

2. En la lista de registros, seleccione el registro que quiera reasignar.  
  
3. En la barra de comandos, seleccione **Asignar**.

   > [!div class="mx-imgBorder"]
   > ![Reasignación de un registro](media/assign1.png "Reasignación de un registro")

   > [!NOTE]
   > Si quiere mantener la propiedad del registro pero dejar que otra persona trabaje en él, seleccione **Compartir**. Después, use la información sobre herramientas para guiarle por la opción **Compartir**. 
   
4. En el área **Asignar a** del cuadro de diálogo Asignar, elija **Yo** o **Usuario o equipo**.

   > [!div class="mx-imgBorder"]
   > ![Reasignación de un registro a mí o a un equipo](media/assign2.png "Reasignación de un registro a mí o a un equipo")
  
   Si selecciona **Usuario o equipo**, escriba el nombre del usuario o del equipo en el cuadro **Buscar registros**. Si necesita crear un registro, seleccione **+ Nuevo**.
  
5. Cuando termine, seleccione **Asignar**.

## <a name="use-advanced-find-to-reassign-records"></a>Uso de la búsqueda avanzada para reasignar registros

Use la búsqueda avanzada para encontrar registros y reasignarlos a otra persona. Para obtener más información sobre la búsqueda avanzada, vea [Crear, editar o guardar búsquedas avanzadas](advanced-find.md).


1. En la barra de comandos, seleccione **Búsqueda avanzada**.

   > [!div class="mx-imgBorder"]
   > ![Búsqueda avanzada](media/assign3.png "Búsqueda avanzada")
   
2. En la lista de registros, seleccione los registros que quiera reasignar y, luego, seleccione la opción Asignar.

   > [!div class="mx-imgBorder"]
   > ![Reasignación de un registro mediante la búsqueda avanzada](media/assign4.png "Reasignación de un registro mediante la búsqueda avanzada")
   
 
 ## <a name="reassign-all-records-for-admins"></a>Reasignación de todos los registros (administradores)
 
 Un administrador puede reasignar todos los registros de un usuario desde el área Configuración del administrador.
 
 1. Vaya a **Configuración** > **Seguridad**.
 2. Seleccione **Usuarios** y seleccione un nombre de usuario para abrir su perfil.
 3. En la barra de comandos, seleccione **REASIGNAR REGISTROS**.
 
   > [!div class="mx-imgBorder"]
   > ![Reasignación de todos los registros](media/assign5.png "Reasignación de todos los registros")
   
 4. En el cuadro de diálogo **Reasignar registros**, elija cómo quiere reasignar todos los registros y, luego, seleccione **Aceptar**.
 
  > [!NOTE]
   > La opción **Reasignar registros** reasignará todos los registros, sea cual sea su estado. Los registros inactivos y activos se reasignarán al otro usuario o equipo. Esto también hará que se desactiven todos los procesos activados (reglas de negocio y flujos de trabajo incluidos) cuando el registro se reasigne a otro usuario o equipo. El nuevo propietario deberá activar los procesos que deban usarse.
 
   > [!div class="mx-imgBorder"]
   > ![Reasignación de todos los registros a un usuario o un equipo](media/assign6.png "Reasignación de todos los registros a un usuario o un equipo")
 

