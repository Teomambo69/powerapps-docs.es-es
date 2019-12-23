---
title: Controles adicionales para Dynamics 365 para teléfonos y tabletas | MicrosoftDocs
description: Una lista de controles disponibles para su uso con Dynamics 365 para teléfonos y tabletas
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 7920ef78-2540-48ad-ba25-9ce9cb995ed1
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d2883f0912f9708acf8c24b5ec32996cb96ad3c6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2863623"
---
# <a name="additional-controls-for-dynamics-365-for-phones-and-tablets"></a>Controles adicionales para Dynamics 365 para teléfonos y tabletas 

 Puede usar un completo conjunto de controles adicionales para crear una experiencia más táctil en Dynamics 365 para teléfonos y tabletas. Esto incluye los controles deslizantes, modificadores, reproductor multimedia, máscaras de entrada, calendario, y otros controles.  

 
> [!NOTE]
>  Puede usar estos controles adicionales solo con las aplicaciones móviles. No se admiten en la aplicación web.  
  
 Para usar estos controles en el editor de formularios:  
  
1.  Haga doble clic en el campo o la lista a la que desea agregar el control.  
  
2.  Haga clic en la pestaña **Controles**.  
  
3.  Haga clic en **Agregar control**.  
  
4.  Seleccione el control que desee y, a continuación, haga clic en **Agregar**.  
  
    > [!NOTE]
    >  Hay diferentes controles disponibles según el tipo de campo o lista. Por ejemplo, los controles de control deslizante pueden estar disponibles solo para campos numéricos o de divisa, y el control de calendario solo está disponible para listas.  
  
5.  Seleccione los dispositivos en los que desea que aparezca el control (teléfono, tableta, o ambos). Los controles no están disponibles para campos de encabezado de teléfono.  
  
6.  Configure los valores para cada propiedad.  
  
7.  Haga clic en **Aceptar** cuando haya terminado de configurar el control.  
  
 A continuación se ofrecen descripciones de cada control que puede usar en formularios de Dynamics 365 para teléfonos y tabletas.  
  
## <a name="calendar-control"></a>Control del calendario  
 Use este control para configurar formularios de modo que aparezcan como vista de calendario en Dynamics 365 para teléfonos y tabletas. También puede usar este control para reemplazar paneles, listas, o cuadrículas de entidad para teléfonos y tabletas.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Fecha de inicio|Defina la fecha y hora del comienzo del elemento a visualizar en la vista de calendario. Los valores disponibles son cualquiera de las columnas de esta vista de tipo fecha.|  
|Fecha de finalización|Defina la fecha y hora del final del elemento a visualizar en la vista de calendario. Los valores disponibles son cualquiera de las columnas de esta vista de tipo fecha.|  
|Duración|Duración en minutos. Si especifica un valor para Fecha de finalización, se omite Duración.|  
|Descripción|Este es el pie de imagen que desea ver para elementos del calendario.|  
  
 La duración mínima que aparece en el calendario es de 30 minutos. Los elementos que tengan menos una duración de menos de 30 minutos aparecerán con una duración de 30 minutos.  
  
 El control calendario admite todos los comportamientos de fecha (Local del usuario, Solo fecha e Independiente de la zona horaria).  
  
## <a name="timeline-control"></a>Control de escala de tiempo  
 Proporcione una escala de tiempo de artículos de noticias y tweets de Twitter recientes y relevantes para una cuenta.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|CC_Timeline_Title|Propiedad a asignar para el título de cada elemento de la escala de tiempo.|  
