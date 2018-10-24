---
title: Guía detallada sobre el uso del proveedor de datos de OData v4 en entidades virtuales con Common Data Service para aplicaciones | Microsoft Docs
description: Obtenga información sobre cómo usar el proveedor de datos de OData v4 con una entidad virtual.
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: ebdd8f80aad2d353d017626b7c403da93803c19b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699686"
---
# <a name="virtual-entity-walkthrough-using-the-odata-v4-data-provider"></a>Guía detallada sobre el uso del proveedor de datos de OData v4 en entidades virtuales

Imagine que desea acceder a información del vale desde un origen de datos externo dentro de la aplicación basada en modelos o del área de servicio de Dynamics 365 for Customer Engagement. En esta sencilla guía detallada, podrá modelar una entidad virtual con campos asignados al esquema externo que recupera datos de vale en tiempo de ejecución de un servicio web de OData.

## <a name="data-source-details"></a>Detalles del origen de datos

Dado que el origen de datos utilizado para esta guía detallada tiene un servicio web de OData v4, podemos usar el proveedor de datos de OData v4 incluido en su entorno.

Dirección URL del servicio web: `http://contosowebservice.azurewebsites.net/odata/` 

> [!IMPORTANT]
> La dirección URL del servicio web utilizada para esta guía detallada no es un servicio web en funcionamiento.

En esta guía detallada, se necesita una entidad virtual única que contiene los tres campos siguientes.

|Nombre del campo externo |Tipo de datos externos |Tipo de datos de la entidad virtual |Propósito |
|---------|---------|---------|---------|
|TicketID |`Edm.Guid` |Clave principal |Clave principal de la entidad |
|Título  |`Edm.String` |Una línea de texto |Título del vale |
|Gravedad |`Edm.Int32`| Número entero |Valor numérico de 0 a 4, que indica la gravedad del vale |

Los metadatos de OData de la entidad Ticket del origen de datos externo:

```xml
<EntityType Name="Ticket">
  <Key>
    <PropertyRef Name="TicketID" />
  </Key>
  <Property Name="TicketID" Nullable="false" Type="Edm.Guid" />
  <Property Name="Title" Type="Edm.String" />
  <Property Name="Severity" Nullable="false" Type="Edm.Int32" />
</EntityType>
```

## <a name="create-the-data-source"></a>Creación del origen de datos

Cree el origen de datos para el proveedor de datos de OData v4 que utiliza el servicio web de ejemplo de OASIS Open Data Protocol (OData).

1. Vaya a **Configuración** > **Administración** > **Orígenes de datos de entidades virtuales**.
1. Seleccione **NUEVO**, **Proveedor de datos de OData v4** y luego **Aceptar**.
1. Escriba o seleccione la siguiente información.

    |Campo|Valor|
    |--|--|
    |**Nombre**|Origen de datos de ejemplo Contoso|
    |**URL**|`http://contosowebservice.azurewebsites.net/odata` |
    |**Tiempo de expiración**|30|
    |**Devolver recuento alineado**|True|

Deje los demás campos tal cual y seleccione **GUARDAR Y CERRAR**.

> [!TIP]
> Si usa su propio servicio web, compruebe que la dirección URL es válida; para ello, péguela en su explorador web. 

## <a name="open-solution-explorer"></a>Abrir el Explorador de soluciones

