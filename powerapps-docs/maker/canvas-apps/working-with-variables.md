---
title: Comprender las variables de aplicaciones de lienzo | Microsoft Docs
description: Información de referencia para trabajar con estado, variables de contexto y colecciones en aplicaciones de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bd5ca15f4c76e1ca69fe143d085e112cdc014dec
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849188"
---
# <a name="understand-canvas-app-variables-in-powerapps"></a>Comprender las variables de aplicaciones de lienzo en PowerApps

Si ha usado otra herramienta de programación como Visual Basic o JavaScript, probablemente se pregunte: **¿dónde están las variables?** PowerApps es ligeramente diferente y requiere otro enfoque. En lugar de buscar una variable al compilar una aplicación de lienzo, pregúntese lo siguiente: **¿qué haría en Excel?**

En otras herramientas, lo más probable es que haya realizado explícitamente un cálculo y haya almacenado el resultado en una variable. Pero PowerApps y Excel recalculan automáticamente las fórmulas cuando los datos de entrada cambian, por lo que normalmente no tendrá que crear ni actualizar las variables. Si adopta este enfoque siempre que sea posible, podrá crear, comprender y mantener la aplicación más fácilmente.

En algunos casos deberá usar variables en PowerApps, que amplía el modelo de Excel mediante la adición de [fórmulas de comportamiento](working-with-formulas-in-depth.md). Estas fórmulas se ejecutan cuando, por ejemplo, un usuario selecciona un botón. Dentro de una fórmula de comportamiento, a menudo resulta útil establecer una variable para su uso en otras fórmulas.

En general debe evitar el uso de variables, pero a veces solo una variable puede habilitar la experiencia que busca.

## <a name="translate-excel-into-powerapps"></a>Traducir Excel a PowerApps

### <a name="excel"></a>Excel
Revisemos el funcionamiento de Excel. Una celda puede contener un valor, como un número o una cadena, o una fórmula basada en los valores de otras celdas. Cuando el usuario introduce un valor diferente en una celda, Excel recalcula automáticamente las fórmulas que dependen del valor nuevo. No hace falta realizar ningún tipo de programación para habilitar este comportamiento.

![](media/working-with-variables/excel-recalc.png)

Excel no tiene variables. El valor de una celda que contiene una fórmula cambia en función de su entrada, pero no es posible recordar el resultado de una fórmula y almacenarlo en una celda o en otro lugar. Si cambia el valor de una celda, toda la hoja de cálculo podría cambiar y los valores calculados previamente se perderían.  Un usuario de Excel puede copiar y pegar las celdas, pero esto depende del control manual del usuario y no es posible hacerlo con las fórmulas.

### <a name="powerapps"></a>PowerApps
Las aplicaciones que se crean en PowerApps se comportan de una manera muy parecida a Excel. En lugar de actualizar las celdas, puede agregar controles donde quiera en una pantalla y asignarles un nombre para usarlos en fórmulas.

Por ejemplo, puede replicar el comportamiento de Excel en una aplicación mediante la adición de un control **[Etiqueta](controls/control-text-box.md)**, denominado **TextBox1** (CuadroDeTexto1), y dos controles **[Entrada de texto](controls/control-text-input.md)**, denominados **TextInput1** (EntradaDeTexto1) y **TextInput2** (EntradaDeTexto2). Si después establece la propiedad **[Text](controls/properties-core.md)** de **TextBox1** en **TextInput1 + TextInput2**, siempre mostrará automáticamente la suma de los números que se encuentren en **TextInput1** y **TextInput2**.

![](media/working-with-variables/recalc1.png)

Tenga en cuenta que el control **TextBox1** está seleccionado y muestra su fórmula **[Text](controls/properties-core.md)** en la barra de fórmulas en la parte superior de la pantalla.  Aquí se encuentra la fórmula **TextInput1 + TextInput2**.  Esta fórmula crea una dependencia entre estos controles, del mismo modo que se crean las dependencias entre las celdas de un libro de Excel.  Vamos a cambiar el valor de **TextInput1**:

![](media/working-with-variables/recalc2.png)

La fórmula de **TextBox1** se ha calculado automáticamente y muestra el nuevo valor.

