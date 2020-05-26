---
title: Actualizar la solución Supervisión y respuesta ante emergencias del gobierno regional | Microsoft Docs
description: Proporciona instrucciones detalladas para que los administradores de TI regionales actualicen la solución de Supervisión y respuesta ante emergencias del gobierno regional para su organización.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: f50cf7a7ae839cd22632bb4f5e1281ad585eb2a6
ms.sourcegitcommit: 2e186321d124dd6c0a4b51df5e8bc94a83ccf1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3342223"
---
# <a name="upgrade-the-regional-governmentemergency-response-and-monitoring-solution"></a>Actualizar la solución Supervisión y respuesta ante emergencias del gobierno regional

Realice los pasos de este artículo para actualizar su instalación *existente* de la solución de Supervisión y respuesta ante emergencias del gobierno regional a la última versión.

Si está instalando esta solución por primera vez, consulte [Implementar la solución](deploy.md).

## <a name="prerequisites"></a>Requisitos previos

- Asegúrese de tener las credenciales de administrador global y los detalles del entorno donde la solución Supervisión y respuesta ante emergencias del gobierno regional está implementada actualmente.

-   Asegúrese de que todos los usuarios estén desconectados de su entorno antes de actualizar. Es posible que tenga que planificar el proceso de actualización en un momento en que haya obstrucciones mínimas para sus usuarios.   

## <a name="step-1-download-the-upgrade-deployment-package"></a>Paso 1: Descargar el paquete de implementación de actualización

Obtenga el último paquete de implementación (.zip) de <https://aka.ms/rer-solution>. Es el mismo paquete de implementación que el que descargó durante el nuevo paso de implementación.

**IMPORTANTE**: Antes de extraer el archivo .zip, asegúrese de desbloquearlo.

1.  Haga clic con el botón secundario en el archivo .zip y seleccione **Propiedades**.

2.  En el cuadro de diálogo de propiedades, seleccione **Desbloquear** y luego seleccione **Aplicar** seguido de **Aceptar**.

Después de desbloquear el archivo, extraiga el archivo .zip; verá lo siguiente en la carpeta extraída:

Al extraer el archivo .zip, verá lo siguiente en la carpeta extraída:

|**Carpeta**  |**Descripción**  |
|---------|---------|
|**Paquete**     |  La carpeta contiene la herramienta Package Deployer y el paquete que importará más adelante para configurar la solución en su entorno.       |
|**Power BIPlantilla**     | Contiene el Archivo de plantilla de informe Power BI (.pbit) que usará para configurar los informes. Más información: [Paso 3: Publicar el último panel de Power BI](#step-3-publish-the-latest-power-bi-dashboard)        |
|**SampleData**     |   Contiene los archivos de datos maestros de muestra (.xlsx) que puede usar para importar datos de ejemplo.       |

## <a name="step-2-install-the-upgrade-package"></a>Paso 2: Instalar el paquete de actualización

Instale el paquete de actualización en el **mismo entorno** en el que tiene instalada la solución existente. Puede instalar el paquete de actualización de una de las siguientes 3 maneras, tal y como lo hizo al implementar la solución por **primera vez**.

- Microsoft AppSource (solo para clientes de Power Apps gobierno de EE. UU.). Ver [Opción A: Instalar la aplicación desde Microsoft AppSource (Clientes del gobierno de EE. UU.)](deploy.md#option-a-install-the-app-from-microsoft-appsource-us-govt-customers) en el tema de implementación

- Microsoft AppSource (para clientes con la versión comercial de Power Apps). Ver [Opción B: Instalar la aplicación desde Microsoft AppSource](deploy.md#option-b-install-the-app-from-microsoft-appsource) en el tema de implementación

- Paquete de implementación que descargó anteriormente. Ver [Opción C: instalar la aplicación desde el paquete de implementación](deploy.md#option-c-install-the-app-from-the-deployment-package) en el tema de implementación

## <a name="step-3-publish-the-latest-power-bi-dashboard"></a>Paso 3: Publicar el último panel de Power BI

Use el archivo .pbit en el paquete de actualización para configurar y publicar el último panel de Power BI. 

Los pasos para usar el archivo .pbit son los mismos que para la implementación original; asegúrese de utilizar el mismo espacio de trabajo para sobrescribir el panel de Power BI existente si desea preservar la dirección URL del informe de Power BI que se utiliza para incrustarlo en el portal de Power Apps. 

Más información: [Paso 5: Configurar y publicar el panel de Power BI](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard)

## <a name="step-4-verify-the-power-bi-report-url-in-your-portal"></a>Paso 4: Comprobar la dirección URL del informe de Power BI en su portal

Este paso es obligatorio solo si su URL del informe de Power BI ha cambiado en el paso anterior debido a que publicó el panel de información en un nuevo espacio de trabajo. Compruebe la configuración del sitio de **Ruta de PowerBI** en su portal y actualice el valor con la última dirección URL del informe de Power BI.

Para conocer los pasos detallados, consulte [Insertar informe de Power BI en el portal](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#the-process-1).

Asegúrese de reiniciar el portal para que los cambios surjan efecto. Más información: [Reiniciar el portal](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#restart-the-portal)

## <a name="step-5-verify-the-send-invitation-and-send-password-reset-to-contact-processes"></a>Paso 5: Comprobar los procesos Enviar invitación y Enviar restablecimiento de contraseña a contacto

Compruebe que los procesos **Enviar invitación** y **Enviar restablecimiento de contraseña a contacto** siguen siendo válidos, es decir, tienen una cuenta en el campo **Desde** que puede enviar correos electrónicos y el resto de los detalles son correctos.

Para obtener detalles sobre cómo solucionar estos procesos, consulte:

-   [Paso 10: Corregir el proceso Enviar invitación](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-10-fix-the-send-invitation-process)

-   [Paso 11: Arreglar el proceso Enviar restablecimiento de contraseña al contacto](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-11-fix-the-send-password-reset-to-contact-process)

## <a name="step-6-verify-the-flow-supply-tracking-flow-is-enabled"></a>Paso 6: Comprobar que el flujo de seguimiento del suministro de Flow está habilitado

Este flujo permite al usuario de de primera línea agregar suministros a través del portal que se guarda en Common Data Service.

Para obtener detalles sobre cómo solucionar estos procesos, vea [Paso 13: Comprobar que el flujo de seguimiento del suministro de Flow esté habilitado](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-13-verify-the-flow-supply-tracking-flow-is-enabled).

## <a name="step-7-verify-and-update-the-details-of-flows-for-sending-emails"></a>Paso 7: Comprobar y actualizar los detalles de los flujos para enviar correos electrónicos

En este paso, haremos lo siguiente:

|Nombre de flujo|Cambios|
|--|--|
|**Solicitud de usuario del portal: enviar correo electrónico al rechazarse la solicitud**|Actualice la conexión para conectarse a Common Data Service y luego especifique una cuenta de usuario para enviar correos electrónicos.|
|**Solicitud de usuario del portal: enviar correo electrónico a los administradores al crearse la solicitud**|Actualice la conexión para conectarse a Common Data Service y luego especifique una cuenta de usuario para enviar correos electrónicos. Además, actualice la URL del portal en el cuerpo del correo electrónico según su URL del portal.| 

Para obtener información detallada sobre esto, consulte [Paso 14: Actualizar los detalles de los flujos para enviar correos electrónicos](deploy.md#step-14-update-the-details-of-flows-for-sending-emails)

