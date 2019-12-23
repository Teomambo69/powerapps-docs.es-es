---
title: Crear cuadrículas (listas) editables de aplicaciones controladas por modelos mediante el control personalizado Cuadrícula editable con Power Apps | MicrosoftDocs
description: Obtenga información sobre cómo usar el control personalizado de cuadrícula editable
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: cefbc0c2-769b-4230-ab5a-b28a84630a42
caps.latest.revision: 8
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 866c058ad873fa278ee0bb8bf026983ed0201df7
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868003"
---
# <a name="make-model-driven-app-grids-lists-editable-using-the-editable-grid-custom-control"></a>Crear cuadrículas (listas) editables de aplicaciones controladas por modelos mediante el control personalizado Cuadrícula editable

En versiones anteriores de Dynamics CRM, los usuarios no podían introducir datos directamente en cuadrículas (a veces denominadas las listas) o subcuadrículas de formularios. Tenían que seleccionar en el registro en la cuadrícula para abrir un formulario, modificar los datos, y luego guardarlos, lo que requería varios pasos. Con las cuadrículas editables, los usuarios pueden editar en línea con gran detalle directamente desde cuadrículas y subcuadrículas tanto si usan una aplicación web, tableta o teléfono.  
  
 ![Ejemplos de cuadrícula editable](media/editable-grid-examples.png "Ejemplos de cuadrícula editable")  
  
 Cuando se habilitan cuadrículas editables a través del control personalizado Cuadrículas editables, los usuarios pueden editar la mayoría de los tipos de campos, incluidos campos de búsqueda básicos y conjuntos de opciones.  

**Las cuadrículas editables admiten:**
  
-   Edición en línea de registros en el nivel de entidad o subcuadrícula (incluye entidades personalizadas)  
  
-   Vistas del sistema y vistas personales  
  
-   Clientes web y móviles  
  
-   Navegación con un teclado o un mouse  
  
-   Agrupación y orden (puede agrupar/ordenar por cualquier columna de la vista actual)  
  
-   Filtrado  
  
-   Mover y cambiar el tamaño de columnas  
  
-   Paginación  
  
-   Guardar cambios de sesión a otra para agrupar, ordenar, filtrar, paginar y mover y cambiar de tamaño columnas  
  
-   Configuración de búsqueda  
  
-   Campos calculados y campos consolidados  
  
-   Reglas de negocio (campo Mostrar mensaje de error, Establecer valor de campo, Establecer Requerido por la empresa, Establece valor predeterminado, Bloquear o desbloquear)  
  
-   Eventos JavaScript  
  
-   Habilitar o deshabilitar celdas en función del rol de seguridad  
  
-   Los usuarios pueden seguir usando búsqueda y gráficos, y pueden acceder a la barra de acción como cuadrículas de solo lectura  
  
## <a name="make-main-grids-editable"></a>Hacer editables las cuadrículas principales  
  
1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2.  En la lista **Entidades**, abra la entidad adecuada, seleccione la pestaña **Controles**, y después seleccione **Agregar control**.  
  
     ![Agregar control personalizado Cuadrículas editables](media/add-editable-grids-custom-control.png "Agregar control personalizado Cuadrículas editables")  
  
3.  En el cuadro de diálogo **Agregar control**, seleccione **Cuadrícula editable**, y después seleccione **Agregar**.  
  
4.  En la fila **Cuadrícula editable** que se agrega, seleccione los factores de forma que desea aplicar a la cuadrícula. Esto convierte al control de cuadrícula editable en el control predeterminado para el factor de forma seleccionado.  
  
     ![Fila de cuadrícula editable con selección de factor de forma](media/editable-grid-row-wit-factor-selection.png "Fila de cuadrícula editable con selección de factor de forma")    

   > [!NOTE]
   >  En tiempo de ejecución, los usuarios cambiar entre cuadrículas editables y cuadrículas de solo lectura.  
      
