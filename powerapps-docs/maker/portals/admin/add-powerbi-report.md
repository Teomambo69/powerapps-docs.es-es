---
title: Agregar informes o un panel de Power BI a una página web en un portal | MicrosoftDocs
description: Instrucciones para agregar informes o un panel de Power BI a una página web en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3735a0ef1a26fdd19b7bfb7f6db717cf9bd07861
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710087"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>Adición de informes o un panel de Power BI a una página web en un portal

Puede agregar un informe o un panel de Power BI a una página web en un portal usando la etiqueta de Liquid [powerbi](../liquid/portals-entity-tags.md#powerbi). Puede agregar la etiqueta en el campo **Copiar** en una página web o en el campo **Origen** en una Plantilla web. Si que agrega un informe o un panel de Power BI creado en el nuevo espacio de trabajo en Power BI, deberá especificar el tipo de autenticación como powerbiembedded en la etiqueta powerbi Liquid.

Por ejemplo: 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> Si ha especificado DAA como tipo de autenticación en la etiqueta powerbi Liquid, debe compartirla con los usuarios requeridos antes de agregar el informe o el panel seguro de Power BI a una página web en portal. Más información: [Compartir área de trabajo de Power BI](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) y [Compartir el panel y el informe de Power BI](https://docs.microsoft.com/power-bi/service-share-dashboards).

## <a name="get-the-path-of-a-dashboard-or-report"></a>Obtenga la ruta de un panel o informe

1.  Inicie sesión en [Power BI](https://powerbi.microsoft.com/).

2.  Abra el panel o informe que desea insertar en el portal.

3.  Copie la dirección URL de la barra de direcciones.

    > [!div class=mx-imgBorder]
    > ![Obtenga la ruta de un panel de Power BI](../media/powerbi-dashboard-url.png "Obtenga la ruta de un panel de Power BI")

## <a name="get-the-id-of-a-dashboard-tile"></a>Obtener el identificador de una ventana de panel

1.  Inicie sesión en [Power BI](https://powerbi.microsoft.com/).

2.  Abra el panel desde el que desea insertar una ventana en el portal.

3.  Apunte al mosaico, seleccione **Más opciones**y, a continuación seleccione **Abrir en modo de enfoque**.

    > [!div class=mx-imgBorder]
    > ![Abrir ventana del panel de Power BI en modo de enfoque](../media/powerbi-dashboard-tile-focus.png "Abrir ventana del panel de Power BI en modo de enfoque")

4.  Copie el identificador del mosaico de la dirección URL en la barra de direcciones. El identificador del mosaico es el valor que está después de /tiles/.

    > [!div class=mx-imgBorder]
    > ![Id. de ventana del panel de Power BI](../media/powerbi-dashboard-tile-id.png "Id. de ventana del panel de Power BI")


### <a name="see-also"></a>Vea también


[etiqueta powerbi de Liquid](../liquid/portals-entity-tags.md#powerbi)<br> 
[Configurar la integración de Power BI](set-up-power-bi-integration.md)
