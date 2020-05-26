---
title: Resumen de temas en portales Power Apps | Microsoft Docs
description: Introducción a temas en los portales de Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/28/2020
ms.author: tapanm
ms.reviewer: tapanm
ms.openlocfilehash: ae7543b2e2983f24303a9f67e881380670600b90
ms.sourcegitcommit: b75b29d58adf1547c9fcd3ddd1f14f69fb7f572b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2020
ms.locfileid: "3330357"
---
# <a name="overview-of-themes-in-power-apps-portals"></a>Información general de temas en los portales de Power Apps

En los portales de Power Apps, la característica **Habilitar tema básico** está establecida en **Desactivado**. Cuando activa esta característica, puede usar temas predeterminados llamados **Preestablecidos**. También puede crear copias de los temas preestablecidos para una personalización adicional.

En este artículo, recorrerá la característica de temas básicos. Para la personalización avanzada de temas, vea [Editar CSS](edit-css.md).

> [!IMPORTANT]
> El característica de tema básico está en vista previa. Para obtener más información sobre las características en vista previa (GB), vea [Descripción de las características experimentales y en vista previa de Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview).

## <a name="enable-basic-themes-for-existing-portals-preview"></a>Habilitar temas básicos para portales existentes (vista previa)

[Este tema es documentación preliminar y está sujeto a modificaciones.]

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo y después seleccione el portal.

    ![Seleccione Aplicaciones y un portal](./media/theme-overview/select-app-portal.png "Seleccionar Aplicaciones y un portal")

1. Seleccione **Más Comandos** (**...**) y seleccione **Editar**.

    ![Editar un portal](./media/theme-overview/edit-portal.png "Editar un portal")

1. Seleccione **Temas** en el panel de navegación izquierdo y luego active **Habilitar tema básico**.

    ![Habilitar temas básicos](./media/theme-overview/enable-basic-theme.png "Habilitar temas básicos")

## <a name="change-theme-for-your-portal"></a>Cambiar el tema del portal

Puede establecer cualquier tema existente en su portal a un tema predeterminado.

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo y después seleccione el portal.

1. Seleccione **Más Comandos** (**...**) y seleccione **Editar**.

1. Seleccione **Tema** en el panel de componentes.

    ![Seleccionar tema de icono](./media/theme-overview/select-theme.png "Seleccionar tema de icono")

1. Seleccione cualquier tema predeterminado de los ajustes preestablecidos disponibles (en nuestro ejemplo, hemos seleccionado **Verde**).

    ![Seleccionar un tema predeterminado](./media/theme-overview/basic-theme.png "Seleccionar un tema predeterminado")

El tema seleccionado se aplica a su portal.

![Tema aplicado](./media/theme-overview/theme-applied.png "Tema aplicado")

## <a name="create-a-new-theme"></a>Crear un tema nuevo

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo y después seleccione el portal.

1. Seleccione **Más Comandos** (**...**) y seleccione **Editar**.

1. Seleccione **Tema** en el panel de componentes.

1. Seleccione **Nuevo tema**.

    ![Crear un tema nuevo](./media/theme-overview/new-theme.png "Crear un tema nuevo")

## <a name="edit-theme-details"></a>Editar detalles del tema

Puede actualizar el nombre del tema, la descripción, el color y otras configuraciones tipográficas en Power Apps Studio. 

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo y después seleccione el portal.

1. Seleccione **Más Comandos** (**...**) y seleccione **Editar**.

1. Seleccione **Tema** en el panel de componentes.

1. Seleccione el tema que se aplica actualmente o seleccione un nuevo tema de los ajustes preestablecidos.
   Al seleccionar un tema, se abre el panel de detalles en la parte derecha de su espacio de trabajo.

    ![Detalles del tema](./media/theme-overview/theme-details.png "Detalles del tema")

1. Edite detalles del tema como el nombre, la descripción o el color para diferentes áreas.

    |Opción de color | Área afectada |
    | --- | ---  |
    | Primario | Colores de botones y vínculos. |
    | Encabezado | Color de fondo del encabezado |
    | Texto de menú de encabezado | Color del texto para el menú del encabezado. |
    | Mantener el puntero sobre el menú de encabezado | Color de fondo de los elementos del menú al desplazarse sobre ellos. |
    | Fondo del cuerpo |  Color de fondo de la sección del cuerpo. |
    | Fondo del pie de página | Color de fondo para el pie de página. |
    | Texto del pie de página | Color del texto del pie de página. |

1. Guarde y publique los cambios.

## <a name="copy-a-preset-theme"></a>Copiar un tema preestablecido

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo y después seleccione el portal.

1. Seleccione **Más Comandos** (**...**) y seleccione **Editar**.

1. Seleccione **Tema** en el panel de componentes.

1. Seleccione el tema de los ajustes preestablecidos que desea copiar, seleccione **...** y luego seleccione **Guardar como copia**.

    ![Copiar tema preestablecido](./media/theme-overview/copy-preset-theme.png "Copiar un tema preestablecido")

1. Actualice los detalles del tema como se describe en la sección anterior y luego guarde el tema.

## <a name="sass-variables"></a>Variables Sass

[Sass](https://sass-lang.com/) es un lenguaje de hoja de estilo con sintaxis totalmente compatible con CSS. Cuando habilita la función de tema básico, puede usar [Variables Sass](https://sass-lang.com/documentation/variables) en lugar de valores para configurar los colores del tema.

Por ejemplo, si quiere que el color del **Encabezado** sea un 25 por ciento más claro que el color **Primario**, puede usar el siguiente valor en lugar de un color específico:

```
lighten($primaryColor, 25%);
```

![ejemplo Sass](./media/theme-overview/sass-example.png "Ejemplo Sass")

Puede usar las siguientes variables Sass con temas básicos:

|Opción de color | Nombre de variable Sass |
| - | - |
| Primario | ```$primaryColor``` |
| Encabezado | ```$headerColor``` |
| Texto de menú de encabezado | ```$headerMenuTextColor``` |
| Mantener el puntero sobre el menú de encabezado | ```$headerMenuHoverColor``` |
| Fondo del cuerpo |  ```$bodyBackground``` |
| Fondo del pie de página | ```$footerColor``` |
| Texto del pie de página | ```$footerTextColor``` |

### <a name="sass-variable-order"></a>Orden de variable Sass

Las variables Sass funcionan de arriba a abajo. Puede establecer el color del *Encabezado* en ```lighten($primaryColor, 25%);```. Pero no puede establecer el color *Primario* en ```lighten($headerColor, 25%);``` porque el *Encabezado* está debajo de *Primario* en la lista de opciones de color.

## <a name="basic-theme-considerations"></a>Consideraciones sobre temas básicos

- No puede tener dos temas con el mismo nombre de tema o el mismo nombre de archivo de tema. 
- Cualquier valor de color que introduzca manualmente debe ser para un color válido.
- Cambiando el CSS para temas preestablecidos no es compatible.
- La relación de contraste de color de primer plano y de fondo recomendada es 4.5:1, para accesibilidad.

### <a name="next-steps"></a>Pasos siguientes

[Editar tema CSS](edit-css.md)
