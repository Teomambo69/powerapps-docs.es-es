---
title: Administración de campos personalizados en una entidad | Microsoft Docs
description: Tutorial sobre cómo crear, leer, actualizar y eliminar los campos personalizados de una entidad en Common Data Service (CDS) for Apps.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: a9fff4cc61f6416ef8dbc3c03d96be7082fe3a51
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218749"
---
# <a name="manage-custom-fields-in-an-entity"></a>Administración de campos personalizados en una entidad
En todas las entidades se pueden crear y actualizar uno o varios campos. Al crear un campo personalizado, especifica un conjunto de propiedades, como el nombre del campo, el nombre para mostrar y el tipo de datos que va a contener. Para obtener más información, vea [Entity attribute metadata](../../developer/common-data-service/entity-attribute-metadata.md) (Metadatos de atributo de entidad).

> [!NOTE]
> Todas las entidades tienen campos del sistema, como los que indican la última vez que se actualizó un registro y quién lo actualizó. Además, las entidades estándar tienen campos estándar (predeterminados). Ni los campos estándar ni los del sistema se pueden modificar o eliminar. Si crea un campo personalizado, debe proporcionar funcionalidad además de estos campos integrados.

## <a name="create-a-field"></a>Crear un campo
1. En [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. Pulse o haga clic en una entidad existente, o bien en [Crear una nueva entidad](data-platform-create-entity.md)

3. Agregue un campo nuevo a la entidad haciendo clic en **Agregar campo**.

4. En el panel Nuevo campo, escriba el **Nombre para mostrar** para el campo, **Nombre** se rellenará automáticamente y se usará como el nombre único del campo. El **Nombre para mostrar** se usa cuando se presenta este campo a los usuarios, el **Nombre** se usa al compilar la aplicación, en las fórmulas y expresiones.

    > [!NOTE]
    > Los campos **Nombre para mostrar** se pueden actualizar en cualquier momento para mostrarlos de otra forma en las aplicaciones; el campo **Nombre** no se puede cambiar después de guardar la entidad, ya que se podría interrumpir una aplicación existente.

    ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel.png "Panel Nuevo campo")

5. Seleccione el **Tipo de datos** del campo, esto controla la forma en que se almacena la información, así como el modo en que se presenta en las aplicaciones. Por ejemplo, el texto se almacena de forma diferente a un número decimal o una dirección URL. Para obtener más información de los tipos de datos disponibles, vea [Entity attribute metadata](../../developer/common-data-service/entity-attribute-metadata.md) (Metadatos de atributo de entidad).

    Si se le solicita, especifique información adicional del tipo de datos especificado. Según el tipo de datos, se presentarán otros campos. Si se va a crear un campo de tipo Conjunto de opciones o Conjunto de opciones de selección múltiple, puede hacer clic en **Nuevo conjunto de opciones** y crear un conjunto de opciones al crear el campo. Para obtener más información, vea [Create Option set](custom-picklists.md) (Creación de un conjunto de opciones).

    ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Panel Nuevo campo")


7. En **Requerido**, active la casilla si quiere recomendar este campo como obligatorio en las aplicaciones. Esto no ofrece aplicación forzada en todas las conexiones a Common Data Service. Si necesita asegurarse de que el campo se rellena, cree una [regla de negocio](data-platform-create-business-rule.md).

8. En **Se puede buscar**, active la casilla es necesario que este campo esté disponible en Vistas, Gráficos, Paneles y Búsqueda avanzada. En la mayoría de los casos, se debe activar esta casilla.

9. Pulse o haga clic en **Listo** para cerrar el panel Campo y volver a la entidad. Puede repetir los pasos del 3 al 9 para cada campo adicional.
   
    > [!IMPORTANT]
    > El campo todavía no se guarda ni se crea hasta que guarde los cambios en la entidad.

10. Pulse o haga clic en **Guardar entidad** para finalizar los cambios y guardarlos en Common Data Service.

    Cuando la operación se complete correctamente recibirá una notificación. Si la operación no se realiza correctamente, aparecerá un mensaje de error que indica los problemas que han aparecido y cómo solucionarlos.

## <a name="create-a-calculated-or-roll-up-field"></a>Crear un campo calculado o consolidado
Los campos calculados permiten automatizar los cálculos manuales que se usan en los procesos empresariales. Por ejemplo, puede que a un vendedor le interese conocer los ingresos ponderados de una oportunidad que se basan en los ingresos estimados de una oportunidad multiplicados por la probabilidad. O bien, que quiera aplicar automáticamente un descuento, si un pedido es superior a 500 USD. Un campo calculado puede contener valores resultantes de operaciones matemáticas sencillas, u operaciones condicionales como if-else, o mayor que y muchas otras. Los campos calculados se pueden crear mediante los tipos de datos siguientes:

* Una línea de texto
* Conjunto de opciones
* Dos opciones
* Número entero
* Número decimal
* Divisa
* Fecha y hora

Para obtener más información sobre los tipos de expresiones admitidos y ejemplos, vea [Definir campos calculados](/dynamics365/customer-engagement/customize/define-calculated-fields).

## <a name="update-or-delete-a-field"></a>Actualizar o eliminar un campo
1. En [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda y, después, pulse o haga clic en una entidad.
2. En la lista de campos de la entidad que ha seleccionado, haga clic en uno de ellos, o púlselo, y siga uno de estos pasos:
   
   * Cambie una o varias propiedades del campo.
   * Para eliminar el campo, pulse o haga clic en los puntos suspensivos (...) que hay cerca al borde derecho y, luego, en **Eliminar**.

3. Pulse o haga clic en **Guardar entidad** para enviar los cambios.
   
    > [!IMPORTANT]
    > Los cambios se perderán si no los guarda antes de abrir otra página en el explorador o si sale de este.

    Cuando la operación se complete correctamente recibirá una notificación. Si la operación no se realiza correctamente, aparecerá un mensaje de error que indica los problemas que han aparecido y cómo solucionarlos.

## <a name="best-practices-and-restrictions"></a>Procedimientos recomendados y restricciones
Al crear y modificar campos, tenga en cuenta estos puntos:

* No puede modificar ni eliminar campos del sistema ni sus valores.
* En una entidad estándar, no puede modificar ni eliminar un campo estándar (predeterminado), agregar un campo que requiera datos o realizar cualquier otro cambio que pueda interrumpir una aplicación que confíe en la entidad.
* En una entidad personalizada, debe asegurarse de que los cambios que realice no van a interrumpir ninguna aplicación que confíe en la entidad.
* Debe asignar a cada campo personalizado un nombre que sea único dentro de la entidad y no puede cambiar el nombre de un campo después de crearlo.

## <a name="next-steps"></a>Pasos siguientes
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)
* [Crear una regla de negocio](data-platform-create-business-rule.md)
* [Crear una aplicación mediante entidades](../canvas-apps/data-platform-create-app.md)
* [Crear una aplicación desde cero mediante una base de datos de Common Data Service](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, recopilamos y almacenamos los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos creados nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).

