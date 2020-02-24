---
title: Editar CSS en un portal | Microsoft Docs
description: Instrucciones para editar CSS en un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: f8a610d77da477595545003b801711c8151ce8f6
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2976937"
---
# <a name="edit-css"></a>Editar CSS

Las hojas de estilo en cascada (CSS) le permiten controlar el formato de la página web. De forma predeterminada, los archivos bootstrap.min.css y theme.css están disponibles. Puede editar los archivos CSS existentes y cargar los nuevos archivos CSS. Cuando carga un nuevo archivo CSS, estará disponible como archivo web en la aplicación de administración de portales.

> [!NOTE]
> Los portales de Power Apps se basan en Bootstrap 3.3.x con la excepción del [Portal de eventos](https://docs.microsoft.com/dynamics365/marketing/developer/event-management-web-application). Los desarrolladores del portal no deben reemplazar Bootstrap 3 con otras bibliotecas CSS ya que algunos de los escenarios en Power Apps dependen de Bootstrap 3.3.x.

Para abrir un CSS en el editor de código:

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione **Tema** ![icono Tema](media/theme-icon.png "Icono de tema") del toolbelt en el lateral izquierdo de la pantalla. Se muestran los temas disponibles.  

    > [!div class=mx-imgBorder]
    > ![Panel de tema](media/theme-pane.png "Panel de tema")  

3.  Seleccione la CSS requerida para abrirla en el editor de código.

4.  Edite el código y guarde los cambios.

Para cargar un nuevo archivo CSS:

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en portales de Power Apps Studio.  

2.  Seleccione **Tema** ![icono Tema](media/theme-icon.png "Icono de tema") del toolbelt en el lateral izquierdo de la pantalla. Se muestran los temas disponibles.  

3. Seleccionar **Cargar CSS personalizada**.

    > [!div class=mx-imgBorder]
    > ![Panel de tema](media/upload-css.png "Panel de tema")  

4. Busque el archivo CSS, y selecciónelo para cargarlo.


