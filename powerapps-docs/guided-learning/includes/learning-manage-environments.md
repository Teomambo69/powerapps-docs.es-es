Si ha seguido el curso hasta ahora, habrá pasado algo de tiempo trabajando en web.powerapps.com. Tanto si lo sabía como si no, ha estado trabajando en un determinado *entorno* todo el tiempo. Un entorno es simplemente una agrupación de aplicaciones y otros recursos (más información sobre esto en un momento). Mire en la esquina superior derecha de la pantalla en web.powerapps.com y verá un menú desplegable que le muestra el entorno actual.

![Selector del entorno](./media/learning-manage-environments/environment-picker.png)

Si no está familiarizado con PowerApps, es posible que tenga solo el entorno predeterminado en este momento. Haga clic o pulse en el menú para ver si hay otros entornos disponibles.

## <a name="why-use-environments"></a>¿Por qué se usan los entornos?
Un entorno es un contenedor de aplicaciones y otros recursos como conexiones de datos y flujos de Microsoft Flow. Es una forma de agrupar los elementos según los requisitos empresariales. Hay varias razones para crear entornos adicionales además del predeterminado:

* **Separar el desarrollo de aplicaciones por departamento**: en una organización grande, cada departamento podría trabajar en un entorno diferente.
* **Admitir la administración del ciclo de vida de las aplicaciones (ALM)**: podría tener entornos independientes para las aplicaciones en desarrollo y para aquellas aplicaciones que ya ha finalizado y compartido.
* **Administrar el acceso a los datos**: cada entorno puede tener su propia base de datos de Common Data Service y las demás conexiones de datos son específicas del entorno (es decir, no se comparten entre entornos).

Hay que tener en cuenta que los entornos son importantes solo para los creadores de aplicaciones y los administradores de PowerApps. Cuando comparte una aplicación con un usuario, este simplemente ejecutará la aplicación siempre que tenga los permisos adecuados. El usuario no tendrá que preocuparse de qué entorno procedía.

## <a name="create-an-environment"></a>Creación de un entorno
Hasta ahora en este curso, nos hemos centrado en los creadores de aplicaciones, pero son los administradores los que crean y mantienen los entornos. Aunque no sea un administrador, esta información puede resultarle útil cuando hable a su administrador acerca de la configuración de entornos. En el centro de administración de PowerApps, haga clic o pulse en **Entornos** y, a continuación, en **Nuevo entorno**. En la pantalla **Nuevo entorno**, escriba un nombre para el entorno, seleccione una región, seleccione si desea crear una base de datos de Common Data Services para el entorno y haga clic o pulse en **Crear un entorno**.

![Creación de un entorno](./media/learning-manage-environments/create-environment.png)

Y eso es todo. Ahora ya tiene un nuevo entorno en el que trabajar. Si vuelve a web.powerapps.com, lo verá en el menú desplegable de entornos.

## <a name="manage-access-to-an-environment"></a>Administración del acceso a un entorno
Tiene acceso a un entorno si es:

* Un **administrador del entorno**: tiene permisos completos en el entorno.
* Un **creador del entorno**: puede ver todas las aplicaciones, crear aplicaciones y trabajar con Common Data Service (también se pueden aplicar otros permisos).

Como administrador, puede conceder acceso a un entorno desde la pestaña **Entornos**. En primer lugar, haga clic o pulse en un entorno. Para agregar a alguien (un **creador de entorno** en este ejemplo), haga clic o pulse en **Environment roles** (Roles de entorno) y, a continuación, en **Environment Maker** (Creador de entorno). Desde allí, agregue usuarios o grupos al rol y haga clic en **Guardar**.

![Administrar acceso al entorno](./media/learning-manage-environments/environment-access.png)

Ahora ya comprende las ventajas de los entornos y cómo crearlos y conceder acceso a ellos. Incluso si no tiene un rol de administrador, es útil saber cómo funciona. Esto nos lleva al final de la sección de administración de aplicaciones y ya está preparado para pasar a la siguiente sección, "Administración de datos", que se centra en Common Data Service.

