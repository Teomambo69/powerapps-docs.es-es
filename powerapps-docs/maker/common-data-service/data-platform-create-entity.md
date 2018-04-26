---
title: Inicio rápido para crear una entidad personalizada | Microsoft Docs
description: Inicio rápido para crear una entidad personalizada basada en otra entidad o desde cero.
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 2232083de556bafcc978423dafb0e98e564aaa3b
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-create-a-custom-entity"></a>Inicio rápido: Creación de una entidad personalizada
Puede crear una entidad personalizada para almacenar datos específicos de su organización. Después, puede mostrar dichos datos si desarrolla una aplicación que haga referencia a la entidad. Después de crear una entidad, puede [crear o modificar uno o varios de sus campos](data-platform-manage-fields.md) y [crear relaciones entre entidades](data-platform-entity-lookup.md).

En estas instrucciones se mostrará cómo crear manualmente una entidad personalizada; también se puede usar Power Query para crear una entidad basada en los datos existentes. Para obtener más información, vea [Creación de una entidad con Power Query](data-platform-cds-newentity-pq.md).

> [!NOTE]
> Antes de crear una entidad, vea la [referencia de entidades](../../developer/common-data-service/reference/about-entity-reference.md). Estas entidades tratan los escenarios típicos, como cuentas y contactos. Si una de estas entidades cumple sus requisitos sin cambios o después de realizar cambios menores, puede ahorrarse tiempo partiendo de ella.

## <a name="create-an-entity"></a>Crear una entidad
1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/entitylist.png "lista de entidades")

2. En la barra de comandos, pulse o haga clic en **Nueva entidad**.
3. En el campo **Nombre para mostrar**, escriba un nombre que sea fácilmente reconocible para hacer referencia a esta entidad en el futuro. Esto también se usa en formularios, gráficos y otros objetos creados con esta entidad. Observará que se rellenan otros dos campos:

    * Nombre para mostrar en plural: se usa al interactuar con esta entidad desde PowerApps o Flow, y se usa como el nombre de la entidad en la API web de Common Data Service. El nombre en plural se debe generar de forma automática, pero se puede cambiar.
    * Nombre. Se trata del nombre único de la entidad, no puede contener caracteres especiales ni espacios y debe ser único. El nombre también incluye un prefijo que se configura al crear el entorno y que se usa para garantizar que las entidades que se crean se puedan importar y exportar en otros entornos sin que entren en conflicto con otros nombres de entidad. Este prefijo se puede cambiar si se actualiza el prefijo en el editor para la solución predeterminada de Common Data Service.

    > [!NOTE]
    > Los campos **Nombre para mostrar** se pueden actualizar en cualquier momento para mostrarlos de otra forma en las aplicaciones; el campo **Nombre** no se puede cambiar después de guardar la entidad, ya que se podría interrumpir una aplicación existente.

    ![Nueva entidad](./media/data-platform-cds-create-entity/newentitypanel.png "Panel Nueva entidad")

4. Haga clic en **Siguiente** y se le dirigirá a la página de detalles de la entidad. De forma predeterminada, todas las entidades se inician con un campo, "Nombre principal", que se usa cuando se crean búsquedas sobre esta entidad. Por lo general, se debe usar para almacenar el nombre o la descripción principal de los datos que se almacenan en la entidad.

    > [!NOTE]
    > El nombre y el nombre para mostrar del campo **Nombre principal** se pueden actualizar antes de guardar la entidad por primera vez. Por ejemplo, si quiere que este campo se denomine "Nombre del alumno" en lugar de "Nombre principal"

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/newentitydetails.png "Detalles de la nueva entidad")

5. Opcional: agregue un campo de texto a la entidad haciendo clic en **Agregar campo**. En el panel Nuevo campo, escriba el **Nombre para mostrar** para el campo y seleccione el tipo de datos. Para más información, consulte [Administración de campos en una entidad](data-platform-manage-fields.md).

    ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Panel Nuevo campo")


6. Haga clic en **Listo** para agregar el campo y repita el paso 5 para agregar más campos.
7. Haga clic en **Guardar entidad** para guardar la entidad y que esté disponible para su uso en las aplicaciones.

    La entidad aparece en la lista de entidades de la base de datos. Para ver las entidades que ha creado, puede cambiar el filtro en la barra de comandos de "Predeterminado" a "Personalizado".

## <a name="system-fields"></a>Campos del sistema
Todas las entidades tienen campos del sistema. Estos campos son de solo lectura. Por tanto, no se pueden modificar ni eliminar, y tampoco se les asignan valores. De forma predeterminada, los campos del sistema no se mostrarán en la lista de campos, aunque existan en la entidad. Para ver todos los campos, puede cambiar el filtro en la barra de comandos de **Predeterminado** a **Todo**.

Para obtener más información sobre los metadatos relacionados con una entidad, vea [Metadatos de entidad](../../developer/common-data-service/entity-metadata.md)

## <a name="next-steps"></a>Pasos siguientes
* [Administrar campos de una entidad](data-platform-manage-fields.md)
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)
* [Generar una aplicación mediante una base de datos de Common Data Service](../canvas-apps/data-platform-create-app.md)
* [Create an app from scratch using a Common Data Service database](../canvas-apps/data-platform-create-app-scratch.md) (Crear una aplicación desde cero mediante una base de datos de Common Data Service)

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, recopilamos y almacenamos los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos creados nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).

