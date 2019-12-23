---
title: Crear o editar paneles de aplicaciones controladas por modelos | MicrosoftDocs
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 641885d2-4a08-41b8-b914-d9a244e4d5b1
caps.latest.revision: 10
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 81943d73ac8c6189e62d25af4ff38b993182c269
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875506"
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>Crear o editar paneles de aplicaciones controladas por modelos

Existen dos tipos de paneles: paneles de usuario y paneles del sistema. Un usuario de la aplicación puede crear un panel visible solo para él en las áreas de la aplicación para las que tenga privilegio. Un administrador o personalizador crea o personaliza paneles del sistema que, cuando se publican, están visibles para todos los usuarios de la aplicación. Un usuario puede optar por establecer su panel de usuario como predeterminado y reemplazar el panel del sistema. Este tema se centra en los paneles de sistema.  
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-dashboard"></a>Crea un panel  
  
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    > [!IMPORTANT]
    > “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment).   
  
2. Expanda **Datos**, seleccione **Entidades**, seleccione la entidad en la que desee que se base el panel, como la entidad **Cuenta** y, a continuación, seleccione la pestaña **Paneles**. 

3. En la barra de herramientas seleccione **Agregar un panel** y, a continuación, elija un diseño de 2, 3 o 4 columnas.  
  
4.  En el cuadro de diálogo **Panel: Nuevo** escriba un nombre para el panel.  
  
5.  Seleccione una de las áreas del componente y seleccione el icono para un gráfico o una lista.  
  
     Puede tener hasta seis componentes en el panel.  
  
6.  Por ejemplo, si agrega un gráfico, en el cuadro de diálogo **Agregar componente**, seleccione valores para **Tipo de registro**, **Ver** y **Gráfico** y, a continuación seleccione **Agregar** para agregar el gráfico al panel.  
  
7.  Cuando haya terminado de agregar componentes al panel, seleccione **Guardar** y luego **Publicar**.  
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>Editar un panel existente  
  
1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    > [!IMPORTANT]
    > “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment).    
  
2. Expanda **Datos**, seleccione **Entidades**, seleccione la entidad en la que desee que se base el panel, como la entidad **Cuenta** y, a continuación, seleccione la pestaña **Paneles**.  

3. Abra un panel, seleccione una de las áreas del componente y, a continuación, en la barra de herramientas, seleccione **Editar componente**.  
  
4.  En el cuadro de diálogo **Establecer propiedades**, puede realizar cambios en un gráfico o lista, como cambiar la entidad o la vista predeterminada, agregar un seleccionador de gráfico o hacer que el panel esté disponible en las aplicaciones móviles. Cuando esté listo, seleccione **Establecer**.  
  
     Para obtener más información sobre cómo establecer propiedades de los componentes del panel, consulte [Establecer las propiedades para un gráfico o una lista incluidos en un panel](set-properties-chart-list-included-dashboard.md).  
  
4.  Cuando haya completado sus cambios asegúrese de guardarlos y después publíquelos.  
  
Tareas adicionales de paneles del sistema que puede realizar son:  
  
-   Quitar una lista o un gráfico de un panel  

-   Agregar una lista o un gráfico a un panel  

-   Establecer el panel predeterminado  

-   Usar roles de seguridad para crear un panel visible solo para determinados roles    

## <a name="next-steps"></a>Pasos siguientes  
[Establecimiento de propiedades para un gráfico o una lista incluidos en un panel](set-properties-chart-list-included-dashboard.md)
