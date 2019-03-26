---
title: Interactuar con recursos HTTP y HTTPS de forma asincrónica | MicrosoftDocs
description: Debe interactuar con los recursos HTTP y HTTPS de forma asincrónica al escribir las extensiones de cliente de JavaScript para aplicaciones basadas en modelos.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/20/2018
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="interact-with-http-and-https-resources-asynchronously"></a>Interactuar con recursos HTTP y HTTPS de forma asincrónica

**Categoría**: rendimiento

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

La solicitudes sincrónicas bloquean la ejecución de otros scripts, que pueden provocar lo siguiente:

- Aplicaciones de lienzo y basadas en modelos que dejan de responder
- Interacciones lentas con el cliente

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Interactuar con recursos HTTP y HTTPS de forma asincrónica siempre que sea posible. Los usuarios deberían notar mejoras en el tiempo real de carga de la página o en la velocidad percibida de carga de la página. La capacidad de respuesta de la página también debe aumentar.

Las siguientes opciones están disponibles en los exploradores modernos para interactuar con servicios de forma asincrónica.

> [!NOTE]
> Agregar interacciones asincrónicas requiere otro estilo de diseño que las interacciones asincrónicas. Las devoluciones de llamada se pueden ejecutar en un orden que no sea determinista, lo que significa que deben dedicar más tiempo a asegurarse de que el flujo y la integridad de la página sean correctos en todo momento. Por ejemplo, a menudo deberá establecer medidas para garantizar que los controles no están habilitados hasta que todas las llamadas de servicio dependientes se hayan devuelto. Realizar algunos pasos adicionales puede garantizar una experiencia más de usuario más atractiva.

- Tradicionalmente, las reglas de la cinta de opciones se escriben con solicitudes sincrónicas dado que tienen que devolver true o false. La interfaz unificada admite devolver una promesa en lugar de un valor booleana, lo que permite que las reglas de la cinta de opciones emitan solicitudes asincrónicas de red. Para obtener más información, consulte [Definir las reglas de habilitación de la cinta de opciones](/powerapps/developer/model-driven-apps/define-ribbon-enable-rules#custom-rule).

- [`XMLHttpRequest`](https://developer.mozilla.org/docs/Web/API/XMLHttpRequest) con el parámetro asincrónico omitido o establecido en true

  ```javascript
  // Missing the async parameter, which is the third parameter. It defaults to true, which is the value you want.
  var requestXhr = new XMLHttpRequest();
  requestXhr.open('GET', '/test/test.txt');

  // Explicitly setting the async parameter.
  requestXhr.open('GET', '/test/test.txt', true);
  ```

- Uso de la API [Fetch](https://developer.mozilla.org/docs/Web/API/Fetch_API)

  > [!IMPORTANT]
  > Antes de continuar con esta opción, asegúrese de que el soporte está disponible para exploradores que se usan para interactuar con las personalizaciones. Consulte la sección **Compatibilidad del explorador** de la documentación de [Fetch](https://developer.mozilla.org/docs/Web/API/Fetch_API).

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

Hay varias formas de interactuar con el servidor o solicitar recursos. Los enfoques habituales que permiten comunicaciones sincrónicos incluyen los siguientes:

> [!WARNING]
> Estos escenarios deben evitarse.

- Uso del objeto `XMLHttpRequest` con `false` para el valor del parámetro `async` para la función de llamada de `open`

  ```javascript
  var requestXhr = new XMLHttpRequest();

  // Explicitly setting the async parameter to false or supplying a variable with a value of false will force this as a synchronous call.
  requestXhr.open('GET', '/test/test.txt', false);
  ```

- Uso de la función [`ajax`](http://api.jquery.com/jquery.ajax/) de [`jQuery`](https://www.jquery.com) con `false` para el valor del parámetro `async`

  ```javascript
  // Explicitly setting the async parameter to false or supplying a variable with a value of false will force this as a synchronous call.
  var requestAjax = $.ajax({ async: false, url: '/test/test.txt' });
  ```

- Específicamente para las interacciones con los servicios de Microsoft Dynamics 365, hay bibliotecas de JavaScript que proporcionan las operaciones explícitas para las interacciones comunes con el producto. Entre las bibliotecas comunes, se incluyen: [`SDK.REST.js`](https://msdn.microsoft.com/library/gg334427(v=crm.7).aspx#BKMK_SDKREST), [`SDK.Soap.js`](https://code.msdn.microsoft.com/sdksoapjs-9b51b99a) y [`XrmServiceToolkit.js`](https://github.com/XrmServiceToolkit/XrmServiceToolkit).
  - Para estas, hay algunas funciones que solo admiten operaciones sincrónicas; otras requieren pasar en una función de devolución de llamada como parámetro para establecer async en true. El comportamiento predeterminado para la mayoría es establecer el parámetro async subyacente en false para la llamada abierta del objeto `XMLHttpRequest`.

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

### <a name="performance"></a>Rendimiento

Un explorador interpreta el script en un solo subproceso. Si ese subproceso se usa para ejecutar un proceso forma sincrónica, el explorador dejará de responder a las interacciones del usuario (se “congela”) mientras espera a que el proceso se comple. Las llamadas sincrónicas también eliminan la capacidad de realizar más de una interacción simultánea, forzando a todas las llamadas sean en serie por naturaleza. En muchos casos, esto conlleva la frustración de los usuarios. Optimizar la capacidad de respuesta del usuario incorporando llamadas de servicio asincrónicas.

### <a name="browser-support"></a>Compatibilidad del explorador

La especificación para `XMLHttpRequest` indica que el uso sincrónico se quita del estándar porque ahora está en desuso. Actualmente, los exploradores solo presentan advertencias, pero se podría generar una excepción `InvalidAccessError` en el futuro cuando un valor false se pase al parámetro async. Los exploradores modernos han declarado solicitudes sincrónicas que se ejecutan en el subproceso principal como en desuso.

> [!NOTE]
> Se están incluyendo API modernas que no proporcionarán una opción para las operaciones sincrónicas. Remítase a la documentación de la [API Fetch](https://developer.mozilla.org/docs/Web/API/Fetch_API) para obtener más detalles.

### <a name="windowsettimeout"></a>window.setTimeout

Pese a que incluir los bloques del script como parámetro para la función `window.setTimeout` interrumpe el flujo sincrónico normal de la ejecución de la página, no se consigue un procesamiento en paralelo.

```javascript
window.setTimeout(
    function () {
        var oReq = new XMLHttpRequest();
        oReq.open('GET', '/test/action', false);
    }, 0);
```

El método de este ejemplo se sigue procesando en el subproceso de IU del explorador principal, por lo que bloquea el explorador.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Definir las reglas de la cinta de opciones](/powerapps/developer/model-driven-apps/define-ribbon-enable-rules#custom-rule)
[XMLHttpRequest](https://docs.microsoft.com/microsoft-edge/dev-guide/performance/xmlhttprequest)<br />
[Especificación de XMLHttpRequest (con instrucción síncrona de desuso)](https://xhr.spec.whatwg.org/#the-open()-method)<br />
[Especificación de la API Fetch](https://fetch.spec.whatwg.org/#fetch-api)<br />
[API Fetch](https://developer.mozilla.org/docs/Web/API/Fetch_API)
