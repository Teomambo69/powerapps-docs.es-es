---
title: Transformar el formulario de InfoPath en una aplicación de lienzo | Microsoft Docs
description: Comience a transformar su formulario InfoPath a PowerApps con información sobre escenarios comunes y sobre cómo crear estos elementos en una aplicación de lienzo.
author: richardriley99
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/05/2018
ms.author: rriley
ms.openlocfilehash: a249d0a9096117badfe3e4eb7ad9dcf6b75662a1
ms.sourcegitcommit: e3f5a2bef64085d02aec82e62ff94ae8a4d01d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39470118"
---
# <a name="transform-your-infopath-form-to-powerapps"></a>Transformar el formulario de InfoPath en PowerApps

¿Ha creado grandes contenidos en InfoPath, pero le gustaría ofrecerlos en una plataforma más sólida?

## <a name="key-advantages-of-powerapps-over-infopath"></a>Principales ventajas de PowerApps con respecto a InfoPath

Como la mayoría de los usuarios avanzados de InfoPath, llevará cierto tiempo usando un único conjunto de aptitudes para crear sus formularios. Está satisfecho con los formularios, pero también sabe que tienen sus limitaciones: el estilo &quot;clásico&quot;, una experiencia para dispositivos móviles no del todo satisfactoria, la incertidumbre de su viabilidad futura y la imposibilidad de conectar los formularios a otros servicios sin necesidad de escribir código.

El equipo de PowerApps ha sabido de estos y otros muchos desafíos. Ha trabajado arduamente para incorporar una mejor experiencia y permitirle crear aplicaciones de lienzo aprovechando sus conocimientos empresariales y tecnológicos existentes. Mediante PowerApps, se pueden compilar e implementar rápidamente las soluciones empresariales adecuadas sin escribir código.

**Eficacia futura con PowerApps**  
PowerApps es una plataforma de software como servicio (SaaS) que está diseñada para permitir la compilación rápida de aplicaciones de elevada funcionalidad que se pueden implementar en la Web, en SharePoint, en Dynamics 365, en Teams, en Power BI o en un dispositivo móvil sin ningún esfuerzo extra. Y, al ser tan fáciles de implementar (basta con facilitar la dirección URL a la aplicación publicada), también son muy fáciles de actualizar.

**Aplicaciones compartidas**  
¿Alguna vez ha intentado compilar una aplicación y luego publicarla en la tienda de aplicaciones de Google o Apple? Es complicado. Otro reto es implementar una segunda aplicación o actualizar una existente, dado que el proceso que deberán seguir los usuarios incluye mucho más pasos. Con PowerApps es diferente. Los usuarios solo tienen que instalar la aplicación de Microsoft PowerApps desde su tienda de aplicaciones e iniciar sesión con el nombre de usuario y la contraseña de su cuenta de Microsoft. A continuación, ya podrán disfrutar de las aplicaciones funcionales que ha compartido con ellos. En el futuro, si actualiza las aplicaciones o les envía aplicaciones nuevas, estas aparecerán en sus dispositivos. Disponer de aplicaciones móviles sin tener que administrar los dispositivos constituye una gran ventaja para usted y el negocio.

**Hablando de dispositivos móviles**  
Con PowerApps se puede aprovechar la funcionalidad del dispositivo móvil del usuario, como la aceleración, la cámara, la brújula, la información de conexión y las señales de ubicación, y todo ello desde dentro de la aplicación. Esto abre todo un mundo de posibilidades para compilar aplicaciones orientadas al trabajo. Y, por supuesto, la funcionalidad táctil es automática en PowerApps, por lo que no es necesario escribir código al compilar la aplicación.

