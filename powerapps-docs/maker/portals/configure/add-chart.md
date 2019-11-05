---
title: Agregar un gráfico a una página web en un portal | MicrosoftDocs
description: Instrucciones para agregar un gráfico creado en una aplicación controlada por modelos a una página web en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3cc2e390b988689e9a21317d80aa7d94d2ea9e6d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553886"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>Agregar un gráfico creado en una aplicación controlada por modelos a una página web en el portal

Puede Agregar un gráfico a una página web mediante una etiqueta líquida denominada [gráfico](../liquid/portals-entity-tags.md#chart). Puede Agregar la etiqueta Liquid del gráfico en el campo **copiar** en una página web o en el campo de **origen** de una [plantilla Web](../liquid/store-content-web-templates.md).
 
Por ejemplo, {% ID. de gráfico: EE3C733D-5693-DE11-97D4-00155DA3B01E%}

![Ejemplo de gráfico](../media/dynamics365-chart-example.png "Ejemplo de gráfico")

También puede especificar el identificador de una vista (consulta guardada) para filtrar la consulta. Por ejemplo:

<!—Leads by Source – Open Leads -->

{% ID. de gráfico: "EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid: "00000000-0000-0000-00AA-000010001006"%}

## <a name="get-the-id-of-a-chart"></a>Obtener el identificador de un gráfico

1.  Vaya a la entidad de destino, por ejemplo, **Sales** > **leads**.
2.  Expanda el área de **gráficos** .
3.  Elija el gráfico que desee.
4.  Seleccione **más comandos**y, a continuación, seleccione **exportar gráfico**.

    ![Exportar un gráfico](../media/export-dynamics365-chart.png "Exportar un gráfico")

5. Abra el archivo XML del gráfico exportado en un editor de texto.
6. Copie el valor de la etiqueta \<visualizationid\>.

    ![Obtener chartid para un gráfico](../media/dynamics365-chart-chartid.png "Obtener el identificador de gráfico de un gráfico")

7. Pegue el valor visualizationid en la declaración de etiqueta de gráfico líquido para el parámetro de identificador de gráfico, por ejemplo:

    {% ID. de gráfico: EE3C733D-5693-DE11-97D4-00155DA3B01E%}.

## <a name="get-the-id-of-a-view"></a>Obtener el identificador de una vista

Debe abrir el editor de vistas para obtener el identificador de la vista que se va a usar con la etiqueta del gráfico líquido.
 
1.  Vaya a la entidad de destino, por ejemplo, **Sales** > **leads**.
2.  Seleccione la vista que desee en el encabezado desplegable ver.
3.  Seleccione **vista** en la barra de herramientas. Se abre la ventana vista.

    ![Ver los clientes potenciales en el editor de vistas](../media/dynamics365-chart-view.png "Ver los clientes potenciales en el editor de vistas")

4. Copie el valor de **identificador** de la dirección URL de la ventana de vista.

    ![Obtener el ID. de vista del editor de vistas](../media/dynamics365-chart-viewid.png "Obtener el identificador de vista del editor de vistas")

5. Pegue este identificador en la declaración de etiqueta de gráfico líquido para el parámetro viewid, por ejemplo:

    <!—Leads by Source – Open Leads -->

    {% ID. de gráfico: "EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid: "00000000-0000-0000-00AA-000010001006"%}

## <a name="entity-permission-requirement"></a>Requisito de permiso de entidad

Se ha declarado el privilegio de lectura para la entidad de destino que se está consultando en el gráfico. Para que los usuarios anónimos o autenticados puedan ver el gráfico, debe asegurarse de que los registros de [permisos de entidad](assign-entity-permissions.md) adecuados se crean y se asignan a los [roles web](create-web-roles.md)correspondientes. 
 
Si no se concede el permiso, el usuario verá un mensaje de acceso denegado.

## <a name="unsupported-charts-and-chart-types"></a>Gráficos y tipos de gráfico no admitidos

Los siguientes tipos de gráficos no se admiten actualmente en los portales:
- Donut
- Etiqueta

En la tabla siguiente se enumeran los gráficos que actualmente no se admiten en los portales.

| Nombre del gráfico                              | IDENTIFICADOR de gráfico                             | Tipo de entidad      |
|-----------------------------------------|--------------------------------------|------------------|
| Cuentas por propietario: gráfico de etiquetas           | be178262-6142-4b41-85b7-4ccedc62cfd9 | Código          |
| Actividades por propietario: gráfico de etiquetas         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| Actividades por prioridad: gráfico de anillos | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| Contactos por cuenta                     | 2ff3ebea-6310-4dde-b3a1-e1144ea42b7b | Póngase          |
| Contactos por país                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | Póngase          |
| Contactos por método de contacto preferido    | 751b7456-308e-4568-a3a9-47135aae833a | Póngase          |
| Progreso del objetivo (recuento)                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | goal             |
| Progreso del objetivo (dinero)                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | goal             |
| Destino de hoy frente a valores reales (recuento)      | 1b697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| Destino de hoy frente a reales (dinero)      | 1e697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| Casos por cuenta                        | 38872e4f-ac99-e511-80da-00155dc1b253 | incident         |
| Casos por prioridad                       | 0f0fb995-9d6f-453c-b26d-8f443e42e676 | incident         |
| Casos por producto                        | 17c3f166-5b22-4476-819b-b05da2e8d24f | incident         |
| Artículos que van a expirar este mes por propietario   | 47d696ad-7c3b-e511-80d1-00155db10d2b | knowledgearticle |
| Por propietario                                | 330068fd-833b-e511-80d1-00155db10d2b | knowledgearticle |
| Por asunto                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | knowledgearticle | 
| | |
