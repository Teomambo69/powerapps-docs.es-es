Es estupendo compilar aplicaciones que satisfagan sus propias necesidades empresariales, pero lo realmente estupendo de PowerApps es que puede compartir las aplicaciones con otras personas. Ahora que sabe cómo compilar una aplicación, en este tema aprenderá a compartirla. Puede compartir una aplicación con usuarios o grupos específicos, o puede compartirla con toda la organización. Cuando se comparte una aplicación con otros usuarios, estos pueden ejecutarla desde Dynamics 365 en un explorador o en PowerApps Mobile para Windows, iOS o Android. Si concede a alguien permisos de colaborador también podrán actualizar la aplicación.

## <a name="prepare-to-share-an-app"></a>Prepararse para compartir una aplicación
Debe guardar una aplicación en la nube para poder compartirla con alguien. Asigne a la aplicación un nombre significativo y una descripción, para que los usuarios sepan de qué trata la aplicación y puedan elegirla fácilmente de una lista. En PowerApps Studio, haga clic o pulse en **Archivo** y, a continuación, escriba una descripción.

![Descripción de la aplicación](./media/learning-manage-share-apps/app-description.png)

Tenga en cuenta que los cambios que realice en una aplicación compartida llegarán a los usuarios con los que la compartió tan pronto como guarde los cambios. Esto puede ser bueno si mejora la aplicación, pero también puede afectar a otros usuarios si quita o cambia de forma significativa las características.

## <a name="share-an-app"></a>Compartir una aplicación
En web.powerapps.com, en el icono de una aplicación, haga clic en los puntos suspensivos (. . .) y, después, en **Compartir**.

![Compartir una aplicación desde web.powerapps.com](./media/learning-manage-share-apps/share-app.png)

Desde aquí, puede compartir una aplicación y controlar también las versiones de esta, asunto que abordaremos en el siguiente tema. Especifique los usuarios y grupos con los que compartir la aplicación y qué rol debe tener cada uno: **usuario** o **colaborador**. Haga clic o pulse en **Guardar**.

![Seleccionar usuarios y grupos](./media/learning-manage-share-apps/select-users.png)

Si decide notificar a los usuarios por correo electrónico, todos los usuarios con los que compartió la aplicación recibirán un correo electrónico con un vínculo a Dynamics 365. Los colaboradores de la aplicación también recibirán un vínculo a web.powerapps.com.  Si alguien no sigue el vínculo a Dynamics 365, la aplicación no aparecerá para ellos allí. Estará en AppSource, pero tendrán que agregarla a Dynamics 365 por sí mismos.

![Aplicación en Dynamics 365](./media/learning-manage-share-apps/dynamics-365.png)

## <a name="permissions-and-licensing"></a>Permisos y licencias
No vamos a entrar en detalles sobre los permisos y licencias, pero queremos explicar un par de conceptos básicos relativos al uso compartido:

* Los usuarios y colaboradores necesitan permisos para todas las conexiones de datos y puertas de enlace que utilice una aplicación compartida. Algunos permisos vienen implícitos en la aplicación, pero otros se deben conceder explícitamente.
* Si la aplicación usa entidades de Common Data Service, los usuarios y los colaboradores necesitan tener acceso a la base de datos de Common Data Service. Los colaboradores también necesitarán una licencia de PowerApps "P2" si trabajan directamente con entidades.

Compartir aplicaciones es fácil y es una excelente manera de hacer que una aplicación que le resulta útil se ponga a disposición de personas de su organización. En el siguiente tema explicaremos cómo controlar qué versión de una aplicación está activa cuando utiliza y comparte la aplicación.