**Lista para usar**  
Con InfoPath la norma era trabajar con datos de un solo origen de datos. Sin embargo, si se quería actualizar alguna otra cosa (por ejemplo, una lista de SharePoint de otra colección de sitios) o conectarse a servicios externos, la cosa se complicaba y conceptos como código subyacente suponían un quebradero de cabeza. Con PowerApps esto no ocurre, puesto que está diseñado para que en una misma aplicación pueda trabajar con varios orígenes de datos y establecer distintas conexiones de servicio. Actualmente, hay [más de 150 conectores](https://docs.microsoft.com/powerapps/connections-list#all-connectors) que admiten una combinación de datos locales y en la nube, servicios de Microsoft Office 365 y Azure como Flow y Dynamics 365, y multitud de servicios de terceros como Dropbox, Google, Salesforce y Slack. Ahora puede compilar soluciones que se escalan donde lo necesitan los usuarios, no solo en la ubicación original de los datos.

## <a name="powerapps-and-sharepoint-even-better-together"></a>PowerApps y SharePoint: mejor incluso juntos

PowerApps es una herramienta excelente para mejorar su experiencia de SharePoint de dos maneras. Tiene la opción de personalizar los formularios para una lista de SharePoint o para crear una aplicación independiente que trabaje con datos de SharePoint.

**Personalizar un formulario de SharePoint** es muy útil si los usuarios van a usar la lista en su trabajo cotidiano, pero se quiere personalizar cómo se agregan, visualizan y modifican los elementos de la lista de SharePoint. Si hace clic en **Personalizar formularios**, se creará una &quot;aplicación de formularios&quot; de una sola pantalla que cambiará de modo (nuevo/editar/ver) en función del contexto. Estas aplicaciones son administradas por SharePoint; sus permisos son los mismos que los permisos de lista para edición y visualización.

**Crear una aplicación de lienzo PowerApps desde SharePoint** permite ejecutar la aplicación por sí sola en un dispositivo móvil. También pueden insertarse en una página de SharePoint. Si hace clic en esto se creará una aplicación de tres pantallas (vista de lista, nuevo o editar formulario, ver formulario).  El modelo de permiso/uso compartido de estas aplicaciones no está vinculado a SharePoint, sino que se administra desde PowerApps.

Ahora que comprende la diferencia entre las dos opciones, la siguiente sección le proporcionará una visión general del uso de cada una de ellas.

## <a name="sharepoint-forms"></a>Formularios de SharePoint

El equipo de PowerApps y el de SharePoint han trabajado juntos para crear una nueva forma de personalización que se puede utilizar con SharePoint.  Si es como la mayoría de los desarrolladores de InfoPath, conoce las posibilidades de interacción entre InfoPath y SharePoint. Aunque SharePoint es un servicio fantástico, los formularios predeterminados son un poco básicos y no permiten personalizarlos ni usar la lógica de negocios sin InfoPath. Bueno, eso era antes.

Con PowerApps, ya puede personalizar los formularios de lista como una funcionalidad nativa. Y, al hacerlo, obtendrá todo el rendimiento de PowerApps. En la siguiente captura de pantalla, puede ver un ejemplo de un formulario PowerApps con un informe de Power BI insertado.  Toda la solución se realizó en menos de 15 minutos.

![Integración con SharePoint](./media/transform-infopath/sharepoint-integration.png)

Otra característica importante de PowerApps es la capacidad de conectarse fácilmente a otra colección de sitios de SharePoint o a otro entorno desde el mismo formulario. Por ejemplo, ¿quiere crear un formulario que muestre y actualice al mismo tiempo los datos de SharePoint Online y el entorno local de SharePoint? Si quiere, puede hacerlo. Instale la [puerta de enlace de datos](https://docs.microsoft.com/powerapps/gateway-management) y, en minutos, estará activa y conectando sus datos locales a PowerApps, Power BI, Microsoft Flow y Azure Logic Apps. No es necesario modificar ninguna regla de firewall. Al conectar esta aplicación con Microsoft Flow, se puede utilizar otro nivel de funcionalidad.

## <a name="a-standalone-sharepoint-app"></a>Una aplicación de SharePoint independiente

Utilice esta técnica si, en lugar de simplemente actualizar la experiencia del formulario de lista, quiere compilar una aplicación completa e independiente basada en los datos de SharePoint. Esta también es la mejor manera de comenzar a trabajar, ya que puede familiarizarse con el lienzo de PowerApps y compilar las aplicaciones futuras desde cualquiera de los múltiples orígenes de datos.

Para comenzar, vaya a la lista de SharePoint con la que le gustaría interactuar y:

1. Haga clic en PowerApps en la barra de menús.
2. Seleccione Crear una aplicación.
3. Proporcione un nombre.
4. Haga clic en Crear.

A continuación, PowerApps creará una aplicación predeterminada que se pueden personalizar.

Empiece por algo simple. Para su primera aplicación, use una lista personalizada simple con solo un par de campos de diferente tipo. Esto le permitirá partir de una base sólida sin verse desbordado. No se preocupe; en poco tiempo se convertirá en un profesional y podrá abordar aplicaciones complejas.  Para obtener ayuda con su primera aplicación, consulte esta [documentación](https://docs.microsoft.com/powerapps/generate-app-from-sharepoint-list-interface) o el [vídeo](https://youtu.be/BnYe_7fpZRM) de la comunidad. En los ejemplos siguientes se muestran las tareas comunes de InfoPath y cómo realizarlas en PowerApps. Cada una de ellas se basa en una aplicación sencilla de lista de SharePoint.

# <a name="how-do-you-do-that-with-powerapps"></a>Cómo se consigue con PowerApps

Ahora que conoce los conceptos fundamentales, vayamos más lejos. Con su primera aplicación, la sección siguiente le ayudará a aplicar en PowerApps algunos de los conceptos comunes de InfoPath.

**Ocultar/Mostrar/Bloquear un campo en función de un valor**  
Una de las maneras más comunes de crear un buen formulario es tener una lógica de negocios sólida y ser capaz de aplicarla. Una forma de conseguir esto es cambiar el estado de un campo en función de un valor o una acción. Con PowerApps puede seleccionar el control y establecer DisplayMode en Editar o Ver para especificar si un usuario puede cambiar el campo. Un segundo método que puede utilizar es una simple fórmula If para hacerlo de forma condicional. En primer lugar, seleccione la etiqueta que quiere editar y haga clic en el icono de bloqueo para desbloquear la tarjeta y poder cambiar el valor.

![Ocultar, mostrar o bloquear las tarjetas de datos](./media/transform-infopath/hide-show-lock.png)

Ahora, desplácese hasta el final de la tarjeta a la derecha y edite la propiedad DefaultMode.

![Expresiones de instrucción If Else](./media/transform-infopath/if-else-statement.png)

En este ejemplo utilice una instrucción If. If(ThisItem.Color = &quot;Azul&quot;, DisplayMode.View, DisplayMode.Edit). Esta instrucción indica que si el campo Color del elemento actual es azul, entonces el campo de animal es de solo lectura; de lo contrario, el campo es editable.

Si no quiere que se muestre la tarjeta, puede insertar una función similar en el campo Visible justo encima de DisplayMode.

Otro elemento con el que se puede jugar aquí sería, por ejemplo, la posibilidad de ocultar un botón de aprobación para que únicamente se muestre cuando la dirección de correo electrónico del usuario coincida con la dirección de correo electrónico del aprobador. Sugerencia: User().Email es cómo se accede a la dirección de correo electrónico del usuario actual. Se podría hacer que el valor del botón Visible fuese If(YourDataCard.Text = User().Email, true, false), donde YourDataCard es la tarjeta en la que se almacena la dirección de correo electrónico del aprobador.

**Formato condicional**  
De forma similar a como anteriormente ocultó el campo, también puede proporcionar comentarios visuales a los usuarios. Quizá le interese resaltar texto en color rojo si el valor especificado queda fuera del intervalo aceptable o reemplazar el texto y el color de los botones de carga por la opción eliminar después de cargar un archivo. Todo esto se realiza mediante funciones, como If, en los campos de propiedades como color o visible.

Por ejemplo, se podría utilizar la función If emparejada a la función [IsMatch](https://docs.microsoft.com/powerapps/functions/function-ismatch) para que el texto del campo de correo electrónico cambie a color rojo si el usuario no especifica una dirección de correo con el formato correcto en el cuadro de entrada. Para hacerlo, se establecería el valor de Color de TextInput1 en If(IsMatch (TextInput1.Text, Correo electrónico), Negro, Rojo) donde TextInput1 es el campo donde el usuario escribe una dirección de correo electrónico. IsMatch admite una gran cantidad de patrones predefinidos, como por ejemplo correo electrónico, o la capacidad de crear los suyos propios. Para obtener más información sobre cómo dar formato condicional, vea este [vídeo de la comunidad](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962).

**Implementación de seguridad basada en roles**  
La primera función a tener en cuenta es [DataSourceInfo](https://docs.microsoft.com/powerapps/functions/function-datasourceinfo). La información que se obtiene desde el origen de datos variará en función del origen de datos, pero a menudo se puede utilizar DataSourceInfo(YourDataSource, DataSourceInfo.EditPermission) para comprobar si el usuario tiene acceso para editar los datos. Reemplace YourDataSource por el nombre del origen de datos. Con esto, solo se muestran un formulario o un botón si el usuario tiene acceso para editar. Consulte la documentación de DataSourceInfo para ver la lista completa de la información que puede consultar en la función.

Si prefiere utilizar grupos de Active Directory para administrar el acceso a los botones o a los formularios en la aplicación, deberá ir un poco más allá. Para ello, puede sacar ventaja de la flexibilidad de PowerApps y crear su propio conector mediante Microsoft Graph API. Y aunque pueda parecer desalentador, no lo es tanto gracias a la [documentación](https://powerapps.microsoft.com/blog/implementing-role-based-permission/) detallada que puede usar como guía.

**Enviar un correo electrónico desde la aplicación**  
Hay muchas maneras de enviar un correo electrónico desde PowerApps. La más fácil es usar Office 365 Outlook Connector. Con este conector, puede enviar un correo electrónico en su nombre desde la aplicación. También puede obtener mensajes de correo electrónico y otras tareas que interactúan con el buzón. Para obtener información respecto al envío de correo electrónico, puede consultar la [documentación](https://docs.microsoft.com/powerapps/connections/connection-office365-outlook) o este [vídeo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349) de la comunidad.

Si necesita enviar un correo electrónico más complejo, por ejemplo con la creación de una cadena de aprobación de flujo de trabajo de aprobación de SharePoint, la mejor opción es crear un Microsoft Flow y conectar a él la aplicación. Una vez que la aplicación se conecta a Microsoft Flow, se abren todas las posibilidades funcionales de un motor de flujo de trabajo que, al igual que PowerApps, está muy bien conectado a servicios y datos externos. Para obtener más información sobre la conexión de PowerApps y Microsoft Flow, vea esta [documentación](https://docs.microsoft.com/powerapps/using-logic-flows).

Y si todavía no ha encontrado la opción de correo electrónico que busca, puede sacar provecho de los conectores de PowerApps para Benchmark Email, Gmail, MailChimp, Outlook.com, SendGrid o SMTP. Es lo más bonito de PowerApps, la conectividad.

**Flujos de trabajo**  
Se hace difícil hablar de aplicaciones empresariales y lógica de negocios sin un motor de flujo de trabajo. Lo bueno es que el equipo de PowerApps no ha reinventado la rueda y le proporciona otro motor de flujo de trabajo, sino que, en su lugar, le ofrece un potente conector para el servicio de Microsoft Flow. Ahora puede automatizar procesos y tareas en más de [200 servicios distintos](https://flow.microsoft.com/connectors/) mediante su sencillo motor de flujo de trabajo. Para obtener más información sobre la conexión de PowerApps y Microsoft Flow, vea esta [documentación](https://docs.microsoft.com/powerapps/using-logic-flows).

**Variables con PowerApps**  
Al compilar soluciones, es natural pensar que habrá que utilizar variables. Si bien PowerApps ofrece tres tipos de variables, solo hay que usarlas cuando sea necesario. En lugar de pensar en obtener datos, almacenarlos en una variable y hacer referencia a esa variable, piense en hacer referencia directamente a esos datos. La mejor manera de hacerlo es con Excel. En Excel, Total no es una variable, sino la suma de otros campos. Por lo tanto, si quiere usar ese valor en otra parte de la hoja, especifique el campo en el que se calcula el total. Lea la [documentación](https://docs.microsoft.com/powerapps/working-with-variables), donde se explica perfectamente todo esto. Esté abierto a un proceso de pensamiento diferente.

Si aun así necesita variables (hay muchos casos en que será así), esto le permitirá comprender las distintas opciones. Tenga en cuenta que con PowerApps no tiene que definir las variables. Simplemente utilice una de las funciones para especificar el nombre y el valor que se van a almacenar, y la variable se crea. Para ver las variables que ha creado, haga clic en Ver en la barra de menús y seleccione Variables. Las variables se mantienen en la memoria y sus valores se pierden cuando se cierra la aplicación. Los tres tipos de variable son los siguientes:

- Las variables globales son las que se suelen considerar primero. Aquí puede usar la función [Set](https://docs.microsoft.com/powerapps/functions/function-set) para especificar un valor para la variable y que esté disponible en toda la aplicación. Un ejemplo de cómo usar la función es Set(SuVariable, SuValor). A continuación, puede hacer referencia a SuVariable por su nombre en toda la aplicación.
- Las variables de contexto son variables que solo están disponibles en la pantalla donde se han definido. Al salir de la pantalla, se restablecen. A menudo se utilizan para, por ejemplo, almacenar información que se pasa de una pantalla anterior o para realizar un seguimiento de si el formulario se ha enviado. Un uso común de [UpdatedContext](https://docs.microsoft.com/powerapps/functions/function-updatecontext) es UpdateContext( { Submitted: "true" } ). Esto establecería la variable Submitted en true. Esto podría incluirse en la página como parte del elemento de botón de envío a fin de realizar un seguimiento de la información, comprobar que se ha enviado y cambiar todos los campos a solo lectura. Nota: Las colecciones ":" se utilizan para almacenar tablas de información que se pueden actualizar de forma individual. Para empezar, consulte [Collect](https://docs.microsoft.com/powerapps/functions/function-clear-collect-clearcollect). Un ejemplo de uso podría ser la creación de un carro de la compra cuando el usuario etiqueta varios elementos de SharePoint que quiere enviar. Hay un [vídeo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180) de la comunidad que muestra dicho concepto en acción.

**Listas desplegables en cascada**  
Las listas desplegables en cascada son muy útiles. Permiten filtrar las opciones en una lista desplegable en función del valor seleccionado en la lista desplegable anterior. Para crearlas en PowerApps, a menudo se utilizan dos orígenes de datos en la aplicación. El primer origen de datos se compone de los datos con los que se está trabajando o que se están actualizando, y el segundo origen de datos se utiliza para almacenar los valores que generarán el efecto en cascada que quiera. A continuación se muestra un ejemplo del segundo origen de datos con las posibilidades de elección.

![Listas desplegables en cascada](./media/transform-infopath/cascading-dropdowns.png)

Ahora habría que crear el primer control de lista desplegable y, para la propiedad Elementos, se usaría la fórmula Distinct(Impactos, Título) para mostrar únicamente el costo, el impacto del programa y la programación en la lista desplegable. A continuación, se podría agregar una segunda lista desplegable y establecer la propiedad Elementos en Filter(Impactos,ddSelectType.Selected.Value en SCategory) donde ddSelectType es el nombre del primer cuadro de lista desplegable. De esta manera tendríamos listas desplegables en cascada. Para obtener más información, consulte esta entrada del equipo de PowerApps [SharePoint: Cascading Dropdowns in 4 Easy Steps!](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248) (SharePoint: listas desplegables en cascada en 4 pasos sencillos) o este [vídeo de la comunidad](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813). Y no se preocupe, sin SharePoint es igual de fácil.

**No cree una superaplicación**  
Con PowerApps es posible llamar a una aplicación desde otra, por lo que en lugar de tener un enorme formulario de InfoPath tan difícil de mantener, se puede crear un grupo de aplicaciones que se llaman entre sí e incluso se pasan datos, lo que facilita mucho las labores de desarrollo.

## <a name="next-steps"></a>Pasos siguientes

Con la información anterior, ya tiene todo lo necesario para empezar a crear aplicaciones de PowerApps de una en una. Para acompañarlo en su viaje, a continuación tiene algunos vínculos que le servirán de ayuda. Uno de esos vínculos es el que dirige al sitio de la comunidad de PowerApps. Implíquese en la comunidad y aumente sus conocimientos mucho más rápido de lo que lo haría por sí mismo.

[**Referencia sobre fórmulas**](https://docs.microsoft.com/powerapps/formula-reference): una excelente manera de inspirarse mediante la exploración de algunas de las funciones predeterminadas.

[**Comunidad de PowerApps**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1): vea los ejemplos, relaciónese con otros usuarios, plantee sus dudas, responda a las de los demás y contribuya al crecimiento de la comunidad de PowerApps.