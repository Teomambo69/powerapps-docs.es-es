---
title: Tutorial de entidad virtual mediante el proveedor de datos en Common Data Service | MicrosoftDocs
description: Aprenda a usar el proveedor de datos de OData v4 con una entidad virtual
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: null
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="virtual-entity-walkthrough-using-the-odata-v4-data-provider"></a>Tutorial de entidad virtual mediante el proveedor de datos de OData v4

Imagine que quiere acceder a la información del vale desde un origen de datos externos en la aplicación basada en modelos. En este sencillo tutorial, modelará una entidad virtual con los campos asignados al esquema externo que recupera datos del vale en tiempo de ejecución de un servicio web de OData.

## <a name="data-source-details"></a>Detalles del origen de datos:

Puesto que el origen de datos que se utiliza para este tutorial tiene un servicio web de OData v4, podemos usar el proveedor de datos OData v4 que se incluye con su entorno.

Dirección URL del servicio web: `http://contosowebservice.azurewebsites.net/odata/` 

> [!IMPORTANT]
> La url del servicio web utilizado para este tutorial no es un servicio web operativo.

Para este tutorial, se necesita una única entidad virtual que contiene los tres campos siguientes.

|Nombre de campo externo |Tipo de datos externos |Tipo de datos de entidad virtual |Finalidad |
|---------|---------|---------|---------|
|TicketID |`Edm.Guid` |Clave principal |Clave principal de la entidad |
|Título  |`Edm.String` |Línea de texto única |Título del vale |
|Gravedad |`Edm.Int32`| Número entero |Valor numérico de 0 a 4 que indica la gravedad del vale |

Los metadatos de OData de la entidad de vale de origen de datos externos:

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

## <a name="create-the-data-source"></a>Cree el origen de datos

Crear el origen de datos para el proveedor de datos de OData v4 que utiliza el servicio web de ejemplo de OASIS Open Data Protocol (OData).

1. Acceda a **Configuración** > **Administración** > **Orígenes de datos de entidad virtual**.
1. Seleccione **NUEVO**, seleccione **Proveedor de datos de OData v4** y luego seleccione **Aceptar**.
1. Introduzca o seleccione la siguiente información.

    |Campo|Value|
    |--|--|
    |**Nombre**|Origen de datos de ejemplo de Contoso|
    |**Dirección URL**|`http://contosowebservice.azurewebsites.net/odata` |
    |**Tiempo de espera**|30|
    |**Devolver recuento alineado**|Verdadero|

Deje los demás campos tal cual y seleccione **GUARDAR Y CERRAR**.

> [!TIP]
> Cuando utilice su propio servicio web, compruebe que la dirección URL es válida pegándola en su explorador web. 

## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier entidad personalizada que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="create-the-virtual-entity"></a>Crear la entidad virtual

1. En el panel de navegación izquierdo del explorador de soluciones seleccione **Entidades** y seleccione **Nuevo** desde el panel principal.
2. En el formulario **Entidad: nueva**, seleccione la opción **Entidad virtual** y luego introduzca la siguiente información: 

    |Campo|Value|
    |--|--|
    |**Origen de datos**|Origen de datos de ejemplo de Contoso|
    |**Nombre para mostrar**|Vale|
    |**Nombre plural**|Vales|
    |**Nombre**|new_ticket|
    |**Nombre externo**|Vale|
    |**Nombre de colección externa**|Vales|
    |**Notas (incluye archivos adjuntos)**|seleccionado|
    |**Actividades**|seleccionado|

1. Al lado de **Áreas que muestran esta entidad**, seleccione **Servicio** y seleccione **Guardar** (pero no cierre el formulario de entidad).
    ![Definición de entidad del vale](media/ticket-entity.png)

## <a name="create-the-fields-for-the-virtual-entity"></a>Crear los campos de la entidad virtual

En el panel de navegación izquierdo de la página **Entidad: vale**, seleccione **Campos**. Como parte de este tutorial, editará los dos campos existentes y agregará un tercer campo.

> [!IMPORTANT]
> Los nombres externos distinguen mayúsculas de minúsculas. Consulte los metadatos del servicio web para asegurarse de que utiliza el nombre correcto.
> Un valor false que acepta NULL indica que es necesario el atributo. Tenga en cuenta que los campos de clave principal son siempre obligatorios para el sistema.

1. Abra el campo **new_ticketid** y cambie el siguiente atributo con el valor que se indica aquí: **Nombre externo**: TicketID  ![Campo TicketID](media/ticketid-field.png)
1. Seleccione **Guardar y cerrar**.
1. Abra el campo **new_name** y cambie los siguientes atributos que tenga los valores que se indican aquí:
    - **Nombre para mostrar**: Título
    - **Nombre externo**: Título ![Campo de título](media/title-field.png)
1. Seleccione **Guardar y cerrar**.
1. Seleccione **Nuevo** y en la página **Campo: nuevo para vale**, introduzca la siguiente información:

    |Campo|Value|
    |--|--|
    |**Nombre para mostrar**|Gravedad|
    |**Nombre**|new_severity|
    |**Nombre externo**|Gravedad|
    |**Requisito de campo**|Requerido por la empresa|
    |**Tipo de datos**|Número entero|
    |**Valor mínimo**|0|
    |**Valor máximo**|4|

  ![Campo Gravedad](media/severity-field.png)
1. Seleccione **Guardar y cerrar**.

## <a name="add-the-fields-to-the-main-form"></a>Agregar los campos al formulario principal

1. En la ventana de entidad Vale, seleccione **Formularios**.
1. Abra el formulario principal, arrastre y coloque el campo **Gravedad** del panel derecho del formulario de la sección **General** en el campo **Título**. 
    ![Campo Gravedad agregado al formulario principal](media/drop-severity-field.png)
1. En la ventana de entidad Vale, seleccione **Guardar y cerrar**.

## <a name="configure-the-default-view"></a>Configurar la vista predeterminada

1. En el panel izquierdo del explorador de soluciones, en la **Entidad Vale**, seleccione **Vistas**.
1. Abra la vista **Todos los vales**.
1. En el panel **Tareas comunes**, seleccione **Agregar columnas**.
    ![Agregar columnas para vista](media/addcolumns.png)
1. Seleccione **Gravedad** y, a continuación, **Aceptar**.
1. En la ventana **Ver: todos los vales**, seleccione **Guardar y cerrar**.
1. En la ventana del explorador de soluciones, seleccione **Publicar todas las personalizaciones**.
    ![Publicar todas las personalizaciones](media/publishall.png)
1. Una vez publicadas todas las personalizaciones, cierre la ventana del explorador de soluciones.

## <a name="view-the-virtual-entity-in-action-with-dynamics-365"></a>Vea la entidad virtual en acción con Dynamics 365

1. Vaya a **Servicio** > **Extensiones** > **Vales**.
    
    ![Área de vale](media/ticket-area.png)

    Se muestra la vista **Todos los vales**. Tenga en cuenta que puede que tenga que actualizar el explorador para ver la entidad del área **Servicio**.

    ![Vista Todos los vales](media/all-tickets-view.png)
1. Abra un registro **Vale** para ver el formulario que incluye los campos **Título** y **Gravedad** para el registro determinado.
    ![Registro de vale](media/ticket-record.png)

### <a name="see-also"></a>Vea también

[Configuración, requisitos y prácticas recomendadas del proveedor de datos de OData v4](virtual-entity-odata-provider-requirements.md)<br />
[Crear y editar entidades virtuales que contienen datos desde un origen de datos externo](create-edit-virtual-entities.md)
