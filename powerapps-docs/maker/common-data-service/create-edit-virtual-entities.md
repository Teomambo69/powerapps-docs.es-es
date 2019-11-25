---
title: Crear y editar de entidades virtuales con Common Data Service | MicrosoftDocs
description: Aprenda a crear entidades virtuales
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 44834893-0bf6-4a64-8f06-7583fe08330d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ecb0731d3cbba030f3b819e2b2744cb6a7b29c20
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706919"
---
# <a name="create-and-edit-virtual-entities-that-contain-data-from-an-external-data-source"></a>Crear y editar entidades virtuales que contienen datos desde un origen de datos externo

Una entidad virtual es una entidad personalizada de Common Data Service que tiene campos que contienen datos de un origen de datos externo. Las entidades virtuales aparecen en la aplicación para los usuarios como registros de entidad normales, pero contienen datos procedentes de una base de datos externa, como una base datos SQL de Azure. Los registros basados en las entidades virtuales están disponibles en todos los clientes, incluidos los clientes personalizados desarrollados con los servicios web de Common Data Service.  
  
En el pasado, para integrar los orígenes de datos dispares habría que crear un conector para mover datos o para desarrollar un complemento personalizado, en el lado del cliente o del servidor. Sin embargo, con las entidades virtuales, puede conectarse directamente con un origen de datos externo en el tiempo de ejecución de forma que los datos específicos del origen de datos externo estén disponibles en un entorno, sin necesidad de replicación de datos.  

Las entidades virtuales están formadas por tres componentes principales: un *proveedor de datos*, un registro de *origen de datos* y una *entidad virtual*. El proveedor de datos está formado por complementos y una entidad de origen de datos. El origen de datos es un registro de entidad en Common Data Service, que incluye los metadatos que representan el esquema de los parámetros de conexión. Cada entidad virtual hace referencia a un origen de datos en la definición de la entidad.  
  
Common Data Service incluye un proveedor de datos de OData que se puede usar para conectarse con un servicio web de OData v4 que tenga acceso a los datos externos. 
  
Como alternativa, los programadores pueden crear sus propios proveedores de datos. Los proveedores de datos están instalados en un entorno como solución. Más información: [Documentación para desarrolladores: Introducción a las entidades virtuales](../../developer/common-data-service/virtual-entities/get-started-ve.md)
  
 ![Diagrama de entidad virtual](media/virtual-entity-diagram.png "Diagrama de entidad virtual")  
  
<a name="benefits"></a> 
  
## <a name="virtual-entity-benefits"></a>Ventajas de la entidad virtual  
  
- Los desarrolladores pueden implementar complementos para leer los datos externos con los servicios web de Common Data Service y la herramienta de registro de complementos.  
- Los personalizadores del sistema usan el explorador de soluciones de PowerApps para configurar el registro del origen de datos y crear las entidades virtuales que se usan para tener acceso a datos externos sin necesidad de escribir código.  
- Los usuarios finales trabajan con los registros creados por la entidad virtual para ver los datos en campos, cuadrículas, resultados de la búsqueda e informes y paneles basados en Fetch XML.  
  
<a name="AddDataSource"></a> 
  
## <a name="add-a-data-source-to-use-for-virtual-entities"></a>Agregar un origen de datos para usarlo con las entidades virtuales 
 
 Los desarrolladores pueden crear un complemento personalizado a fin de usarlo como proveedor de datos para una entidad virtual.  Como alternativa, puede usar el proveedor de datos OData v4 que se proporciona. Más información: [Configuración, requisitos y prácticas recomendadas del proveedor de datos de OData v4](virtual-entity-odata-provider-requirements.md)  
  
