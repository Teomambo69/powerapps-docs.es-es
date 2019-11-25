---
title: Administrar campos personalizados en una entidad | Microsoft Docs
description: Tutorial sobre cómo crear, leer, actualizar y eliminar campos personalizados de una entidad en Common Data Service.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b0c576b8eab2b547c66a90f0693becf516b01207
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758608"
---
# <a name="manage-custom-fields-in-an-entity"></a>Administrar campos personalizados de una entidad
Puede crear y actualizar uno o varios campos personalizados de cualquier entidad. Cuando crea un campo personalizado, especifica un conjunto de propiedades, como el nombre del campo, el nombre para mostrar y el tipo de datos que contendrá. Para obtener más información, consulte [Metadatos de atributos de entidad](../../developer/common-data-service/entity-attribute-metadata.md).

> [!NOTE]
> Cada entidad tiene campos del sistema, como campos que indican cuándo se actualizó un registro por última vez y quién lo actualizó. Además, las entidades estándar tienen campos (predeterminados) estándar. No puede modificar o eliminar campos del sistema o campos estándar. Si crea un campo personalizado, debe proporcionar funcionalidad sobre estos campos integrados.

## <a name="create-a-field"></a>Crear un campo
1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. Haga clic o pulse en una entidad existente o [Cree una nueva entidad](data-platform-create-entity.md)

3. Agregue un nuevo campo a la entidad haciendo clic en **Agregar campo**.

4. En el panel Nuevo campo, introduzca el **Nombre para mostrar** para el campo, el **Nombre** se rellenará automáticamente y se usa como el nombre único para el campo. Se usa **Displayname** al mostrar este campo a sus usuarios, se usa **Nombre** cuando crea la aplicación, en expresiones y fórmulas.

    > [!NOTE]
    > Los campos **Nombre para mostrar** se pueden actualizar en cualquier momento para que se muestre de forma diferente en sus aplicaciones, el campo **Nombre** no se puede cambiar una vez guardada la entidad, ya que esto podría dañar una aplicación existente.

    > [!div class="mx-imgBorder"] 
    > ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel.png "Panel Nuevo campo")

5. Seleccione el **Tipo de datos** del campo, esto controla la forma en que se almacena la información y también cómo se muestra en aplicaciones. Por ejemplo, el texto se almacena de forma diferente a un número decimal o una dirección URL. Para obtener información detallada de los tipos de datos disponibles, consulte [Metadatos de atributos de entidad](../../developer/common-data-service/entity-attribute-metadata.md).

    Si se le solicita, especifique información adicional para el tipo de datos que ha especificado. Según el tipo de datos, distintos campos se mostrarán. Si está creando un campo de tipo Conjunto de opciones o Conjunto de opciones de selección múltiple, puede seleccionar **Nuevo conjunto de opciones** y crear un nuevo conjunto de opciones cuando cree el campo. Para obtener más información, consulte [Crear un conjunto de opciones](custom-picklists.md)

    > [!div class="mx-imgBorder"] 
    > ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Panel Nuevo campo")


7. En **Obligatorio**, active la casilla si desea recomendar este campo como obligatorio en sus aplicaciones. Esto no proporciona una aplicación fija en todas las conexiones a Common Data Service. Si necesita asegurarse de si el campo se ha rellenado, cree una [Regla de negocio](data-platform-create-business-rule.md)

8. En **Buscable**, active la casilla si necesita que este campo esté disponible en vistas, gráficos, paneles y búsqueda avanzada. En la mayoría de los casos deberá activarse esta casilla.

9. Haga clic o pulse en **Hecho** para cerrar el panel Campo y volver a la entidad. Puede repetir los pasos 3-9 para cada campo adicional.
   
    > [!IMPORTANT]
    > El campo aún no se guarda ni crea hasta que guarde los cambios en la entidad.

10. Haga clic o pulse en **Guardar entidad** para finalizar los cambios y guardarlos en Common Data Service.

    Se le notificará cuando la operación finalice correctamente. Si la operación no se realiza correctamente, aparece un mensaje de error que indica los problemas que se han producido y cómo puede corregirlos.

## <a name="create-a-calculated-or-roll-up-field"></a>Crear un campo calculado o consolidado
Los campos calculados permiten automatizar cálculos manuales que se usan en los procesos de negocio. Por ejemplo, un comercial puede querer conocer los ingresos ponderados de una oportunidad que se basan en los ingresos estimados de una oportunidad multiplicados por la probabilidad. O bien, automáticamente desea aplicar un descuento, si un pedido es superior a $500. Un campo calculado puede que contenga valores resultado de simples operaciones matemáticas, u operaciones condicionales, por ejemplo, Mayor que o If-Else, y muchos otras. Los campos calculados se pueden crear mediante los siguientes tipos de datos:

* Línea única de texto
* Conjunto de opciones
* Dos opciones
* Número entero
* Número decimal
* Divisa
* Fecha y hora

Para obtener más detalles sobre los tipos de expresiones compatibles y ejemplos, consulte [Definir campos calculados](/dynamics365/customer-engagement/customize/define-calculated-fields)

## <a name="update-or-delete-a-field"></a>Actualizar o eliminar un campo
1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda, y haga clic o pulse en una entidad.
2. En la lista de campos para la entidad seleccionada, haga clic o pulse en un campo, y luego siga uno de estos pasos:
   
   * Cambie una o más propiedades del campo.
   * Elimine el campo haciendo clic o pulsando en los puntos suspensivos (...) cerca del borde derecho del campo y haciendo clic o pulsando en **Eliminar**.

3. Haga clic o pulse en **Guardar entidad** para enviar los cambios.
   
    > [!IMPORTANT]
    > Los cambios se perderán si no los guarda antes de abrir otra página en el explorador o de salir del explorador.

    Se le notificará cuando la operación finalice correctamente. Si la operación no se realiza correctamente, aparece un mensaje de error que indica los problemas que se han producido y cómo puede corregirlos.

## <a name="best-practices-and-restrictions"></a>Prácticas recomendadas y restricciones
Cuando cree y modifique campos, tenga en cuenta lo siguiente:

* No puede modificar o eliminar campos del sistema ni sus valores.
* En una entidad estándar, no puede modificar o eliminar un campo (predeterminado) estándar, agregar un campo que requiera datos o efectuar ningún otro cambio que pudiera dañar una aplicación basada en esa entidad.
* En una entidad personalizada, debe asegurarse de que los cambios realizados no dañen ninguna aplicación basada en esa entidad.
* Debe asignar a cada campo personalizado un nombre que sea único en la entidad y no es posible cambiar el nombre de un campo después de crearlo.

## <a name="next-steps"></a>Pasos siguientes
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)
* [Crear una regla de negocio](data-platform-create-business-rule.md)
* [Crear una aplicación usando entidades](../canvas-apps/data-platform-create-app.md)
* [Crear una aplicación desde cero usando una base de datos de Common Data Service](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo común de datos de Microsoft PowerApps, recopilamos y almacenamos la entidad personalizada y los nombres de campo en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo común de datos para los clientes. La entidad y los nombres de campo que los creadores crean nos ayudan a comprender los escenarios que son comunes en la comunidad de Microsoft PowerApps y a determinar los huecos en la cobertura de las entidades estándar del servicio, como los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa o replica fuera de la región en la que se proporciona la base de datos. No obstante, tenga en cuenta que la entidad personalizada y los nombres de campo se pueden replicar en las regiones y que se eliminan de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a proteger su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).

