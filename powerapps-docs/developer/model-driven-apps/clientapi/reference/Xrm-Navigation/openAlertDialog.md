---
title: openAlertDialog (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8615a284-41b4-479c-81bd-577b3b7c79ad
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openalertdialog-client-api-reference"></a>openAlertDialog (referencia de la API de cliente)



[!INCLUDE[./includes/openAlertDialog-description.md](./includes/openAlertDialog-description.md)]

## <a name="syntax"></a>Sintaxis

`Xrm.Navigation.openAlertDialog(alertStrings,alertOptions).then(closeCallback,errorCallback);`

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|alertStrings|Objeto|Sí|Las cadenas que se usan en el cuadro de diálogo de alerta. El objeto contiene los siguientes atributos:<br/>- **confirmButtonLabel**: cadena (opcional). Etiqueta del botón Confirmar. Si no especifica la etiqueta del botón, se usa **OK** como etiqueta del botón.<br/>- **text**: cadena. Mensaje que se muestra en el cuadro de diálogo de alerta.|
|alertOptions|Objeto|No|Las opciones de alto y ancho para el cuadro de diálogo de alerta. El objeto contiene los siguientes atributos:<br/>- **height**: número (opcional). Alto del cuadro de diálogo de alerta, en píxeles.<br/>- **width**: número (opcional). Ancho del cuadro de diálogo de alerta, en píxeles.|
|successCallback|función|No|Función que se ejecutará cuando el cuadro de diálogo de alerta se cierre haciendo clic en el botón Confirmar o se cancele presionando ESC.|
|errorCallback|función|No|Función que se ejecuta cuando la operación produce un error.|


## <a name="example"></a>Ejemplo

El código de ejemplo siguiente, muestra un cuadro de diálogo de alerta. Al hacer clic en el botón **Yes** en el cuadro de diálogo de alerta o al cancelar el cuadro de diálogo de alerta presionando ESC, se llama a la función `close`:

```JavaScript
var alertStrings = { confirmButtonLabel: "Yes", text: "This is an alert." };
var alertOptions = { height: 120, width: 260 };
Xrm.Navigation.openAlertDialog(alertStrings, alertOptions).then(
    function success(result) {
        console.log("Alert dialog closed");
    },
    function (error) {
        console.log(error.message);
    }
);
```

### <a name="related-topics"></a>Temas relacionados

[Xrm.navigation](../xrm-navigation.md)

