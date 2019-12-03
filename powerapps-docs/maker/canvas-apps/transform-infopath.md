---
title: Transformar el formulario de InfoPath en una aplicación de lienzo | Microsoft Docs
description: Comience a transformar su formulario de InfoPath en Power apps con información sobre escenarios comunes y cómo crear estos elementos en una aplicación de lienzo.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/05/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 811f58243413c4de58e4cdb8868d838349248991
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732372"
---
# <a name="transform-your-infopath-form-to-power-apps"></a>Transformación del formulario de InfoPath en Power apps

¿Ha creado grandes contenidos en InfoPath, pero le gustaría ofrecerlos en una plataforma más sólida?

## <a name="key-advantages-of-power-apps-over-infopath"></a>Principales ventajas de Power Apps en InfoPath

Como la mayoría de los usuarios avanzados de InfoPath, lleva cierto tiempo usando un único conjunto de aptitudes para crear sus formularios. Está satisfecho con los formularios, pero también sabe que tienen sus limitaciones: el estilo &quot;clásico&quot;, una experiencia para dispositivos móviles no del todo satisfactoria, la incertidumbre de su viabilidad futura y la imposibilidad de conectar los formularios a otros servicios sin necesidad de escribir código.

El equipo de Power apps ha oído estos y muchos otros desafíos. Ha trabajado arduamente para incorporar una mejor experiencia y permitirle crear aplicaciones de lienzo aprovechando sus conocimientos empresariales y tecnológicos existentes. Mediante el uso de Power Apps, puede compilar e implementar rápidamente las soluciones empresariales adecuadas sin necesidad de escribir código.

**Power apps permite un futuro eficaz**  
Power apps es una plataforma de software como servicio (SaaS) diseñada para que pueda compilar rápidamente aplicaciones de alto rendimiento que puede implementar en la web, SharePoint, Dynamics 365, Teams, Power BI o un dispositivo móvil sin ningún trabajo adicional. Al poderse implementar con solo facilitar a alguien la dirección URL de la aplicación publicada, también son muy fáciles de actualizar.

**Aplicaciones compartidas**  
¿Ha intentado alguna vez compilar una aplicación y luego publicarla para dispositivos Android o iOS? Es complicado. Si quiere implementar una segunda aplicación o actualizar una existente, los usuarios deben realizar muchos más pasos. No con Power apps. Los usuarios instalan Power apps Mobile en sus dispositivos e inician sesión. Y ya está. Ya tienen todas las aplicaciones de elevada funcionalidad que ha compartido con ellos. En el futuro, si actualiza esas aplicaciones o les envía aplicaciones nuevas, estas aparecerán en sus dispositivos. Disponer de aplicaciones móviles sin tener que administrar los dispositivos constituye una gran ventaja para usted y el negocio.

**Hablando de dispositivos móviles**  
Con Power Apps, puede aprovechar la eficacia del dispositivo móvil del usuario. como la aceleración, la cámara, la brújula, la información de conexión y las señales de ubicación: y todo ello desde dentro de la aplicación. Esto abre todo un mundo de posibilidades para compilar aplicaciones orientadas al trabajo. Por supuesto, la funcionalidad táctil es simplemente automática en Power apps: no hay ningún código adicional al compilar la aplicación.

