---
title: Test Studio para la realización de pruebas de la aplicación de lienzo | Microsoft Docs
description: Describe Test Studio con información general, terminología, procedimientos recomendados y limitaciones.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/18/2019
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dc5ad83a127c812c2a97750ce0fbd05abee50bc7
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541184"
---
# <a name="test-studio-experimental"></a>Test Studio (experimental) 

Cree pruebas de interfaz de usuario de un extremo a otro para la aplicación de lienzo con Test Studio. Mantenga la calidad de la aplicación al validar de manera continuada que funciona según lo esperado cuando se implementan nuevos cambios o actualizaciones. 

## <a name="overview"></a>Información general

La realización de pruebas es una parte importante del ciclo de desarrollo de software (SDLC). La realización de pruebas ayuda a garantizar la calidad de la aplicación que se ofrece a los clientes. Puede identificar problemas o defectos al principio del proceso de lanzamiento y proporciona una oportunidad para corregir estos problemas con el fin de que la aplicación sea más confiable antes de publicar los cambios. En función del tamaño y el uso de la aplicación, es posible que la prueba manual de nuevos cambios sea suficiente. Sin embargo, a medida que la aplicación crezca en complejidad y uso, puede que tenga que considerar una estrategia de prueba en lugar de realizar pruebas manuales. Si la aplicación es crítica, incluso un pequeño error puede tener un impacto significativo.

El aumento de los cambios de la aplicación puede dar lugar a ciclos de prueba más largos. Finalmente, las pruebas de regresión de la aplicación pueden requerir más tiempo que el desarrollo de nuevas características. En el desarrollo rápido, probar exhaustivamente todas las características de la aplicación se convierte en un cuello de botella para la publicación de actualizaciones de software. Una opción para reducir el tiempo que se tarda en realizar un ciclo de pruebas y las pruebas de regresión es la automatización de las pruebas. La automatización de las pruebas puede ayudar a probar la aplicación con un esfuerzo mínimo, lo que reduce el tiempo de prueba e identifica los problemas críticos antes del lanzamiento.

Power Apps Test Studio es una solución de código bajo para escribir, organizar y automatizar pruebas para aplicaciones de lienzo. En Test Studio, es posible escribir pruebas mediante expresiones de Power Apps o usar una grabadora para guardar la interacción de la aplicación para generar automáticamente las expresiones. Es posible volver a reproducir las pruebas escritas en Test Studio para validar la funcionalidad de la aplicación, así como ejecutar las pruebas en un navegador web y compilar las pruebas automatizadas en el proceso de implementación de la aplicación.

![Test Studio](./media/test-studio/test-studio.png)

> [!NOTE]
> Esta característica aún es experimental y se recomienda usarla para escribir pruebas para aplicaciones que no sean de producción. Para obtener más información, vea [Características en versión preliminar y experimentales](working-with-experimental-preview.md).

## <a name="test-studio-terminology"></a>Terminología de Test Studio

En la siguiente sección se explica la terminología clave de Test Studio:

### <a name="test-cases"></a>Casos de prueba

Los casos de prueba se componen de una serie de instrucciones o acciones, llamadas pasos de prueba. Los casos de prueba se ejecutan para validar que la aplicación, o características específicas de ella, funcionan como se espera. Por ejemplo, en una aplicación de Gastos, conviene asegurarse de que solo se puedan enviar los gastos con el costo real asociado. Un caso de prueba puede ayudar a comprobar que esta condición o requisito siempre se cumpla.

En Test Studio, los pasos de prueba se escriben mediante el lenguaje de expresiones de Power Apps. Las expresiones de prueba pueden estar formadas por las funciones disponibles al compilar la aplicación y expresiones adicionales para admitir las pruebas automatizadas.

### <a name="test-suites"></a>Conjuntos de pruebas

Los conjuntos de pruebas se usan para organizar o agrupar casos de prueba. A medida que crece el número de casos de prueba de la aplicación, puede considerar la posibilidad de organizar los casos de prueba por características o funciones específicas. Por ejemplo, puede tener un conjunto de pruebas con casos de prueba para validar los envíos de informes de gastos y otro conjunto de pruebas que se centra solo en las aprobaciones de gastos.

