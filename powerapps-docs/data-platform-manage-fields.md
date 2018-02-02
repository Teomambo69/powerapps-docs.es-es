---
title: "Administración de campos personalizados en una entidad | Microsoft Docs"
description: Cree, lea, actualice y elimine campos personalizados en una entidad.
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/20/2017
ms.author: kfend
ms.openlocfilehash: 87be6f571688fd040c5f2578015e1a3393ca9ea1
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="manage-custom-fields"></a>Administración de campos personalizados
En todas las entidades se pueden crear y actualizar uno o varios campos. Al crear un campo personalizado, especifica un conjunto de propiedades, como el nombre del campo, el nombre para mostrar y el tipo de datos que va a contener. Para más información, consulte [Entity field data types](https://docs.microsoft.com/en-us/common-data-service/entity-reference/field-data-types) (Tipos de datos del campo Entidad) y [Entity field properties](https://docs.microsoft.com/en-us/common-data-service/entity-reference/field-properties) (Propiedades del campo Entidad).

> [!NOTE]
> Todas las entidades tienen [campos del sistema](data-platform-create-entity.md#system-fields-and-the-record-title-field), como los campos que indican la última vez en que se actualizó un registro y quién lo actualizo. Asimismo, las [entidades estándar](data-platform-intro.md#standard-entities) tienen campos estándar (predeterminados). Ni los campos estándar ni los del sistema se pueden modificar o eliminar. Si crea un campo personalizado, debe proporcionar funcionalidad además de estos campos integrados.

## <a name="create-a-field"></a>Crear un campo

1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Common Data Service** y pulse o haga clic en **Entidades** en el panel de navegación izquierdo. Aparece una lista de entidades. Para mostrar las entidades personalizadas al principio de la lista, pulse o haga clic en el encabezado de la columna **Tipo**. También puede filtrar la lista escribiendo uno o varios caracteres en la barra de búsqueda.

2. Haga clic o pulse en una entidad y, luego, en **Agregar campo** junto a la parte superior de la pantalla.

3. En **Nombre para mostrar**, especifique la cadena de texto que identificará el campo para los usuarios. Para más información, consulte [Crear una aplicación](data-platform-create-app.md).

4. En **Nombre**, especifique la cadena de texto que usará para hacer referencia al campo en, por ejemplo, en una fórmula al compilar una aplicación.
   
    > [!IMPORTANT]
    > Especifique un nombre que sea único, claro y significativo, ya que no podrá cambiarlo una vez creado el campo.

5. En **Tipo**, especifique el tipo de datos que contendrá el campo, como **Texto** o **Número**.
   
    > [!IMPORTANT]
    > Especifique esta propiedad con cuidado porque es posible que no pueda cambiarla una vez que el campo contenga datos. Para más información acerca de los tipos de datos que puede especificar, consulte [Comprender las entidades](data-platform-intro.md#custom-fields).

6. Si se le solicita, especifique información adicional del tipo de datos especificado.

7. En **Único**, active la casilla si cada registro debe tener un valor único en este campo.

8. En **Requerido**, active la casilla si cada registro debe tener un valor en este campo.
   
    > [!IMPORTANT]
    > No puede requerir que un campo personalizado de una entidad estándar contenga datos. Esta restricción impide interrumpir las aplicaciones que se basan en esa entidad.

9. Haga clic o pulse en **Guardar** para enviar los cambios.
   
    > [!IMPORTANT]
    > Los cambios se perderán si no los guarda antes de abrir otra página en el explorador o si sale de este.

Cuando la operación se complete correctamente recibirá una notificación. Si la operación no se realiza correctamente, aparecerá un mensaje de error que indica los problemas que han aparecido y cómo solucionarlos.

## <a name="update-or-delete-a-field"></a>Actualizar o eliminar un campo
1. En [powerapps.com](https://web.powerapps.com), haga clic o pulse en **Administrar**, en **Entidades** y, después, en una entidad.
2. En la lista de campos de la entidad que ha seleccionado, haga clic en uno de ellos, o púlselo, y siga uno de estos pasos:
   
   * Cambie una o varias propiedades del campo. Tenga en cuenta los [procedimientos recomendados y restricciones](data-platform-manage-fields.md#best-practices-and-restrictions).
     
       Para seleccionar la propiedad siguiente, presione la tecla Tab. Para deshacer todos los cambios de un campo, haga clic o pulse en el botón de puntos suspensivos (...) del campo y, después, en **Deshacer**.
   * Para eliminar el campo, pulse o haga clic en los puntos suspensivos (...) que hay cerca al borde derecho y, luego, en **Eliminar**.
3. Haga clic o pulse en **Guardar** para enviar los cambios.
   
    > [!IMPORTANT]
    > Los cambios se perderán si no los guarda antes de abrir otra página en el explorador o si sale de este.

Cuando la operación se complete correctamente recibirá una notificación. Si la operación no se realiza correctamente, aparecerá un mensaje de error que indica los problemas que han aparecido y cómo solucionarlos.

## <a name="best-practices-and-restrictions"></a>Procedimientos recomendados y restricciones
Al crear y modificar campos, tenga en cuenta estos puntos:

* No puede modificar ni eliminar campos del sistema ni sus valores.
* En una entidad estándar, no puede modificar ni eliminar un campo estándar (predeterminado), agregar un campo que requiera datos o realizar cualquier otro cambio que pueda interrumpir una aplicación que confíe en la entidad.
* En una entidad personalizada, debe asegurarse de que los cambios que realice no van a interrumpir ninguna aplicación que confíe en la entidad.
* Debe asignar a cada campo personalizado un nombre que sea único dentro de la entidad y no puede cambiar el nombre de un campo después de crearlo.
* Puede cambiar el tipo de datos de cualquier campo, siempre que este no contenga datos. Si el campo contiene datos, puede cambiar el tipo de datos, siempre que todos los datos existentes cumplan los requisitos del nuevo tipo de datos. Por ejemplo, puede cambiar el tipo de datos de un campo **Número** a **Cadena**, pero no puede cambiarlo de **Cadena** a **Número** si contiene datos no numéricos.
* Puede interrumpir una aplicación que utiliza una entidad si modifica un campo de esa entidad de una o varias de las siguientes maneras:
  * Cambiar el tipo de datos del campo.
  * Requerir valores, pero uno o varios registros no contienen un valor en ese campo.
  * Requerir valores únicos, pero dos o más registros contienen el mismo valor en ese campo.

## <a name="next-steps"></a>Pasos siguientes
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)
* [Crear una aplicación mediante entidades](data-platform-create-app.md)
* [Crear una aplicación desde cero mediante una base de datos de Common Data Service](data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, recopilamos y almacenamos los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos creados nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).

