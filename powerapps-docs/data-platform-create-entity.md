---
title: "Creación de una entidad personalizada | Microsoft Docs"
description: Cree una entidad personalizada basada en otra entidad o desde cero.
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
ms.openlocfilehash: e02a423f6a951c1c479b3941c6f361383244cafc
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="create-a-custom-entity"></a>Crear una entidad personalizada
Puede crear una entidad personalizada para almacenar datos específicos de su organización. Después, puede mostrar dichos datos si desarrolla una aplicación que haga referencia a la entidad.

Hay dos maneras de crear una entidad:

* Crear la entidad desde cero. De forma predeterminada, la entidad solo contiene [cuatro campos de sistema y un campo de título de registro](data-platform-create-entity.md#system-fields-and-the-record-title-field).
* Crear una entidad que se basa en otra entidad, mediante la copia tanto de los campos como de la configuración de dicha entidad, pero no de sus datos.

En ambos casos, Microsoft PowerApps almacena y ayuda automáticamente a proteger los datos. Después de crear una entidad, puede [crear o modificar uno o varios de sus campos](data-platform-manage-fields.md) y [crear relaciones entre entidades](data-platform-entity-lookup.md).

> [!NOTE]
> Antes de crear una entidad, consulte la [lista de entidades estándar](data-platform-intro.md#standard-entities). Estas entidades tratan los escenarios típicos, como cuentas y contactos. Si una de estas entidades cumple sus requisitos sin cambios o después de realizar cambios menores, puede ahorrarse tiempo partiendo de ella.

## <a name="create-an-entity"></a>Crear una entidad
1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Common Data Service** y pulse o haga clic en **Entidades** en el panel de navegación izquierdo.
2. Si no ha creado una base de datos, debe crearla. Para más información, consulte [Crear una base de datos de Common Data Service](create-database.md).
3. Cerca de la esquina superior derecha, pulse o haga clic en **Nueva entidad**.
4. En el campo **Nombre**, escriba un nombre para la entidad. Asegúrese de que sea claro y significativo, ya que no podrá cambiarlo una vez creada la entidad. Cuando desarrolle una aplicación, hará referencia a la entidad por este nombre en una fórmula.
5. Especifique un nombre para mostrar y, opcionalmente, una descripción para la entidad; después, pulse o haga clic en **Siguiente**.
6. Opcional: Cambie el valor del campo **Título** a algo que sea más significativo para los datos.
7. Haga clic o pulse en **Crear** para crear la entidad.

La entidad aparece en la lista de entidades de la base de datos. Para mostrar la entidad en la parte superior de la lista, pulse o haga clic en el encabezado de columna **Tipo**. Las entidades se ordenarán por tipo y todas las personalizadas aparecerán antes que las estándar.

## <a name="system-fields-and-the-record-title-field"></a>Campos del sistema y el campo de título de registro
Todas las entidades tienen cinco campos de sistema. Estos campos son de solo lectura. Por tanto, no se pueden modificar ni eliminar, y tampoco se les asignan valores.

| Nombre para mostrar | Nombre del campo de sistema | Tipo de datos | Descripción |
| --- | --- | --- | --- |
| Identificador |Nombre del campo de sistema |Número entero grande |Identificador único del registro. |
| Creado por |CreatedByUser |Texto |Usuario que creó un registro. |
| Fecha de creación del registro |CreatedOnDateTime |DateTime |Fecha y hora en que se creó un registro. |
| Modificado por última vez por |LastModifiedByUser |Texto |Usuario que realizó la última modificación del registro. |
| Fecha de modificación del registro |LastModifiedDateTime |DateTime |Fecha y hora en que se modificó un registro por última vez. |

Si crea una entidad desde cero, también contiene un campo personalizado llamado **Título**. Este campo se establece como campo **Título** del registro. El valor del campo **Título** es el identificador descriptivo de un registro cada vez que se usa ese registro en una aplicación. Puede cambiar cuál es el campo **Título**, pero cada entidad debe tener uno.

## <a name="next-steps"></a>Pasos siguientes
* [Administrar campos de una entidad](data-platform-manage-fields.md)
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)
* [Generar una aplicación mediante una base de datos de Common Data Service](data-platform-create-app.md)
* [Create an app from scratch using a Common Data Service database](data-platform-create-app-scratch.md) (Crear una aplicación desde cero mediante una base de datos de Common Data Service)

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, recopilamos y almacenamos los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos creados nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).

