---
title: getBarcodeValue| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0218b96c-2809-4f2d-9f9f-d8ee8f8e3b7b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getbarcodevalue-client-api-reference"></a>getBarcodeValue (referencia de la API de cliente)



[!INCLUDE[./includes/getBarcodeValue-description.md](./includes/getBarcodeValue-description.md)]


## <a name="syntax"></a>Sintaxis

`Xrm.Device.getBarcodeValue().then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|successCallback |Función | Sí|Una función para llamar cuando el valor del código de barras se devuelve como cadena.|
|errorCallback |Función | Sí|Una función para llamar cuando la operación tiene error. Se pasará un objeto de error con la propiedad (de cadena) **message** que describe los detalles del error.|
 

## <a name="return-value"></a>Valor devuelto
Si funciona, devuelve una cadena que contiene el valor de código de barras escaneado.

## <a name="remarks"></a>Comentarios
Este método solo es compatible para los clientes móviles.

## <a name="example"></a>Ejemplo

```JavaScript
Xrm.Device.getBarcodeValue().then(
    function success(result) {
        Xrm.Navigation.openAlertDialog({ text: "Barcode value: " + result });
    },
    function (error) {
        Xrm.Navigation.openAlertDialog( {text: error.message} );
    }
);
``` 

### <a name="related-topics"></a>Temas relacionados
[Xrm.Device](../xrm-device.md)