Parte del nombre de cualquier entidad personalizada que se crea es el prefijo de personalización. Esto se establece en función del editor de soluciones de la solución en la que está trabajando. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada, donde el prefijo de personalización es lo que necesita para esta entidad. Más información: [Cambio del prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="create-the-virtual-entity"></a>Creación de la entidad virtual

1. En el panel de navegación de la izquierda del Explorador de soluciones, seleccione **Entidades** y, después, seleccione **Nuevo** en el panel principal.
2. En el formulario **Entidad: nueva**, seleccione la opción **Entidad virtual** y luego escriba la siguiente información: 

    |Campo|Valor|
    |--|--|
    |**Origen de datos**|Origen de datos de ejemplo Contoso|
    |**Nombre para mostrar**|Vale|
    |**Nombre en plural**|Vales|
    |**Nombre**|new_ticket|
    |**Nombre externo**|Vale|
    |**Nombre de colección externa**|Vales|
    |**Notas (incluye los datos adjuntos)**|seleccionado|
    |**Actividades**|seleccionado|

1. Junto a **Áreas que muestran esta entidad**, seleccione **Servicio** y después seleccione **Guardar** (pero no cierre el formulario de entidad).
    ![Definición de la entidad de vale](media/ticket-entity.png)

## <a name="create-the-fields-for-the-virtual-entity"></a>Creación de los campos de la entidad virtual

En el panel de navegación izquierdo de la página **Entidad: vale**, seleccione **Campos**. Como parte de esta guía detallada, editará dos campos existentes y agregará un tercer campo.

> [!IMPORTANT]
> Los nombres externos distinguen mayúsculas de minúsculas. Haga referencia a los metadatos del servicio web para asegurarse de que use el nombre correcto.
> Un valor false que admite un valor NULL indica que el atributo es necesario. Tenga en cuenta que los campos de clave principal siempre son necesarios para el sistema.

1. Abra el campo **new_ticketid** y cambie el atributo siguiente con el valor indicado aquí: **Nombre externo**: TicketID ![campo TicketID](media/ticketid-field.png)
1. Haga clic en **Guardar y cerrar**.
1. Abra el campo **new_name** y cambie los siguientes atributos para que tengan los valores indicados aquí:
    - **Nombre para mostrar**: título
    - **Nombre externo**: título ![Campo Título](media/title-field.png)
1. Haga clic en **Guardar y cerrar**.
1. Seleccione **Nuevo** y, en la página **Campo: New for Ticket**, escriba la siguiente información:

    |Campo|Valor|
    |--|--|
    |**Nombre para mostrar**|Gravedad|
    |**Nombre**|new_severity|
    |**Nombre externo**|Gravedad|
    |**Requisito de campo**|Requerido por la empresa|
    |**Tipo de datos**|Número entero|
    |**Valor mínimo**|0|
    |**Valor máximo**|4|

  ![Campo de gravedad](media/severity-field.png)
1. Haga clic en **Guardar y cerrar**.

## <a name="add-the-fields-to-the-main-form"></a>Adición de campos al formulario principal

1. En la ventana de la entidad Ticket, seleccione **Formularios**.
1. Abra el formulario principal, arrastre y coloque el campo **Gravedad** arrastrándolo desde el panel derecho hasta el formulario en la sección **General** del campo **Título**. 
    ![Campo de gravedad agregado al formulario principal](media/drop-severity-field.png)
1. En la ventana de la entidad Ticket, seleccione **Guardar y cerrar**.

## <a name="configure-the-default-view"></a>Configuración de la vista predeterminada

1. En el panel izquierdo del Explorador de soluciones, en la **entidad Ticket**, seleccione **Vistas**.
1. Abra la vista **All Tickets**.
1. En el panel **tareas comunes**, seleccione **Agregar columnas**.
    ![Agregar columnas para la vista](media/addcolumns.png)
1. Seleccione **Gravedad** y luego **Aceptar**.
1. En la ventana **Vista: All Tickets**, seleccione **Guardar y cerrar**.
1. En la ventana del Explorador de soluciones, seleccione **Publicar todas las personalizaciones**.
    ![Publicar todas las personalizaciones](media/publishall.png)
1. Una vez publicadas todas las personalizaciones, cierre la ventana del Explorador de soluciones.

## <a name="view-the-virtual-entity-in-action-with-dynamics-365-customer-engagement"></a>Visualización de las entidades virtuales en acción con Dynamics 365 for Customer Engagement

1. Vaya a **Servicio** > **Extensiones** > **Vales**.
    
    ![Área de vale](media/ticket-area.png)

    Se abre la vista **All Tickets**. Tenga en cuenta que puede que deba actualizar su explorador para ver la entidad en el área **Servicio**.

    ![Vista All Tickets](media/all-tickets-view.png)
1. Abra un registro de **vale** para ver el formulario que incluye los campos **Título** y **Gravedad** del registro determinado.
    ![Registro de vale](media/ticket-record.png)

### <a name="see-also"></a>Vea también

[Configuración, requisitos y procedimientos recomendados del proveedor de datos de OData v4](virtual-entity-odata-provider-requirements.md)<br />
[Crear y editar entidades virtuales que contienen datos de un origen de datos externo](create-edit-virtual-entities.md)
