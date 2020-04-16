---
title: " Establecer y recuperar imágenes de entidad (Common Data Service) | Microsoft Docs"
description: En este ejemplo se muestra cómo establecer y recuperar imágenes de entidad.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 79a2b18db60afa9f487f4313116c9600c72a13c0
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155576"
---
# <a name="set-and-retrieve-entity-images"></a>Establecer y recuperar imágenes de entidad

En este ejemplo se muestra cómo establecer y recuperar datos de las imágenes de entidad. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SetRetrieveImages).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo crear un rol de conexión que puede usarse para cuentas y contactos.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

Comprueba la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. Utiliza el método CreateImageAttributeDemoEntity para crear una entidad personalizada con el nombre de esquema `sample_ImageAttributeDemo` y un atributo principal con el nombre de esquema `sample_Name`.
2. Crear un atributo de imagen con el nombre de esquema `EntityImage`. Todos los atributos de imagen usan este nombre.

3. Recupera y actualiza el formulario principal para la entidad `sample_ImageAttributeDemo` para establecer el atributo `showImage` a true de forma que la imagen se muestre en el formulario.

4. Publicar la entidad `sample_ImageAttributeDemo`.

5. Crea cinco nuevos registros para la entidad `sample_ImageAttributeDemo` utilizando cinco imágenes de diferentes tamaños ubicadas en la carpeta Imágenes como se muestra aquí. Después de crear cada registro, tiene la oportunidad de ver el registro en la aplicación del navegador web utilizando el método `ShowEntityFormInBrowser` para que pueda ver cómo se redimensionan las imágenes de origen para ajustarse al espacio disponible en el formulario.
6. Recupera los registros con el atributo `entityimage` y guarda los archivos redimensionados. Después de ejecutar el ejemplo puede encontrar los archivos guardados en la carpeta `\bin\Debug`.
7. Recupera los registros con el atributo `entityimage_url` y muestra los valores de la dirección URL relativa que puede incluir en la aplicación para tener acceso a las imágenes. Esta consulta debe ser más dinámica porque la cantidad de datos transmitidos es inferior.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
