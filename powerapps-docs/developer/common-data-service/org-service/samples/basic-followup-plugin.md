---
title: 'Ejemplo: Crear un complemento básico (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo escribir un complemento sencillo que cree una actividad de seguimiento.
ms.custom: ''
ms.date: 1/29/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-create-a-basic-plug-in"></a>Ejemplo: Crear un complemento básico

En este ejemplo se muestra cómo escribir un complemento sencillo que cree una actividad de seguimiento. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/FollowupPlugin).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

1. Descargar o clonar el informe de [Muestras](https://github.com/Microsoft/PowerApps-Samples) para que tenga una copia local. Este ejemplo se encuentra en PowerApps-Samples-master\cds\orgsvc\C#\FollowupPlugin.
2. Abra la solución de ejemplo en Visual Studio, vaya a las propiedades del proyecto y comprueba que el ensamblado se firmará durante la compilación. Presione la F6 para compilar el ensamblado del ejemplo (FollowupPlugin.dll).
3. Ejecute la herramienta de registro de complementos y registre el ensamblado del ejemplo en el espacio asilado y la base de datos del servidor de D365. Al registrar un paso, especifique el mensaje Create, la entidad de la cuenta y el modo asíncrono.
4. Con la aplicación D365, lleve a cabo la operación adecuada para invocar la solicitud de mensaje y de entidad donde registró al complemento (cree una cuenta).
5. Después de que se ejecute el complemento, debe ver una nueva entrada de registro de seguimiento “FollowupPlugin: Successfully created the task activity” y una nueva actividad con el asunto “Enviar correo electrónico al nuevo cliente.” programada para que se active en 7 días.
6. Cuando haya terminado con la prueba, cancele el registro del ensamblado y el paso.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Cuando se ejecuta en el momento de la creación de una cuenta, el complemento crea una actividad para recordar al usuario realizar un seguimiento del cliente de la cuenta en 7 días.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="demonstrate"></a>Demostración

1. Cómo crear una actividad de tareas y programarla para una fecha futura.
2. Cómo usar el servicio de seguimiento para registrar información en tiempo de ejecución.
3. Cómo seleccionar las excepciones desde servicio web y procesarlas.

### <a name="see-also"></a>Vea también
[Escribir un complemento](../../write-plug-in.md)  
[Registro de un complemento](../../register-plug-in.md)