---
title: openErrorDialog (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9749143d-c159-4833-aff9-d8bc2c3395f3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openerrordialog-client-api-reference"></a>openErrorDialog (referencia de la API de cliente)



[!INCLUDE[./includes/openErrorDialog-description.md](./includes/openErrorDialog-description.md)]

## <a name="syntax"></a>Sintaxis

`Xrm.Navigation.openErrorDialog(errorOptions).then(successCallback,errorCallback);`

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|errorOptions|Objeto|Sí|Objeto para especificar las opciones del cuadro de diálogo de error. El objeto contiene los siguientes atributos:<br/>- **details**: cadena (opcional). Detalles sobre el error. Cuando especifica esto, el botón **Descargar archivo de registro** botón está disponible en el mensaje de error y hacer clic en él permite que los usuarios descarguen un archivo de texto con el contenido especificado en este atributo.<br/>- **errorCode**: número (opcional). Código de error. Si solo configurar **errorCode**, el mensaje para el código de error se recupera del servidor automáticamente y se muestra en el cuadro de diálogo de error. Si especifica un valor de **errorCode** no válido, se muestra un cuadro de diálogo de error con un mensaje de error predeterminado.<br/>- **message**: cadena (opcional). El mensaje que se muestra en el cuadro de diálogo de error.<br/><br/>Debe establecer el atributo **errorCode** o **message**. |
|successCallback|función|No|Una función que se ejecuta cuando se cierra el cuadro de diálogo de error.|
|errorCallback|función|No|Función que se ejecuta cuando la operación produce un error.|

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente pasa un código de error incorrecto (1234) para mostrar un cuadro de diálogo de error con el mensaje predeterminado:

```JavaScript
Xrm.Navigation.openErrorDialog({ errorCode:1234 }).then(
    function (success) {
        console.log(success);        
    },
    function (error) {
        console.log(error);
    });
```

Esto muestra un cuadro de diálogo de error con el mensaje predeterminado:

![Cuadro de diálogo de error con el mensaje predeterminado](../../../media//clientapi_sampleerrordialog.png)

### <a name="related-topics"></a>Temas relacionados

[Xrm.Navigation](../xrm-navigation.md)

