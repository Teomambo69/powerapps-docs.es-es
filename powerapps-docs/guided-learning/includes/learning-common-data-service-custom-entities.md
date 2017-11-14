Common Data Service está diseñado para todos los clientes empresas, desde las tiendas más pequeñas a las empresas más grandes. Common Data Model incluye un conjunto de entidades estándares que cubren muchos escenarios empresariales comunes y, como ya se indicó en el tema anterior, dichas entidades estándar se pueden extender. Pero a veces es necesario algo completamente diferente para solucionar los problemas específicos de su negocio. En ese caso necesita una entidad personalizada y en este tema se mostrará cómo crear una.

Hay dos maneras de crear una entidad:

* Crear la entidad desde cero. Eso es lo que haremos en este tema.
* Crear una entidad que se basa en otra entidad, mediante la copia tanto de los campos como de la configuración de dicha entidad, pero no de sus datos.

## <a name="creating-an-entity-from-scratch"></a>Creación de una entidad desde cero
En este ejemplo, se va a crear desde cero una entidad personalizada denominada Product review. Para empezar, en la pestaña **Entidades**, haga clic en **Nueva entidad**. Escriba un **nombre de entidad** (sin espacios ni caracteres especiales), un **nombre para mostrar** descriptivo y una **descripción** significativa. Haga clic en **Siguiente**.

![Nueva entidad](./media/learning-common-data-service-custom-entities/new-entity.png)

En la siguiente pantalla, verá los cinco campos predeterminados que contienen todas las entidades estándar y personalizadas. Haga clic en **Agregar campo** para empezar a agregar sus campos.

![Campos de entidad predeterminados](./media/learning-common-data-service-custom-entities/default-fields.png)

En este ejemplo, se van a agregar cuatro campos:

* **Fecha de revisión**, que es un campo de fecha y es requerido.
* **Clasificación de producto**, que es un campo entero y es requerido. Aquí se puede usar una lista desplegable que permita especificar solo ciertos valores (por ejemplo, 1-5), pero por el momento será algo más sencillo.
* **Nombre de revisor**, que es un campo de texto y no es requerido.
* **Comentario de revisor**, que es un campo de texto y tampoco es requerido. 

Cuando esté satisfecho con la entidad, haga clic en **Crear**. Cuando se crea la entidad, no tiene datos. En el tema siguiente, se mostrará cómo importar datos.

![Campos de entidad personalizada](./media/learning-common-data-service-custom-entities/custom-fields.png)

## <a name="creating-a-relationship-between-two-entities"></a>Creación de una relación entre dos entidades
Puesto que deseamos asociar cada revisión con un producto determinado, es preciso crear una relación entre las entidades Revisión de producto y Producto. En la entidad Revisión de producto, en la pestaña **Relaciones**, haga clic en **Nueva relación**. A continuación, seleccione una **entidad relacionada** y rellene los campos **Nombre**, **Nombre para mostrar** y **Descripción**. Haga clic en **Guardar** para crear la relación.

![Crear relación entre entidades](./media/learning-common-data-service-custom-entities/create-entity-relationship.png)

## <a name="connecting-to-a-custom-entity-in-powerapps-studio"></a>Conexión a una entidad personalizada en PowerApps Studio
La conexión a una entidad personalizada en PowerApps Studio se realiza de la misma forma que la conexión a una entidad estándar. Haga clic en **Nuevo** y, en **Common Data Service**, haga clic en **Diseño de teléfono**. Se ven las conexiones de datos disponibles a la izquierda y la lista de entidades a la derecha.

![Conexión a una entidad en PowerApps Studio](./media/learning-common-data-service-custom-entities/connect-to-custom-entity.png)

En el tema siguiente, se mostrará cómo administrar datos en Common Data Service.

