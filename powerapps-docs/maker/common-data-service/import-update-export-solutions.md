---
title: Importar, actualizar y exportar soluciones | Microsoft Docs
description: Obtenga información sobre cómo importar, actualizar y exportar una solución.
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 89907e80085fe2bfcf3c38972724a0f9b55836c7
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699798"
---
# <a name="import-update-and-export-solutions"></a>Importar, actualizar y exportar soluciones 

 Puede importar soluciones manualmente mediante los pasos siguientes. Importe solo las soluciones que se obtienen de una fuente de confianza. Las personalizaciones pueden incluir código que puede enviar datos a orígenes externos. Puede importar la solución predeterminada solo a la organización desde la que la exportó, pero no a otra organización.  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.  
  
2.  En el menú de la lista de soluciones, elija **Importar**.  
  
3.  En el cuadro de diálogo **Importar soluciones**, en el paso **Seleccionar paquete de solución**, busque el archivo comprimido (.zip o .cab) que contiene la solución que desea importar. 
  
4.  Seleccione **Siguiente**.  
  
5.  Puede ver información sobre la solución antes de elegir **Importar**.  
  
6.  Puede que deba esperar unos minutos mientras se completa la importación de la solución. Si se realiza correctamente, puede ver los resultados y seleccionar **Cerrar**.  
  
 Si ha importado los cambios que requieren su publicación, debe publicar personalizaciones antes de que estén disponibles. 
  
 Si la importación no se realiza correctamente, verá un informe que muestra los errores o advertencias que se capturaron. Puede elegir **Descargar archivo de registro** para capturar los detalles sobre lo que ha provocado el error de importación. La causa más común por la que se produce un error de importación es que la solución no contiene algunos componentes necesarios de la solución.  
  
 Al descargar el archivo de registro, encontrará un archivo XML que puede abrir mediante Office Excel para ver el contenido.  
  
