---
title: Creación de una solución | Microsoft Docs
description: Información sobre cómo crear una solución
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: e21a4876-08b4-417a-a644-c577a27c5cf1
caps.latest.revision: 12
ms.author: matp
manager: kvivek
ms.openlocfilehash: 26ecc9b2f83375ba10e6b32dfc12d6cc37342cf4
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712250"
---
# <a name="create-a-solution"></a>Crear una solución

Debido a que la solución predeterminada contiene todos los componentes de las soluciones, podría ser más fácil solo ubicar los componentes de la solución que se personalizaron si se crea una solución independiente en la que hacer todas las personalizaciones. Esto también facilita la exportación de una copia de seguridad de la solución como un archivo más pequeño. Si decide hacer esto, siempre debe recordar que tiene que agregar cualquiera de los componentes de la solución que edita a esta solución. Al crear nuevos componentes de solución, siempre debe crearlos en el contexto de esta solución. De este modo, el prefijo de personalización del editor de soluciones se aplicará de manera coherente. Después de crear componentes de solución en la solución o de agregar componentes de solución existentes a dicha solución, también puede editarlos en la solución predeterminada, si así lo desea.  
  
 Para más información sobre los conceptos de las soluciones, consulte el artículo sobre cómo [trabajar con soluciones](solutions-overview.md).  
  
1.  Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**. 
  
2.  Elija **Nuevo** y complete los campos necesarios para la solución.  
  
    |Campo|Descripción|  
    |-----------|-----------------|  
    |**Nombre para mostrar**|El nombre que se muestra en la lista de soluciones. Puede cambiarlo más adelante.|  
    |**Nombre**|El nombre único de la solución. Se genera a partir del valor que escribió en el campo Nombre para mostrar. Puede editarlo antes de guardar la solución, pero no podrá hacerlo después de guardarla.|  
    |**Editor**|Puede seleccionar el editor predeterminado o crear uno nuevo. A menos que planee distribuir la solución, solo debería usar el editor predeterminado para la organización.|  
    |**Versión**|Escriba un número para la versión de la solución. Este valor solo es importante si exporta la solución. El número de versión se incluirá en el nombre del archivo cuando exporte la solución.|  
  
3.  Elija **Guardar**.  
  
 Una vez que guarda la solución, es posible que quiera agregar información a campos que no son obligatorios. Estos pasos son opcionales. Use el campo **Descripción** para describir la solución y elija un recurso web HTML como **Página de configuración** para la solución. Por lo general, la página de configuración la usan los ISV que distribuyen las soluciones. Cuando se establece, aparece un nodo **Configuración** nuevo debajo del nodo **Información** para mostrar este recurso web. Los desarrolladores usarán esta página para incluir instrucciones o controles que le permitirán establecer los datos de configuración o iniciar la solución.  
  
<a name="BKMK_AddSolutionComponents"></a>   

## <a name="add-solution-components"></a>Incorporación de componentes de solución  
 Después de crear la solución, esta no contendrá ningún componente de solución. Puede crear componentes de solución nuevos o usar el botón **Agregar existente** en el menú de lista para agregar cualquier componente de solución de la solución predeterminada.  
  
 Cuando lo haga, es posible que vea un cuadro de diálogo que indique que **Faltan componentes necesarios**.  
   
 ![Cuadro de diálogo para agregar componentes necesarios](media/crm-itpro-cust-addrequiredcomponents.PNG "Cuadro de diálogo para agregar componentes necesarios")  
  
 Este cuadro de diálogo le envía una alerta respecto de que el componente de la solución tiene dependencias de otros componentes de la solución. Si selecciona **No, do not include required components** (No, no incluir componentes necesarios), es posible que la solución no se importe a otra organización si no existen todos los componentes necesarios. Si la importación se realiza correctamente, es posible que el comportamiento en la otra solución no sea idéntico a la organización original, porque los componentes están configurados de una manera distinta a los componentes de la solución de origen.  
  
 Por lo general, es más seguro incluir los componentes necesarios si va a exportar la solución a otra organización. Si no agrega estos componentes cuando agrega un componente de solución individual, puede volver más tarde, seleccionar el componente de solución que agregó y elegir **Add Required Components** (Agregar componentes necesarios) en el menú.  
  
 Si no va a exportar la solución o si solo quiere exportarla como una solución no administrada e importarla de vuelta a la misma organización, no es necesario incluir los componentes necesarios. Si alguna vez exporta la solución, verá otra advertencia que le indicará que faltan algunos componentes necesarios. Si solo va a importar esta solución de vuelta a la misma organización, no hay problemas con que pase por alto esta advertencia. Los pasos para editar el menú de navegación o la cinta de opciones de una aplicación sin usar una herramienta de edición de terceros esperan que exporte la solución de vuelta a la misma organización.  

> [!IMPORTANT]
>  Si tiene previsto incluir citas en las soluciones, le recomendamos que no incluya solo citas ni solo citas periódicas en soluciones independientes. Si instala y desinstala soluciones independientes con distintos tipos de citas, se encontrará con un error de SQL Server y deberá volver a crear las citas. 
