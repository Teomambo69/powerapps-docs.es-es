---
title: Hacer cuadrículas (listas) de aplicaciones basadas en modelos editables mediante el control personalizado Cuadrícula editable con PowerApps | Microsoft Docs
description: Obtenga información sobre cómo usar el control personalizado Cuadrícula editable
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 704280dbed2177ba9a5467e2897980f78c31b050
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39711562"
---
# <a name="make-model-driven-app-grids-lists-editable-using-the-editable-grid-custom-control"></a>Hacer cuadrículas (listas) de aplicaciones basadas en modelos editables mediante el control personalizado Cuadrícula editable

En versiones anteriores de Dynamics CRM, los usuarios no podían escribir datos directamente en las cuadrículas (a veces llamadas listas) o subcuadrículas de los formularios. Tenían que seleccionar el registro en la cuadrícula para abrir un formulario, editar los datos y, a continuación, guardarlos. Esto requería varios pasos. Con las cuadrículas editables, los usuarios pueden realizar una edición enriquecida en línea directamente desde las cuadrículas y subcuadrículas, ya sea que estén utilizando una aplicación web, una tablet o un teléfono.  
  
 ![Ejemplos de cuadrícula editable](media/editable-grid-examples.png "Ejemplos de cuadrícula editable")  
  
 Al habilitarse las cuadrículas editables a través del control personalizado Cuadrículas editables, los usuarios pueden editar la mayoría de los tipos de campos, incluidos conjuntos de opciones y los campos de búsqueda básicos.  

**Compatibilidad con cuadrículas editables:**
  
-   La edición de registros en línea en el nivel de entidad o subcuadrícula (incluye las entidades personalizadas)  
  
-   Vistas del sistema y vistas personales  
  
-   Clientes web y móviles  
  
-   Navegación con un teclado o mouse  
  
-   Agrupación y ordenación (puede agrupar u ordenar por cualquier columna en la vista actual)  
  
-   Filtrado  
  
-   Mover y cambiar de tamaño las columnas  
  
-   Paginación  
  
-   Guardar los cambios de una sesión a otra para agrupar, ordenar, filtrar, paginar, mover y cambiar de tamaño las columnas  
  
-   Configuración de búsqueda  
  
-   Campos calculados y campos consolidados  
  
-   Reglas de negocio (mostrar mensaje de error, establecer valor de campo, establecer requerido por la empresa, establecer valor predeterminado, bloquear o desbloquear campo)  
  
-   Eventos de JavaScript  
  
-   Habilitación o deshabilitación de celdas en función del rol de seguridad  
  
-   Los usuarios pueden seguir usando la búsqueda y gráficos, y pueden tener acceso a la barra de acción como sucede con las cuadrículas de solo lectura  
  
## <a name="make-main-grids-editable"></a>Hacer que las cuadrículas principales sean editables  
  
