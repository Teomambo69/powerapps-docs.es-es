---
title: Crear una entidad personalizada | Microsoft Docs
description: Aprenda a crear una entidad personalizada en Power Apps.
author: Mattp123
ms.service: powerapps
ms.component: cds
ms.topic: quickstart
ms.date: 12/23/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d5ce493618d5a7b7d736f56714fcfa2a1c6ba068
ms.sourcegitcommit: da1a13776f3e27d6b3d2157d17196681e6fe3619
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2019
ms.locfileid: "2922844"
---
# <a name="create-a-custom-entity"></a>Creación de una entidad personalizada
En Power Apps, una *entidad* define la información de la que desea realizar un seguimiento en forma de registros, que incluyen normalmente propiedades como el nombre, ubicación, productos, correo electrónico, y teléfono de la compañía. A continuación puede exponer los datos desarrollando una aplicación que haga referencia a la entidad. Power Apps ofrece entidades estándar “listas para usar” que cubren los escenarios típicos de una organización (como citas de seguimiento), pero puede haber ocasiones en las que necesite crear entidades personalizadas para almacenar datos que sean específicos de la organización.

En este tema, aprenderá a crear una entidad personalizada llamada Valoración de producto que puede usar para crear una aplicación que muestre calificaciones y comentarios de los productos que vende su compañía.

## <a name="prerequisites"></a>Requisitos previos
Para seguir este procedimiento, debe tener un rol de seguridad de administrador del sistema o personalizador del sistema en Common Data Service.

