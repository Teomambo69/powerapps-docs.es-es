---
title: "Información acerca de los orígenes de datos | Microsoft Docs"
description: "Información de referencia para trabajar con conexiones y orígenes de datos en Microsoft PowerApps."
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/08/2017
ms.author: gregli
ms.openlocfilehash: 381fe4021a06b13d6fbdf3887e42616a30053030
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="understand-data-sources-in-powerapps"></a>Información acerca de los orígenes de datos en PowerApps
La mayoría de las aplicaciones de PowerApps utilizan información externa almacenada en servicios en la nube denominados **Orígenes de datos**. Uno de los ejemplos más frecuentes son tablas que pertenecen a archivos de Excel guardados en OneDrive para la Empresa. Las aplicaciones acceder a estos orígenes de datos a través de las **conexiones**.

En este artículo se describen los diferentes tipos de orígenes de datos y cómo trabajar con orígenes de datos de tabla.

Es fácil crear una aplicación que realice las operaciones básicas de lectura y escritura a un origen de datos. Pero a veces desea más control sobre cómo fluyen los datos dentro y fuera de la aplicación.  Este artículo se describe cómo proporcionan más control las funciones **[Patch](functions/function-patch.md)**, **[DataSourceInfo](functions/function-datasourceinfo.md)**, **[Validate](functions/function-validate.md)** y **[Errores](functions/function-errors.md)**.

## <a name="kinds-of-data-sources"></a>Tipos de orígenes de datos
Los orígenes de datos pueden estar conectados a un servicio en la nube, o bien pueden ser locales a una aplicación.

### <a name="connected-data-sources"></a>Orígenes de datos conectados
Los orígenes de datos más frecuentes son las **tablas**, que se pueden usar tanto para recuperar como para guardar información. Las **conexiones** con los orígenes de datos se pueden usar para leer y escribir datos en libros de Microsoft Excel, listas de SharePoint, tablas SQL y muchos otros formatos, que pueden almacenarse en servicios en la nube, como OneDrive para la Empresa, DropBox, SQL Server, etc.

Los orígenes de datos distintos de las tablas incluyen el correo electrónico, los calendarios, Twitter y las notificaciones, pero en este artículo no se habla de otros tipos de orígenes de datos.

### <a name="local-data-sources"></a>Orígenes de datos locales
Con los controles **[Galería](controls/control-gallery.md)**, **[Formulario de presentación](controls/control-form-detail.md)** y **[Formulario de edición](controls/control-form-detail.md)**, resulta muy fácil crear una aplicación que lea y escriba datos en un origen de datos.  Para empezar, lea el artículo [Understand data forms](working-with-forms.md) (Introducción a los formularios de datos).  

Cuando se solicita a PowerApps que cree una aplicación a partir de los datos, se utilizan estos controles. En segundo plano, la aplicación utiliza una tabla interna para almacenar y manipular los datos procedentes del origen de datos.

