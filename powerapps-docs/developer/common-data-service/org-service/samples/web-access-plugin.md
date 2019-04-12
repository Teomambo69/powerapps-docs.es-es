---
title: 'Ejemplo: Acceso web desde un complemento (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo escribir un complemento que tiene acceso a recursos en la red.
ms.custom: ''
ms.date: 1/16/2019
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
# <a name="sample-web-access-from-a-plug-in"></a>Ejemplo: Acceso web desde un complemento

En este ejemplo se muestra cómo escribir un complemento que tiene acceso a recursos en la red como un servicio web o fuente. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WebAccessPlugin).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

1. Descargar o clonar el informe de [Muestras](https://github.com/Microsoft/PowerApps-Samples) para que tenga una copia local. Este ejemplo se encuentra en PowerApps-Samples-master\cds\orgsvc\C#\WebAccessPlugin.
2. Abra la solución de ejemplo en Visual Studio, vaya a las propiedades del proyecto y comprueba que el ensamblado se firmará durante la compilación. Presione la F6 para compilar el ensamblado del ejemplo (WebAccessPlugin.dll).
3. Ejecute la herramienta de registro de complementos y registre el ensamblado del ejemplo en el espacio asilado y la base de datos del servidor de D365. Al registrar un paso, especifique una cadena URI web (es decir, http://www.microsoft.com) en el campo no seguro de configuración.
4. Con la aplicación D365, lleve a cabo la operación adecuada para invocar la solicitud de mensaje y de entidad donde registró al complemento.
5. Cuando el complemento se ejecute, el código en la línea 63 genera una excepción. Esto resulta un diálogo de error de ISV que se mostrará en la aplicación D365. En ese diálogo, seleccione **Descargar archivo** para ver el registro de errores que contiene los resultados del complemento incluida la respuesta de servicio web.
6. Cuando haya terminado con la prueba, cancele el registro del ensamblado y el paso.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Cuando se ejecuta, el complemento descarga la página web desde la dirección del servicio web especificado (o la dirección predeterminada) y después escribe esos datos en un archivo de registro de errores o en el servicio de seguimiento.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprueba el parámetro de configuración sin proteger del constructor para un valor de dirección web; de lo contrario, se usa el valor predeterminado.
2. La clase `System.Net.WebClient` la usa el método `Execute` del complemento para descargar datos de la página web.
3. Se genera una excepción para volver que la respuesta de servicio web esté disponible mediante un archivo de descarga del registro de errores con el fin de realizar comprobaciones.

### <a name="demonstrate"></a>Demostración

1. El método `WebClient.DownloadData` descarga datos de la página web mediante una solicitud de servicio web.
2. Los datos de la respuesta se escriben en un registro de errores de excepciones o (opcionalmente) en el servicio de seguimiento para comprobarlo después en la aplicación D365.
3. El código del complemento también muestra cómo capturar una WebException desde el servicio web y procesarla.

### <a name="see-also"></a>Vea también
[Acceso a recursos web externos](../../access-web-services.md)<br/>
[Registro de un complemento](../../register-plug-in.md)