> [!NOTE]
>  No se puede editar un conjunto de reglas de enrutamiento activas. Por lo tanto, si va a importar una solución que incluye una regla de enrutamiento activa establecida en una organización donde la regla ya existe con el mismo identificador, se producirá un error de importación de la solución. Más información: [Crear reglas para enrutar casos automáticamente](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

## <a name="update-solutions"></a>Actualización de soluciones  
 Puede que algunas veces desee instalar una actualización en una solución administrada existente. El procedimiento es similar a la instalación de una nueva solución administrada, salvo que obtendrá algunas opciones diferentes. Si va a actualizar una solución que obtuvo de otra persona, obtendrá instrucciones del editor de soluciones sobre las opciones que debe elegir.  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.   
  
2.  En el menú de la lista de soluciones, elija **Importar**.  
  
3.  En el cuadro de diálogo **Importar soluciones**, en el paso **Seleccionar paquete de solución**, busque el archivo comprimido (.zip o .cab) que contiene la solución que desea actualizar.  
4.  Seleccione **Siguiente**.  
  
5.  Puede ver información sobre la solución antes de elegir **Siguiente**. Esta página mostrará una barra amarilla con el texto: **Este paquete de solución contiene una actualización para una solución que ya está instalada**.  
  
6.  Dispondrá de las opciones siguientes:  
  
    - **Mantener personalizaciones (recomendada)**  
  
         Al seleccionar esta opción, mantendrá todas las personalizaciones no administradas realizadas en los componentes, pero también conlleva que algunas de las actualizaciones incluidas en esta solución no surtirán efecto.  
  
    - **Sobrescribir personalizaciones**  
  
         Al seleccionar esta opción, se sobrescriben las personalizaciones no administradas realizadas anteriormente en los componentes incluidos en esta solución. Todas las actualizaciones incluidas en esta solución surtirán efecto.  
  
     Elija la opción adecuada y después seleccione **Siguiente**.  
  
7.  Puede que deba esperar unos minutos mientras se completa la importación de la solución. Si se realiza correctamente, puede ver los resultados y seleccionar **Cerrar**.  
  
 Si ha importado los cambios que requieren su publicación, debe publicar personalizaciones antes de que estén disponibles. 
  
 Los editores de soluciones pueden pedirle que exporte las personalizaciones no administradas existentes, que actualice su solución administrada con la opción para sobrescribir las personalizaciones y después que vuelva a importar las personalizaciones no administradas. Esto ayudará a garantizar que los cambios esperados se apliquen a la vez que se mantienen las personalizaciones.  
  
<a name="BKMK_ExportSolutions"></a>   

## <a name="export-solutions"></a>Exportación de soluciones  
 Es recomendable que exporte periódicamente las personalizaciones no administradas para que tenga una copia de seguridad en caso de que suceda algo. No se pueden exportar las soluciones administradas.  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.   
  
2.  En la lista, seleccione la solución que desea exportar y elija **Exportar**.  
  
3.  En el paso **Publicar personalizaciones**, se le recordará que se exporten solo las personalizaciones publicadas y tendrá la opción de **Publicar todas las personalizaciones** antes de elegir  **Siguiente**.  
  
4.  Si a la solución le faltan componentes necesarios, verá el paso **Faltan componentes necesarios**. Puede pasar por alto esta advertencia solo si piensa realizar la importación como una solución no administrada en la organización original. En caso contrario, siga las instrucciones del cuadro de diálogo para cancelar la exportación y agregar los componentes necesarios.  
  
5.  En el paso **Exportar configuración del sistema (avanzada)**, puede elegir algunas configuraciones del sistema para incluirlas en la solución. Si la solución depende de cualquiera de los grupos de configuraciones del sistema, selecciónelos y elija **Siguiente**.  
  
     Consulte **Opciones de configuración para exportar la solución** a continuación para obtener más información sobre la configuración que se incluirá con cada opción.  
  
6.  En el paso **Tipo de paquete**, debe elegir si desea exportar la solución como una solución **no administrada** o **administrada**.  
  
7.  El siguiente paso le permite elegir una solución de destino para una versión específica de Dynamics 365. Esta opción la suelen usar los ISV que deseen exportar una solución que sea compatible con una versión anterior. A menos que desee importar esta solución en una organización que no se actualiza a la misma versión que la versión de la organización que usa, acepte el valor predeterminado.   
  
8.  Elija **Exportar** para descargar el archivo de la solución.  
  
 El comportamiento exacto para descargar archivos varía entre exploradores.  

<a name="BKMK_SettingsOptionsOnSolutionExport"></a>  
 
## <a name="settings-options-for-solution-export"></a>Opciones de configuración para exportar la solución  
 En la siguiente tabla se muestran las opciones disponibles cuando se exporta una solución:  
  
|Grupo|Configuración|Descripción|  
|-----------|-------------|-----------------|  
|Numeración automática|Prefijo de la campaña|Prefijo que se usa para la numeración de la campaña.|  
|Prefijo del caso|Prefijo que se usa para todos los casos en toda la aplicación.|  
|Prefijo del contrato|Prefijo que se usa para todos los contratos en toda la aplicación.|  
|Prefijo de factura|Prefijo que se usa para todos los números de factura en toda la aplicación.|  
|Prefijo de artículo|Prefijo que se usa para todos los artículos de la aplicación.|  
|Prefijo de pedido|Prefijo que se usa para todos los pedidos en toda la aplicación.|  
|Longitud de cadena única|Número de caracteres que se anexa a los números de factura, presupuesto y pedido.|  
|Calendario|Tipo de calendario|Tipo de calendario del sistema. Se establece en Gregoriano EE.UU. de manera predeterminada|  
|Código de formato de fecha|Información sobre cómo se muestra la fecha en Dynamics 365.|  
|Separador de fecha|Carácter utilizado para separar el mes, día y año en las fechas en toda la aplicación.|  
|Duración máxima de cita|Número máximo de días que puede durar una cita.|  
|Mostrar número de semana|Información que especifica si se muestra el número de semana en el calendario de toda la aplicación.|  
|Código de formato de hora|Información que especifica cómo se muestra la hora en toda la aplicación.|  
|Código de primer día de la semana|Primer día de la semana designado en toda la aplicación.|  
|Personalización|Está habilitado el modo de aplicación|Indica si se habilita la carga de la aplicación en una ventana del explorador que no tiene barras de dirección, herramientas y menús habilitadas.|  
|Seguimiento de correo electrónico|Permitir envío de mensajes de correo electrónico con direcciones sin resolver|Indica si los usuarios pueden enviar correo electrónico a elementos sin resolver (los elementos deben seguir teniendo una dirección de correo electrónico).|  
|Omitir mensajes de correo electrónico internos|Indica si es necesario realizar un seguimiento del correo electrónico entrante enviado por los usuarios o las colas de la aplicación.|  
|Número de seguimiento máximo|Número de seguimiento máximo antes de que se realice el reciclaje.|  
|Representar marco seguro para correo electrónico|Marca para representar el cuerpo del correo electrónico en el formulario web de un IFRAME con el atributo seguridad="restringida" establecido. Se trata de seguridad adicional, pero puede generar una solicitud de credenciales.|  
|Prefijo de seguimiento|Lista de historial de los prefijos de token de seguimiento.|  
|Seguimiento de base del token|Número base que se usa para proporcionar identificadores de token de seguimiento diferentes a usuarios que pertenecen a distintas implementaciones.|  
|Seguimiento de dígitos del token|Número de dígitos utilizados para representar un identificador de token de seguimiento.|  
|General|Bloquear datos adjuntos|Evitar la carga o descarga de determinados tipos de datos adjuntos que se consideran peligrosos.|  
|Código de formato de la divisa|Información sobre cómo se colocan los símbolos de la divisa en toda la aplicación.|  
|Símbolo de divisa|Símbolo de divisa|  
|Pedido de visualización de nombre completo|Pedido en el que se mostrarán los nombres en toda la aplicación.|  
|Presencia habilitada|Información sobre si está habilitada la presencia de mensajería instantánea.|  
|Formato negativo|Información que especifica cómo se muestran los números negativos en toda la aplicación.|  
|Formato de número|Especificación de cómo se muestran los números en toda la aplicación.|  
|Precisión decimal de precios|Número de posiciones decimales que se pueden usar para los precios.|  
|Compartir con propietario anterior tras asignación|Información que especifica si se comparte con el propietario anterior tras la asignación.|  
|Marketing|Permitir creación de respuesta automática|Indica si se permite crear una respuesta automática.|  
|Permitir cancelación automática de suscripciones|Indica si se permite la cancelación automática de suscripciones.|  
|Permitir confirmación de cancelación automática de suscripciones|Indica si se permite enviar un correo electrónico de confirmación de cancelación automática de suscripciones.|  
|Permitir ejecución de mensajes de correo electrónico de marketing|Indica si se permite la ejecución de correos electrónicos de marketing.|  
| Sincronización con Outlook|Permitir sincronización de libreta de direcciones|Indica si se permite la sincronización de la libreta de direcciones en segundo plano con Microsoft Office Outlook.|  
|Permitir sincronización programada sin conexión|Indica si se permite la sincronización sin conexión en segundo plano con Outlook.|  
|Permitir sincronización programada|Indica si se permiten las sincronizaciones programadas con Outlook.|  
|Frecuencia de sondeo de envío de correos electrónicos|Frecuencia de sondeo normal usada para enviar correo electrónico en Outlook.|  
|Frecuencia mínima de sincronización de direcciones|Frecuencia de sondeo normal usada para la sincronización de la libreta de direcciones en Outlook.|  
|Frecuencia mínima de sincronización sin conexión|Frecuencia de sondeo normal usada para la sincronización sin conexión en segundo plano con Outlook.|  
|Frecuencia mínima de sincronización|Tiempo mínimo permitido entre [!INCLUDEsincronizaciones con Outlook programadas.|  
|Máximo de ciclos de etiquetado automático|Número máximo de ciclos de sondeo dinámicos ejecutados para el etiquetado automático de correo electrónico cuando se recibe un correo electrónico nuevo.|  
|Intervalo de etiquetado automático|Frecuencia de sondeo normal usada para el etiquetado automático de correo electrónico en Outlook.|  
|Configuración ISV|Configuración de apariencia del calendario de servicios|Puede definir los estilos visuales de los calendarios de servicios.

Más información: [Configuración de la apariencia del calendario de servicios](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration)|

  
## <a name="next-steps"></a>Pasos siguientes

[Distribución de soluciones y revisiones](use-segmented-solutions-patches-simplify-updates.md)