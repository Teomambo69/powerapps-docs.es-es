---
title: Inicio rápido para crear una entidad personalizada | Microsoft Docs
description: En este inicio rápido obtendrá información sobre cómo crear un entidad personalizada en PowerApps.
author: Mattp123
ms.service: powerapps
ms.component: cds
ms.topic: quickstart
ms.date: 05/01/2018
ms.author: matp
ms.openlocfilehash: a7fed26dafcf0b1d73ae6ba362964de5e9fd1ad5
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218726"
---
# <a name="quickstart-create-a-custom-entity"></a>Inicio rápido: Creación de una entidad personalizada
En PowerApps, una *entidad* define la información de la que se quiere realizar el seguimiento en forma de registros, que suelen incluir propiedades como el nombre de la empresa, la ubicación, los productos, el correo electrónico y el teléfono. Después, se pueden mostrar esos datos si se desarrolla una aplicación que haga referencia a la entidad. PowerApps ofrece entidades estándar listas para usar para abarcar los escenarios típicos de una organización (por ejemplo, el seguimiento de las citas), pero puede haber ocasiones en las que sea necesario crear entidades personalizadas para almacenar datos específicos de la organización.

En este inicio rápido, obtendrá información sobre cómo crear una entidad personalizada denominada Revisión del producto, que se puede usar para crear una aplicación en la que se muestren las clasificaciones y comentarios para los productos que vende la empresa.

## <a name="prerequisites"></a>Requisitos previos
Para seguir este tutorial rápido, se requieren los elementos siguientes:
* Licencia de Plan 2 de PowerApps o Plan 2 de Microsoft Flow. Como alternativa, se puede suscribir a una [evaluación gratuita del Plan 2 de PowerApps](https://web.powerapps.com/signup?redirect=marketing&email=).
* Un rol de seguridad de Administrador del sistema o Personalizador del sistema dentro de Common Data Service for Apps.

## <a name="sign-in-to-powerapps"></a>Inicio de sesión en PowerApps
Inicie sesión en PowerApps en [https://web.powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="create-an-entity"></a>Crear una entidad
1. En el panel de navegación, pulse o haga clic en **Datos** y, después, en **Entidades**.

    ![Lista de entidades y sus detalles](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. En la barra de comandos, pulse o haga clic en **Nueva entidad**.

    Antes de crear una entidad, consulte la [referencia de entidades](../../developer/common-data-service/reference/about-entity-reference.md) para obtener una descripción de las entidades estándar disponibles. Estas entidades abarcan los escenarios típicos. Si una de estas entidades cumple sus requisitos sin cambios o después de realizar cambios menores, puede ahorrar tiempo si empieza con esa entidad. 

3. En el panel **Nueva entidad**, en el cuadro **Nombre para mostrar**, escriba **Revisión del producto** y, después, escriba una descripción opcional (las descripciones son útiles si otros usuarios van a usar esta entidad). Los demás campos del panel se rellenan automáticamente, como se describe a continuación. Cuando termine, haga clic en **Siguiente**.

   * **Nombre para mostrar en plural**: este campo se rellena automáticamente cuando se escribe un nombre para mostrar, pero se puede cambiar si es necesario. El nombre para mostrar en plural es el nombre de la entidad en la API web de Common Data Service y se usa al interactuar con esta entidad desde PowerApps o Flow.
   * **Nombre**: este campo también se rellena automáticamente al escribir un nombre para mostrar. El prefijo se configuró al crear el entorno y garantiza que las entidades que se crean se puedan importar y exportar en otros entornos sin que entren en conflicto con otros nombres de entidad. Este prefijo se puede cambiar si se actualiza el prefijo en el editor para la solución predeterminada de Common Data Service. Para evitar que las aplicaciones existentes dejen de funcionar, no se puede cambiar el nombre después de guardar la entidad.
     
     ![Nueva entidad](./media/data-platform-cds-create-entity/newentitypanel.png "Panel Nueva entidad")

4. En la página de detalles de la entidad, pulse o haga clic en el campo **Nombre principal** para abrir el panel **Nombre principal** y, después, en el cuadro **Nombre para mostrar**, sustituya **Nombre principal** con **Revisión del producto**. En el cuadro **Nombre**, sustituya **PrimaryName** con **RevisionProducto** y, después, pulse o haga clic en **Listo**.
 
    De forma predeterminada, cada entidad contiene un campo Nombre principal, que los campos de búsqueda usan al establecer relaciones con otras entidades. Por lo general, en el campo Nombre principal se almacena el nombre o la descripción principal de los datos que se almacenan en la entidad. El nombre y el nombre para mostrar del campo Nombre principal se pueden actualizar antes de guardar la entidad por primera vez.

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/newentitydetails.png "Detalles de la nueva entidad")

5. Para agregar un campo a la entidad, siga estos pasos:
 
    a. En la barra de comandos, pulse o haga clic en **Agregar campo** para abrir el panel **Propiedades de campo**.

    b. En el cuadro **Nombre para mostrar**, escriba **Fecha de revisión**.

    c. En la lista desplegable **Tipo de datos**, seleccione **Solo fecha**.

    d. Pulse o haga clic en la casilla **Necesario**.
    
    e. Pulse o haga clic en **Listo**.
     
    Para más información, consulte [Administración de campos en una entidad](data-platform-manage-fields.md).

    ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Panel Nuevo campo")

6. Repita el paso anterior para agregar tres campos más con las configuraciones siguientes:
   * **Nombre para mostrar** = Clasificación de producto; **Tipo de datos** = Número entero; pulse o haga clic en la casilla **Necesario**.
   * **Nombre para mostrar** = Nombre del revisor; **Tipo de datos** = Texto.
   * **Nombre para mostrar** = Comentario de revisor; **Tipo de datos** = Texto.

     Cuando termine, debería tener cinco campos enumerados en la página de detalles de la entidad.

     ![Lista de campos](./media/data-platform-cds-create-entity/addedfields.png "Lista de campos")

     Tenga en cuenta que todas las entidades tienen campos del sistema de solo lectura. De forma predeterminada, los campos del sistema no se muestran en la lista de campos, aunque existan en la entidad. Para ver todos los campos, cambie el filtro en la barra de comandos de **Predeterminado** a **Todo**. Para obtener más información sobre los metadatos relacionados con una entidad, vea [Metadatos de entidad](../../developer/common-data-service/entity-metadata.md).

7. Haga clic en **Guardar entidad** para guardar la entidad y que esté disponible para su uso en las aplicaciones.

    La entidad Revisión del producto debe aparecer en la lista de entidades en la base de datos. Si no la ve, cambie el filtro en la barra de comandos de **Predeterminado** a **Personalizado**.

    ![Filtro](./media/data-platform-cds-create-entity/filter.png "Filtrar la selección")

## <a name="next-steps"></a>Pasos siguientes
En este inicio rápido, ha obtenido información sobre cómo crear una entidad personalizada denominada Revisión del producto que se puede usar para crear una aplicación en la que se muestren las clasificaciones y comentarios de cada producto que vende una empresa concreta. A continuación, obtendrá información sobre cómo definir relaciones entre las entidades (en este caso, entre la entidad estándar Producto y la entidad personalizada Revisión del producto) para que cada producto se pueda asociar con las revisiones y los comentarios que recibe.

> [!div class="nextstepaction"]
> [Crear una relación](data-platform-entity-lookup.md)

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, Microsoft recopila y almacena los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico. Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos que los creadores de aplicaciones crean nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).