En PowerApps, puede usar fórmulas para determinar no solo el valor principal de un control, sino propiedades como el formato. En el ejemplo siguiente, una fórmula para la propiedad **[Color](controls/properties-color-border.md)** de la etiqueta mostrará automáticamente los valores negativos en rojo. El aspecto de la función **[If](functions/function-if.md)** debería resultarle familiar de Excel:
<br>**If( Value(TextBox1.Text) < 0, Red, Black )**

![](media/working-with-variables/recalc-color1.png)

Ahora, si el resultado del cálculo en **TextBox1.Text** es negativo, el número se mostrará en color rojo:

![](media/working-with-variables/recalc-color2.png)

Puede usar fórmulas para una amplia variedad de escenarios:

* Mediante el uso del GPS de su dispositivo, un control de mapa puede mostrar su ubicación actual con una fórmula que use **Location.Latitude** y **Location.Longitude**.  A medida que se desplaza, el mapa seguirá automáticamente su ubicación.
* Otros usuarios pueden actualizar los [orígenes de datos](working-with-data-sources.md).  Por ejemplo, otros miembros del equipo pueden actualizar los elementos de una lista de SharePoint.  Al actualizar un origen de datos, las fórmulas dependientes se recalculan automáticamente para que reflejen los datos actualizados. En este mismo ejemplo, puede establecer la propiedad **[Items](controls/properties-core.md)** de una galería en la fórmula **Filter( SharePointList )**, que mostrará automáticamente el conjunto recién filtrado de [registros](working-with-tables.md#records).

### <a name="benefits"></a>Ventajas
El uso de fórmulas para compilar aplicaciones tiene muchas ventajas:

* Si está familiarizado con Excel, sabrá usar PowerApps. El lenguaje de fórmulas y modelos es el mismo.
* Si ha usado otras herramientas de programación, piense en la gran cantidad de código que sería necesario para llevar a cabo estos ejemplos.  En Visual Basic, tendría que escribir un controlador de eventos para el evento de cambio en cada control de entrada de texto.  El código para realizar el cálculo de cada uno de ellos es redundante y podría desincronizarse, o tendría que escribir una subrutina común.  En PowerApps, todo esto se consigue con una única fórmula de una línea.
* Para entender de dónde viene el texto de **TextBox1**, sabe exactamente dónde buscar: la fórmula de la propiedad **[Text](controls/properties-core.md)**.  No hay otra manera de influir en el texto de este control.  En una herramienta de programación tradicional, cualquier controlador de eventos o subrutina puede cambiar el valor de la etiqueta desde cualquier lugar del programa.  Esto puede hacer que sea difícil detectar cuándo y dónde se ha cambiado una variable.
* Si el usuario cambia un control deslizante pero después cambia de opinión, puede devolver el control deslizante a su valor original  y es como si nunca hubiera cambiado nada: la aplicación muestra los mismos valores de control que antes.  No hay repercusiones si se experimenta y se comprueba qué sucede al cambiar algo, igual que en Excel.  

En general, si puede conseguir un efecto mediante una fórmula, lo mejor es que la use. Deje que el motor de fórmulas de PowerApps trabaje por usted.  

## <a name="know-when-to-use-variables"></a>Saber cuándo usar variables
Vamos a cambiar el sumador simple para que actúe como una máquina de sumar antigua, con un total acumulado. Si selecciona el botón **Sumar**, sumará un número al total acumulado. Si selecciona el botón **Borrar**, restablecerá en cero el total acumulado.

![](media/working-with-variables/button-changes-state.png)

Esta máquina de sumar usa algo que no existe en Excel: un botón. En esta aplicación, no puede usar solamente fórmulas para calcular el total acumulado, ya que su valor depende de una serie de acciones que realiza el usuario. El total acumulado debe registrarse y actualizarse manualmente. La mayoría de las herramientas de programación almacena esta información en una *variable*.    

En ocasiones necesitará una variable para que la aplicación se comporte de la manera deseada,  pero debe tener en cuenta una serie de advertencias:

* Debe actualizar manualmente el total acumulado. El recálculo automático no lo hará por usted.
* El total acumulado ya no se puede calcular en función de los valores de otros controles. Depende del número de veces que el usuario haya seleccionado el botón **Sumar** y del valor que se encontrase en cada ocasión en el control de entrada de texto. ¿El usuario ha escrito 77 y ha seleccionado **Sumar** dos veces, o bien ha escrito 24 y 130 para cada una de las sumas? No es posible determinarlo una vez que el total haya alcanzado 154.
* Los cambios en el total pueden proceder de diferentes acciones. En este ejemplo, tanto el botón **Sumar** como el botón **Borrar** pueden actualizar el total. Si la aplicación no se comporta de la manera esperada, ¿qué botón causa el problema?

## <a name="create-a-global-variable"></a>Creación de una variable global
Para crear la máquina de sumar, necesitamos una variable que contenga el total acumulado. Las variables más sencillas para trabajar con PowerApps son las *variables globales*.  

Cómo funcionan las variables globales:

* Establezca el valor de la variable global con la función **[Set](functions/function-set.md)**.  **Set( MyVar, 1 )** establece la variable global **MyVar** en un valor de **1**.
* Use la variable global mediante la referencia al nombre usado con la función **Set**.  En este caso, **MyVar** devolverá **1**.
* Las variables globales pueden contener cualquier valor, como cadenas, números, registros y [tablas](working-with-tables.md).

Vamos a recompilar la máquina de sumar mediante el uso de una variable de global:

1. Agregue un control de entrada de texto, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:
   
    **Set( RunningTotal, RunningTotal + Text1 )**
   
    La primera vez que un usuario selecciona el botón **Sumar** y se llama a **[Set](functions/function-set.md)**, se crea **RunningTotal** con un valor predeterminado *en blanco*.  Además, se tratará como un cero.
   
    ![](media/working-with-variables/global-variable-1.png)
4. Para establecer el total acumulado en **0** cada vez que el usuario seleccione el botón **Borrar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:
   
    **Set( RunningTotal, 0 )**
   
    ![](media/working-with-variables/global-variable-2.png)
5. Agregue un control **[Etiqueta](controls/control-text-box.md)** y establezca su propiedad **[Texto](controls/properties-core.md)** en **RunningTotal** (TotalAcumulado).
   
    Esta fórmula se recalculará automáticamente y mostrará al usuario el valor de **RunningTotal** cuando cambie en función de los botones que el usuario seleccione.
   
    ![](media/working-with-variables/global-variable-3.png)
6. Obtenga una vista previa de la aplicación y ya tiene la máquina de sumar, tal como se describió anteriormente.  Escriba un número en el cuadro de texto y presione el botón de **suma** varias veces.  Cuando esté listo, vuelva a la experiencia de creación mediante la tecla Esc.  
   
    ![](media/working-with-variables/global-variable-4.png)
7. Para ver el valor de la variable global, seleccione el menú **Archivo** y seleccione **Variables** en el panel izquierdo.
   
    ![](media/working-with-variables/global-variable-file-1.png)
8. Para ver todos los lugares donde se define y se usa la variable, selecciónela.
   
    ![](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>Tipos de variables
Hay tres tipos de variables en PowerApps:

| Tipo de variable | Ámbito | Descripción | Functions |
| --- | --- | --- | --- |
| Variables globales |App |Las más sencillas de utilizar.  Contiene un número, una cadena de texto, un valor booleano, un registro, una tabla, etc. a los que se puede hacer referencia desde cualquier parte de la aplicación. |[**Set**](functions/function-set.md) |
| Variables de contexto |Pantalla |Idóneas para pasar valores a una pantalla, de forma parecida a como se pasan los parámetros a un procedimiento en otros lenguajes.  Solo se puede hacer referencia a ellas desde una pantalla. |[**UpdateContext**](functions/function-navigate.md) |
| Colecciones |App |Contiene una tabla a la que se puede hacer referencia desde cualquier lugar de la aplicación.  Permite que el contenido de la tabla se pueda modificar en lugar de establecerla como un todo. Se pueden guardar en el dispositivo local para su uso posterior. |[**Collect**](functions/function-savedata-loaddata.md)<br>etc. |

Todas las variables se crean implícitamente cuando se utilizan en las funciones **Set**, **UpdateContext**, **Navegar** o **Collect**.  No hay ninguna declaración explícita de variables como se hace en otras herramientas de programación.  Los tipos de las variables también se derivan implícitamente de los valores que se colocan en ellas.

Todas las variables se mantienen en la memoria mientras se ejecuta la aplicación.  Una vez que se cierra la aplicación, se pierden los valores almacenados en las variables.  Puede almacenar el contenido de una variable en un origen de datos mediante las funciones **Revisión** o **Collect**, o en el caso de las colecciones, puede almacenarlo en el dispositivo local con la función **SaveData**.  Cuando se carga la aplicación por primera vez, todas las variables tienen el valor *en blanco*.

Utilice el nombre de las variables para leer su valor.  Por ejemplo, una vez definido con **Set( MyColor, Red )** solo tiene que usar **MyVar** en cualquier lugar en el que un valor de color se use y se reemplazará por el color **rojo**.  Es posible tener una variable global o una colección con el mismo nombre que una variable de contexto.  En este caso, la variable de contexto tiene prioridad.  Todavía puede hacer referencia a la variable global o a la colección mediante el [operador de desambiguación](functions/operators.md#disambiguation-operator) **@[MyColor]**.

## <a name="create-a-context-variable"></a>Crear una variable de contexto
Veamos cómo se crearía la máquina de sumar mediante una variable de contexto en lugar de una variable global.    

Cómo funcionan las variables de contexto:

* Para crear y establecer variables de contexto, se usa la función **[UpdateContext](functions/function-updatecontext.md)**.  Si una variable de contexto todavía no existe cuando se actualiza por primera vez, se creará con un valor predeterminado *en blanco*.
* Las variables de contexto se crean y se actualizan con registros. En otras herramientas de programación, normalmente se usa "=" para la asignación, como en "x = 1".  En el caso de las variables de contexto, se usa **{ x: 1 }**. Cuando se usa una variable de contexto, se usa su nombre directamente.  
* También puede establecer una variable de contexto cuando se muestra una pantalla, mediante el uso de la función **[Navigate](functions/function-navigate.md)**. Si considera una pantalla como una especie de procedimiento o subrutina, es como pasar parámetros en otras herramientas de programación.
* Excepto en el caso de **[Navigate](functions/function-navigate.md)**, las variables de contexto están limitadas al contexto de una sola pantalla, que es donde obtienen su nombre.  No puede usarlas ni establecerlas fuera de este contexto.
* Las variables de contexto pueden contener cualquier valor, como cadenas, números, registros, y [tablas](working-with-tables.md).

Vamos a volver a compilar la máquina de sumar mediante el uso de una variable de contexto:

1. Agregue un control de entrada de texto, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:
   
    **UpdateContext( { RunningTotal: RunningTotal + Text1 } )**
   
    La primera vez que un usuario selecciona el botón **Sumar** y se llama a **[UpdateContext](functions/function-updatecontext.md)**, se crea **RunningTotal** con un valor predeterminado *en blanco*.  Además, se tratará como un cero.
   
    ![](media/working-with-variables/context-variable-1.png)
4. Para establecer el total acumulado en **0** cada vez que el usuario seleccione el botón **Borrar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:
   
    **UpdateContext( { RunningTotal: 0 } )**
   
    Una vez más, se usa **[UpdateContext](functions/function-updatecontext.md)** con la fórmula **UpdateContext( { RunningTotal: 0 } )**.
   
    ![](media/working-with-variables/context-variable-2.png)
5. Agregue un control **[Etiqueta](controls/control-text-box.md)** y establezca su propiedad **[Texto](controls/properties-core.md)** en **RunningTotal** (TotalAcumulado).
   
    Esta fórmula se recalculará automáticamente y mostrará al usuario el valor de **RunningTotal** cuando cambie en función de los botones que el usuario seleccione.
   
    ![](media/working-with-variables/context-variable-3.png)
6. Obtenga una vista previa de la aplicación y ya tiene la máquina de sumar, tal como se describió anteriormente.  Escriba un número en el cuadro de texto y presione el botón de **suma** varias veces.  Cuando esté listo, vuelva a la experiencia de creación mediante la tecla Esc.  
   
    ![](media/working-with-variables/context-variable-4.png)
7. Puede establecer el valor de una variable de contexto mientras se desplaza a una pantalla.  Esto resulta útil a la hora de pasar "contexto" o "parámetros" de una pantalla a otra.  Para verlo, inserte una nueva pantalla e inserte un botón con la propiedad **AlSeleccionar** establecida en:
   
    **Navegar( Screen1, None, { RunningTotal: -1000 } )**
   
    ![](media/working-with-variables/context-variable-5.png)
   
    Si selecciona este botón en **Screen2** (lo que puede hacer durante la creación si selecciona el botón situado en los extremos) aparecerá **Screen1** y se establecerá también la variable de contexto **RunningTotal** en -1000.
   
    ![](media/working-with-variables/context-variable-6.png)
8. Para ver el valor de la variable de contexto, seleccione el menú **Archivo** y seleccione **Variables** en el panel izquierdo.
   
    ![](media/working-with-variables/context-variable-file-1.png)
9. Para ver dónde se define y se usa la variable de contexto, selecciónela.
   
    ![](media/working-with-variables/context-variable-file-2.png)

## <a name="create-a-collection"></a>Crear una colección
Por último, veamos cómo crear la máquina de sumar con una colección.  Puesto que una colección contiene una tabla que es fácil modificar, vamos a hacer que esta máquina de sumar tenga un "registro" de todos los valores a medida que se escriben.

Cómo funcionan las colecciones:

* Para crear y establecer colecciones, use la función **[ClearCollect](functions/function-clear-collect-clearcollect.md)**.  También puede usar la función **[Collect](functions/function-clear-collect-clearcollect.md)**, pero requerirá otra variable en vez de reemplazar la anterior.  
* Una colección es una clase de origen de datos y, por lo tanto, una tabla. Para obtener acceso a un valor único de una colección, use la función **[First](functions/function-first-last.md)** y extraiga un campo del registro resultante. Si ha usado un solo valor con **[ClearCollect](functions/function-clear-collect-clearcollect.md)**, este será el campo **Value**, como en este ejemplo:<br>**First(** *VariableName* **).Value**

Vamos a recrear la máquina de sumar mediante una colección:

1. Agregue un control **[Text input](controls/control-text-input.md)**, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:
   
    **Collect( PaperTape, TextInput1.Text )**
   
    Esta fórmula agregará el nuevo valor al final de la colección.  Puesto que estamos agregando un valor único, **Collect** lo colocará automáticamente en una tabla de una sola columna con el nombre **Valor** que se utilizará más adelante.
   
    ![](media/working-with-variables/papertape-1.png)
4. Para borrar el registro cada vez que el usuario seleccione el botón **Borrar**, establezca su propiedad **[AlSeleccionar](controls/properties-core.md)** en esta fórmula:
   
    **Clear( PaperTape )**
   
    ![](media/working-with-variables/papertape-2.png)
5. Para mostrar el total acumulado, agregue una etiqueta y establezca su propiedad **[Texto](controls/properties-core.md)** en esta fórmula:
   
    **Sum( PaperTape, Value )**
   
    ![](media/working-with-variables/papertape-3.png)
6. Para ejecutar la máquina de sumar, presione F5 para abrir la vista previa, escriba números en el control de entrada de texto y seleccione botones.
   
    ![](media/working-with-variables/papertape-run-1.png)
7. Presione la tecla Esc para volver al área de trabajo predeterminada.
8. Para mostrar el registro, inserte un control **Tabla de datos** y establezca su propiedad **[Items](controls/properties-core.md)** en esta fórmula:
   
    **PaperTape**
   
    También debe seleccionar las columnas que se van a mostrar en el panel derecho, en nuestro caso, vamos a mostrar la columna **Valor**:
   
    ![](media/working-with-variables/papertape-4.png)
9. Para ver los valores de la colección, seleccione **Colecciones** en el menú **Archivo**.
   
    ![](media/working-with-variables/papertape-file.png)
10. Para almacenar y recuperar la colección, agregue dos controles de botón adicionales y establezca su texto en **Cargar** y **Guardar**.  Para **Cargar**, establezca la propiedad **AlSeleccionar** en:
    
     **Clear( PaperTape ); LoadData( PaperTape, "StoredPaperTape", true )**
    
     Es necesario borrar la colección primero ya que **LoadData** anexará los valores almacenados al final de la colección.
    
     ![](media/working-with-variables/papertape-5.png)
11. Para **Guardar**, establezca la propiedad **AlSeleccionar** en:
    
     **SaveData( PaperTape, "StoredPaperTape" )**
    
     ![](media/working-with-variables/papertape-6.png)
12. Vuelva a obtener la vista previa pulsando la tecla F5, escriba números en el control de entrada de texto y seleccione botones.  Seleccione el botón **Guardar**.  Cierre y vuelva a cargar la aplicación y seleccione el botón **Cargar** para volver a cargar la colección.  
    
    > [!NOTE]
    > **SaveData** y **LoadData** no funcionan en PowerApps Studio, pero sí en PowerApps Mobile.

