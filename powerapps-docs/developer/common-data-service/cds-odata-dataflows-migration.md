---
title: Migrar datos entre entornos Common Data Service que utilizan el conector OData de flujos de datos
author: denisem-msft
ms.reviewer: nabuthuk
description: Migrar datos entre entornos Common Data Service que utilizan el conector OData de flujos de datos.
ms.date: 05/05/2020
ms.service: powerapps
ms.topic: article
ms.author: demora
search.app:
- PowerApps
ms.openlocfilehash: 7cf920032665f911554d2acca434709256127c8b
ms.sourcegitcommit: 13a78a66408d39b4bc90a72613b0d303abc07b1b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "3338249"
---
# <a name="migrate-data-between-common-data-service-environments-using-the-dataflows-odata-connector"></a>Migrar datos entre entornos Common Data Service que utilizan el conector OData de flujos de datos

Common Data Service [API web](/powerapps/developer/common-data-service/webapi/overview) funciona con cualquier tecnología que admita OData y Oauth. Hay muchas opciones disponibles para mover datos dentro y fuera de Common Data Service. El conector OData es uno de los flujos de datos, que está diseñado para admitir la migración y sincronización de grandes conjuntos de datos en Common Data Service. 

En este artículo, le explicamos cómo migrar datos entre entornos Common Data Service que utilizan el conector OData de flujos de datos. 

## <a name="prerequisites"></a>Requisitos previos

- Permiso de rol de seguridad de Administrador del sistema o Personalizador del sistema tanto en el entorno de origen como en el objetivo.

- Licencia de Power Apps, Power Automate o Common Data Service (por aplicación o por usuario).

