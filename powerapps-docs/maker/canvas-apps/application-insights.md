---
title: Analizar la telemetría de la aplicación mediante Application Insights | Microsoft Docs
description: Cómo analizar la telemetría de la aplicación mediante Application Insights
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/25/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cf7e65d395e8ad28e434cc957502a5bce52a3e6e
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2020
ms.locfileid: "80328925"
---
# <a name="analyze-app-telemetry-using-application-insights"></a>Analizar la telemetría de la aplicación mediante Application Insights

Puede conectar la aplicación con [Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview), una característica de [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview). Application Insights incluye eficaces herramientas de análisis para ayudarle a diagnosticar problemas y comprender lo que los usuarios hacen realmente con la aplicación. 

Con la aplicación conectada a Application Insights, puede recopilar información para ayudarle a impulsar mejores decisiones empresariales y mejorar la calidad de las aplicaciones.

En esta guía de inicio rápido, va a instrumentar una aplicación de lienzo denominada Kudos. Esto le ayudará a explorar, detectar conceptos de telemetría y aplicarlos a sus propias aplicaciones de canvas. La aplicación Kudos de ejemplo forma parte de un conjunto de aplicaciones de Employee Engagement disponibles para su descarga desde el [Starter Kit de experiencia de empleado](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit).

## <a name="prerequisites"></a>Requisitos previos

