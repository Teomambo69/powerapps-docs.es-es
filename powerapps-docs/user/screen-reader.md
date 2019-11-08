---
title: " Usar un lector de pantalla en aplicaciones controladas por modelos | MicrosoftDocs"
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543444"
---
# <a name="use-a-screen-reader"></a>Usar el lector de pantalla 


Los lectores de pantalla hacen que las aplicaciones controladas por modelos estén accesibles para personas con poca o ninguna visión o que necesiten soporte adicional para un escenario temporal, como la fatiga ocular. Se admiten lectores de pantalla de uso frecuente como narrador, JAWS y NVDA. 

- [Más información sobre cómo trabajar con el narrador de Microsoft](https://support.microsoft.com/help/22798)
- [Más información sobre cómo trabajar con JAWS](https://www.freedomscientific.com/Products/Blindness/JawsDocumentation)


- [Más información sobre cómo trabajar con NVDA](https://www.nvaccess.org/get-help/)


## <a name="basic-tasks-using-a-screen-reader"></a>Tareas básicas con un lector de pantalla 

### <a name="open-an-app"></a>Abrir una aplicación

1.  En la barra de navegación, use la tecla **Tab** para desplazarse al control desplegable de la aplicación y presione **entrar** para abrir el mapa del sitio.
2.  Presione la tecla **Tab** hasta que escuche el nombre de la aplicación que desea abrir (por ejemplo, "ventas"). Presione **entrar** para abrir la aplicación.

### <a name="use-scan-mode-in-narrator"></a>Usar el modo de exploración en narrador
Puede usar el modo de exploración para navegar rápidamente por las aplicaciones con las teclas de dirección y los métodos abreviados de teclado comunes. Saltar rápidamente a los encabezados, los vínculos, los puntos de referencia, los campos de formulario, los controles y las tablas en este modo. Active y desactive el modo de exploración presionando **Bloq Mayús + barra espaciadora**. Más información: [uso del modo de recorrido](https://support.microsoft.com/help/22809/windows-10-narrator-using-scan-mode)

### <a name="find-your-way-around-the-app"></a>Buscar el modo de la aplicación

#### <a name="navigation-bar"></a>Barra de navegación
Al abrir una aplicación, se muestra una barra vertical con iconos de subárea a la izquierda. Puede usar la tecla **Tab** para desplazarse por estos iconos hasta que escuche el nombre del área que desee, como "cuentas", o bien puede usar el control mapa del sitio. Por ejemplo, presione la tecla **Tab** hasta que escuche "cuentas" y, a continuación, presione **entrar** para abrir la vista cuentas.

#### <a name="grids"></a>Cuadrículas
Los lectores de pantalla navegan por las cuadrículas de forma más confiable y coherente, y anuncian los encabezados de fila y de columna, así como la posición dentro de la cuadrícula. La primera vez que se abre una cuadrícula, la tabulación predeterminada es el selector de vistas. 

Siempre que escriba una celda dentro de la cuadrícula desde fuera de la cuadrícula, el narrador anunciará el nombre de la tabla, los recuentos de filas y columnas y la posición del cursor en la tabla.

Si el cursor se encuentra dentro del encabezado de la tabla, desplácese rápidamente entre los encabezados mediante la tecla **Tab** o **MAYÚS + TAB**. El narrador anunciará el nombre de cada encabezado a medida que escriba la celda de encabezado. También se anuncia el tipo de celda (por ejemplo, "encabezado de columna"), la ubicación de la columna (por ejemplo, "columna 1 de 6") y si la columna está ordenada o seleccionada. Si presiona **entrar** en un encabezado de tabla, la tabla se ordenará por esa columna. Narrador anuncia el criterio de ordenación y puede presionar **entrar** de nuevo para cambiar el orden.

Al salir de la última columna de la tabla, el cursor se desplaza a la segunda fila de la cuadrícula y, desde este punto, debe utilizar las teclas de dirección arriba y abajo para desplazarse por las celdas que no son de encabezado. Si en su lugar vuelve a presionar la tecla **Tab** , el cursor se moverá al siguiente elemento interactivo, normalmente la lista de filtros de tabla. Al moverse entre las celdas que no son de encabezado, el narrador anuncia el nombre de la columna, la ubicación de la columna y el texto dentro de la celda.

#### <a name="forms"></a>Formularios
Hay varios modos de navegación disponibles para navegar por un formulario mediante narrador, donde los modos más comunes son puntos de referencia, encabezados y campos de formulario. Para cambiar el modo de navegación, presione **Bloq Mayús + Flecha arriba**. Mantenga presionada la tecla Bloq Mayús mientras presiona la tecla flecha arriba para desplazarse por los modos hasta oír el modo que desea usar. A continuación, use Bloq Mayús + las teclas de flecha izquierda y derecha para desplazarse por los distintos elementos. Por ejemplo, si desea ir al campo apellido en la sección información de contacto de un contacto, haga lo siguiente:

1.  Mantenga presionada la tecla **Bloq Mayús** y presione la tecla **flecha arriba** hasta que escuche "puntos de referencia".
2.  Mantenga presionada la tecla **Bloq Mayús** y presione la tecla de **flecha derecha** hasta que escuche "información de contacto".
3.  Para cambiar el modo, presione y mantenga presionada la tecla **Bloq Mayús** y presione la tecla **flecha arriba** hasta que escuche "campos de formulario".
4.  Navegue hasta el campo Last Name mediante Bloq Mayús + las teclas de dirección izquierda y derecha hasta que escuche "Last Name". El narrador también anuncia el tipo de control, el valor, el estado y las instrucciones especiales para el campo.

También puede usar la tecla TAB para desplazarse rápidamente a los elementos interactivos del formulario. Algunos campos de formulario tienen un icono que realizará la acción predeterminada al presionar Ctrl + entrar. Por ejemplo, un campo de formulario de correo electrónico podría tener un icono de sobre que abra un editor de correo electrónico. 

#### <a name="dashboardscharts"></a>Paneles y gráficos
Puede navegar por los gráficos del panel mediante la tecla TAB y Bloq Mayús + teclas de dirección. Presione la tecla **Tab** para ir rápidamente a los elementos interactivos y use Bloq Mayús + una tecla de dirección para navegar por los elementos no interactivos, como los encabezados, los puntos de referencia y los elementos.


> [!NOTE]
> Debe tener instalada la actualización más reciente de [Windows 10](https://www.microsoft.com/enable/products/windows10/default.aspx) para tener todas las características de accesibilidad disponibles para los gráficos.

#### <a name="interactive-dashboard-streams"></a>Flujos de paneles interactivos
Puede usar las teclas **Tab** o **MAYÚS + TAB** para desplazarse entre las secuencias del panel interactivo, como las que se encuentran en el panel cuentas, o simplemente cambiar el modo de navegación hasta que escuche "encabezados" y, a continuación, use la tecla **Tab** para desplazarse rápidamente entre secuencias del panel.

Para navegar por cada elemento de una secuencia del panel, utilice las teclas de dirección arriba y abajo. Narrador leerá el tipo de control y el título del control.

#### <a name="business-process-flows"></a>Flujos de procesos empresariales
Puede navegar por un flujo de proceso de negocio, como el que se encuentra en la parte superior del formulario de cliente potencial, presionando la tecla **Tab** para avanzar y **MAYÚS + TAB** para desplazarse hacia atrás entre las entidades. Use la tecla **entrar** en el **desplazamiento a la izquierda** o **Desplácese a los botones de la derecha** para mostrar entidades adicionales en el flujo del proceso. El narrador lee el tipo de entidad, la fase, el estado, el título, el número de elemento de los elementos totales y si está seleccionado actualmente.

#### <a name="dialog-boxes"></a>Cuadros de diálogo

Cuando se abre un cuadro de diálogo, narrador anuncia el título. En los cuadros de diálogo con campos de entrada, el botón **cerrar** tiene el foco predeterminado, lo que le permite cerrar el cuadro de diálogo presionando **entrar**. En los cuadros de diálogo que requieren una acción del usuario, el foco está en el botón acción principal, como **eliminar** o **Aceptar**.

Puede navegar por los controles mediante la tecla **Tab** . El cursor recorrerá en bucle cada elemento del cuadro de diálogo y podrá presionar **ESC** para cerrarlo.