- Dos [entornos con bases de datos](/power-platform/admin/create-environment#create-an-environment-with-a-database) Common Data Service.

## <a name="scenarios"></a>Escenarios

 - Se necesita una migración única entre entornos o entre inquilinos (por ejemplo, geo-migración)

 - El desarrollador necesita actualizar una aplicación que se está utilizando en producción. Se necesitan datos de prueba en su entorno de desarrollo para construir fácilmente los cambios. 

## <a name="step-1-plan-out-the-dataflow"></a>Paso 1: Planificar el flujo de datos

1. Identificar los entornos de destino y de origen.

    - El **entorno origen** es de donde se migran los datos. 

    - El **entorno destino** es a donde se migran los datos. 

1. Asegúrese de que las entidades ya estén definidas en el entorno de destino. Idealmente, ambos entornos deberían tener las mismas entidades definidas con la misma solución.

1. Al importar relaciones, se requieren múltiples flujos de datos.

    Una entidad (primaria / independiente) a muchas (secundarias / dependientes) requieren flujos de datos separados. Configure el flujo de datos primario para que se ejecute antes que cualquier entidad secundaria, ya que los datos en el primario deben cargarse primero para correlacionarse correctamente con los campos en las entidades secundarias correspondientes.

## <a name="step-2-get-the-odata-endpoint"></a>Paso 2: Obtener el extremo OData 

Common Data Service proporciona un extremo OData que no requiere ninguna configuración adicional para autenticarse con el conector de flujos de datos. Es un proceso relativamente fácil conectarse al entorno de origen. 

Este artículo explicará cómo configurar un nuevo flujo de datos con el conector OData. Vea el artículo [Crear flujos de datos](https://docs.microsoft.com/powerapps/maker/common-data-service/create-and-use-dataflows) para conectarse a todas las fuentes de datos compatibles con los flujos de datos.

Desde el entorno **origen**, obtenga el [extremo OData](https://docs.microsoft.com/powerapps/developer/common-data-service/view-download-developer-resources) (también conocido como URL raíz del servicio) para ese entorno:

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione el entorno de origen obligatorio de la esquina superior derecha.

1. Seleccione el icono Configuración (rueda dentada) en la esquina superior derecha y después seleccione **Configuración avanzada**.

1. En la página de **Configuración**, seleccione la flecha desplegable situada junto a ****Configuración** y, a continuación, seleccione **Personalizaciones**.

1. En la página **Personalizaciones**, seleccione **Recursos para desarrolladores**.

1. Copia la **URL raíz del servicio** al bloc de notas.

    > [!div class="mx-imgBorder"]
    > ![Copie la URL raíz del servicio en los recursos del desarrollador](./media/get-odata-endpoint-url.png)
 
## <a name="step-3-create-a-new-odata-dataflow"></a>Paso 3: Crear un nuevo flujo de datos OData

En el entorno **destino**, cree un nuevo flujo de datos con el conector OData.

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione el entorno de destino obligatorio de la esquina superior derecha.

1. En el panel de navegación izquierdo, expanda el menú **Datos**, y seleccione **Flujos de datos**.

1. Seleccione **Nuevo flujo de datos** para crear un flujo de datos nuevo. Proporcione un nombre descriptivo para el flujo de datos. Seleccione **Crear**.
   > [!div class="mx-imgBorder"]
   > ![Solicitar un nuevo flujo de datos](./media/enter-name-for-new-dataflow.png)

1. Seleccione el conector **OData**.

    > [!div class="mx-imgBorder"]
    > ![Seleccionar origen OData](media/select-odata-data-source.png)

1. En el cuadro de diálogo Configuración de conexión, escriba los valores del campo:

    > [!div class="mx-imgBorder"]
    > ![Confirme que los valores del campo son correctos](./media/enter-odata-connector-parameters.png)


    | Campo | Descripción |
    |--|--|
    | Dirección URL | Proporcione la URL raíz del servicio en el campo URL de la configuración de conexión |
    | Conexión | Crear una nueva conexión. Esto se elegirá automáticamente si no ha realizado una conexión OData en flujos de datos anteriormente. |
    | Nombre de conexión | Opcionalmente, cambie el nombre del nombre de la conexión, pero se rellena automáticamente con un valor |  |
    | Puerta de enlace de datos local | Ninguno. No se necesita una puerta de enlace de datos local para las conexiones a este servicio en la nube. |
    | Tipo de autenticación | Cuenta de la organización. Seleccione el botón de inicio de sesión para abrir el cuadro de diálogo de inicio de sesión que autentica la cuenta asociada con la conexión. |    

    > [!IMPORTANT] 
    > Deshabilite el bloqueador de pop-ups y cookies en su navegador para configurar la autenticación de Azure AD. Esto es ortogonal al hecho de que está utilizando el extremo OData de Common Data Service o cualquier otra autenticación basada en origen de datos de OAuth. 
    
1. Seleccione **Siguiente** en la parte inferior derecha.

## <a name="step-4-select-and-transform-data-with-the-power-query"></a>Paso 4: Seleccionar y transformar datos con Power Query 

Use Power Query para seleccionar las tablas y también transformar los datos según sus necesidades.

Primero, seleccione las entidades que deben transferirse. Puede examinar todas las entidades en el entorno de origen y obtener una vista previa de algunos de los datos en cada entidad.

> [!div class="mx-imgBorder"]
> ![Navegador de Power Query](./media/edit-queries-for-selected-entities.png)

1. Seleccione una o varias entidades según sea necesario, luego seleccione **Transformar datos**.

    > [!NOTE]
    > Al importar relaciones, recuerde que el flujo de datos de la entidad primaria debe importarse antes que los secundarios. Los datos para el flujo de datos secundario requerirán que los datos estén en la entidad primaria para que se asignen correctamente, de lo contrario, podría darse un error.
 
1. En la ventana **Power Query - Editar consultas**, puede transformar la consulta antes de importar.

    - Si solo está migrando datos, no debería ser necesario modificar nada aquí. 

    - Reducir el número de columnas innecesarias mejorará el rendimiento del flujo de datos para conjuntos de datos más grandes.

    > [!TIP]
    > Puede volver a elegir más tablas en la opción de cinta **Obtener datos** para el mismo conector OData.

1. Seleccione **Siguiente** en la parte inferior derecha.

## <a name="step-5-configure-target-environment-settings"></a>Paso 5: Configurar el entorno de destino

Esta sección describe cómo definir la configuración del entorno de destino.

### <a name="step-51-map-entities"></a>Paso 5.1: Asignar entidades 

Para cada entidad elegida, seleccione el comportamiento para importar esa entidad en esta configuración y seleccione **Siguiente**.

> [!div class="mx-imgBorder"]
> ![Asignar entidades](./media/map-entities-to-target.png)

- **Cargar a la entidad existente (recomendado)**

    - El flujo de datos sincroniza los datos de la entidad del entorno de origen con el entorno de destino,y el mismo esquema de entidad ya está definido en el entorno de destino.

    - Idealmente, use la misma solución en los entornos de destino y origen para que la transferencia de datos sea fluida. Otra ventaja de tener una entidad predefinida es un mayor control sobre en qué solución se define la entidad y el prefijo.
    
    - Elija la casilla **Eliminar las filas que ya no existan en la salida de la consulta**. Esto asegura que las relaciones se asignarán correctamente porque mantiene los valores para las búsquedas.
    
    - Si el esquema es idéntico en las tablas de origen y destino, puede seleccionar el botón **Asignación automática** para asignar rápidamente los campos.
    
    - Requiere una configuración clave en el entorno de destino (ya que los campos de identificador único no están disponibles para modificar).

- **Cargar a entidad nueva (no recomendado)**

    - Idealmente, debería haber una entidad predefinida en el entorno de destino desde la misma importación de solución que el entorno de origen. Sin embargo, hay casos en los que esto podría no ser factible, por lo que existe esta opción para elegir si no hay una entidad existente para cargar. 

    - Crea una nueva entidad personalizada en la solución predeterminada del entorno de destino.

- Hay una opción para **No cargar**, pero no incluye entidades en el flujo de datos que no se estén cargando. Puede elegir **Atrás** desde este menú para volver al menú Power Query y eliminar las entidades que no son necesarias.

### <a name="step-52-refresh-settings"></a>Paso 5.2: Actualizar configuración

Seleccione **Actualizar manualmente** dado que esta migración solo se hará una vez y seleccione **Crear**. 

## <a name="step-6-run-the-dataflow"></a>Paso 6: Ejecutar el flujo de datos

La carga de flujo de datos inicial se inicia cuando selecciona el botón **Crear**. 

> [!div class="mx-imgBorder"]
> ![Actualizar manualmente](./media/initiate-dataflow-process.png)

Puede iniciar manualmente un flujo de datos seleccionando **(...)** en la lista de flujos de datos. Asegúrese de ejecutar flujos de datos dependientes una vez que se hayan completado los flujos primarios.

> [!div class="mx-imgBorder"]
> ![Actualizar manualmente](./media/refresh-dataflow-manually.png) 

## <a name="tips"></a>Sugerencias

- Pruebe una entidad primero para recorrer los pasos, luego desarrolle todos los flujos de datos.

- Si hay más entidades que contienen grandes cantidades de datos, considere configurar múltiples flujos de datos separados para entidades individuales.

- Las relaciones uno a varios requerirán flujos de datos separados para cada entidad. Configure y ejecute el flujo de datos de la entidad primaria (también conocido como uno o independientemente) antes de la entidad secundaria (también conocido como varios o dependiente).

- Si hay errores con la actualización del flujo de datos, puede ver el historial de actualización en el menú **(...)** en la lista de flujos de datos y descargar cada registro de actualización.

## <a name="limitations"></a>Limitaciones

- No se admiten las importaciones de datos de varias a varias relaciones.

- Los flujos de datos primarios deben configurarse manualmente para ejecutarse antes que los flujos de datos secundarios.