1. Acceda a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Administración** > **Orígenes de datos de entidad virtual**.  
1. En la barra de herramientas de acciones, seleccione **Nuevo**.  
1. En el cuadro de diálogo **Seleccionar proveedor de datos**, seleccione uno de los siguientes orígenes de datos y, a continuación, seleccione **Aceptar**.
 
    |Proveedor de datos|Descripción|
    |--|--|
    |*Proveedor de datos personalizado*|Si ha importado un complemento del proveedor de datos, el proveedor de datos aparecerá aquí. Más información: [Documentación para desarrolladores: Introducción a las entidades virtuales](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)|
    |**Proveedor de datos OData v4**|Common Data Service incluye un proveedor de datos OData que puede usarse con los servicios web de OData v4. Más información: [Configuración, requisitos y prácticas recomendadas del proveedor de datos de OData v4](virtual-entity-odata-provider-requirements.md)|

  
### <a name="add-a-secured-field-to-a-data-source"></a>Agregar un campo protegido a un origen de datos

Puede crear los campos de un origen de datos igual que con cualquier otra entidad. Para los datos cifrados o confidenciales, habilite el atributo Secreto del origen de datos en el campo personalizado del origen de datos. Por ejemplo, para proteger un campo de que contiene una cadena de conexión de base de datos. 

> [!NOTE]
> El atributo Secreto del origen de datos solo está disponible con campos agregados a un formulario del origen de datos.

> [!div class="mx-imgBorder"] 
> ![Atributo Secreto del origen de datos](media/datasourcesecret.png)
  
<a name="createVirtualEntity"></a> 
  
## <a name="create-a-virtual-entity"></a>Crear entidad virtual
  
Puede crear una entidad virtual al igual que cualquier otra entidad en Common Data Service con la incorporación de algunos atributos adicionales descritos aquí. Las entidades virtuales deben crearse usando el explorador de soluciones.