**Lista para usar**  
Con InfoPath, normalmente se trabaja con datos de un origen. Pero las cosas se complican si quiere actualizar otro origen (por ejemplo, una lista de SharePoint en otra colección de sitios) o conectarse a servicios externos. Conceptos como el código subyacente le mantienen despierto durante la noche. Power apps está diseñado para permitirle trabajar con varios orígenes de datos y conexiones de servicio en una aplicación. Actualmente, [más de 200 conectores](connections-list.md#all-standard-connectors) admiten una combinación de datos locales y en la nube, incluidos Microsoft Office 365 y servicios de Azure, como Power Automatic y Dynamics 365. También puede conectarse a una gran variedad de servicios de terceros como Dropbox, Google, Salesforce, Slack y otros destinos populares.

Ahora puede compilar soluciones que se escalan donde lo necesitan los usuarios, no solo en la ubicación original de los datos.

## <a name="power-apps-and-sharepoint-even-better-together"></a>Power apps y SharePoint: incluso mejor juntos

Power apps es una excelente herramienta para mejorar la experiencia de SharePoint de dos maneras. Tiene la opción de personalizar los formularios para una lista de SharePoint o para crear una aplicación independiente que trabaje con datos de SharePoint.

**Personalizar un formulario de SharePoint** es muy útil si quiere personalizar el modo en que los usuarios agregan, ven o editan elementos de una lista que usan para su trabajo cotidiano. Si hace clic en **Personalizar formularios**, se crea una &quot;aplicación de formularios&quot; de una sola pantalla que cambia de modo (nuevo/editar/ver) en función del contexto. SharePoint administra estas aplicaciones; sus permisos son los mismos que los permisos de lista para edición y visualización.

La **creación de una aplicación de lienzo de Power apps desde SharePoint** permite ejecutar la aplicación por sí misma en un dispositivo móvil. También puede insertar la aplicación en una página de SharePoint. Al hacer clic, se crea una aplicación de tres pantallas (examinar lista, ver detalles y crear o actualizar un elemento). El modelo de permiso/uso compartido de estas aplicaciones no está asociado a SharePoint, sino que se administra desde Power apps.

Ahora que comprende la diferencia entre las dos opciones, la siguiente sección le proporciona una visión general del uso de cada una de ellas.

## <a name="sharepoint-forms"></a>Formularios de SharePoint

Los equipos de Power apps y SharePoint han trabajado juntos para crear una historia de personalización para su uso con SharePoint. Si es como la mayoría de los desarrolladores de InfoPath, ha aprendido a usar InfoPath para interactuar con SharePoint. SharePoint es fantástico, pero los formularios predeterminados son un poco básicos y no permiten personalizarlos ni usar la lógica de negocios sin InfoPath. Bueno, eso era antes.

Con Power Apps, ahora puede personalizar los formularios de lista como funcionalidad nativa. Y al hacerlo, obtendrá todo el potencial de las aplicaciones de energía. En la captura de pantalla siguiente, puede ver un ejemplo de un formulario de Power apps con un Power BI informe incrustado. Toda la solución se realizó en menos de 15 minutos.

![Integración con SharePoint](./media/transform-infopath/sharepoint-integration.png)

Otra característica importante de Power apps es la posibilidad de conectarse fácilmente a otra colección de sitios de SharePoint o a un entorno diferente del mismo formulario. Por ejemplo, ¿quiere crear un formulario que muestre y actualice al mismo tiempo los datos de SharePoint Online y el entorno local de SharePoint? No hay problema. Si instala la [puerta de enlace de datos local](gateway-management.md), está en funcionamiento en unos minutos, conectando Power Apps, Power BI, Power automatic y Azure Logic apps con sus datos locales. No se requiere ningún cambio en las reglas de firewall. Puede seguir un paso más conectando esta aplicación con Power Automatic.

## <a name="a-standalone-sharepoint-app"></a>Una aplicación de SharePoint independiente

Use esta técnica si, en lugar de simplemente actualizar la experiencia del formulario de lista, quiere compilar una aplicación completa e independiente basada en los datos de SharePoint. Esta es también la mejor manera de empezar, por lo que puede empezar a aprender cómo funciona el lienzo de Power apps y crear aplicaciones futuras a partir de cualquiera de las multitudes de orígenes de datos.

Siga estos pasos para comenzar:

1. Abra la lista de SharePoint a partir de la que quiere compilar una aplicación.
1. En la barra de menús, seleccione **PowerApps** y luego **Crear una aplicación**.
1. Proporcione un nombre y seleccione **Crear**.

Power apps le creará una aplicación que puede personalizar.

Comience con una lista personalizada simple que solo contenga un par de campos de diferentes tipos para la primera aplicación. Esto le permitirá partir de una base sólida sin verse desbordado. No se preocupe; en poco tiempo se convertirá en un profesional y podrá abordar aplicaciones complejas. Para obtener ayuda con su primera aplicación, vea esta [documentación](app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online) o el [vídeo](https://youtu.be/BnYe_7fpZRM) de esta comunidad. En los ejemplos siguientes se muestran las tareas comunes de InfoPath y cómo realizarlas en Power apps. Cada una de ellas se basa en una aplicación sencilla de lista de SharePoint.

## <a name="how-do-you-do-that-with-power-apps"></a>¿Cómo hacerlo con Power apps?

Ahora que conoce los conceptos fundamentales, vayamos más lejos. Con su primera aplicación bajo su cinturón, esta sección le ayudará a aplicar algunos de los conceptos comunes de InfoPath en Power apps.

**Ocultar, mostrar o bloquear un campo en función de un valor**  
Los formularios útiles suelen aplicar una eficaz lógica de negocios, por ejemplo, al cambiar el estado de un campo en función de un valor o una acción. Con Power Apps, puede establecer la propiedad **DisplayMode** de un control en **Editar** o **Ver** para especificar si un usuario puede cambiar el campo. También puede usar una simple fórmula **If** para hacerlo de forma condicional. En primer lugar, seleccione la tarjeta que quiere editar y luego el icono de bloqueo. Este paso desbloquea la tarjeta para que pueda cambiar el valor.

![Ocultar, mostrar o bloquear las tarjetas de datos](./media/transform-infopath/hide-show-lock.png)

En el panel derecho, desplácese a la propiedad **DisplayMode** para que pueda editarlo.

![Expresiones de instrucción If Else](./media/transform-infopath/if-else-statement.png)

En este ejemplo use una fórmula **If**:

```If(ThisItem.Color = "Blue", DisplayMode.View, DisplayMode.Edit)```

Esta fórmula indica que, si el campo **Color** del elemento actual es **Blue**, el campo **Animal** es de solo lectura. Si no, el campo se puede modificar.

Para ocultar la tarjeta en lugar de hacer que sea de solo lectura, inserte una función similar en la propiedad **Visible** justo encima de **DisplayMode**.

También puede jugar con, por ejemplo, mostrar un botón de aprobación solo si la dirección de correo electrónico del usuario coincide con la dirección de correo electrónico del aprobador. (Sugerencia: use **User (). Correo electrónico** para tener acceso a la dirección de correo electrónico del usuario actual). Por lo tanto, puede almacenar la dirección de correo electrónico del aprobador en **YourDataCard** y, a continuación, establecer la propiedad **visible** del botón en esta fórmula:

```If( YourDataCard.Text = User().Email, true, false )```

**Formato condicional**  
De forma similar a como anteriormente ocultó el campo, también puede proporcionar comentarios visuales a los usuarios. Puede que quiera resaltar texto en rojo si el valor especificado queda fuera del intervalo aceptable o cambiar el texto y el color del botón de carga después de que el usuario cargue un archivo. Puede hacer ambas cosas con una función, como **If**, en propiedades como **Color** o **Visible**.

Por ejemplo, podría usar la función **If** emparejada con la función [IsMatch](functions/function-ismatch.md) para que el texto del campo de correo electrónico cambie a color rojo si el usuario no especifica una dirección de correo con el formato correcto en el cuadro de entrada. Se haría al establecer el valor **Color** de **TextInput1** (donde el usuario escribe una dirección de correo electrónico) en esta fórmula:

```If( IsMatch(TextInput1.Text, Email), Black, Red )```

**IsMatch** admite una gran cantidad de patrones predefinidos, como Correo electrónico, o puede crear los suyos propios. Para obtener más información sobre el formato condicional, vea este [vídeo de la comunidad](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962).

**Implementación de seguridad basada en roles**  
La primera función a tener en cuenta es [DataSourceInfo](functions/function-datasourceinfo.md). La información que se obtiene desde el origen de datos varía, pero a menudo se puede usar esta fórmula para confirmar si el usuario tiene acceso para editar los datos (sustituya *YourDataSource* por el nombre del origen de datos):

```DataSourceInfo( YourDataSource, DataSourceInfo.EditPermission )```

Así, puede mostrar un formulario o un botón únicamente si el usuario tiene acceso para editar. Vea la documentación de [DataSourceInfo](functions/function-datasourceinfo.md) para obtener la lista completa de la información que puede consultar en la función.

Si quiere usar grupos de Active Directory para administrar el acceso a los botones o a los formularios de la aplicación, deberá profundizar más. Para ello, aprovechará la flexibilidad de Power apps y creará su propio conector mediante el Microsoft Graph API. Si eso suena complicado, puede seguir este [entrada de blog](https://powerapps.microsoft.com/blog/implementing-role-based-permission/) para obtener instrucciones paso a paso.

**Enviar un correo electrónico desde la aplicación**  
Puede enviar un mensaje de correo electrónico desde Power apps de muchas maneras, pero lo más fácil es usar el conector de Office 365 Outlook. Con este conector, puede enviar un mensaje en su nombre desde la aplicación. También puede obtener mensajes de correo electrónico y otras tareas que interactúan con el buzón. Existe [documentación](connections/connection-office365-outlook.md) o este [vídeo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349) de la comunidad sobre el envío de correo electrónico.

Puede enviar un mensaje más complejo (por ejemplo, como parte de un flujo de trabajo de aprobación de SharePoint) mediante el uso de Power Automatic y la conexión de la aplicación al flujo que cree. Una vez que conecte la aplicación a Power Automate, habrá abierto toda la potencia de un motor de flujo de trabajo que, como Power Apps, está muy bien conectada a los datos y servicios externos. Para obtener más información sobre cómo conectar Power apps y Power Automate, consulte esta [documentación](using-logic-flows.md).

Si todavía no ha encontrado la opción de correo electrónico que está buscando, también puede aprovechar los conectores de Power apps para Benchmark Email, gmail, MailChimp, Outlook.com, SendGrid o SMTP. La conectividad es la belleza de las aplicaciones de energía.

**Flujos de trabajo**  
Es difícil hablar de aplicaciones empresariales y lógica de negocios sin un motor de flujo de trabajo. La buena noticia es que el equipo de Power apps no ha reinventado la rueda y le proporciona otro motor de flujo de trabajo. En su lugar, proporcionan un conector sólido al servicio Power Automatic. Puede automatizar procesos y tareas en más de [200 servicios distintos](https://flow.microsoft.com/connectors/) mediante su sencillo motor de flujo de trabajo. Para obtener más información sobre cómo conectar Power apps y Power Automate, consulte esta [documentación](using-logic-flows.md).

**Variables con Power apps**  
Al compilar soluciones, es natural pensar que habrá que usar variables. Power Apps ofrece varios tipos de variables, pero úselas solo cuando sea necesario. En lugar de pensar en obtener datos, almacenarlos en una variable y luego hacer referencia a esa variable, piense en hacer referencia directamente a esos datos. Comprenderá mejor este modelo si lo compara con Excel. En Excel, Total no es una variable, sino la suma de otros campos. Por lo tanto, si quiere usar ese valor en otra parte de la hoja, especifica la celda en la que ha calculado el total. En la [documentación](working-with-variables.md) hay una magnífica explicación de todo esto. Esté abierto a un proceso de pensamiento diferente.

Si aun así necesita una variable (hay muchos casos en que será así), esto le ayudará a comprender las distintas opciones. Tenga en cuenta que, con Power Apps, no tiene que definir variables. Simplemente use una función para especificar un nombre y un valor que se van a almacenar, y la variable se crea. Puede ver las variables que ha creado seleccionando **variables** en la pestaña **vista** . las variables se mantienen en la memoria y sus valores se pierden cuando se cierra la aplicación. Puede crear estos tipos de variables:

- Las variables globales son las que se suelen considerar primero. Use la función [Set](functions/function-set.md) para especificar un valor para una variable global y haga que esté disponible en toda la aplicación:

    ```Set( YourVariable, YourValue )```

    Luego puede hacer referencia a *YourVariable* por nombre en toda la aplicación.

- Las variables de contexto solo están disponibles en la pantalla donde se han definido. Al salir de la pantalla, se restablecen. A menudo se usan para, por ejemplo, almacenar información pasada desde una pantalla anterior o para realizar un seguimiento de si el formulario se ha enviado. Para establecer una variable de contexto, use la función [UpdateContext](functions/function-updatecontext.md), como en este ejemplo:

    ```UpdateContext( { Submitted: "true" } )```

    Este ejemplo establece el valor de una variable, denominada **Submitted**, en **true**. Podría agregar esta fórmula a la propiedad **OnSelect** de un botón de envío a fin de realizar un seguimiento de si la información se ha enviado y cambiar todos los campos a solo lectura.

- Las colecciones almacenan tablas de información que se pueden actualizar de forma individual. Use [Collect](functions/function-clear-collect-clearcollect.md) para crear un carro de la compra, por ejemplo, cuando el usuario etiquete varios elementos de SharePoint que quiere enviar. Un [vídeo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180) de la comunidad muestra ese concepto en acción.

**Listas desplegables en cascada**  
Las listas desplegables en cascada son muy útiles porque permiten, por ejemplo, filtrar las opciones en una lista desplegable en función del valor seleccionado en la lista desplegable anterior. En Power Apps, a menudo se crean con dos orígenes de datos en la aplicación. El primer origen de datos se compone de los datos que se están viendo o actualizando, y el segundo origen de datos almacena los valores para compilar el efecto en cascada. Este gráfico muestra un ejemplo del segundo origen de datos con las posibilidades de elección.

![Listas desplegables en cascada](./media/transform-infopath/cascading-dropdowns.png)

En este ejemplo, podría agregar una lista desplegable denominada **ddSelectType** y establecer su propiedad **Items** en esta fórmula:

```Distinct( Impacts, Title )```

La lista desplegable solo mostraría el costo, el impacto del programa y la programación. Luego podría agregar una segunda lista desplegable y establecer su propiedad **Items** en esta fórmula:

```Filter( Impacts, ddSelectType.Selected.Value in SCategory )```

De esta manera tendríamos listas desplegables en cascada. Para obtener más información, consulte esta entrada del equipo de Power apps [SharePoint: listas desplegables en cascada en 4 pasos sencillos.](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248) o este [vídeo de la comunidad](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813). No se preocupe: sin SharePoint es igual de fácil.

**No cree una superaplicación**  
Con Power Apps, puede llamar a una aplicación desde otra. Así que, en lugar de tener un enorme formulario de InfoPath tan difícil de mantener, se puede crear un grupo de aplicaciones que se llaman entre sí e incluso se pasan datos, lo que facilita mucho las labores de desarrollo.

## <a name="next-steps"></a>Pasos siguientes

Con Power apps y la información de este tema, ya está listo para entrar en el mundo y comenzar a conquistarla una aplicación a la vez. A medida que continúe con el recorrido, a continuación se muestran algunos vínculos útiles para ayuda, como el vínculo al sitio de la comunidad de Power apps. Implíquese en la comunidad y aumente sus conocimientos mucho más rápido de lo que lo haría por sí mismo.

[**Referencia sobre fórmulas**](formula-reference.md): una excelente manera de inspirarse mediante la exploración de algunas de las funciones predeterminadas.

[**Comunidad de Power apps**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) : vea ejemplos, participe con otras personas, formule preguntas y respuestas, y ayude a la comunidad de Power apps a crecer.