- Debe tener acceso a [Azure portal](https://portal.azure.com).
- Debe tener los permisos necesarios para [crear recursos de Azure](https://docs.microsoft.com/azure/role-based-access-control/quickstart-assign-role-user-portal).

### <a name="optional"></a>Opcional

- Descargue e instale la aplicación de Kudos desde el [Starter Kit de experiencia de empleado](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit). En su lugar, también puede usar una aplicación existente.

## <a name="create-an-application-insights-resource"></a>Creación de un recurso de Application Insights

Antes de poder enviar telemetría para una aplicación, debe crear un recurso de Aplicación de Azure Insights para almacenar los eventos.

1. Inicie sesión en el [Azure portal](https://portal.azure.com/).

1. Busque Application Insights:

    ![Azure Application Insights](./media/application-insights/azureappinsights.png)

1. Cree un recurso de Application Insights:

    ![Adición de un recurso de Aplicación de Azure Insights](./media/application-insights/azureappinsights-add.png)

1. Escriba los valores adecuados y seleccione **revisar y crear**. Para obtener más información, lea [creación de un recurso de Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/create-new-resource). 

    ![Crear un recurso](./media/application-insights/createresource.png)

1. Una vez creada la instancia de Application Insights, verá la información general de la instancia. Copie la **clave de instrumentación**. Necesitará esta clave para configurar la aplicación.

    ![Copiar clave de instrumentación](./media/application-insights/instrumentation-key.png)

## <a name="connect-your-app-to-application-insights"></a>Conectar la aplicación a Application Insights

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **aplicaciones** en el panel de navegación izquierdo. En la lista de aplicaciones, seleccione la aplicación **Kudos** y, a continuación, seleccione **Editar**:

    ![Editar aplicación de Kudos](./media/application-insights/edit-kudos-app.png)

    > [!NOTE]
    > También puede [crear](open-and-run-a-sample-app.md) una nueva aplicación o [Editar](edit-app.md) cualquier aplicación existente en su lugar.

1. Seleccione el objeto de **aplicación** en la vista de árbol de navegación de la izquierda y pegue la **clave de instrumentación**:

    ![Agregar clave de instrumentación](./media/application-insights/add-instrumentation-key.png)

1. **Guarde** & **publicar** la aplicación.

1. **Reproduzca** la aplicación publicada y examine distintas pantallas. 

A medida que examina diferentes pantallas, los eventos se registran automáticamente en Application Insights incluidos los detalles de uso, como:

- Desde el que se tiene acceso a la aplicación.
- Cuáles son los dispositivos usados.
- Tipos de explorador utilizados.

> [!IMPORTANT]
> Debe reproducir la aplicación publicada para enviar eventos a Application Insights. Los eventos no se envían a Application Insights cuando se obtiene una vista previa de la aplicación en Power apps Studio.

## <a name="view-events-in-application-insights"></a>Ver eventos en Application Insights

1. Inicie sesión en el [Azure portal](https://portal.azure.com/) y abra el Application Insights recurso que creó [anteriormente](#create-an-application-insights-resource).

1. Desplácese hacia abajo en el panel de navegación izquierdo y seleccione **usuarios** en la sección **uso** . 

    > [!NOTE]
    > La vista **usuarios** muestra los detalles de uso de la aplicación, como:
    > - Número de usuarios que han visto la aplicación.
    > - Número de sesiones por los usuarios de la aplicación.
    > - Número de eventos registrados para la aplicación.
    > - Sistemas operativos y detalles de versión del explorador de los usuarios.
    > - Región y ubicación de los usuarios.
    > 
    > Para obtener más información, consulte [análisis de usuarios, sesiones y eventos en Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/usage-segmentation).

1. Seleccione una de las sesiones de usuario para profundizar en detalles concretos. Puede ver información como la duración de la sesión y las pantallas visitadas:

    ![Detalles de uso de los usuarios](./media/application-insights/appinsights-users.gif)

1. Seleccione la vista **eventos** en el panel de navegación izquierdo en la sección **uso** . Puede ver un resumen de todas las pantallas que se ven en todas las sesiones de la aplicación:

    ![Detalles de evento de la aplicación](./media/application-insights/appInsights-events.gif)

> [!TIP]
> Algunas de las características de Application Insights adicionales que puede usar son:  
> - [**Embudos**](https://docs.microsoft.com/azure/azure-monitor/app/usage-funnels)
> - [**Cohortes**](https://docs.microsoft.com/azure/azure-monitor/app/usage-cohorts)
> - [**Análisis de impacto**](https://docs.microsoft.com/azure/azure-monitor/app/usage-impact)
> - [**Análisis de retención**](https://docs.microsoft.com/azure/azure-monitor/app/usage-retention)
> - [**Flujos de uso**](https://docs.microsoft.com/azure/azure-monitor/app/usage-flows)

## <a name="create-custom-trace-events"></a>Crear eventos de seguimiento personalizados

Puede escribir seguimientos personalizados directamente en Application Insights y empezar a analizar la información específica de su escenario. La función de [seguimiento](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-trace) le permite recopilar:

- Información de uso granular para los controles de las pantallas.
- Qué usuarios específicos acceden a la aplicación.
- Los errores que se producen.

El seguimiento también puede ayudar a diagnosticar problemas, ya que puede enviar un rastro de la información a medida que los usuarios navegan por la aplicación y realizan acciones diferentes.

Hay 3 niveles de gravedad para los mensajes de seguimiento al enviar información de seguimiento personalizada a Application Insights desde la aplicación:

- **Informaciones**
- **Atención**
- **Error**

En función de su escenario, puede elegir enviar el mensaje de seguimiento con la gravedad adecuada. Puede consultar los datos y realizar acciones específicas en función de la gravedad del mensaje.

> [!NOTE]
> Si está registrando datos de personal, tendrá que tener en cuenta las obligaciones de cumplimiento de datos, como RGPD, que también puede necesitar implementar.

Ahora se actualizará la aplicación y se creará un nuevo componente para recopilar comentarios en cada pantalla de la aplicación. Escribirá los eventos en Application Insights.

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **aplicaciones** en el panel de navegación izquierdo. En la lista de aplicaciones, seleccione la aplicación **Kudos** y, a continuación, seleccione **Editar**.

    > [!NOTE]
    > También puede [crear](open-and-run-a-sample-app.md) una nueva aplicación o [Editar](edit-app.md) cualquier aplicación existente en su lugar.

1. Seleccione la opción **componentes** en la **vista de árbol**:

    ![Componentes](./media/application-insights/new-component.png)

1. Seleccione **nuevo componente**y, a continuación, cambie el tamaño del ancho a 200, alto a 75:

    ![Alto y ancho](./media/application-insights/resize-component.png)

1. Seleccione **Insertar** en el menú y, a continuación, seleccione **iconos** para agregar iconos *Emoji-desaprobación* y *Emoji-sonrisa* :

    ![Adición de iconos](./media/application-insights/add-icons.png)

1. Seleccione **nueva propiedad personalizada** para crear una propiedad personalizada:

    ![Crear propiedad personalizada](./media/application-insights/create-custom-property.png)

1. Escriba *el nombre* de la propiedad y *el nombre para mostrar* , como *FeedbackSceen*.

1. Escriba la *Descripción*de la propiedad.

1. Seleccione **el tipo de propiedad** como **entrada** y **tipo de datos** como **pantalla**:

    ![Propiedad personalizada](./media/application-insights/custom-input-property.png)

    > [!NOTE]
    > La propiedad entrada permite capturar el nombre de la pantalla y su componente para que pueda registrar esta información en Application Insights.

1. Seleccione el componente en la **vista de árbol**, seleccione las **acciones más** (**...**) y, a continuación, seleccione cambiar **nombre** para cambiar el nombre del componente por un nombre descriptivo como *FeedbackComponent*.

    ![Cambiar el nombre del componente y de los inconvenientes](./media/application-insights/rename-component-icons.png)

1. Seleccione iconos, seleccione **más acciones** (**...**) y, luego, seleccione **cambiar nombre** para cambiar el nombre de los iconos por nombres descriptivos, como *FrownIcon* y *SmileIcon*.

1. Seleccione *FrownIcon*, seleccione la propiedad **alseleccionar** y, a continuación, escriba la siguiente expresión en la barra de fórmulas:

    ```
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeedbackValue: "-1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

    ![Fórmula del icono desaprobación](./media/application-insights/frownicon-formula.png)

    > [!NOTE]
    > La expresión de fórmula envía el *nombre de usuario*, *UserEmail*, *pantalla* y los *comentarios* (con el valor *-1*) a Application Insights.

1. Seleccione *SmileIcon*, seleccione la propiedad **alseleccionar** y, a continuación, escriba la siguiente expresión en la barra de fórmulas:
    
    ```
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeebackValue: "1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

1. Agregue el componente a una de las pantallas de la aplicación:

    ![Agregar componente de comentarios](./media/application-insights/add-feedback-component.png)

1. Seleccione **Guardar** y, a continuación, seleccione **publicar** para guardar & publicar la aplicación.

1. Reproducir la aplicación publicada y enviar una sonrisa y un comentario desenfadado de las pantallas.

    > [!IMPORTANT]
    > Debe reproducir la aplicación publicada para enviar eventos a Application Insights. Los eventos no se envían a Application Insights cuando se obtiene una vista previa de la aplicación en Power apps Studio.

    ![Reproducir aplicación publicada](./media/application-insights/play-published-app.png)

## <a name="analyze-data-in-application-insights"></a>Analizar datos en Application Insights

Ahora puede empezar a analizar los datos enviados con la función de [seguimiento](#create-custom-trace-events) desde la aplicación en App Insights.

1. Inicie sesión en el [Azure portal](https://portal.azure.com/) y abra el Application Insights recurso que creó [anteriormente](#create-an-application-insights-resource):

    ![Selección de Application Insights](./media/application-insights/select-app-insights.png)

1. Seleccione **registros** en **supervisión** en el panel de navegación izquierdo:

    ![Seleccionar registros](./media/application-insights/select-logs.png)

1. Escriba la siguiente consulta y seleccione **Ejecutar**. Se devuelven los comentarios recibidos de la aplicación:

    ```powerappsfl
    traces
    | where message == "App Feedback"
    | order by timestamp
    ```

    ![Ver comentarios de la aplicación](./media/application-insights/view-app-feedback.png)

1. Seleccione una fila en los resultados y expanda el campo *dimensiones personalizadas* . 

    Se han grabado los valores de **Screen**, **username**, **UserEmail**y **FeedbackValue** para el evento **alseleccionar** del icono de sonrisa o desaprobación en el componente. <br>
    También hay algunos valores adicionales registrados para cada evento enviado a Application Insights; como **AppID**, **appname** y **appSessionId**.

    ![Expandir dimensiones personalizadas](./media/application-insights/expand-custom-dimensions.png)

1. Con la consulta de ejemplo siguiente, puede extender las propiedades de las dimensiones personalizadas de JSON y proyectar las columnas en la vista de resultados.

    ```powerappsfl
    traces
        | extend customdims = parse_json(customDimensions)
        | where message == "App Feedback"
        | project timestamp
            , message
            , AppName = customdims.['ms-appName']
            , AppId = customdims.['ms-appId']
            , FeedbackFrom = customdims.UserEmail
            , Screen = customdims.Screen
            , FeedbackValue = customdims.FeedbackValue
        | order by timestamp desc
    ```

    ![Extender consulta customDimensions](./media/application-insights/custom-dimensions-extend-query.png)

    > [!TIP]
    > *Las consultas de registro* son muy eficaces. Puede utilizarlos para combinar varias tablas, agregar grandes cantidades de datos y realizar operaciones complejas. Para obtener más información, lea [consultas de registro](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview).

## <a name="export-data-to-power-bi"></a>Exportar datos a Power BI

Puede exportar los datos del Application Insights y los resultados de la consulta a Power BI para el análisis y la presentación de los datos.

1. Inicie sesión en el [Azure portal](https://portal.azure.com/) y abra el Application Insights recurso que creó [anteriormente](#create-an-application-insights-resource):

1. Seleccione **registros** en **supervisión** en el panel de navegación izquierdo:

1. En la ventana de consulta de log Analytics, seleccione el menú desplegable **exportar** .

1. Seleccione la opción **exportar a Power BI (consulta M)** . Se descargará un archivo de consulta de Power BI en el equipo:

    ![Exportar Power BI consulta](./media/application-insights/export-powerbi-query.png)

1. Abra el archivo descargado en un editor de texto y copie la consulta en el portapapeles.

1. Abra Power BI.

1. Seleccione el menú desplegable **obtener datos** en la cinta de opciones **Inicio** y, después, seleccione **consulta en blanco**:

    ![Power BI consulta en blanco](./media/application-insights/powerbi-blank-query.png)

1. En la ventana de consulta, seleccione **editor avanzado**. Pegue la consulta del paso 5 en la ventana, seleccione **listo**y, a continuación, seleccione **Cerrar & aplicar**:

    ![Power BI consulta avanzada](./media/application-insights/powerbi-advance-query.png)

1. También puede crear gráficos y visualizaciones en Power BI para representar los comentarios recibidos en la aplicación. Y tomar decisiones y acciones basadas en datos.

    ![Gráficos y visualizaciones](./media/application-insights/powerbi-feedback.png)

## <a name="default-trace-event-context-and-dimensions"></a>Dimensiones y contexto de eventos de seguimiento predeterminados

También se agrega un conjunto de dimensiones predeterminadas a la propiedad *customDimensions* en cada evento de seguimiento. Estas dimensiones se pueden usar para identificar la aplicación y las sesiones de aplicación en las que se produjeron los eventos. Si registra datos personalizados adicionales con la función de seguimiento, también aparecerán en las dimensiones personalizadas.

| Nombre de dimensión  | Representa                                            |
|-----------------|-------------------------------------------------------|
| MS-appId        | El identificador de aplicación de la aplicación que envió el evento.     |
| MS-appName      | El nombre de aplicación de la aplicación que envió el evento.   |
| MS-appSessionId | IDENTIFICADOR de sesión de la aplicación.                           |