> [!NOTE]
>  Aunque puede crear una entidad virtual seleccionando **Ninguno** como origen de datos, para adquirir datos una entidad virtual requiere un origen de datos. Más información [Agregar un origen de datos para usarlo con las entidades virtuales](#AddDataSource)

### <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier entidad virtual que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad virtual. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="create-a-virtual-entity"></a>Crear entidad virtual
  
1. En el explorador de soluciones, cree una nueva entidad. Para ello, seleccione **Entidades** en el panel de navegación izquierdo y, luego, seleccione **Nuevo**.  
2. En la pestaña **General** de **Definición de entidad**, seleccione **Entidad virtual** y, a continuación, en la lista desplegable **Origen de datos**, seleccione el origen de datos que desee.  

    > [!div class="mx-imgBorder"] 
    > ![Opción Entidad virtual en la definición de la entidad](media/virtual-entity-click-option.png)  
  
1. En la definición de entidad, rellene los siguientes campos obligatorios.
  
    |Campo|Descripción|
    |--|--|
    |**Nombre externo**|Especifique el nombre de la tabla del origen de datos externos al que se asigna esta entidad.|
    |**Nombre de colección externa**|Especifique el nombre plural de la tabla del origen de datos externos al que se asigna esta entidad.|
      
    Aquí mostramos un ejemplo de una entidad virtual denominada *Movie* que usa un proveedor de datos de Azure Cosmos DB para tener acceso a los archivos de documento.  
      
    > [!div class="mx-imgBorder"] 
    > ![Definición de la entidad virtual usando el proveedor de datos de Azure Cosmos DB](media/virtual-entity-definition.PNG)  
      
    > [!IMPORTANT]
    > Varias opciones, como equipos de acceso, colas y creación rápida, no están disponibles con las entidades virtuales. Más información [Consideraciones al usar las entidades virtuales](#considerations)  
      
    Rellene las propiedades necesarias y opcionales adicionales, como los nombres en plural y los nombres para mostrar, según sea necesario. Para obtener más información acerca estas propiedades, consulte [Crear y editar entidades](create-edit-entities.md).  
  
1. Crear y agregar uno o varios campos para la entidad virtual. Además de las propiedades de campo estándar necesarias para crear un campo personalizado, estas propiedades opcionales están disponibles para cada campo personalizado que se cree para una entidad virtual.

    |Campo|Descripción|
    |--|--|
    |**Nombre externo**|Normalmente, este es el nombre único para identificar los datos que se deben mostrar en el campo.|
    |**Nombre de tipo externo**|Si el tipo de campo que crea es OptionSet: esta propiedad establece una relación con el nombre externo del conjunto de valores en el servicio externo para el conjunto de opciones.  Normalmente, puede tratarse de una enumeración o del nombre de una clase de valor de cadena. El Nombre de tipo externo se puede usar cuando se requiere un nombre completo.  Por ejemplo, como en el caso de *Nombre de tipo* con OData, donde los parámetros de una consulta requieren el nombre completo, como [*Nombre de tipo*].[*Valor*].|
    |**Valor externo**|Si el tipo de campo que crea es OptionSet: esta propiedad establece una relación con el valor correspondiente en el origen de datos externo para el elemento del conjunto de opciones.  Este valor especificado se usa para determinar qué elemento del conjunto de opciones se mostrará en la aplicación.  |

    Rellene las propiedades adicionales según sea necesario. Para obtener más información acerca estas propiedades, consulte [Crear y editar campos](create-edit-fields.md).  
  
1. Seleccione **Guardar y cerrar** en la página de propiedades **Campo**.  
1. En la barra de herramientas del explorador de soluciones, seleccione **Guardar**.  
1. En la barra de herramientas del explorador de soluciones, seleccione **Publicar**.  
1. Cierre el explorador de soluciones.  

<a name="considerations"></a>
   
## <a name="considerations-when-you-use-virtual-entities"></a>Consideraciones al usar las entidades virtuales  

Las entidades virtuales presentan estas restricciones.  
  
- Todas las entidades virtuales son de solo lectura.  
- Las entidades existentes no pueden convertirse en entidades virtuales.  
- De forma predeterminada, las entidades virtuales contienen solo un campo de nombre e Id.  No se admite ningún otro campo del sistema administrado, como estado o fecha de creación o modificación.
- Las entidades virtuales no admiten campos personalizados con los tipos de datos de moneda, imagen o cliente.
- Las entidades virtuales no admiten funciones de auditoría.  
- Los campos de la entidad virtual no se pueden usar en paquetes acumulativos ni campos calculados.
- Una entidad virtual no puede ser un tipo de actividad de entidad.  
- Muchas características que afectan a filas de la tabla de la entidad no se pueden habilitar con entidades virtuales.  Los ejemplos incluyen colas, administración del conocimiento, SLA, detección de duplicados, seguimiento de los cambios, capacidad de Mobile offline, seguridad de campo, Búsqueda por relevancia, portales para soluciones de portal web de Dynamics 365 y relaciones N:N entre entidades virtuales.  
- Las entidades virtuales son propiedad de la organización y no admiten los conceptos de seguridad de nivel de fila de Common Data Service. Se recomienda implementar su propio modelo de seguridad para el origen de datos externo.  
- Se recomienda centrarse en un único origen de datos al usar las entidades virtuales en las búsquedas avanzadas. Por ejemplo, no se admite crear una búsqueda avanzada que, en última instancia, cree una combinación entre los datos nativos de Common Data Service y los datos externos de la entidad virtual.  
- Las propiedades de metadatos de campos que se validan en la actualización no se aplican a las entidades virtuales. Por ejemplo, un campo Número entero en un campo de la entidad virtual puede establecerse para tener un valor mínimo de cero. Sin embargo, ya que el valor se proporcionará de un origen de datos externos, una consulta devolverá valores menores que cero cuando se recuperen de una entidad virtual.  La propiedad de valor mínimo no se implica en la consulta.  Aún debería filtrar los valores para que sean mayores que 0 si es lo se desea.
- Las entidades virtuales no admiten el seguimiento de los cambios y no se pueden sincronizar usando una característica de Common Data Service, como el Servicio de exportación de datos.
  
### <a name="see-also"></a>Vea también  

[Requisitos y prácticas recomendadas del proveedor de datos OData v4](virtual-entity-odata-provider-requirements.md)</br> 
[Crear y editar entidades](create-edit-entities.md)</br>
[Crear y editar campos](create-edit-fields.md)