Los casos de prueba que contienen los conjuntos de prueba se ejecutan secuencialmente. El estado de la aplicación se conserva en todos los casos de prueba de un conjunto. Por ejemplo, si tiene un caso de prueba que se completa en la pantalla 5 de la aplicación, el siguiente caso de prueba del conjunto de pruebas comenzará a ejecutarse desde la pantalla 5. Permite dividir un escenario de prueba complejo en varios casos de prueba dentro de un único conjunto y el estado se comparte entre todos los casos de prueba. Si el segundo caso de prueba debe comenzar en la pantalla de inicio de la aplicación, puede ir a la pantalla de inicio como primer paso en el caso de prueba. Al planear la ejecución de la prueba, es importante recordar que la aplicación no se vuelve a cargar al comienzo de cada caso de prueba de un conjunto.

### <a name="test-assertions"></a>Aserciones de pruebas

Cada caso de prueba debe tener un resultado esperado. Para validar el resultado esperado de una prueba con respecto al resultado real, puede escribir aserciones de prueba. Una aserción es una expresión que se evalúa como true o false en la prueba. Si la expresión devuelve false, se producirá un error en el caso de prueba.

En el ejemplo anterior de la aplicación de gastos, puede escribir una aserción para validar si un informe de gastos se crea con un elemento de la línea de gastos sin ningún costo asociado.

## <a name="best-practices"></a>Procedimientos recomendados

Al probar la aplicación de lienzo con Test Studio, cabe tener en cuenta las siguientes prácticas recomendadas para obtener las mayores ventajas para mejorar la calidad de la aplicación:

1. **Determine los casos de prueba que se deben automatizar.**

    Es difícil automatizar todas las pruebas y no se recomienda confiar completamente en la automatización. Las pruebas manuales deben realizarse junto con las automatizadas. Las pruebas más adecuadas para la automatización son:

    - Pruebas repetitivas.
    - Pruebas de funcionalidad de gran impacto empresarial.
    - Características que son estables y no están experimentando cambios significativos.
    - Características que requieren varios conjuntos de datos.
    - Pruebas manuales que requieren mucho tiempo y esfuerzo.

2. **Mantenga los casos de prueba pequeños.**

    Aunque un único caso de prueba puede admitir la prueba de todas las funciones de la aplicación, se recomienda evitar escribir un caso de prueba monolítica e intentar dividirlo en varios casos de prueba. Cada caso de prueba puede probar una característica o funcionalidad específica de la aplicación. Una aserción errónea en un caso de prueba grande puede hacer que no se pruebe otra funcionalidad. El uso de varios casos de prueba contenidos en el conjunto de pruebas permite probar otras funciones, independientemente de si se produjo un error en un caso de prueba anterior. Esta estrategia también facilita el aislamiento de los errores de prueba.

3. **Mantenga las expresiones en una única acción de prueba.**

    Una acción de prueba puede contener varias expresiones. Las expresiones de pruebas con varias acciones para un único paso pueden afectar a la capacidad de depuración y aislamiento de los errores de las pruebas. Considere la posibilidad de dividir un paso de prueba con varias acciones en más pasos de prueba con una única acción para identificar los problemas con mayor rapidez.  

4. **Cada caso de prueba debe tener un resultado esperado.**

    Cada caso de prueba debe tener uno o más resultados esperados. Las aserciones de prueba se deben utilizar para validar los resultados esperados de la prueba respecto a los resultados reales. Se pueden escribir varias aserciones para un único caso de prueba.

5. **Utilice los conjuntos de pruebas.**

    Para realizar tareas de mantenimiento, agrupe o clasifique los casos de prueba similares y describa el propósito y los resultados esperados de la prueba.

## <a name="known-limitations"></a>Limitaciones conocidas

Aunque se está trabajando para proporcionar una cobertura de control total en Power Apps Test Studio, la siguiente funcionalidad no está disponible en estos momentos:

- Componentes.
- Codificación de componentes escritos en el marco de componentes de Power Apps.
- Galerías anidadas.
- Controles multimedia.
- La característica experimental de administración de errores de nivel de fórmula debe estar activada para la aplicación.
- Compatibilidad con los controles que no aparecen en las funciones [Select](./functions/function-select.md) y [SetProperty](./functions/function-setproperty.md).
- Columnas de tipo de persona.
