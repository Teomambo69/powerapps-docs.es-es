---
title: getCurrentPosition| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 062a52d8-170c-4e98-b48a-ac99ec759f83
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcurrentposition-client-api-reference"></a>getCurrentPosition (referencia de la API de cliente)



[!INCLUDE[./includes/getCurrentPosition-description.md](./includes/getCurrentPosition-description.md)]


## <a name="syntax"></a>Sintaxis

`Xrm.Device.getCurrentPosition().then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|successCallback |Función | Sí|Una función para llamar cuando se devuelve información de ubicación geográfica actual. Un objeto de ubicación geográfica con los siguientes atributos se pasa a la función:<br/>- **coords**: contiene un conjunto de coordenadas geográficas junto con la precisión asociada, así como un conjunto de otros atributos opcionales como altitud y velocidad. <br/>- **timestamp**: representa la hora en que se adquirió el objeto y se representa como DOMTimeStamp.|
|errorCallback |Función | Sí|Una función para llamar cuando la operación tiene error. Se pasará un objeto con las siguientes propiedades: <br/>- **code**: el código de error. Número. <br/>- **message**: mensaje localizado que describe los detalles del error. Cadena.<br/><br/>Si la configuración de ubicación del usuario no está habilitada en su dispositivo móvil, el mensaje de error indica lo mismo. Si usa una versión anterior del cliente móvil de aplicaciones basadas en modelos o si la capacidad del ubicación geográfica no está disponible en su dispositivo móvil, se pasa NULL a la dispositivo móvil de error.|
 

## <a name="return-value"></a>Valor devuelto
En caso de éxito, devuelve un objeto de geolocalización que contiene los atributos especificados anteriormente en la función **successCallback**.

## <a name="remarks"></a>Comentarios
Para que el método **getCurrentPosition** funcione, la capacidad de ubicación geográfica debe estar habilitada en su dispositivo móvil y los clientes móviles de las aplicaciones basadas en modelos deben tener permisos de acceso a la ubicación del dispositivo, que no están habilitados de forma predeterminada.

Este método solo es compatible para los clientes móviles.

## <a name="example"></a>Ejemplo

```JavaScript
Xrm.Device.getCurrentPosition().then(
    function success(location) {
        Xrm.Navigation.openAlertDialog({
            text: "Latitude: " + location.coords.latitude +
            ", Longitude: " + location.coords.longitude
        });
    },
    function (error) {
        Xrm.Navigation.openAlertDialog({ text: error.message });
    }
);
```

### <a name="related-topics"></a>Temas relacionados
[Xrm.Device](../xrm-device.md)

