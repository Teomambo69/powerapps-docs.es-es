Hasta ahora en esta sección, se ha generado una aplicación basada en la entidad Case de Common Data Service, se ha explorado la aplicación para ver cómo se ha configurado y se ha personalizado la aplicación de varias maneras. En el tema final de esta sección se aporta otra entidad estándar y se usa Microsoft Flow para enviar un correo electrónico. La aplicación desencadenará un flujo para que la persona que abrió un caso reciba una notificación si este se actualiza. Vamos a completar un escenario determinado en este tema, pero las aptitudes que adquiera se pueden aplicar a muchos tipos de aplicaciones. Comencemos por las entidades.

## <a name="review-entity-relationships"></a>Revisión de las relaciones de entidades
Se va a agregar la entidad Contact en breve, pero primero veremos cómo se relacionan entre sí las entidades Case y Contact. En la entidad Case, puede ver que uno de los campos es **CurrentContact**, con un tipo de datos de **Búsqueda**. Esto significa que este campo se usa en una relación con otra tabla.

![Campos de la entidad Case](./media/learning-case-app-add-source/case-fields.png)

En la pestaña **Relaciones**, verá que la entidad relacionada es **Contact**. Tenga esto en cuenta porque se usará esta relación más adelante en este tema.

![Relaciones de la entidad Case](./media/learning-case-app-add-source/case-relationships.png)

## <a name="add-an-entity-to-the-app"></a>Incorporación de una entidad a la aplicación
La incorporación de un origen de datos en PowerApps es sencilla. En el panel derecho, haga clic o pulse en **Orígenes de datos** y, a continuación, en **Agregar origen de datos**. En este caso, elija la conexión de **Common Data Service** y seleccione la entidad **Contact**. Después de hacer clic o pulsar en **Conectar**, la entidad se agregará a la aplicación. 

![Incorporación de la entidad Contact](./media/learning-case-app-add-source/contact-entity.png)

Tenga en cuenta que en este ejemplo, estamos agregando datos desde otra entidad, pero puede combinar datos de varios orígenes en sus aplicaciones. 

## <a name="look-up-contact-information"></a>Búsqueda de la información de contacto
Ahora que tenemos acceso a los datos de la entidad Contact en nuestra aplicación, es hora de empezar a usarlos. Como se mencionó en la introducción, queremos enviar un correo electrónico cuando se actualice un caso. Usaremos dos fórmulas y un flujo para lograr esto. La primera fórmula es para la pantalla de edición, específicamente la propiedad OnSelect del botón Guardar.

![Pantalla de edición de la aplicación](./media/learning-case-app-add-source/edit-screen.png)

De forma predeterminada, este botón utiliza la fórmula `SubmitForm(EditForm1)` para enviar la actualización cuando un usuario edita los datos del formulario. Tenemos que agregar la fórmula para que busque en primer lugar la información de contacto de la persona que abrió el caso actual y, a continuación, almacene la información localmente en la aplicación: 

```UpdateContext({contact:LookUp(Contact, ContactId=BrowseGallery1.Selected.CurrentContact.ContactId)}); SubmitForm(EditForm1)```

Sí, es algo complicado, pero James hace un trabajo excelente a la hora de explicar esta fórmula con detalle a partir del minuto 2:04 del vídeo.

## <a name="trigger-a-flow-from-the-app"></a>Desencadenamiento de un flujo desde la aplicación
Ahora que sabemos quién es el contacto para cada caso, podemos enviarles un correo electrónico. Se puede enviar un correo electrónico directamente desde la aplicación, pero en este ejemplo vamos a mostrarle cómo desencadenar un flujo desde la aplicación. Este es el flujo, que es tan simple como parece: enviar un correo electrónico en función de una acción de una aplicación. No entraremos en más detalles sobre los flujos aquí, pero hay toda una serie de Aprendizajes guiados para Microsoft Flow. 

![Flujo para enviar un correo electrónico](./media/learning-case-app-add-source/email-flow.png)

De vuelta en la aplicación, es necesario llamar al flujo en función de un evento. Vamos a usar la propiedad OnSuccess del formulario de edición, por lo que el flujo se desencadenará cuando se realice correctamente la edición. Haga clic o pulse en el formulario de edición, después, en la cinta de opciones, haga clic o pulse en **Acción** > **Flujos**. Seleccione el flujo que desea utilizar. 

![Flujo para enviar un correo electrónico](./media/learning-case-app-add-source/add-flow-action.png)

El flujo está ahora asociado con el evento OnSuccess del formulario de edición y podemos hacer referencia al contacto para el correo electrónico. La siguiente fórmula llama al flujo con la dirección de correo electrónico de la persona que abrió el caso, así como con una línea de asunto y el cuerpo del correo electrónico. 

```CaseResolvedEmailConfirmation.Run(contact.EmailPrimary, "Your case has been updated", "Check it out")```

Eso es todo lo que necesita para agregar un origen de datos a la aplicación y desencadenar un flujo que envía un correo electrónico. Si aún no ha visto los vídeos de esta sección, le recomendamos que lo haga. Estos aportan una gran cantidad de detalles sobre asuntos que tuvimos que explicar con rapidez en este tema.

## <a name="wrapping-it-all-up"></a>En resumen
Esto nos lleva al final de esta sección. Esperamos que haya disfrutado y aprendido un montón. Empezamos generando una aplicación básica a partir de una entidad y exploramos un poco esta aplicación para entender cómo se había configurado. Se empleó una gran cantidad de tiempo en la personalización de la aplicación y, a continuación, se agregó un origen de datos y vimos cómo desencadenar un flujo. Se creó una aplicación de administración de casos específicos en esta sección, pero las aptitudes aprendidas se pueden aplicar a muchos tipos de aplicaciones. Como hemos mencionado al principio de esta sección, si desea profundizar en una aplicación de administración de casos más compleja, asegúrese de consultar la plantilla que está disponible en PowerApps Studio para Windows. 

A continuación, pasaremos a las aplicaciones de administración. La sección de administración muestra cómo compartir y controlar las versiones de las aplicaciones, y presenta los entornos, que son contenedores de aplicaciones, datos y otros recursos. 

