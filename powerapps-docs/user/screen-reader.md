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
ms.locfileid: "3302596"
---
# <a name="use-a-screen-reader"></a>Usar el lector de pantalla 


Los lectores de pantalla permiten que las aplicaciones basadas en modelos sean accesibles para personas con poca o ninguna visión o que necesitan soporte adicional en unas determinadas circunstancias, como la fatiga ocular. Los lectores de pantalla de uso general como Narrador, JAWS y NVDA son compatibles. 

- [Más información sobre el trabajo con el Narrador de Microsoft](https://support.microsoft.com/help/22798)
- [Más información sobre el trabajo con JAWS](https://www.freedomscientific.com/Products/Blindness/JawsDocumentation)


- [Más información sobre el trabajo con NVDA](https://www.nvaccess.org/get-help/)


## <a name="basic-tasks-using-a-screen-reader"></a>Tareas básicas con un lector de pantalla 

### <a name="open-an-app"></a>Abrir una aplicación

1.  En la barra de navegación, use la tecla **TAB** para desplazarse al control desplegable de aplicaciones y presione **Entrar** para abrir el mapa del sitio.
2.  Presione la tecla **TAB** hasta que escuche el nombre de la aplicación que quiere abrir (por ejemplo, "Ventas"). Presione **Enter** para abrir la aplicación.

### <a name="use-scan-mode-in-narrator"></a>Uso del modo de exploración en Narrador
El modo de exploración se puede usar para navegar rápidamente por las aplicaciones con las teclas de dirección y los métodos abreviados de teclado comunes. Avance rápidamente a encabezados, vínculos, puntos de referencia, campos de formulario, controles y tablas con este método. Active y desactive el modo de análisis pulsando **Bloq Mayús+barra espaciadora**. Más información: [Usar modo de examen](https://support.microsoft.com/help/22809/windows-10-narrator-using-scan-mode)

### <a name="find-your-way-around-the-app"></a>Obtener información básica sobre la aplicación

#### <a name="navigation-bar"></a>Barra de navegación
Al abrir una aplicación, aparece a la izquierda una barra vertical con iconos de subárea. Puede usar la tecla **TAB** para desplazarse por estos iconos hasta que escuche el nombre del área que quiera (como “Cuentas”), o bien puede usar el control de mapa del sitio. Por ejemplo, presione la tecla **Tabulador** hasta que el oiga “Cuentas” y, a continuación, presione **Enter** para abrir la vista de cuentas.

#### <a name="grids"></a>Cuestionarios
Los lectores de pantalla navegan por las cuadrículas de forma más fiable y consistente y anuncian la fila y encabezados de columna, así como la ubicación dentro de la cuadrícula. La primera vez que abre una cuadrícula, la tabulación predeterminada es el selector de la vista. 

Cada vez que entre en una celda de la cuadrícula desde fuera de la cuadrícula, Narrador anuncia el nombre de la tabla, los recuentos de la fila y de las columnas y la posición del cursor dentro de la tabla.

Si el cursor se encuentra dentro del encabezado de la tabla, navegue rápidamente entre los encabezados con la tecla **Tab** o **Mayús+Tab**. Narrador anunciará el nombre de cada encabezado cuando entre en la celda de encabezado. También se enuncia el tipo de celda (por ejemplo, "encabezado de columna"), la ubicación de la columna (por ejemplo, "columna 1 de 6") y si la columna está ordenada o seleccionada. Si se presiona **Entrar** en un encabezado de tabla, la tabla se ordenará por esa columna. Narrador anuncia el criterio de ordenación y puede presionar **Enter** de nuevo para cambiar el orden.

Cuando se mueve de la última columna de la tabla, el cursor se mueve a la segunda fila de la cuadrícula y, desde este punto, debe usar las teclas de dirección arriba y abajo para desplazarse entre las celdas que no sean de encabezado. Si en su lugar pulsa la tecla **Tabulador** nuevamente, el cursor se moverá al siguiente elemento interactivo, normalmente la lista de filtros de la tabla. Para desplazarse entre las celdas de la fila que no sean de encabezado, Narrador anuncia el nombre de la columna, la ubicación de la columna y el texto dentro de la celda.

#### <a name="forms"></a>Formularios
Los modos de navegación múltiple están disponibles para navegar en un formulario usando Narrador, siendo los modos más comunes los signos, encabezados y campos de formulario. Para cambiar el modo de navegación, presione **Bloq Mayús+Flecha arriba**. Mantenga presionada la tecla Bloq mayús mientras presiona la tecla de flecha arriba para ir pasando por los modos hasta que se oiga el modo desee usar. A continuación use el Bloq mayús + las teclas de dirección izquierda/derecha para desplazarse por los diversos elementos. Por ejemplo, si quiere ir al campo Apellido de la sección Información de contacto de un contacto, haga lo siguiente:

1.  Mantenga presionada la tecla **Bloq mayús** y presione la tecla **Flecha arriba** hasta que oiga “signos”.
2.  Mantenga presionada la tecla **Bloq mayús** y presione la tecla **Flecha derecha** hasta que oiga “Información de contacto”.
3.  Cambie el modo manteniendo presionada la tecla **Bloq mayús** y presionando la tecla **Flecha arriba** hasta que oiga “Campos de formulario”.
4.  Desplácese al campo Apellidos mediante Bloq mayús + las teclas de dirección izquierda/derecha hasta que se oiga “Apellido”. Narrador también anuncia el tipo de control, el valor, estado y cualquier instrucción especial para el campo.

También puede usar el tabulador para navegar rápidamente a los elementos interactivos en el formulario. Algunos campos de formulario tienen un icono que realizará la acción predeterminada al pulsar Ctrl+Enter. Por ejemplo, un campo de formulario de correo electrónico tiene un icono de sobre que abre un editor de correo electrónico. 

#### <a name="dashboardscharts"></a>Paneles/gráficos
Puede desplazarse por los gráficos de panel usando las teclas tabulador y Bloq mayús + las teclas de dirección. Presione la tecla **Tabulador** para obtener acceso rápido a los elementos interactivos y use Bloq mayús + una tecla de dirección para la navegación por elementos no interactivos, como encabezados, signos, y elementos.


> [!NOTE]
> Debe tener la última actualización de [Windows 10](https://www.microsoft.com/enable/products/windows10/default.aspx) instalada para tener todas las características de accesibilidad disponibles para los gráficos.

#### <a name="interactive-dashboard-streams"></a>Secuencias de panel interactivo
Puede usar la tecla **Tabulador** o las teclas **Bloq Mayús+Tab** para desplazarse entre secuencias del panel interactivo, como las que se encuentran en el panel Cuentas, o sólo cambiar el modo de navegación hasta que se oiga “Encabezados” y, a continuación, usar la tecla **Tabulador** para moverse rápidamente entre secuencias de paneles.

Para desplazarse a través de cada elemento de una secuencia de panel, use las teclas de dirección arriba y abajo. Narrador leerá el tipo de control y de título del control.

#### <a name="business-process-flows"></a>Flujos de proceso de negocio
Puede navegar por un flujo de proceso de negocio, como el que se encuentra en la parte superior del formulario de clientes potenciales, pulsando la tecla **Tabulador** para avanzar y **Mayús+Tab** para retroceder entre entidades. Use la tecla **Enter** en los botones **Desplazarse a la izquierda** o **Desplazarse a la derecha** para mostrar entidades adicionales en el flujo de proceso. Narrador enuncia el tipo de entidad, la fase, el estado, el título, el número de elemento del total de elementos y si dicho elemento está seleccionado actualmente.

#### <a name="dialog-boxes"></a>Cuadros de diálogo

Cuando se abre un cuadro de diálogo, Narrador enuncia el título correspondiente. En los cuadros de diálogo con campos de entrada, el botón **Cerrar** tiene el foco de forma predeterminada, con lo cual se puede cerrar presionando **Entrar**. En los cuadros de diálogo que requieren una acción por parte del usuario, el foco está en el botón de acción principal, como **Eliminar** o **Aceptar**.

Puede desplazarse por los controles con la tecla **Tabulador**. El cursor recorrerá cada elemento del cuadro de diálogo, y puede presionar **Esc** para cerrarlo.


