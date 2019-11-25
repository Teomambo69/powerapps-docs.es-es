---
title: Agregar un gráfico a una página web en un portal | MicrosoftDocs
description: Instrucciones para agregar un gráfico creado en una aplicación modelo basada en modelo para una página web en el portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761091"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>Agregar un gráfico creado en una aplicación modelo basada en modelo para una página web en el portal

Puede agregar un gráfico a una página web mediante una etiqueta de Liquid con nombre [Gráfico](../liquid/portals-entity-tags.md#chart). Puede agregar la etiqueta de Liquid del gráfico en el campo **Copiar** en una página web o en el campo **Origen** en una [Plantilla web](../liquid/store-content-web-templates.md).
 
Por ejemplo, {% chart id:EE3C733D-5693-DE11-97D4-00155DA3B01E %}

![Gráfico de ejemplo](../media/dynamics365-chart-example.png "Gráfico de ejemplo")

También puede especificar el identificador de una vista (consulta guardada) para filtrar la consulta. Por ejemplo:

<!—Leads by Source – Open Leads -->

{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}

## <a name="get-the-id-of-a-chart"></a>Obtener el identificador de un gráfico

1.  Vaya a la entidad de destino, por ejemplo, **Ventas** > **Clientes potenciales**.
2.  Expanda el área **Gráficos**.
3.  Elija el gráfico que desee.
4.  Seleccione **Más comandos** y seleccione **Exportar gráfico**.

    ![Exportar un gráfico](../media/export-dynamics365-chart.png "Exportar un gráfico")

5. Abra el archivo XML del gráfico exportado en un editor de texto.
6. Copie el valor de la etiqueta \<visualizationid\>.

    ![Obtenga el id. de gráfico para un gráfico](../media/dynamics365-chart-chartid.png "Obtener el identificador de un gráfico")

7. Pegue el valor de visualizationid en la declaración de la etiqueta de Liquid del gráfico para el parámetro del identificador del gráfico, por ejemplo:

    {% chart id:EE3C733D-5693-DE11-97D4-00155DA3B01E %}.

## <a name="get-the-id-of-a-view"></a>Obtener el identificador de una vista

Debe abrir el editor de vistas para obtener el identificador de la vista que se usará con la etiqueta de Liquid del gráfico.
 
1.  Vaya a la entidad de destino, por ejemplo, **Ventas** > **Clientes potenciales**.
2.  Seleccione la vista que desee del encabezado desplegable de vistas.
3.  Seleccione **Vista** de la barra de herramientas. Se abrirá la ventana Ver.

    ![Ver los clientes potenciales en el editor de vistas](../media/dynamics365-chart-view.png "Ver los clientes potenciales en el editor de vistas")

4. Copie el valor **id** de la dirección URL de la ventana de Ver.

    ![Obtener el Id. de vista del editor de vistas](../media/dynamics365-chart-viewid.png "Obtener el Id. de vista del editor de vistas")

5. Pegue este id. en la declaración de la etiqueta de Liquid del gráfico para el parámetro viewid, por ejemplo:

    <!—Leads by Source – Open Leads -->

    {% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}

## <a name="entity-permission-requirement"></a>Requisito de permiso de entidad

El privilegio de lectura se afirma para la entidad de destino que se consulta en el gráfico. Para que usuarios anónimos o autenticados puedan ver el gráfico, debe asegurarse que los registros [Permisos de entidad](assign-entity-permissions.md) adecuados se creen y asignen a los [roles web](create-web-roles.md) aplicables. 
 
Si el permiso no se concede, el usuario verá un mensaje de acceso denegado.

## <a name="unsupported-charts-and-chart-types"></a>Gráficos y tipos de gráficos no admitidos

Actualmente no se admiten los tipos de gráficos siguientes en los portales:
- Anillo
- Etiqueta

La tabla siguiente enumera los tipos de gráficos que actualmente no se admiten en los portales.

| Nombre al gráfico                              | Id. de gráfico                             | Tipo de entidad      |
|-----------------------------------------|--------------------------------------|------------------|
| Cuentas por propietario: gráfico de etiquetas           | be178262-6142-4b41-85b7-4ccedc62cfd9 | account          |
| Actividades por propietario: gráfico de etiquetas         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| Actividades por prioridad: gráfico de anillos | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| Contactos por cuenta                     | 2ff3ebea-6310-4dde-b3a1-e1144ea42b7b | contacto          |
| Contactos por país                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | contacto          |
| Contactos por método de contacto preferido    | 751b7456-308e-4568-a3a9-47135aae833a | contacto          |
| Progreso de objetivos (recuento)                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | goal             |
| Progreso del objetivo (dinero)                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | goal             |
| Destino de hoy comparado con datos reales (recuento)      | 1b697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| Destino de hoy comparado con datos reales (dinero)      | 1e697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| Casos por cuenta                        | 38872e4f-ac99-e511-80da-00155dc1b253 | incident         |
| Casos por prioridad                       | 0f0fb995-9d6f-453c-b26d-8f443e42e676 | incident         |
| Casos por producto                        | 17c3f166-5b22-4476-819b-b05da2e8d24f | incident         |
| Artículos que expiran este mes por propietario   | 47d696ad-7c3b-e511-80d1-00155db10d2b | Artículo de conocimientos |
| Por propietario                                | 330068fd-833b-e511-80d1-00155db10d2b | Artículo de conocimientos |
| Por tema                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | Artículo de conocimientos | 
| | |
