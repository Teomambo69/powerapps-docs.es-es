---
title: 'Control Visor de archivos PDF: referencia | Microsoft Docs'
description: Información sobre el control Visor de archivos PDF, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/10/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a8136fc1ce04ed696aeb68af7139d1b538dd879e
ms.sourcegitcommit: af653cd30f5879fea97a594d458d355fe18f4834
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223343"
---
# <a name="pdf-viewer-control-experimental-in-power-apps"></a>Control de PDF Viewer (experimental) en Power apps
Un control experimental que muestra el contenido de un archivo PDF.

## <a name="description"></a>Descripción
Muestre texto, gráficos y otro contenido en un archivo PDF mediante la incorporación de este tipo de control y estableciendo su propiedad **Documento** a la dirección URL, entre comillas dobles, del archivo que desea mostrar.

## <a name="limitations"></a>Limitaciones
1. La arquitectura de seguridad de Power apps requiere que el visor de PDF admita solo vínculos HTTPS, no HTTP.  

2. La propiedad **Document** debe vincularse directamente al archivo PDF. No se admiten las redirecciones del servidor ni las vistas HTML del documento.

3. El servidor que hospeda el documento no debe requerir autenticación.

4. Es posible que no pueda ver un documento PDF en la aplicación si el documento reside en un servidor que tiene una configuración de uso compartido de recursos entre orígenes (CORS) restrictiva. Para resolver este problema, el servidor que hospeda documentos PDF debe permitir solicitudes entre orígenes de powerapps.com.

Los usuarios de la aplicación pueden solucionar estas limitaciones abriendo documentos PDF en un explorador externo, como se le pregunta si el control no puede abrir un documento. Esta opción también está disponible en el menú de control para todos los documentos externos.

## <a name="key-properties"></a>Propiedades principales
**Documento**: la dirección URL entre comillas dobles, de un archivo PDF.

## <a name="additional-properties"></a>Propiedades adicionales
**ActualZoom**: el zoom real del control, que puede diferir del zoom solicitado con la propiedad **Ampliar**.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**CurrentFindText**: el término de búsqueda que está en uso en ese momento.

**CurrentPage**: el número de la página en un archivo PDF que se está mostrando en ese momento.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)** : el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**FindNext**: busca la siguiente instancia de **FindText** en el documento.

**FindPrevious**: busca la instancia anterior de **FindText** en el documento.

**FindText**: el término de búsqueda para buscar en el documento.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[OnSelect](properties-core.md)** : indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**OnStateChange**: cómo una aplicación responde cuando cambia el estado del control.

**[RellenoInferior](properties-size-location.md)** : distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)** : distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)** : distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)** : distancia entre el texto de un control y el borde superior de ese control.

**Página**: el número de la página que desea mostrar.

**PageCount**: el número de páginas en un documento.

**[PressedBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario toca o hace clic en ese control.

**MostrarControles**: indica si se muestra un reproductor de audio o vídeo, por ejemplo, un botón de reproducción y un control deslizante de volumen, y un control de entrada manuscrita muestra, por ejemplo, iconos para dibujar, borrar y borrar todo.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

**Zoom**: el porcentaje en que se amplía una imagen de una cámara o la vista de un archivo en un visor de PDF.

## <a name="example"></a>Ejemplo

Agregue un control **Visor de archivos PDF** y establezca su propiedad **Documento** en la dirección URL, entre comillas dobles, de un archivo PDF, como en este ejemplo:

  **"https://blog.mozilla.org/security/files/2015/05/HTTPS-FAQ.pdf"**

El control mostrará el archivo PDF.

¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

No todas las características de accesibilidad de los documentos PDF se admiten ya que el **visor de PDF** aún se encuentra en la fase experimental. Por lo tanto, **ShowControls** debe establecerse en **true** para permitir que los usuarios abran el documento en una aplicación externa.

Aprenda a crear documentos PDF accesibles con los estándares [WCAG 2.0](https://www.w3.org/TR/WCAG-TECHS/pdf.html) y [PDF/UA](https://www.pdfa.org/pdfua-the-iso-standard-for-universal-accessibility/).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* Considere la posibilidad de agregar un encabezado mediante un control **[Etiqueta](control-text-box.md)** si el documento PDF no tiene ningún título. El encabezado puede colocarse inmediatamente delante del **visor de PDF**.
