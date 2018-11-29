---
title: openConfirmDialog (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9c82028d-cbc9-4d40-9987-6ce1ea01fde2
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openconfirmdialog-client-api-reference"></a>openConfirmDialog (referencia de la API de cliente)



[!INCLUDE[./includes/openConfirmDialog-description.md](./includes/openConfirmDialog-description.md)]

## <a name="syntax"></a>Sintaxis

`Xrm.Navigation.openConfirmDialog(confirmStrings,confirmOptions).then(successCallback,errorCallback);`

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|confirmStrings|Objeto|Sí|Las cadenas que se usan en el cuadro de diálogo de confirmación. El objeto contiene los siguientes atributos:<br/>- **cancelButtonLabel**: cadena (opcional). Etiqueta del botón Cancelar. Si no especifica la etiqueta del botón Cancelar, se usa **Cancel** como etiqueta del botón.<br/>- **confirmButtonLabel**: cadena (opcional). Etiqueta del botón Confirmar. Si no especifica la etiqueta del botón Confirmar, se usa **OK** como etiqueta del botón.<br/>- **subtitle**: cadena (opcional). Subtitulo que se muestra en el cuadro de diálogo de confirmación.<br/>- **text**: cadena. Mensaje que se muestra en el cuadro de diálogo de confirmación.<br/>- **title**: cadena (opcional). Título que se muestra en el cuadro de diálogo de confirmación.|
|confirmOptions|Objeto|No|Las opciones de alto y ancho para el cuadro de diálogo de confirmación. El objeto contiene los siguientes atributos:<br/>- **height**: número (opcional). Alto del cuadro de diálogo de confirmación, en píxeles.<br/>- **width**: número (opcional). Ancho del cuadro de diálogo de confirmación, en píxeles.|
|successCallback|función|No|Una función que se ejecutará cuando se cierre el cuadro de diálogo de confirmación al hacer clic en el botón Confirmar, Cancelar o **X** en la esquina superior derecha del cuadro de diálogo. Se pasa un objeto con el atributo **confirmed** (booleano) que indica si se hizo clic en el botón Confirmar para cerrar el cuadro de diálogo.|
|errorCallback|función|No|Función que se ejecuta cuando la operación produce un error.|

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente muestra un cuadro de diálogo de confirmación. El mensaje adecuado se registra en la consola dependiendo de que se haya hecho clic en Confirmar, Cancelar o**X** para cerrar el cuadro de diálogo.

```JavaScript
var confirmStrings = { text:"This is a confirmation.", title:"Confirmation Dialog" };
var confirmOptions = { height: 200, width: 450 };
Xrm.Navigation.openConfirmDialog(confirmStrings, confirmOptions).then(
function (success) {    
    if (success.confirmed)
        console.log("Dialog closed using OK button.");
    else
        console.log("Dialog closed using Cancel button or X.");
});

```

### <a name="related-topics"></a>Temas relacionados

[Xrm.Navigation](../xrm-navigation.md)