1.  Abra el [Explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2.  En la lista **Entidades**, abra la entidad adecuada, seleccione la pestaña **Controles** y, a continuación, seleccione **Agregar control**.  
  
     ![Control personalizado Agregar cuadrículas editables](media/add-editable-grids-custom-control.png "Control personalizado Agregar cuadrículas editables")  
  
3.  En el cuadro de diálogo **Agregar control**, seleccione **Cuadrícula editable** y, a continuación, seleccione **Agregar**.  
  
4.  En la fila **Cuadrícula editable** que se agrega, seleccione los factores de forma a los que desea aplicar la cuadrícula. Esto hace que el control Cuadrícula editable sea el control predeterminado de los factores de forma seleccionados.  
  
     ![Fila Cuadrícula editable con selección de factores de forma](media/editable-grid-row-wit-factor-selection.png "Fila Cuadrícula editable con selección de factores de forma")    

   > [!NOTE]
   >  En tiempo de ejecución, los usuarios pueden alternar entre cuadrículas editables y cuadrículas de solo lectura.  
      
5.  Para agregar una búsqueda, en el grupo de opciones **Cuadrícula editable**, seleccione **Agregar búsqueda** y, a continuación, en el cuadro de diálogo **Configurar propiedad “Agregar búsqueda”**:  
  
    1.  En la lista **Vistas disponibles**, seleccione la vista a la que va a agregar la búsqueda (por ejemplo, seleccione **Mis cuentas activas**).  
  
    2.  En la lista **Columnas disponibles**, seleccione la columna Búsqueda que se va a agregar (por ejemplo, seleccione **Contacto principal**).  
  
    3.  En la lista **Vista predeterminada**, seleccione el origen de datos para el campo de búsqueda.  
  
    4.  Si desea limitar los registros mostrados, active la casilla **Mostrar solo los registros de ubicación** y, a continuación, seleccione sus criterios en la lista y, después, seleccione **Aceptar**.  
  
         ![Agregar búsqueda en control Cuadrícula editable](media/add-lookup-in-editable-grid-control.png "Agregar búsqueda en control Cuadrícula editable")  
     
6.  Si tiene una cuadrícula anidada, seleccione el botón de lápiz para **Vista de cuadrícula anidada** y, a continuación, seleccione la entidad y la vista para la cuadrícula anidada. En **Id. principal de cuadrícula anidada**, seleccione la relación para las entidades. Por ejemplo, el campo ParentAccountID conecta las entidades **Cuenta** y **Contacto**.  
  
    > [!NOTE]
    >  Las cuadrículas anidadas están solo disponibles para teléfonos y tablets, no para la Web.  
  
7.  Si no desea permitir al usuario agrupar datos por cualquier columna de la vista (desea ahorrar espacio, por ejemplo), en la fila **Agrupar por columna**, seleccione el botón de lápiz y, a continuación, en el cuadro de diálogo **Configurar propiedad “Agrupar por columna”**, seleccione **Deshabilitado** y, después, seleccione **Aceptar**.  
  
    > [!TIP]
    >  Esto resulta principalmente útil para las subcuadrículas de los formularios.  
  
8.  Si desea agregar eventos de JavaScript, seleccione la pestaña **Eventos** y, a continuación, seleccione las entidades, los campos y los eventos adecuados. Más información: [Documentación para desarrolladores: usar cuadrículas editables](/dynamics365/customer-engagement/developer/customize-dev/use-editable-grids-dynamics-365.md)  
  
     ![Agregar eventos en control Cuadrícula editable](media/add-events-in-editable-grid-control.png "Agregar eventos en control Cuadrícula editable")  
  
9. Para guardar el trabajo, seleccione **Guardar** en la barra de acción.  
  
10. Cuando esté listo para poner los cambios a disposición de su equipo, seleccione **Publicar** en la barra de acción.  
  
11. Para probar sus cambios, vaya a la vista que especificó en el paso 5 y, a continuación, realice algunos cambios de edición en línea.  
  
## <a name="make-a-sub-grid-on-a-form-editable"></a>Hacer que la subcuadrícula de un formulario sea editable

> [!NOTE] 
> - Para guardar un cambio aplicado a una cuadrícula editable dentro de una subcuadrícula, el usuario debe guardarlo de manera explícita antes de salir del formulario.
> - Si usa formularios heredados (versiones anteriores a Dynamics CRM 2016) y habilita una cuadrícula editable en una subcuadrícula, la subcuadrícula editable no se representará. Los administradores del sistema pueden desactivar los formularios heredados en la configuración del sistema, en caso necesario.
  
1.  Abra el [Explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2.  Abra el formulario que contiene la subcuadrícula.  
  
3.  Seleccione el control adecuado y, a continuación, seleccione **Cambiar propiedades** en la cinta.  
  
4.  En el cuadro de diálogo **Establecer propiedades**, seleccione **Controles**, seleccione **Agregar control** y, a continuación, siga los mismos pasos mencionados anteriormente.  
  
## <a name="supported-standard-entities"></a>Entidades estándar admitidas  
  
||||  
|-|-|-|  
|**Web/tablet/teléfono**|**Solo tablet/teléfono**|**Solo Web**|  
|Cuenta<br /><br /> Appointment<br /><br /> Recurso reservable<br /><br /> Reserva del recurso reservable<br /><br /> Encabezado de reserva del recurso reservable<br /><br /> Categoría del recurso reservable<br /><br /> Asociación de categoría del recurso reservable<br /><br /> Característica del recurso reservable<br /><br /> Grupo de recursos reservables<br /><br /> Estado de reserva<br /><br /> Case<br /><br /> Categoría<br /><br /> Característica<br /><br /> Competidor<br /><br /> Contacto<br /><br /> Correo electrónico<br /><br /> Derecho<br /><br /> Comentarios<br /><br /> Factura<br /><br /> Artículo de conocimientos<br /><br /> Vistas del artículo de conocimientos<br /><br /> Registro de Knowledge Base<br /><br /> Lead<br /><br /> Opportunity<br /><br /> Pedido<br /><br /> Llamada telefónica<br /><br /> Lista de precios<br /><br /> Product<br /><br /> Cola<br /><br /> Oferta<br /><br /> Modelo de clasificación<br /><br /> Valor de clasificación<br /><br /> Instancia de KPI de Acuerdo de Nivel de Servicio<br /><br /> Actividad social<br /><br /> Perfil social<br /><br /> Error de sincronización<br /><br /> Task<br /><br /> Team<br /><br /> Usuario|Actividad<br /><br /> Datos adjuntos<br /><br /> Elemento de la regla de perfil de acceso al canal<br /><br /> Dirección de competidor<br /><br /> Conexión<br /><br /> Rol de conexión<br /><br /> Firma de correo electrónico<br /><br /> Plantilla de correo electrónico<br /><br /> Proceso expirado<br /><br /> Producto de la factura<br /><br /> Incidente del artículo de conocimientos<br /><br /> Dar lugar a ventas de la oportunidad<br /><br /> Proceso<br /><br /> Mailbox<br /><br /> Nuevo proceso<br /><br /> Nota<br /><br /> Producto de oportunidad<br /><br /> Proceso de ventas de la oportunidad<br /><br /> Producto del pedido<br /><br /> Organización<br /><br /> Proceso de teléfono a caso<br /><br /> Elemento de lista de precios<br /><br /> Elemento de cola<br /><br /> Producto de la cotización<br /><br /> Documento de SharePoint<br /><br /> Proceso de traducción|Campaña<br /><br /> Actividad de campaña<br /><br /> Respuesta de campaña<br /><br /> Perfil de acceso al canal<br /><br /> Regla de perfil de acceso al canal<br /><br /> Contrato<br /><br /> Plantilla de derecho<br /><br /> Entidad externa<br /><br /> Fax<br /><br /> Letter<br /><br /> Lista de marketing<br /><br /> Posición<br /><br /> Campaña rápida<br /><br /> Cita periódica<br /><br /> Documentación de ventas<br /><br /> Contrato de nivel de servicio|  
 
##  <a name="data-types-that-arent-editable-in-an-editable-grid"></a>Tipos de datos que no son editables en una cuadrícula editable
Los siguientes tipos de datos no son editables en cuadrículas editables: campos de búsqueda de clientes y PartyList; campos compuestos (dirección); campos de estado; campos relacionados con entidades de búsqueda (por ejemplo, la entidad Cuenta incluye una búsqueda de contactos, donde el campo Contacto es editable, pero el campo EmailAddress(Contact) no lo es).  
 
## <a name="next-steps"></a>Pasos siguientes  
 [Usar métodos abreviados de teclado en cuadrículas editables](https://docs.microsoft.com/dynamics365/customer-engagement/basics/keyboard-shortcuts#editable-grids-views)

