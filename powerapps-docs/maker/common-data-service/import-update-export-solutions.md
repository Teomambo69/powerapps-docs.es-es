---
title: Importar, actualizar y exportar soluciones | MicrosoftDocs
description: Obtener información sobre cómo importar, actualizar y exportar una solución en Power Apps
ms.custom: ''
ms.date: 09/30/2019
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
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d726860afa8aa2f3cdbb60ede7c549df4da424d2
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884738"
---
# <a name="import-update-and-export-solutions"></a>Importar, actualizar y exportar soluciones 

 Puede importar soluciones manualmente usando los pasos siguientes. Importe únicamente las soluciones que se obtengan de una fuente de confianza. Es posible que las personalizaciones incluyan un código que puede enviar datos a orígenes externos.   
  
1.  Seleccione **Soluciones** en la barra de navegación izquierda.  
  
2.  En el menún de la lista de soluciones, seleccione **Importar**.  

    > [!div class="mx-imgBorder"]  
    > ![Importar solución](media/solution-import.png "Importar solución") 
  
3.  En el cuadro de diálogo **Importar solución**, en el paso **Seleccionar paquete de solución**, seleccione **Elegir archivo** y busque el archivo comprimido (.zip o .cab) que contiene la solución que desea importar. 
  
4.  Seleccione **Siguiente**.  
  
5.  Ver información acerca de la solución. Seleccione **importar**.  
  
6. Es posible que tenga que esperar unos momentos mientras la importación se completa. Vea los resultados y, a continuación, seleccione **Cerrar**.  
  
 Si importó cambios que requieren publicación, debe publicar las personalizaciones antes de que estén disponibles. 
  
 Si la importación no es correcta, verá un informe que mostrará los errores o advertencias capturados. Seleccione **Descargar archivo de registro** para capturar detalles sobre la causa del error de importación. La causa más común para que una importación falle es que la solución no contenía algunos componentes requeridos.  
  
 Cuando descargue el archivo de registro, encontrará un archivo XML que puede abrir mediante Office Excel para ver el contenido.  
  