5.  Para agregar una búsqueda, en el grupo de opciones **Cuadrícula editable**, seleccione **Agregar búsqueda** y en el cuadro de diálogo **Configurar propiedad “Agregar búsqueda”**:  
  
    1.  En la lista **Vistas disponibles**, seleccione la vista a la que agregar la búsqueda (por ejemplo, seleccione **Mis cuentas activas**).  
  
    2.  En la lista **Columnas disponibles**, seleccione la columna de búsqueda para agregar (por ejemplo, seleccione **Contacto principal**).  
  
    3.  En la lista **Vista predeterminada**, seleccione el origen de datos del campo de búsqueda.  
  
    4.  Si desea limitar los registros mostrados, seleccione la casilla **Mostrar solo los registros donde**, continuación, seleccione los criterios en la lista y, por último, seleccione **Aceptar**.  
  
         ![Agregar búsqueda en control Cuadrícula editable](media/add-lookup-in-editable-grid-control.png "Agregar búsqueda en control Cuadrícula editable")  
     
6.  Si tiene una cuadrícula anidada, seleccione el botón de lápiz para **Vista de cuadrícula anidada** y seleccione la entidad y la vista de cuadrícula anidadas. Para el **Id. principal de cuadrícula anidada** seleccione la relación de las entidades. Por ejemplo, el campo ParentAccountID conecta las entidades **Cuenta** y **Contacto**.  
  
    > [!NOTE]
    >  Las cuadrículas anidadas solo están disponibles para teléfonos y tabletas, no para la web.  
  
7.  Si no desea permitir que el usuario agrupe datos por cualquier columna de la vista (conviene ahorrar espacio, por ejemplo), en la fila **Agrupar por columna**, seleccione el botón de lápiz y, en el cuadro de diálogo **Configura propiedad “Agrupar por columna”**, seleccione **Deshabilitado** y, a continuación, seleccione **Aceptar**.  
  
    > [!TIP]
    >  Esto es sobre todo útil para subcuadrículas de formularios.  
  
8.  Si desea agregar eventos de JavaScript, seleccione la pestaña **Eventos** y luego seleccione las entidades, los campos y los eventos adecuados. Más información: [Documentación para desarrolladores: Usar cuadrículas editables](/dynamics365/customer-engagement/developer/customize-dev/use-editable-grids-dynamics-365.md)  
  
     ![Agregar eventos en control Cuadrícula editable](media/add-events-in-editable-grid-control.png "Agregar eventos en control Cuadrícula editable")  
  
9. Para guardar el trabajo, seleccione **Guardar** en la barra de acciones.  
  
10. Cuando esté listo para realizar los cambios disponibles para su equipo, seleccione **Publicar** en la barra de acciones.  
  
11. Para comprobar los cambios, vaya a la vista que especificó en el paso 5, y realice algunos cambios de edición en línea.  
  
## <a name="make-a-sub-grid-on-a-form-editable"></a>Hacer editable una subcuadrícula en un formulario

> [!NOTE] 
> - Para guardar un cambio de cuadrícula editable en una subcuadrícula, el usuario debe guardarlo explícitamente antes de salir del formulario.
> - Si usa formularios antiguos (versiones anteriores a Dynamics CRM 2016) y habilita una cuadrícula editable en una subcuadrícula, la subcuadrícula editable no se representará. Los administradores del sistema pueden desactivar los formularios antiguos en la configuración del sistema, si es necesario.
  
1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2.  Abra el formulario que contiene la subcuadrícula.  
  
3.  Seleccione el control adecuado, y después seleccione **Cambiar propiedades** en la cinta de opciones.  
  
4.  En el cuadro de diálogo **Establecer propiedades**, seleccione **Controles**, seleccione **Agregar control**, y siga los mismos pasos indicados anteriormente.  
  
## <a name="supported-standard-entities"></a>Entidades estándar admitidas  
  
