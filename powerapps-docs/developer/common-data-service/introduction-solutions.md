---
title: Introducción a las soluciones | Microsoft Docs
description: Conozca cómo se usan las soluciones para crear aplicaciones modelo.
services: ''
suite: powerapps
documentationcenter: na
author: shmcarth
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: kvivek
ms.workload: na
ms.date: 01/28/2019
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a621bf0ff0093a5100a14ccad9f3e4c3ebb9e1e7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752944"
---
# <a name="introduction-to-solutions"></a>Introducción a soluciones

Las *soluciones* son cómo los personalizadores y desarrolladores crean, empaquetan y mantienen las unidades de software que extienden Common Data Service. Por ejemplo, las aplicaciones de Dynamics 365 for Sales, Marketing, Customer Service se componen de soluciones. Los personalizadores y los desarrolladores distribuyen soluciones de modo que las organizaciones puedan usar Common Data Service para instalar y desinstalar la funcionalidad de su negocio definida por la solución.

Cada personalización que crea para Common Data Service o para una solución instalada anteriormente forma parte de una solución. Se realiza un seguimiento de cada cambio que se aplica y cualquier dependencia puede ser calculada. Cuando exporta una solución administrada, contiene todos los cambios que se han aplicado para esa solución en un archivo que puede importar a continuación en otro entorno de Common Data Service.

Si tiene previsto transportar personalizaciones o extensiones entre diferentes entornos de Common Data Service o distribuir soluciones mediante AppSource, debe comprender el marco de trabajo de la solución.

