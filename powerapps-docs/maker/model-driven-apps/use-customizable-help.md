---
title: Habilitar y utilziar ayuda personalizable (aplicaciones basadas en modelo) | MicrosoftDocs
description: ''
keywords: ''
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
topic-status: Drafting
search.audienceType:
- customizer
search.app:
- PowerApps
ms.openlocfilehash: 3e6b593a30044c6a2c8cfc3e4867cb18156208f5
ms.sourcegitcommit: 7411b4cf9e30e71052fe932dfd3276e969854af4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "2768461"
---
# <a name="enable-and-use-customizable-help"></a>Habilitar y usar ayuda personalizable
La ayuda personalizable le permite ofrecer su propia información contextual a los usuarios de aplicaciones basadas en modelo rellenando formularios. 

> [!NOTE]
> En lugar de crear y de mantener su propio sistema de Ayuda, los paneles personalizados de ayuda y las tareas guiadas están disponibles y puede usarlos para crear Ayuda que dé a la aplicación de la interfaz unificada una experiencia de ayuda en el producto que esté adaptada a su organización. Más información: [Crear ayuda guiada para la aplicación de la Interfaz unificada](../common-data-service/create-custom-help-pages.md)

Con aplicaciones basadas en modelo puede reemplazar la Ayuda predeterminada con la Ayuda personalizada de su elección, en el nivel global (entorno) o de la entidad. La Ayuda personalizada expone el contenido a través de los vínculos de la Ayuda más relevantes para entidades personalizadas o personalizables. Con una dirección URL única y global puede reemplazar los vínculos de la Ayuda estándar para todas las entidades personalizables. Las direcciones URL de la entidad reemplazan los vínculos de la Ayuda estándar en cuadrículas y formularios para una entidad personalizable específica. Puede incluir parámetros adicionales en la dirección URL, tales como código de idioma y el nombre de la entidad. Estos parámetros permiten a los desarrolladores agregar funcionalidad para redirigir el usuario a una página que sea relevante para su idioma o al contexto de entidad dentro de la aplicación. La configuración de la Ayuda personalizada del nivel de la entidad es compatibles con soluciones. Por tanto, puede empaquetarla como parte de una solución y transportarla entre entornos o distribuirla en soluciones. 

## <a name="set-up-customizable-help"></a>Configurar la Ayuda personalizable
La Ayuda personalizable puede establecerse en los niveles globales y de la entidad. 

### <a name="set-customizable-help-at-the-global-level"></a>Establecer Ayuda personalizable en el nivel global
Los usuarios con el rol de seguridad de administrador del sistema pueden usar la configuración para reemplazar la Ayuda predeterminada en el nivel global. 
1. Abra una aplicación basada en modelo y en la barra de comandos seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png) > **Configuración avanzada**.
2. Vaya a **Configuración** > **Administración**.
3. Seleccione **Configuración del sistema** y luego seleccione la pestaña **General**. 
4. En **Establecer dirección URL de Ayuda personalizada**, seleccione y defina la configuración global de Ayuda personalizable siguiente: 
     - **Usar la Ayuda personalizada para entidades personalizables**. Seleccione para habilitar.  
     - **Dirección URL de la ayuda personalizada global**. Escriba la dirección URL de la Ayuda personalizada. 
     - **Anexar los parámetros a la URL**. Seleccione **Sí** para permitir que parámetros como código de idioma o nombre de entidad se anexen a la **Dirección URL de Ayuda** que especifique en la definición de entidad. Más información: [Anexar parámetros a dirección URL](#append-parameters-to-url)  

    > [!div class="mx-imgBorder"] 
    > ![Configuración global de ayuda personalizable](media/customizable-help-global-setting.png)

5. Seleccione **Aceptar**.

### <a name="set-customizable-help-for-a-specific-entity"></a>Establecer Ayuda personalizable para una entidad específica
Después de habilitar Ayuda personalizada en el nivel global, los personalizadores del sistema pueden reemplazar la dirección URL global de Ayuda para una entidad en la definición de entidad. 

1. Abra el explorador de soluciones.
2. Expanda **Entidades** y, a continuación, seleccione la entidad que desea. 
3. En la pestaña **General** de la sección **Ayuda** de la definición de entidad, en la casilla **Dirección URL de Ayuda** escriba la dirección URL de la página de Ayuda personalizada. 

    > [!div class="mx-imgBorder"] 
    > ![Configuración de entidad de ayuda personalizable](media/customizable-help-entity-setting.png)

#### <a name="append-parameters-to-url"></a>Anexar los parámetros a la URL
Como se describió anteriormente, para permitir el anexado de parámetros a la **Dirección URL de Ayuda** para la definición de entidad, establezca **Anexar parámetros a la dirección URL** en la pestaña **Configuración del sistema** > **General** como **Sí**. 

Ejemplos de los parámetros que se pueden anexar a la dirección URL:

- Código de idioma de usuario: userlcid
- Nombre de entidad: entidad
- Punto de entrada: gráfico de jerarquías o formulario
- Identificador de formulario: formid