> [!NOTE]
>  No se puede editar un conjunto de reglas de enrutamiento activo. Por tanto, si importa una solución que incluye un conjunto activo de reglas de enrutamiento a un entorno donde la regla ya existe con el mismo identificador, la importación generará un error. Más información: [Crear reglas para enrutar casos automáticamente](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

## <a name="update-solutions"></a>Actualizar soluciones  
 Hay ocasiones en las que podría desear instalar una actualización de una solución administrada existente. El proceso es similar a instalar una nueva solución administrada, salvo en que obtendrá algunas opciones diferentes. Si va a actualizar una solución que ha obtenido de otra persona, debe obtener instrucciones del editor de soluciones sobre las opciones que debe elegir.  
  
1.  Seleccione **Soluciones** en la barra de navegación izquierda.
  
2.  En el menún de la lista de soluciones, seleccione **Importar**.  
  
3.  En el cuadro de diálogo **Importar solución**, en el paso **Seleccionar paquete de solución**, seleccione **Elegir archivo** y busque el archivo comprimido (.zip o .cab) que contiene la solución que desea actualizar.

4.  Seleccione **Siguiente**.  
  
5.  Vea la información de la solución y seleccione **Siguiente**. Esta página mostrará una barra amarilla que indica que **Este paquete de solución contiene una actualización para una solución que ya está instalada**.  
  
6.  Tendrá las siguientes opciones:  
  
    - **Mantener personalizaciones (recomendado)**  
  
         Al seleccionar esta opción se mantendrán las personalizaciones no administradas realizadas en los componentes, pero algunas de las actualizaciones incluidas en esta solución no surtirán efecto.  
  
    - **Sobrescribir personalizaciones**  
  
         Al seleccionar esta opción se sobrescriben las personalizaciones no administradas realizadas anteriormente en los componentes incluidos en esta solución. Todas las actualizaciones incluidas en esta solución surtirán efecto.  
  
     Elija la opción correcta y seleccione **Siguiente**.  
  
7.  Es posible que tenga que esperar unos momentos mientras la importación se completa. Vea los resultados y, a continuación, seleccione **Cerrar**.  
  
 Si importó cambios que requieren publicación, debe publicar las personalizaciones antes de que estén disponibles. 
  
 Los editores de soluciones pueden pedirle que exporte las personalizaciones no administradas existentes, que actualice su solución administrada mediante la opción para sobrescribir personalizaciones y que vuelva a importar las personalizaciones no administradas. Esto le permitirá asegurarse de que se han aplicado los cambios que están esperando mientras se mantienen las personalizaciones.  
  
<a name="BKMK_ExportSolutions"></a>   

## <a name="export-solutions"></a>Exportar soluciones  
 Se recomienda crear una solución no administrada para usar para exportar las personalizaciones. A continuación exporte las personalizaciones periódicamente para tener una copia de seguridad en caso de que surjan problemas. No puede exportar soluciones administradas. Puede exportar soluciones desde Power Apps o puede exportar mediante la experiencia clásica. 
 
> [!IMPORTANT]
> Exportar la solución predeterminada no se admite. 

### <a name="export-from-power-apps"></a>Exportar de Power Apps
  
1.  Seleccione **Soluciones** en la barra de navegación izquierda.   
  
2.  En la lista, seleccione la solución que desea exportar y luego seleccione **Exportar**. 

3.  Seleccione el tipo de paquete **Como no administrado** o **Como administrado**. Esto iniciará la exportación, que puede tardar varios minutos en completarse. Una vez finalizada, el archivo .zip de exportación está disponible en la carpeta de descarga especificada por el explorador web.

    > [!div class="mx-imgBorder"]  
    > ![Exportar solución](media/solution-export.png "Exportar solución") 

### <a name="export-from-the-classic-experience"></a>Exportación desde la experiencia clásica

1.  Seleccione **Soluciones** desde la barra de navegación izquierda y después seleccione **Cambiar a clásica**. 
  
2.  En la lista, seleccione la solución que desea exportar y luego seleccione **Exportar**. 
  
3.  En el paso **Publicar personalizaciones** se le recordará que solo se exportan las personalizaciones publicadas y podrá utilizar la opción **Publicar todas las personalizaciones** antes de seleccionar **Siguiente**.  
  
4.  Si la solución contiene componentes necesarios que faltan verá el paso **Faltan componentes necesarios**. Puede ignorar esta advertencia solo si tiene previsto volver a realizar la importación como una solución no administrada en el entorno original. De lo contrario, siga las instrucciones del diálogo para cancelar la exportación y agregar los componentes necesarios.  
  
5.  En el paso **Exportar configuración del sistema (avanzado)** puede elegir determinadas configuraciones del sistema para incluir en la solución. Si la solución depende de grupos de configuración del sistema, selecciónelos y elija **Siguiente**.  
  
     Consulte **Opciones de configuración para la exportación de la solución** a continuación para obtener más información sobre la configuración que se incluirá con cada opción.  
  
6.  En el paso **Tipo de paquete**, es necesario elegir si se debe exportar la solución como una solución **No administrada** o **Administrada**.  
  
7.  El siguiente paso le permite elegir una solución de destino para una versión determinada. Esta opción suelen usarla los ISV que desean exportar una solución que sea compatible con una versión anterior. A menos que pretenda importar esta solución en un entorno que no esté actualizado a la misma versión que la versión del entorno que usted está usando, acepte la opción predeterminada.   
  
8.  Seleccone **Exportar** para descargar el archivo de la solución.  
  
 El comportamiento exacto para descargar archivos varía entre exploradores web.  

<a name="BKMK_SettingsOptionsOnSolutionExport"></a>  
 
## <a name="settings-options-for-solution-export"></a>Opciones de configuración para la exportación de la solución  
 Si exporta la solución desde Power Apps, ignore esta sección. La siguiente tabla muestra las opciones disponibles cuando se exporta una solución desde la experiencia clásica.  
  
|Grupo|Configuración|Descripción|  
|-----------|-------------|-----------------|  
|Numeración automática|Prefijo de la campaña|Prefijo usado para la numeración de campañas.|  
|Prefijo del caso|Prefijo para usar en todos los casos en la aplicación.|  
|Prefijo del contrato|Prefijo para usar en todos los contratos en la aplicación.|  
|Prefijo de factura|Prefijo para usar en todos los números de factura en la aplicación.|  
|Prefijo del artículo|Prefijo para usar en todos los artículos en la aplicación.|  
|Prefijo de pedido|Prefijo que se debe usar en todos los pedidos en la aplicación.|  
|Longitud de cadena única|Número de caracteres anexados a los números de factura, oferta y pedido.|  
|Calendario|Tipo de calendario|Tipo de calendario para el sistema. Establecido en Gregoriano EE.UU. de manera predeterminada|  
|Código de formato de fecha|Especifica cómo se muestra la fecha en Common Data Service|  
|Separador de fecha|Carácter usado para separar el día, el mes y el año en las fechas en la aplicación.|  
|Duración máxima de la cita|Número máximo de días que puede durar una cita.|  
|Mostrar número de semana|Especifica si se muestra el número de semana en el calendario en la aplicación.|  
|Código de formato de hora|Especifica cómo se muestra la hora en la aplicación.|  
|Código de primer día de la semana|Primer día de la semana designado en la aplicación.|  
|Personalización|Está habilitado el modo de aplicación|Indica si está habilitada la carga de una aplicación en una ventana de explorador que no tenga barras de menú, de herramientas ni de direcciones.|  
|Seguimiento de correo electrónico|Permitir envío de mensajes de correo electrónico con direcciones sin resolver|Indica si se permite a los usuarios enviar correo electrónico a los grupos sin resolver (los grupos deben seguir teniendo una dirección de correo electrónico).|  
|Omitir mensajes de correo electrónico internos|Indica si se debe seguir el correo electrónico entrante enviado por colas o usuarios de la aplicación.|  
|Número de seguimiento máximo|Número de seguimiento máximo antes de reciclar.|  
|Representar marco seguro para correo electrónico|Marque para representar el cuerpo de correo electrónico del formulario web en un IFRAME con el atributo de security='restricted' definido. Aunque es seguridad adicional, puede causar una solicitud de credenciales.|  
|Prefijo de seguimiento|Lista de historial de prefijos de tokens de seguimiento.|  
|Seguimiento de base del token|Número base usado para proporcionar identificadores de tokens de seguimiento distintos a usuarios que pertenecen a implementaciones diferentes.|  
|Seguimiento de dígitos del token|Número de dígitos usados para representar un identificador de token de seguimiento.|  
|General|Bloquear datos adjuntos|Evita la carga o descarga de determinados tipos de datos adjuntos que se consideran peligrosos.|  
|Código de formato de la divisa|Especifica la colocación de los símbolos de divisa en la aplicación.|  
|Símbolo de moneda|Símbolo de moneda|  
|Pedido de visualización de nombre completo|Orden en que se deben mostrar los nombres en la aplicación.|  
|Presencia habilitada|Información sobre si está habilitada la presencia de MI.|  
|Formato negativo|Información que especifica cómo aparecen los números negativos en la aplicación.|  
|Formato de número|Especifica cómo se muestran los números en la aplicación.|  
|Precisión decimal de precios|Número de posiciones decimales que se pueden usar para los precios.|  
|Compartir con propietario anterior tras asignación|Especifica si se comparte con el propietario anterior tras la asignación.|  
|Marketing|Permitir creación de respuesta automática|Indica si se permite la creación de respuestas automáticas|  
|Permitir cancelación automática de suscripciones|Indica si se permite la cancelación automática de suscripciones.|  
|Permitir confirmación de cancelación automática de suscripciones|Indica si se permite el envío por correo electrónico de la confirmación de cancelación de una suscripción.|  
|Permitir ejecución de mensajes de correo electrónico de marketing|Indica si se permite la ejecución de mensajes de correo electrónico de marketing.|  
| Sincronización con Outlook|Permitir sincronización de libreta de direcciones|Indica si se permite la sincronización de la libreta de direcciones en segundo plano en Microsoft Office Outlook.|  
|Permitir sincronización programada sin conexión|Indica si se permite la sincronización sin conexión en segundo plano en Outlook.|  
|Permitir sincronización programada|Indica si se permiten sincronizaciones programadas de Outlook.|  
|Frecuencia de sondeo de envío de correos electrónicos|Frecuencia normal de sondeo usada para el envío de correo electrónico en Outlook.|  
|Frecuencia mínima de sincronización de direcciones|Frecuencia normal de sondeo usada para la sincronización de la libreta de direcciones en Outlook.|  
|Frecuencia mínima de sincronización sin conexión|Frecuencia normal de sondeo usada para la sincronización sin conexión en segundo plano en Outlook.|  
|Frecuencia mínima de sincronización|Tiempo mínimo permitido entre sincronizaciones de Outlook programadas.|  
|Máximo de ciclos de etiquetado automático|Máximo de ciclos de sondeo dinámicos ejecutados para el etiquetado automático de correo electrónico cuando se recibe un mensaje nuevo.|  
|Intervalo de etiquetado automático|Frecuencia normal de sondeo usada para el etiquetado automático de correo electrónico en Outlook.|  
|Configuración ISV|Configuración de apariencia del calendario de servicios|Puede definir estilos visuales para calendarios de servicio.

Más información: [Configuración de la apariencia del calendario de servicios](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration)|

  
## <a name="next-steps"></a>Pasos siguientes

[Distribuir soluciones y revisiones](use-segmented-solutions-patches-simplify-updates.md)
