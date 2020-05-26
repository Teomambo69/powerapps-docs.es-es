---
title: Crear o editar paneles de aplicaciones controladas por modelos | MicrosoftDocs
ms.custom: ''
ms.date: 04/08/2020
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
ms.openlocfilehash: 9a9e49a14268c3ee82a8c5fb541473903bbf5f11
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285823"
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>Crear o editar paneles de aplicaciones controladas por modelos

Existen dos tipos de paneles: paneles de usuario y paneles del sistema. Un usuario de la aplicación puede crear un panel visible solo para él en las áreas de la aplicación para las que tenga privilegio. Un administrador o personalizador crea o personaliza paneles del sistema que, cuando se publican, están visibles para todos los usuarios de la aplicación. Un usuario puede optar por establecer su panel de usuario como predeterminado y reemplazar el panel del sistema.   

Los paneles pueden ser estándar o interactivos. Los paneles estándar permiten agregar uno o más componentes no relacionados, como gráficos o listas. Los paneles interactivos brindan la capacidad de que los usuarios actúen sobre un registro particular directamente desde el panel. Este tema se centra en los paneles de sistema estándar. Para obtener información sobre los paneles interactivos, vea [Configurar paneles de experiencia interactiva de aplicaciones basadas en modelo](configure-interactive-experience-dashboards.md).
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-standard-dashboard"></a>Crear un nuevo panel estándar  
  
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
  
2. Seleccione **Soluciones** y luego abra la solución que desee.

3. En la barra de herramientas, seleccione **Nuevo**, seleccione **Panel** y, a continuación, elija un diseño de 2, 3 o 4 columnas.  
  
4.  En la página **Panel: Nuevo** escriba un nombre para el panel.  
  
5.  Seleccione una de las áreas del componente y seleccione el icono para un gráfico o una lista.  
  
     Puede tener hasta seis componentes en el panel.  
  
6.  Por ejemplo, para agregar un gráfico, seleccione el icono del gráfico en el icono del lienzo del panel donde desea que aparezca el gráfico. A continuación, en el cuadro de diálogo **Agregar componente**, seleccione valores para **Tipo de registro**, **Ver** y **Gráfico** y, a continuación seleccione **Agregar** para agregar el gráfico al panel. Para obtener información sobre cómo crear un gráfico, consulte [Crear un gráfico de sistema para una aplicación basada en modelo](create-edit-system-chart.md).
  
7.  Cuando haya terminado de agregar componentes al panel, seleccione **Guardar** y luego **Cerrar**.  

8. En la barra de herramientas de soluciones, seleccione **Publicar**. 
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>Editar un panel existente  
  
1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2. Seleccione **Soluciones** y luego abra la solución que desee.  

3. En la lista de componentes de soluciones, abra el panel, seleccione una de +las áreas del componente y, a continuación, en la barra de herramientas, seleccione **Editar componente**.  
  
4.  En el cuadro de diálogo **Establecer propiedades**, puede realizar cambios en un gráfico o lista, como cambiar la entidad o la vista predeterminada, agregar un seleccionador de gráfico o hacer que el panel esté disponible en las aplicaciones móviles. Cuando termine, elija **Aceptar**.  
  
     Para obtener más información sobre cómo establecer propiedades de los componentes del panel, consulte [Establecer las propiedades para un gráfico o una lista incluidos en un panel](set-properties-chart-list-included-dashboard.md).  
  
5.  Cuando haya completado sus cambios en la barra de herramientas, seleccione **Guardar** y luego **Cerrar**. 

6. En la barra de herramientas de soluciones, seleccione **Publicar**.  
  
Tareas adicionales de paneles del sistema que puede realizar son:  
  
-   Quitar una lista o un gráfico de un panel  

-   Agregar una lista o un gráfico a un panel  

-   Establecer el panel predeterminado  

-   Usar roles de seguridad para crear un panel visible solo para determinados roles    

## <a name="next-steps"></a>Pasos siguientes  
[Establecimiento de propiedades para un gráfico o una lista incluidos en un panel](set-properties-chart-list-included-dashboard.md)
