---
title: Agregar un informe o panel de Power BI a una página web en un portal | MicrosoftDocs
description: Instrucciones para agregar un informe o panel de Power BI a una página web en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3735a0ef1a26fdd19b7bfb7f6db717cf9bd07861
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976171"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>Agregar un informe o panel de Power BI a una página web en el portal

Puede Agregar un informe o panel de Power BI a una página web en el portal mediante la etiqueta Liquid de [powerbi](../liquid/portals-entity-tags.md#powerbi) . Puede Agregar la etiqueta en el campo de **copia** de una página web o en el campo de **origen** de una plantilla Web. Si agrega un informe o un panel de Power BI creados en el área de trabajo nueva en Power BI, debe especificar el tipo de autenticación como powerbiembedded en la etiqueta Liquid de powerbi.

Por ejemplo: 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> Si ha especificado AAD como el tipo de autenticación en la etiqueta líquida de powerbi, debe compartirlo con los usuarios necesarios antes de agregar el informe o panel de Power BI seguro a una página web en el portal. Más información: [compartir Power BI área de trabajo](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) y [compartir Power BI panel y el informe](https://docs.microsoft.com/power-bi/service-share-dashboards).

## <a name="get-the-path-of-a-dashboard-or-report"></a>Obtener la ruta de acceso de un panel o informe

1.  Inicie sesión en [Power BI](https://powerbi.microsoft.com/).

2.  Abra el panel o el informe que desea insertar en el portal.

3.  Copie la dirección URL de la barra de direcciones.

    > [!div class=mx-imgBorder]
    > ![Obtener la ruta de acceso de un panel de Power BI](../media/powerbi-dashboard-url.png "obtener la ruta de acceso de un panel de Power BI")

## <a name="get-the-id-of-a-dashboard-tile"></a>Obtener el identificador de un icono de panel

1.  Inicie sesión en [Power BI](https://powerbi.microsoft.com/).

2.  Abra el panel desde el que desea insertar un icono en el portal.

3.  Señale el icono, seleccione **más opciones**y, a continuación, seleccione **abrir en modo de enfoque**.

    > [!div class=mx-imgBorder]
    > ![Abrir Power BI icono del panel en modo de enfoque](../media/powerbi-dashboard-tile-focus.png "abrir Power BI icono del panel en el modo de enfoque")

4.  Copie el ID. de mosaico de la dirección URL en la barra de direcciones. El identificador del icono es el valor después de/tiles/.

    > [!div class=mx-imgBorder]
    > ![Power BI ID. de icono del panel](../media/powerbi-dashboard-tile-id.png "Power BI ID. del icono del panel")


### <a name="see-also"></a>Vea también


[etiqueta líquida de powerbi](../liquid/portals-entity-tags.md#powerbi)<br> 
[configurar la integración de Power BI](set-up-power-bi-integration.md)