|CC_Timeline_Title_Desc|Descripción para el título.|  
|CC_Timeline_Label1|Campo que se mostrará bajo el título del elemento de la escala de tiempo.|  
|CC_Timeline_Label1_Desc|Descripción para Etiqueta 1.|  
|CC_Timeline_Label2|Campo que se mostrará después de la Etiqueta 1.|  
|CC_Timeline_Label2_Desc|Descripción para Etiqueta 2.|  
|CC_Timeline_Label3|Campo que se mostrará después de la Etiqueta 2.|  
|CC_Timeline_Label3_Desc|Descripción para Etiqueta 3.|  
|CC_Timeline_Label4|Campo que se mostrará después de la Etiqueta 3.|  
|CC_Timeline_Label4_Desc|Descripción para Etiqueta 4.|  
|CC_Timeline_Label5|Campo que se mostrará después de la Etiqueta 4.|  
|CC_Timeline_Label5_Desc|Descripción para Etiqueta 5.|  
|CC_Timeline_Timestamp|Campo que se usará para ordenar la escala de tiempo en orden cronológico inverso.|  
|CC_Timeline_Timestamp_Desc|Descripción para marca de tiempo.|  
|CC_Timeline_Group|Campo a asignar para agrupar la escala de tiempo.|  
|CC_Timeline_Group_Desc|Descripción para el campo Grupo.|  
|CC_Timeline_GroupOrder|El orden en el grupo al que pertenece el elemento en relación con otros grupos (asigne valores 1, 2, 3, etc. para los grupos que se mostrarán). El grupo se mostrará en valor ascendente de los valores de grupo asignados.|  
|CC_Timeline_GroupOrder_Desc|Descripción para el campo Orden de grupo.|  
|CC_Timeline_URL|Campo Dirección URL para asignar para mostrar la dirección URL de elemento de la escala de tiempo.|  
|CC_Timeline_URL_Desc|Descripción para el campo Dirección URL.|  
|CC_Timeline_ThumbnailURL|Campo para asignar para la miniatura de imagen/icono que se mostrará para cada elemento.|  
|CC_Timeline_ThumbnailURL_Desc|Descripción del campo `ThumbnailURL`.|  
|CC_Timeline_Filter|Campo a asignar para filtro de la escala de tiempo.|  
|CC_Timeline_Filter_Desc|Descripción para Filtro.|  
|CC_Timeline_Footer|Recurso web para mostrar como pie de página de la escala de tiempo.|  
|CC_Timeline_Footer_Desc|Descripción para el campo Pie de página.|  
  
## <a name="linear-slider"></a>Control deslizante lineal  
 El control deslizante lineal permite a los usuarios especificar valores numéricos arrastrando un control deslizante y también proporciona una opción para escribir la cantidad. El control deslizante permite introducir y ver solo números enteros. Use este control para cualquier campo numérico o de divisa.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Máx.|Establezca el valor máximo que se muestra en el control deslizante.|  
|Mín.|Establezca el valor mínimo que se muestra en el control deslizante.|  
|valor|El valor que se muestra en el control deslizante.|  
|Paso|Establezca la cantidad que se debe sumar o restar del valor actual al entrar datos con este control.|  
  
## <a name="option-sets"></a>Conjuntos de opciones  
 El control de conjunto de opciones muestra un conjunto de opciones para que los usuarios elijan cuando se escriben datos. Use este control para conjuntos de opciones con dos o tres opciones solo.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Campo|Muestra el campo al que está asignado el control.|  
  
## <a name="flip-switch"></a>Cambio de volteo  
 El cambio de volteo como un interruptor de encendido/apagado, que proporciona una selección entre dos valores.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Campo|Muestra el campo al que está asignado el control.|  
  
## <a name="star-rating"></a>Clasificación de estrellas  
 Use la clasificación de estrellas para proporcionar una representación visual de una clasificación. El número máximo de estrellas que puede establecer es cinco. Puede usar este control para números enteros solo; no puede aceptar valores decimales.  
  
> [!NOTE]
>  Asegúrese de seleccionar la opción **Ocultar en la Web** para este control.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Máx.|Seleccione el número máximo de estrellas para el control de la lista desplegable.|  
  
## <a name="radial-knob"></a>Mando radial  
 El mando radial proporciona una forma de que los usuarios especifiquen datos deslizando el mando, y se muestra en la pantalla como un círculo. El control de mando radial permite introducir y ver solo números enteros. Use este control para cualquier campo numérico o de divisa. Puede tocar para cambiar el valor, o puede usar el teclado numérico para poner el enfoque en el número y editarlo.  
  