||||  
|-|-|-|  
|**Web/tableta/teléfono**|**Solo tableta/teléfono**|**Web solo**|  
|Cuenta<br /><br /> Cita<br /><br /> Recurso que se puede reservar<br /><br /> Reserva de recursos que se pueden reservar<br /><br /> Encabezado de reserva de recursos que se pueden reservar<br /><br /> Categoría de recurso que se puede reservar<br /><br /> Asociación de categoría de recurso que se puede reservar<br /><br /> Característica del recurso que se puede reservar<br /><br /> Grupo de recursos que se pueden reservar<br /><br /> Estado de reserva<br /><br /> Caso<br /><br /> Categoría<br /><br /> Característica<br /><br /> Competidor<br /><br /> Contacto<br /><br /> Correo electrónico<br /><br /> Derecho<br /><br /> Comentarios<br /><br /> Factura<br /><br /> Artículo de conocimientos<br /><br /> Vistas del artículo de conocimiento<br /><br /> Registro de Knowledge Base<br /><br /> Cliente potencial<br /><br /> Oportunidad<br /><br /> Pedido<br /><br /> Llamada de teléfono<br /><br /> Lista de precios<br /><br /> Producto<br /><br /> Cola<br /><br /> Oferta<br /><br /> Modelo de clasificación<br /><br /> Valor de la clasificación<br /><br /> Instancia de KPI de SLA<br /><br /> Actividad social<br /><br /> Perfil social<br /><br /> Error de sincronización<br /><br /> Tarea<br /><br /> Equipo<br /><br /> Usuario|Actividad<br /><br /> Datos adjuntos<br /><br /> Elemento de la regla de perfil de acceso al canal<br /><br /> Dirección de competidor<br /><br /> Conexión<br /><br /> Rol de conexión<br /><br /> Firma de correo electrónico<br /><br /> Plantilla de correo electrónico<br /><br /> Proceso expirado<br /><br /> Producto de la factura<br /><br /> Incidente de artículo de conocimientos<br /><br /> Cliente potencial a ventas de la oportunidad<br /><br /> Proceso<br /><br /> Buzón<br /><br /> Proceso nuevo<br /><br /> Nota<br /><br /> Producto de oportunidad<br /><br /> Proceso de ventas de la oportunidad<br /><br /> Producto del pedido<br /><br /> Organización<br /><br /> Proceso de teléfono a caso<br /><br /> Elemento de lista de precios<br /><br /> Elemento de cola<br /><br /> Producto de oferta<br /><br /> Documento de SharePoint<br /><br /> Proceso de traducción|Campaña<br /><br /> Actividad de la campaña<br /><br /> Respuesta de campaña<br /><br /> Perfil de acceso al canal<br /><br /> Regla de perfil de acceso al canal<br /><br /> Contrato<br /><br /> Plantilla de derecho<br /><br /> Parte externa<br /><br /> Fax<br /><br /> Carta<br /><br /> Lista de marketing<br /><br /> Posición<br /><br /> Campaña exprés<br /><br /> Cita periódica<br /><br /> Documentación de ventas<br /><br /> SLA|  
 
##  <a name="data-types-that-arent-editable-in-an-editable-grid"></a>Tipos de datos que no se pueden editar en una cuadrícula editable
Los siguientes tipos de datos no se pueden editar en cuadrículas editables: campos de búsqueda de clientes y Partylist; campos compuestos (dirección); campos de estado; campos relacionados con entidades de búsqueda (por ejemplo, la entidad de cuenta incluye una búsqueda de contacto, donde el campo de contacto se puede editar pero el campo EmailAdress (contacto) no se puede editar).  
 
## <a name="next-steps"></a>Pasos siguientes  
 [Usar métodos abreviados de teclado en cuadrículas editables](https://docs.microsoft.com/dynamics365/customer-engagement/basics/keyboard-shortcuts#editable-grids-views)