> [!NOTE]
> Para obtener información detallada sobre cómo usar eficazmente las soluciones para una administración correcta de del ciclo de vida (ALM) de la aplicación, consulte [Notas del producto: Administración del ciclo de vida de la solución](https://www.microsoft.com/download/details.aspx?id=57777)

## <a name="managed-and-unmanaged-solutions"></a>Soluciones administradas y no administradas

Existen dos tipos de soluciones: *administradas* y *no administradas*.

Una solución **administrada** es una solución completada que está diseñada para distribuir e instalar. 
- No puede editar los componentes de una solución administrada.
- No puede exportar una solución administrada.
- Puede agregar personalizaciones no administradas a componentes de una solución administrada. Al hacerlo, se crea una dependencia entre las personalizaciones no administradas y la solución administrada. Cuando exista una dependencia, la solución administrada no se puede desinstalar hasta que quite la dependencia.
- Cuando se elimina una solución administrada (desinstalada), todas las personalizaciones y extensiones incluidas con ella se quitan.

  > [!IMPORTANT]
  > Cuando desinstala una solución administrada, se pierden los siguientes datos: datos almacenados en las entidades personalizadas que forman parte de la solución adinistrada y datos almacenados en atributos personalizados que forman parte de la solución administrada en otras entidades que no forman parte de la solución administrada.

Una solución **no administrada** es la que aún está en desarrollo o no está diseñada para distribuirse. 
- Mientras una solución no esté administrada, puede seguir agregando y eliminando componentes. 
- Puede exportar una solución no administrada para transportar personalizaciones no administradas desde un entorno a otro.
- Cuando se elimina una solución no administrada, solo se elimina el contenedor de la solución de cualquier personalización incluida en ella. Todas las personalizaciones no administradas permanecen vigentes y pertenecen a la solución predeterminada. 
- Cuando se completa la solución no administrada y se desea distribuir, se puede exportar como una solución administrada.

  > [!NOTE]
  > No puede importar una solución administrada en el mismo entorno que contiene la solución no administrada original. Para probar una solución administrada, es necesario un entorno independiente para importarla.

## <a name="solution-publishers"></a>Editores de soluciones

Cada solución está vinculada a un editor de soluciones. El editor de soluciones proporciona información sobre cómo ponerse en contacto con el editor, así como un valor de prefijo de personalización. El valor predeterminado es `new`.

Cuando se incluyen cambios de esquema como parte de una solución, el prefijo de personalización del editor de soluciones se antepone al nombre de los elementos de esquema. Toda acción personalizada también tiene este valor anexado a ella. Esto es valioso porque permite reconocer fácilmente qué solución agregó el elemento de esquema o acción personalizada. No es necesario para todos los elementos y acciones personalizadas de esquema en una solución usar el mismo prefijo de personalización, pero se recomienda.

> [!IMPORTANT]
> Antes de comenzar a crear una solución, debe crear un registro de editor de soluciones y crear una solución nueva vinculada a él. Debe asegurarse de que el prefijo de personalización represente un valor que tenga sentido para usted. 

La opción del editor de soluciones es importante en caso de que desee publicar una actualización de una solución que ha enviado. Una actualización solo se puede aplicar a una solución administrada con el mismo editor que la solución administrada original. 

Más información: [Mantener soluciones administradas > Crear actualizaciones de soluciones administradas](/dynamics365/customer-engagement/developer/maintain-managed-solutions#create-managed-solution-updates)

## <a name="create-a-solution-publisher-and-solution"></a>Cree un editor de soluciones y una solución 

Para crear un editor de soluciones y una solución necesita navegar al área de personalización de Common Data Service.

Desde [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)

1. Seleccione el icono *gofre* en la esquina superior izquierda
2. En control flotante, seleccione **Todas las aplicaciones**.
3. Busque la **Common Data Service - aplicación personalizada**.
 Es posible que desee hacer clic en las elipses (...) y elegir **Anclar esta aplicación** para que sea más sencillo navegar la próxima vez.
4. Haga clic en la aplicación **Common Data Service - aplicación personalizada** y selecciónela.
5. Navegue a **Configuración** > **Personalización** > **Personalizaciones**.

Desde [home.dynamics.com](https://home.dynamics.com/)

1. Busque la ventana **Common Data Service - personalizada** y haga clic.
2. Navegue a **Configuración** > **Personalización** > **Personalizaciones**.

### <a name="create-a-solution-publisher"></a>Crear un editor de soluciones

1. Desde el área de las personalizaciones, seleccione **Editores**.
2. Haga clic en **Nuevo**.
3. En el formulario del editor escriba un **Nombre para mostrar**. Se generará un valor **Nombre** en función del nombre para mostrar. Puede aceptar el valor generado o especificar uno nuevo.
4. En el campo **prefijo** , especifique el prefijo de personalización que debe anexarse a cualquier elemento de esquema personalizado que agregue al desarrollar su solución. El valor predeterminado es `new`. Elija un valor que represente a la organización y ayude a las personas a identificar qué componentes instalados en su sistema proceden de la solución.
5. Un valor **Prefijo de valor de opción** se generará en función de su elección para el prefijo de personalización. Este es un valor que se anexará a cualquier valor de las opciones del conjunto de opciones que agregue a los atributos en la solución. Este valor ayudará a identificar las opciones que agregue a la solución.
6. En la sección **Detalles de contacto** del formulario, puede agregar la información de contacto que desee proporcionar a las personas que instalen su solución.
7. Haga clic en **Guardar y cerrar** cuando esté listo.

### <a name="create-a-solution"></a>Crear una solución

1. Desde el área de las personalizaciones, seleccione **Soluciones**.
2. Haga clic en **Nuevo**.
3. En el formulario de la solución escriba un **Nombre para mostrar**. Se generará un valor **Nombre** en función del nombre para mostrar. Puede aceptar el valor generado o especificar uno nuevo.
4. En el campo **Editor** busque el editor que haya creado en [Crear un editor de soluciones](#create-a-solution-publisher)
5. En el campo **Versión** seleccione una versión adecuada para la solución, como 1.0.0.0.
6. Haga clic en **Guardar** cuando haya terminado.

> [!IMPORTANT]
> Siempre que cree un nuevo componente de solución que se incluirá en esta solución, use esta solución u otra solución asociada con mismo editor de soluciones para agregarlo.
> Los componentes de una solución creados en el contexto de una solución asociada a otro editor de soluciones se pueden agregar a esta solución, pero podrían tener valores de prefijo de personalización incoherentes establecidos.

## <a name="solution-layering"></a>Disposición en capas de la solución

Es posible que dos soluciones administradas que se van a instalar se contradigan entre ellas o que algunas personalizaciones aplicadas al entorno reemplacen a una solución administrada. ¿Cómo funciona?

Funciona porque Common Data Service evalúa las soluciones administradas por el orden en el que se instalan y cualquier personalización que no esté en una solución administrada se evalúa al final.

El siguiente diagrama muestra cómo las soluciones administradas y la personalizaciones no administradas interactúan para controlar lo que está incluido en el tiempo de ejecución de la aplicación.

![Diagrama que muestra la disposición en capas de la solución](media/solution-layering.png)

En este ejemplo, el comportamiento predeterminado definido en la solución del sistema es reemplazado o anexado por soluciones administradas. Las personalizaciones no administrada pueden reemplazar o anexar las personalizaciones que sean visibles en la aplicación.

Más información: [Introducción a soluciones > Soluciones administradas y no administradas](/dynamics365/customer-engagement/developer/introduction-solutions#managed-and-unmanaged-solutions).

## <a name="managed-properties"></a>Propiedades administradas

Cuando distribuya una solución administrada, cualquier persona que instale la solución puede incluir sus propias personalizaciones no administradas. Esas personalizaciones no administrada se pueden a agregar a una solución que distribuyeron como una solución administrada que depende de su solución. ¿Pero qué sucede si no desea que los usuarios hagan esto? Como el editor de la solución administrada puede usar propiedades administradas para deshabilitar las personalizaciones específicas de los componentes de la solución administrada.

Más información: [Usar propiedades administradas](use-managed-properties.md)

## <a name="modular-solutions"></a>Soluciones modulares

Puede usar el marco de trabajo de la solución para crear un conjunto discreto de componentes que proporcionen un conjunto de funcionalidades. Cada solución administrada se puede instalar y desinstalar para devolver la implementación del cliente a su estado original. Cada solución administrada que cree se ejecuta sobre la solución del sistema y puede tener acceso a las capacidades de esa solución subyacente.

También puede crear soluciones administradas que se ejecuten sobre otras soluciones para crear un conjunto de funcionalidades que se puedan compartir por diferentes soluciones. De esta forma, puede crear y mantener un módulo común como una solución para admitir varias soluciones. Por este motivo, los clientes solo necesitan instalar las soluciones adecuadas para ellos y usted no necesita incluir la misma funcionalidad compartida en cada solución. Si necesita eliminar una actualización a la solución que admite varias soluciones, solo necesita actualizar el módulo común.

Los clientes, los implementadores del sistema y otros ISV pueden a crear soluciones sobre sus soluciones para conseguuir las personalizaciones específicas que necesitan.

Cuando forman un conjunto de funcionalidad de su negocio con varias soluciones, estas se denominan los paquetes. Puede usar el *Package Deployer* para combinar varias soluciones en una sola unidad instalable.

## <a name="deploy-solution-packages"></a>Implementar paquetes de soluciones

Use el *Package Deployer* para crear un instalador personalizado para un paquete que pueda incluir 
- Uno o varios archivos de solución.
- Archivos sin formato o archivos de datos de configuración exportados. 
- El código personalizado que puede ejecutarse antes, durante o después de la implementación del paquete.
- Contenido HTML específico del paquete que mostrarse al principio y al final del proceso de implementación. Puede resultar útil para proporcionar una descripción de las soluciones y los archivos que se implementan en el paquete.

Más información: [Crear paquetes para Common Data Service Package Deployer](package-deployer/create-packages-package-deployer.md).

## <a name="team-development-of-solutions"></a>Desarrollo del equipo de soluciones

Un archivo de solución es un solo archivo binario que no permite el control de código fuente ni el desarrollo en equipo. No hay forma de que varios programadores trabajen en los componentes personalizados de la solución.

La herramienta *SolutionPackager* resuelve el problema del control del código fuente y el desarrollo en equipo de los archivos de solución. La herramienta identifica los componentes individuales del archivo de solución comprimido y los extrae en archivos individuales. La herramienta puede también volver a crear un archivo de solución empaquetando los archivos que se habían extraídos anteriormente. Esto permite a varios usuarios trabajar de forma independiente en una sola solución y extraer los cambios en una ubicación común. Ya que cada componente del archivo de solución está separado en varios archivos, es posible combinar personalizaciones sin sobrescribir cambios anteriores. Un uso secundario de la herramienta SolutionPackager es que puede ser invocada desde un proceso automatizado de compilación para generar un archivo de solución comprimido a partir de los archivos componentes extraídos anteriormente sin necesidad de una instancia de Common Data Service.

Más información: [Herramientas de solución para el desarrollo en equipo](/dynamics365/customer-engagement/developer/solution-tools-team-development)

### <a name="see-also"></a>Vea también

[Información general para desarrolladores de Common Data Service](overview.md)