> [!NOTE]
>  Este control no se admite en dispositivos Android 4.2 y 4.3. Afecta a la experiencia de desplazamiento en esas versiones.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Máx.|Establezca el valor máximo que se debe mostrar en el medidor.|  
|Mín.|Establezca el valor mínimo que se debe mostrar en el medidor.|  
|valor|Obtenga o establezca el valor que se debe mostrar en el medidor.|  
|Paso|Establezca la cantidad que se debe sumar o restar del valor actual al entrar datos con este control.|  
  
## <a name="website-preview"></a>Vista previa del sitio web  
 Use el control de vista previa de sitio web para asignar un campo de dirección URL y mostrar una vista previa del sitio web.  
  
> [!IMPORTANT]
>  Al habilitar este control, usted consiente permitir que los usuarios compartan cierta información identificable de dispositivos con un sistema externo. Los datos importados de sistemas externos en la aplicación de Power Apps o aplicaciones de Dynamics 365 como Dynamics 365 Sales o Dynamics 365 Customer Service están sujetas a nuestra declaración de privacidad en [Privacidad y cookies de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=521839).  
>   
>  [Avisos de privacidad](use-the-form-editor-legacy.md#BKMK_PrivacyNotices)  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Campo|Muestra el campo al que está asignado el control.|  
  
## <a name="bullet-graph"></a>Gráfico de viñetas  
 El control de gráficos de viñetas muestra una sola medida clave con una medida comparativa e intervalos cualitativos para señalar inmediatamente si la medida es buena, malo u otro estado. Use este control en paneles para cualquier campo numérico o de divisa. Por ejemplo, puede asignar el valor a ingresos reales y el destino a los ingresos estimados para visualizar ingresos reales frente a estimados.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Máx.|Establezca el valor máximo que se muestra en el gráfico.|  
|Mín.|Establezca el valor mínimo que se muestra en el gráfico.|  
|Correcto|Establezca un valor que sea considera bueno para la medida (opcional).|  
|Incorrecto|Establezca un valor que sea considera malo para la medida (opcional).|  
|valor|Muestra el campo al que está asignado el control.|  
|Destino|Asigne esto al campo con el que desee comparar el valor. Por ejemplo, si se asigna **Valor** a **Ingresos reales**, puede asignar **Destino** a **Ingresos estimados**, o puede proporcionar un valor estático.|  
  
## <a name="pen-control"></a>Control de lápiz  
 Use el control de lápiz para capturar entrada escrita como firmas.  
  
> [!NOTE]
>  El mínimo requerido **Longitud máxima** especificado para el campo al que se asigna este control es 15000 horas.  
>   
>  Asegúrese de seleccionar la opción **Ocultar en la Web** para este control.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|PenMode|Especifique **PenMode!Draw**, **PenMode!Erase** o **PenMode!Select** para determinar lo que sucede cuando un usuario arrastra un dispositivo señalador en un control de lápiz.|  
  
## <a name="auto-complete"></a>Autocompletar  
 El control de Autocompletar filtra una lista de elementos a medida que escribe y permite seleccionar un valor de la lista desplegable. Por ejemplo, puede usar este control para permitir que los usuarios elijan de una lista desplegable de estados o de países y regiones. Este control se asigna a un campo de tipo **Línea de texto única**.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Campo|Muestra el campo al que está asignado el control.|  
|Origen|Establezca el origen de datos (Opciones agrupadas, Conjunto de opciones o Vista).|  
|Conjunto de opciones|Seleccione el conjunto de opciones para este campo.|  
|Vista|Seleccione la entidad y la vista para este campo.|  
|Campo|Seleccione el campo de la entidad principal de la vista que desee usar como origen de datos.|  
  
## <a name="multimedia"></a>Multimedia  
 Puede incrustar vídeos para proporcionar una experiencia más rica a los clientes para el personal comercial y sobre el terreno. Use este control para asignar a un campo de dirección URL que contiene el vínculo de audio o vídeo que se reproducirá en el control.  
  
> [!NOTE]
>  Este control se admite en Android versiones 4.4 y posteriores.  
>   
>  Los vídeos de YouTube no son compatibles actualmente en teléfonos y tabletas con Windows 8 y Windows 8.1. En Windows 10, solo se admiten actualmente vídeos HTTPS, incluidos los de YouTube.  
  
 Tipos de medios compatibles:  
  
-   Archivos MP4 en streaming  
  
-   Vídeos de YouTube  
  
-   Medios de Azure  
  
-   Secuencias de audio  
  
 [Aviso de privacidad](use-the-form-editor-legacy.md#BKMK_PrivacyNotices)  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Medios|Especifique la dirección URL de los medios que se reproducirán en este control.|  
  
## <a name="number-input"></a>Entrada numérica  
 Use el control de entrada de número para ayudar a los usuarios a escribir datos rápidamente. Los usuarios solo tienen que pulsar e los botones más y menos para cambiar un valor numérico en los incrementos que configure. Use este control para cualquier campo numérico o de divisa. Los usuarios también pueden escribir un número directamente en el campo. Este campo se admite únicamente en modo de edición.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Paso|Establezca la cantidad que se debe sumar o restar del valor actual al entrar datos con este control.|  
|Campo|Muestra el campo al que está asignado el control.|  
  
## <a name="input-mask"></a>Máscara de entrada  
 Con el control de máscara de entrada, se establece el formato para un campo como número de teléfono o tarjeta de crédito para evitar especificar datos no válidos. Por ejemplo, si desea que los usuarios introduzcan un número de teléfono de Estados Unidos en el formato +1-222-555-1011, use la máscara de entrada +1-000-000-0000.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Máscara|Introduzca la máscara que se debe usar para validar datos cuando los usuarios los introduzcan. Puede usar una combinación de los caracteres siguientes para la máscara:<br /><br /> 0 – dígito<br /><br /> 9 – dígito o espacio<br /><br /> # – dígito, signo o espacio<br /><br /> L – letra<br /><br /> I - letra o espacio<br /><br /> A – alfanumérico<br /><br /> A – alfanumérica o espacio<br /><br /> < - convierte los caracteres que siguen a minúscula<br /><br /> > - convierte los caracteres que siguen a mayúscula<br /><br /> &#124; – Deshabilita la conversión de mayúsculas y minúsculas<br /><br /> \ – Aplica un carácter de escape a cualquier carácter, convirtiéndolo en un literal<br /><br /> Todos los demás - literales|  
|Campo|Muestra el campo al que está asignado el control.|  
  
## <a name="linear-gauge"></a>Medidor lineal  
 El medidor lineal permite a los usuarios especificar valores numéricos arrastrando un control deslizante en lugar de escribir la cantidad exacta. El control deslizante permite introducir y ver solo números enteros. Use este control para cualquier campo numérico y de divisa.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Máx.|Establezca el valor máximo que se debe mostrar en el medidor.|  
|Mín.|Establezca el valor mínimo que se debe mostrar en el medidor.|  
|valor|Obtenga o establezca el valor que se debe mostrar en el medidor.|  
|Paso|Establezca la cantidad que se debe sumar o restar del valor actual al entrar datos con este control.|  
  
## <a name="arc-knob"></a>Mando esférico  
 El mando esférico proporciona una forma de que los usuarios especifiquen datos deslizando el mando, y aparece en la pantalla como una esfera. El control de mando esférico permite introducir y ver solo números enteros. Use este control para cualquier campo numérico y de divisa. Puede tocar para cambiar el valor, también puede poner el enfoque en el número y editarlo usando el teclado numérico.  
  
> [!NOTE]
> Este control no se admite en dispositivos Android 4.2 y 4.3. Afecta a la experiencia de desplazamiento en esas versiones.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Máx.|Establezca el valor máximo que se debe mostrar en el medidor.|  
|Mín.|Establezca el valor mínimo que se debe mostrar en el medidor.|  
|valor|Obtenga o establezca el valor que se debe mostrar en el medidor.|  
|Paso|Establezca la cantidad que se debe sumar o restar del valor actual al entrar datos con este control.|  
  
## <a name="next-steps"></a>Pasos siguientes
[Tutorial: Usar controles personalizados para visualizaciones de datos](use-custom-controls-data-visualizations.md)