Un tipo especial de origen de datos es la [colección](working-with-data-sources.md#Collections), que está en la propia aplicación y no tiene el respaldo de una conexión a un servicio en la nube, por lo que la información no se puede compartir entre los distintos dispositivos de un mismo usuario ni entre usuarios. Las colecciones se pueden cargar y guardar localmente.

### <a name="kinds-of-tables"></a>Tipos de tablas
Las tablas internas de una aplicación de PowerApps son valores fijos, como un número o una cadena son un valor. Las tablas internas no se almacenan en ningún lugar, solo existen en la memoria de la aplicación. La estructura y los datos de una tabla no se pueden modificar directamente. En su lugar, lo que puede hacer es crear una nueva tabla a través de una fórmula: dicha fórmula se usa para hacer una copia modificada de la tabla original.

Las tablas externas se almacenan en un origen de datos para su posterior recuperación y uso compartido.  PowerApps proporciona "conexiones" para leer y escribir los datos almacenados.  En una conexión se puede acceder a varias tablas de información.  Seleccione las tablas que desea utilizar en la aplicación y cada uno de ellas pasará a ser un *origen de datos* independiente.  

Para más información, consulte [Trabajar con tablas](working-with-tables.md), donde se proporcionan más detalles acerca de las tablas internas, pero también se explican las tablas externas que residen en un servicio en la nube.

## <a name="working-with-tables"></a>Trabajo con tablas
Los orígenes de datos en tabla se pueden usar del mismo modo que se usa una tabla interna de PowerApps.  Al igual que una tabla interna, cada origen de datos tiene [registros](working-with-tables.md#records), [columnas](working-with-tables.md#columns)y propiedades que se pueden usar en las fórmulas. Asimismo:

* El origen de datos tiene la mismos nombres de columna y tipos de datos que la tabla subyacente de la conexión.
  
    > [!NOTE]
> En los orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, PowerApps los sustituirá por **"\_x0020\_"**. Por ejemplo, **"Nombre de columna"** en SharePoint o Excel aparecerá como **"Nombre_x0020_de_columna"** en PowerApps cuando se muestre en el diseño de datos o se use en una fórmula.
* El origen de datos se carga desde el servicio automáticamente cuando se carga la aplicación.  Con la función **[Actualizar](functions/function-refresh.md)** se puede forzar la actualización de los datos.
* Cuando los usuarios ejecutan una aplicación, pueden crear, modificar y eliminar registros, y aplicar esos cambios posteriormente a la tabla subyacente del servicio.
  * Los registros se pueden crear con las funciones **[Patch](functions/function-patch.md)** y **[Recopilar](functions/function-clear-collect-clearcollect.md)**.  
  * Los registros se pueden modificar con las funciones **[Patch](functions/function-patch.md)**, **[Actualizar](functions/function-update-updateif.md)** y **[UpdateIf](functions/function-update-updateif.md)**.
  * Los registros se pueden quitar con las funciones **[Quitar](functions/function-remove-removeif.md)**  y **[RemoveIf](functions/function-remove-removeif.md)**.
  * Los errores que se producen al trabajar con un origen de datos están disponibles a través de la función **[Errores](functions/function-errors.md)**.
* Las funciones **[DataSourceInfo](functions/function-datasourceinfo.md)**, **[Defaults](functions/function-defaults.md)** y **[Validate](functions/function-validate.md)** proporcionan información acerca del origen de datos que se puede usar para optimizar la experiencia del usuario.

### <a name="creating-data-sources"></a>Creación de orígenes de datos
PowerApps no se puede usar para crear un origen de datos conectado ni para modificar su estructura; el origen de datos ya debe existir en algún servicio. Por ejemplo, para crear una tabla en un libro de Excel almacenado en OneDrive, primero es preciso usar Excel Online en OneDrive para crear un libro. Después, se crea una conexión a él desde la aplicación.  

Sin embargo, los orígenes de datos de la colección se *pueden* crear y modificar dentro de una aplicación, pero son temporales.

### <a name="display-one-or-more-records"></a>Visualización de uno o varios registros
![](media/working-with-data-sources/reading-from-a-datasource.png) El diagrama anterior muestra el flujo de información cuando una aplicación la lee de un origen de datos:

* La información se almacena y comparte a través de un servicio de almacenamiento (en este caso, una lista de SharePoint de un sitio de Office 365).
* Una conexión hace que esta información esté disponible para la aplicación.  La conexión se encarga de autenticación del usuario que va a acceder a la información.
* Cuando se inicia la aplicación, o cuando se pulsa la función **[A](functions/function-refresh.md)**, la información se extrae de la conexión y llega a un origen de datos de la aplicación para su uso local.
* Las fórmulas se usan para leer la información y exponerla en controles que el usuario pueda ver. Para mostrar los registros de un origen de datos, use una galería en una pantalla y conecte la propiedad **[Elementos](controls/properties-core.md)** al origen de datos: **Gallery.Items = DataSource**.  Para conectar los controles dentro de la galería a la galería, use la propiedad **[Default](controls/properties-core.md)** de los controles.  
* El origen de datos también es una tabla.  Por consiguiente, puede usar **[Filter](functions/function-filter-lookup.md)**, **[Sort](functions/function-sort.md)**, **[AddColumns](functions/function-table-shaping.md)** y otras funciones para refinar y aumentar el origen de datos antes de usar su totalidad.  También puede usar **[Buscar](functions/function-filter-lookup.md)**, **[First](functions/function-first-last.md)**, **[Last](functions/function-first-last.md)** y otras funciones para trabajar con los registros individuales.

### <a name="modify-a-record"></a>Modificación de un registro
En la sección anterior se ha explicado cómo leer un origen de datos.  Tenga en cuenta que las flechas del diagrama anterior son unidireccionales.  Los cambios en un origen de datos no se recuperan a través de la mismas fórmulas con las que se recuperaron los datos.  En su lugar, se utilizan fórmulas nuevas.  A menudo no se utiliza la misma pantalla para editar un registro que para explorar los registros, sobre todo en los dispositivos móviles.

Tenga en cuenta que, para modificar un registro existente de un origen de datos, debe provenir originalmente del origen de datos.  El registro puede haber viajado a través de una galería, una [variable de contexto](working-with-variables.md#create-a-context-variable) y cualquier número de fórmulas, pero su origen debe de poder rastrearse hasta el origen de datos.  Esto es importante porque hay información adicional que acompaña al registro que lo identifica de forma única, lo que garantiza que el registro que se modifica es el correcto.    

![](media/working-with-data-sources/writing-to-a-datasource.png) El diagrama anterior muestra el flujo de información para actualizar un origen de datos:

* Un control **[Formulario de edición](controls/control-form-detail.md)** proporciona un contenedor para las tarjetas de entrada, que se componen de controles de entrada de usuario, como un control de entrada de texto o un control deslizante.  Las propiedades **[DataSource](controls/control-form-detail.md)** y **[Elemento](controls/control-form-detail.md)** se utilizan para identificar el registro que se va a editar.
* Cada tarjeta de entrada tiene una propiedad **[Default](controls/properties-core.md)**, que normalmente se establece en el campo del registro **EsteElemento** del formulario.  Luego, los controles de la tarjeta de entrada tomarán sus valores de entrada de **[Default](controls/properties-core.md)**.  Normalmente este comportamiento no es preciso modificarlo.
* Cada tarjeta de entrada expone una propiedad **[Actualizar](controls/control-card.md)**.  Dicha propiedad asigna la entrada del usuario a un campo específico del registro reescribir en el origen de datos.  Normalmente este comportamiento no es preciso modificarlo.
* Un botón o un control de imagen de la pantalla permite al usuario guardar los cambios en el registro.  La fórmula **[AlSeleccionar](controls/properties-core.md)** del control llama a la función **[SubmitForm](functions/function-form.md)** para realizar este trabajo.  **[SubmitForm](functions/function-form.md)**  lee todas las propiedades **[Actualizar](controls/control-card.md)** de las tarjetas y lo utiliza para reescribir en el origen de datos.
* A veces surgirán problemas.  Una conexión de red puede estar inactiva o el servicio realiza una comprobación de validación sin que lo sepa la aplicación.  Las propiedades **Error** y **[ErrorKind](controls/control-form-detail.md)** del control del formulario hacen que esta información está disponible, por lo que se puede mostrar al usuario.  

Para lograr un mayor control sobre el proceso, también se pueden usar las funciones  **[Patch](functions/function-patch.md)** y **[Errores](functions/function-errors.md)**.  El control **[Formulario de edición](controls/control-form-detail.md)** expone una propiedad **[Actualizaciones](controls/control-form-detail.md)** para que pueda leer los valores de los campos del formulario.  Esta propiedad también se puede utilizar para llamar a un conector personalizado en una conexión, omitiendo completamente las funciones **Patch** y **SubmitForm**.

### <a name="validation"></a>Validación
Antes de realizar cualquier cambio en un registro, la aplicación debe hacer todo lo posible por asegurarse de que el cambio será aceptable.  Hay dos motivos para ello:

* *Comentarios inmediatos para el usuario*.  El mejor momento para corregir un problema es cuando ocurre, cuando está fresco en la mente del usuario.  Cada vez que se toca o se pulsa una tecla, puede texto en rojo que identifica un problema.
* *Menor tráfico de red y menor latencia de los usuarios*.  La detección de un mayor número de problemas en la aplicación implica que habrá menos conversaciones a través de la red para detectar y solucionar problemas.  Cada conversación lleva su tiempo y el que usuario debe esperar.

PowerApps ofrece dos herramientas para la validación:

* El origen de datos puede proporcionar información sobre lo que es valido, y lo que no lo es.  Por ejemplo, los números pueden tener valores mínimo y máximo, y puede que se requieran una o varias entradas.  Para acceder a esta información, puede usar la función **[DataSourceInfo](functions/function-datasourceinfo.md)**.  
* La función **[Validate](functions/function-validate.md)** función usa esta misma información para comprobar el valor de una sola columna o de todo un registro.

### <a name="error-handling"></a>Control de errores
Ya ha validado el registro.  Ha llegado el momento de actualizar el registro con **[Patch](functions/function-patch.md)**.

Sin embargo, aún puede haber un problema.  La red no está activa, se produce un error en la validación en el servicio o el usuario no tiene los permisos adecuados, por nombrar algunos de los posibles errores con que puede toparse la aplicación.  Es preciso que responda correctamente en situaciones de error, es decir, que proporcione al usuario no solo información, sino también una forma de salir de dichas situaciones.  

Si los errores se producen en un origen de datos, la aplicación registra automáticamente la información del error y la pone a disposición del usuario a través de la función **[Errores](functions/function-errors.md)**.  Los errores están asociados a los registros que tenían los problemas.  Si el problema puede corregirlo el usuario, como por ejemplo, un problema de validación, puede volver a enviar el registro y los errores desaparecerán.

Si se produce un error cuando un registro se crea con **[Patch](functions/function-patch.md)** o **[Recopilar](functions/function-clear-collect-clearcollect.md)**, no hay registro con los que se puedan asociar los errores.  En este caso, la función *Patch* devolverá un espacio **[en blanco](functions/function-patch.md)** que puede utilizarse como argumento de registro en **[Errores](functions/function-errors.md)**.  Los errores de creación se eliminan con la siguiente operación.

La función **[Errores](functions/function-errors.md)** devuelve una tabla de información del error.  Dicha información puede incluir información de una columna, en caso de que el error se pueda atribuir a una columna concreta.  Utilice mensajes de error de nivel de columna en los controles de etiqueta que estén cerca del lugar ne que se encuentra la columna en la pantalla de edición.  Utilice mensajes de error de nivel de registro donde el valor de **Columna** en la tabla de errores esté *en blanco*, en una ubicación próxima al botón **Guardar** de todo el registro.  

### <a name="working-with-large-data-sources"></a>Uso de orígenes de datos grandes
Cuando se crean informes de orígenes de datos de gran tamaño (quizás millones de registros), se desea minimizar el tráfico de red. Supongamos que desea mostrar todos los clientes cuyo StatusCode sea "Platinum" en New York City. Y supongamos también que la tabla de clientes contiene millones de registros.

Lógicamente, **no** desea incorporar todos esos millones de clientes a la aplicación para elegir los que desee. Lo que realmente desea es que la elección se realice dentro del servicio en la nube en que está almacenada la tabla y enviar a través de la red solo los registros seleccionados.

Aunque no todas, muchas de las funciones que puede usar para elegir los registros se pueden *delegar*, lo que significa que se ejecutan en el servicio en la nube. Para aprender a hacerlo, lea la información existente acerca de la [delegación](delegation-overview.md).

## <a name="collections"></a>Colecciones
Las colecciones son un tipo especial de origen de datos.  Se encuentran en la propia aplicación y no tienen el respaldo de una conexión a un servicio en la nube, por lo que la información no se puede compartir entre los distintos dispositivos de un mismo usuario ni entre usuarios.  Funcionan como cualquier otro origen de datos, con algunas excepciones:

* Las colecciones se pueden crear dinámicamente con la función **[Recopilar](functions/function-clear-collect-clearcollect.md)**.  No es preciso establecerse con antelación, como debe hacerse con orígenes de datos basados en conexión.
* Las columnas de una colección pueden modificarse en cualquier momento mediante la función **[Recopilar](functions/function-clear-collect-clearcollect.md)**.
* Las recopilaciones permiten duplicar registros.  En una colección puede haber más de una copia del mismo registro.  Las funciones como **[Quitar](functions/function-remove-removeif.md)**  operarán en la primera coincidencia que encuentran, salvo que se haya usado el argumento **Todos**.
* Puede usar las funciones **[SaveData](functions/function-savedata-loaddata.md)** y **[LoadData](functions/function-savedata-loaddata.md)** para guardar y volver a cargar una copia de la colección.  La información se almacena en una ubicación privada a la que no pueden acceder otros usuarios, aplicaciones o dispositivos.
* Puede usar los controles **[Export](controls/control-export-import.md)** e **[Import](controls/control-export-import.md)** para guardar y volver a cargar una copia de la colección en un archivo con el que el usuario puede interactuar.  

Para más información acerca de cómo trabajar con una colección como origen de datos, consulte [Create and update a collection in your app](create-update-collection.md) (Creación y actualización de una colección en una aplicación).

Las colecciones se usan normalmente para almacenar el estado global de la aplicación.  Para conocer las opciones disponibles para administrar el estado, consulte [Trabajar con variables](working-with-variables.md).