## <a name="sign-in-to-power-apps"></a>Iniciar sesión en Power Apps
Iniciar sesión en Power Apps en [https://make.powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="create-an-entity"></a>Crear una entidad
1. En el panel de navegación, haga clic o pulse en **Datos** para expandirlo y haga clic o pulse en **Entidades**.

    ![Lista de entidades y sus detalles](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. en la barra de comandos, haga clic o pulse en **Nueva entidad**.

    Antes de crear una entidad, compruebe la [referencia de entidad](../../developer/common-data-service/reference/about-entity-reference.md) para ver una descripción de las entidades estándar disponibles. Estas entidades cubren los escenarios típicos. Si una de estas entidades cumple sus requisitos tal como están o tras pocos cambios, puede ahorrar tiempo comenzando con esa entidad. 

3. En el panel **Nueva entidad**, haga lo siguiente:

    a. En el cuadro **Nombre para mostrar**, introduzca **Valoración de producto**.

    Observe que los cuadros siguientes se rellenan automáticamente mientras escribe un nombre para mostrar:

    * **Nombre para mostrar plural** - Este cuadro se rellena automáticamente cuando introduce un nombre para mostrar, pero puede cambiarlo si fuera necesario. El nombre para mostrar plural es el nombre de la entidad en la API web de Common Data Service y se usa para interactuar con esta entidad desde Power Apps o Flow.
    * **Nombre** - Este cuadro también se rellena automáticamente al escribir un nombre para mostrar. El prefijo se definió cuando se creó el entorno y garantiza que las entidades que cree se puedan exportar e importar en otros entornos sin entrar en conflicto con otros nombres de entidad. Puede cambiar este prefijo actualizándolo en su publicador para la solución predeterminada de Common Data Service. Para evitar que se dañen las aplicaciones existentes, no puede cambiar el nombre después de guardar la entidad.

       > [!NOTE]
       > Para que el nombre de la entidad funcione con la [búsqueda de conocimiento incrustado de Dynamics 365 for Customer Service](/dynamics365/customer-engagement/customer-service/set-up-knowledge-management-embedded-knowledge-search), la longitud máxima del nombre de entidad, incluido el prefijo del editor, no puede superar los 24 caracteres.

    b. En la sección **Campo principal**, en el cuadro **Nombre para mostrar**, reemplace **Nombre** por **Valoración del producto**. 

    De forma predeterminada, cada entidad contiene un campo **Campo principal**, que se usa en los campos de búsqueda al establecer relaciones con otras entidades. El campo principal almacena normalmente el nombre o la descripción principal de los datos almacenados en la entidad. Puede actualizar el nombre y el nombre para mostrar del campo principal antes de guardar la entidad por primera vez.

    Además, observe que el campo principal también tiene su propio cuadro **Nombre** , que funciona semejantemente al nombre de entidad descrito anteriormente. El nombre del campo principal se rellena automáticamente cuando se especifica un nombre para mostrar, usa la misma prefijo que la entidad, y no se puede cambiar después de que se crean a la entidad.

    c. Abra la sección **Más valores** y expanda el acordeón **Descripción**. Puede especificar una descripción para la entidad si lo desea (las descripciones son útiles si otras personas usan esta entidad). 

    d. Selecciona la opción de entidad **Actvidad** de la lista desplegable **Elegir tipo de entidad** para habilitar una entidad como una actividad.

    e. Asegúrese de que la casilla **Mostrar en menús de actividades** está seleccionada. Esta opción garantiza que la actividad está disponible en el menú de actividades.

      > [!Note]
      > Asegúrese de habilitar la opción **Mostrar en menús de actividades** antes de crear la entidad.

    f. Expanda **Crear y actualizar configuración** y seleccione la casilla **Habilitar formularios de creación rápida**. Esta opción garantiza que puede usar el formulario de creación rápida para crear un registro.
    
    g. Cuando acabe, haga clic en **Crear**.
     
    ![Entidad nueva](./media/data-platform-cds-create-entity/newentitypanel.png "Panel Nueva entidad")

4. En la página de detalles de la entidad, observe que la entidad ahora se está aprovisionando en segundo plano. Una vez completado el aprovisionamiento, la entidad se guardará y estará disponible para su uso en aplicaciones. Los campos, relaciones, y las claves se pueden agregar a la entidad en cualquier momento (incluso mientras el aprovisionamiento aún está en curso), pero las vistas, formularios, gráficos, paneles, y las reglas de negocio se pueden agregar sólo a la entidad después de completar el aprovisionamiento.

    ![Detalles de entidad](./media/data-platform-cds-create-entity/newentitydetails.png "Nuevos detalles de la entidad")

5. En la pestaña **Campos**, observe el **Campo principal** al que dio nombre en el paso anterior. Haga clic o pulse en el campo **Campo principal** para abrir el panel **Campo principal** si desea realizar personalizaciones adicionales al campo. Tenga en cuenta que **Nombre** ya no se puede cambiar más, ya que la entidad ya se ha guardado.

5. Para agregar un campo a la entidad, realice lo siguiente:
 
    a. En la barra de comandos, haga clic o pulse en **Agregar campo** para abrir el panel **Propiedades de campo**.

    b. En el cuadro **Nombre para mostrar**, introduzca **Fecha de valoración**.

    c. En la lista desplegable **Tipo de datos** seleccione **Solo fecha**.

    d. Haga clic o pulse en la casilla **Necesario**.
    
    e. Haga clic o pulse en **Hecho**.
     
    Para obtener más información, consulte [Administrar campos de una entidad](data-platform-manage-fields.md).

    > [!div class="mx-imgBorder"] 
    > ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Panel Nuevo campo")

6. Repita el paso anterior para agregar tres campos más con las siguientes configuraciones:
    * **Nombre para mostrar** = Calificación de productos; **Tipo de datos** = Número entero; haga clic o pulse en la casilla **Necesario**
    * **Nombre para mostrar** = Nombre del revisor; **Tipo de datos** = Texto
    * **Nombre para mostrar** = Comentario del revisor; **Tipo de datos** = Texto

    Cuando finalice, debería tener cinco campos en la lista de la página de detalles de la entidad.

    ![Lista de campos](./media/data-platform-cds-create-entity/addedfields.png "Lista de campos")

    Tenga en cuenta que todas las entidades tienen campos del sistema de solo lectura. De forma predeterminada, los campos del sistema no se muestran en la lista de campos aunque existan en la entidad. Para ver todos los campos, cambie el filtro en la barra de comandos de **Predeterminado** a **Todos**. Para obtener más información sobre los metadatos relacionados con una entidad, consulte [Metadatos de entidad](../../developer/common-data-service/entity-metadata.md).

7. Haga clic en **Guardar entidad** para guardar los últimos cambios a la entidad.

    La entidad Valoración de producto debería aparecer en la lista de entidades en la base de datos. Si no la ve, cambie el filtro en la barra de comandos de **Predeterminado** a **Personalizado**.

    > [!div class="mx-imgBorder"] 
    > ![Filtro](./media/data-platform-cds-create-entity/filter.png "Selección de filtro")

## <a name="next-steps"></a>Pasos siguientes
En este tema, ha aprendido a crear una entidad personalizada llamada Valoración de producto que puede usar para crear una aplicación que muestre calificaciones y comentarios para cada uno de los productos que vende una determinada compañía. A continuación, aprenderá a definir relaciones entre entidades (en este caso entre la entidad estándar Producto y la entidad personalizada Valoración de producto) para que pueda asociar cada producto con las reseñas y comentarios que recibe.

> [!div class="nextstepaction"]
> [Crear una relación](data-platform-entity-lookup.md)

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo común de datos de Microsoft Power Apps, Microsoft recopila y almacena la entidad personalizada y los nombres de campo en nuestros sistemas de diagnóstico. Usamos esta información para mejorar el modelo común de datos para los clientes. La entidad y los nombres de campo que los creadores de la aplicación crean nos ayudan a comprender los escenarios que son comunes en la comunidad de Microsoft Power Apps y a determinar los huecos en la cobertura de las entidades estándar del servicio, como los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa o replica fuera de la región en la que se proporciona la base de datos. No obstante, tenga en cuenta que la entidad personalizada y los nombres de campo se pueden replicar en las regiones y que se eliminan de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a proteger su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).
