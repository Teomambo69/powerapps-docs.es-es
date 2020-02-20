---
title: " Uso de un lector de pantalla en aplicaciones basadas en modelos | Microsoft Docs"
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: c8ef71753fd743788b52b4f3578f829f153c0898
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543444"
---
# <a name="use-a-screen-reader"></a>Usar el lector de pantalla 


Los lectores de pantalla permiten que las aplicaciones basadas en modelos sean accesibles para personas con poca o ninguna visión o que necesitan soporte adicional en unas determinadas circunstancias, como la fatiga ocular. Se admiten los lectores de pantalla de uso más habitual, como Narrador, JAWS y NVDA. 

- [Más información sobre cómo trabajar con Narrador de Microsoft](https://support.microsoft.com/help/22798)
- [Más información sobre cómo trabajar con JAWS](https://www.freedomscientific.com/Products/Blindness/JawsDocumentation)


- [Más información sobre cómo trabajar con NVDA](https://www.nvaccess.org/get-help/)


## <a name="basic-tasks-using-a-screen-reader"></a>Tareas básicas con un lector de pantalla 

### <a name="open-an-app"></a>Abrir una aplicación

1.  En la barra de navegación, use la tecla **TAB** para desplazarse al control desplegable de aplicaciones y presione **Entrar** para abrir el mapa del sitio.
2.  Presione la tecla **TAB** hasta que escuche el nombre de la aplicación que quiere abrir (por ejemplo, "Ventas"). Presione **Entrar** para abrir la aplicación.

### <a name="use-scan-mode-in-narrator"></a>Uso del modo de exploración en Narrador
El modo de exploración se puede usar para navegar rápidamente por las aplicaciones con las teclas de dirección y los métodos abreviados de teclado comunes. Avance rápidamente a encabezados, vínculos, puntos de referencia, campos de formulario, controles y tablas con este método. Para activar y desactivar el modo de exploración, presione **Bloq Mayús+barra espaciadora**. Más información: [Uso del modo de examen](https://support.microsoft.com/help/22809/windows-10-narrator-using-scan-mode)

### <a name="find-your-way-around-the-app"></a>Obtener información básica sobre la aplicación

#### <a name="navigation-bar"></a>Barra de navegación
Al abrir una aplicación, aparece a la izquierda una barra vertical con iconos de subárea. Puede usar la tecla **TAB** para desplazarse por estos iconos hasta que escuche el nombre del área que quiera (como “Cuentas”), o bien puede usar el control de mapa del sitio. Por ejemplo, presione la tecla **TAB** hasta que escuche “Cuentas” y, después, presione **Entrar** para abrir la vista Cuentas.

#### <a name="grids"></a>Cuadrículas
Los lectores de pantalla navegan por las cuadrículas de forma más confiable y coherente, y enuncian los encabezados de fila y de columna, así como la posición dentro de la cuadrícula. La primera vez que se abre una cuadrícula, la tabulación predeterminada es el selector de vistas. 

Cada vez que se acceda a una celda de la cuadrícula desde fuera de la cuadrícula, Narrador enunciará el nombre de la tabla, los recuentos de filas y columnas y la posición del cursor en la tabla.

Si el cursor se encuentra dentro del encabezado de la tabla, desplácese rápidamente entre los encabezados usando la tecla **TAB** o **Mayús+TAB**. Narrador enunciará el nombre de cada encabezado a medida que se vaya accediendo a cada celda de encabezado. También se enuncia el tipo de celda (por ejemplo, "encabezado de columna"), la ubicación de la columna (por ejemplo, "columna 1 de 6") y si la columna está ordenada o seleccionada. Si se presiona **Entrar** en un encabezado de tabla, la tabla se ordenará por esa columna. Narrador enuncia el criterio de ordenación, y se puede presionar **Entrar** de nuevo para cambiar el orden.

Al salir de la última columna de la tabla, el cursor se desplaza a la segunda fila de la cuadrícula y, a partir de ese punto, hay que usar las teclas de dirección arriba y abajo para desplazarse por las celdas que no sean de encabezado. Si, en vez de eso, se vuelve a presionar la tecla **TAB**, el cursor se moverá al siguiente elemento interactivo, que suele ser la lista de filtros de la tabla. Al desplazarse por celdas que no son de encabezado, Narrador enuncia el nombre de la columna, la ubicación de la columna y el texto dentro de la celda.

#### <a name="forms"></a>Formularios
En Narrador existen varios modos de navegación disponibles para navegar por un formulario, siendo los más comunes los puntos de referencia, los encabezados y los campos de formulario. Para cambiar el modo de navegación, presione **Bloq Mayús+flecha arriba**. Mantenga presionada la tecla Bloq Mayús mientras presiona la tecla de flecha arriba para desplazarse por los modos hasta oír el modo que quiera usar. Luego, use Bloq Mayús+teclas de flecha izquierda y derecha para desplazarse por los distintos elementos. Por ejemplo, si quiere ir al campo Apellido de la sección Información de contacto de un contacto, haga lo siguiente:

1.  Mantenga presionada la tecla **Bloq Mayús** y presione la tecla de **flecha arriba** hasta que escuche "Puntos de referencia".
2.  Mantenga presionada la tecla **Bloq Mayús** y presione la tecla de **flecha derecha** hasta que escuche "Puntos de referencia".
3.  Para cambiar el modo, presione y mantenga presionada la tecla **Bloq Mayús** y presione la tecla de **flecha arriba** hasta que escuche "Campos de formulario".
4.  Navegue hasta el campo Apellido usando Bloq Mayús y las teclas de flecha izquierda y derecha hasta que escuche "Apellido". Narrador también enuncia el tipo de control, el valor, el estado y las instrucciones especiales relativas al campo.

La tecla TAB también se puede usar para desplazarse rápidamente a los elementos interactivos del formulario. Algunos campos de formulario tienen un icono que realizará la acción predeterminada si se presiona Ctrl+Entrar. Por ejemplo, un campo de formulario de correo electrónico podría tener un icono de sobre que abre un editor de correo electrónico. 

#### <a name="dashboardscharts"></a>Paneles/gráficos
Se puede navegar por los gráficos de un panel usando la tecla TAB y Bloq Mayús+teclas de flecha. Presione la tecla **TAB** para ir rápidamente a los elementos interactivos y use Bloq Mayús+una tecla de flecha para navegar por los elementos no interactivos, como encabezados, puntos de referencia y elementos.


> [!NOTE]
> Para disfrutar de todas las características de accesibilidad disponibles en los gráficos, debe tener instalada la actualización más reciente de [Windows 10](https://www.microsoft.com/enable/products/windows10/default.aspx).

#### <a name="interactive-dashboard-streams"></a>Secuencias de panel interactivo
Puede usar la tecla **TAB** o las teclas **Mayús+TAB** para desplazarse por las secuencias de panel interactivo (como las del panel Cuentas), o simplemente cambiar el modo de navegación hasta que escuche “Encabezados” y, seguidamente, usar la tecla **TAB** para desplazarse rápidamente por las secuencias de panel.

Para navegar por cada elemento de una secuencia de panel, use las teclas de flecha arriba y abajo. Narrador leerá el tipo de control y el título del control.

#### <a name="business-process-flows"></a>Flujos de proceso de negocio
Para navegar por un flujo de proceso de negocio, como el que se encuentra en la parte superior del formulario Cliente potencial, presione la tecla **TAB** para avanzar y **Mayús+TAB** para retroceder entre las entidades. Use la tecla **Entrar** en los botones **Mover a la izquierda** o **Mover a la derecha** para mostrar más entidades en el flujo del proceso. Narrador enuncia el tipo de entidad, la fase, el estado, el título, el número de elemento del total de elementos y si dicho elemento está seleccionado actualmente.

#### <a name="dialog-boxes"></a>Cuadros de diálogo

Cuando se abre un cuadro de diálogo, Narrador enuncia el título correspondiente. En los cuadros de diálogo con campos de entrada, el botón **Cerrar** tiene el foco de forma predeterminada, con lo cual se puede cerrar presionando **Entrar**. En los cuadros de diálogo que requieren una acción por parte del usuario, el foco está en el botón de acción principal, como **Eliminar** o **Aceptar**.

Para desplazarse por los controles, puede usar la tecla **TAB**. El cursor recorrerá cada elemento del cuadro de diálogo, y puede presionar **Esc** para cerrarlo.


