---
title: Introducción a las soluciones | Microsoft Docs
description: Obtenga información sobre cómo se usan las soluciones para crear aplicaciones de modelo.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: jdaly
ms.openlocfilehash: b9e06888a23426a44eeaf4354bf456dd8b15cfad
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="introduction-to-solutions"></a>Introducción a las soluciones

Las *soluciones* son cómo los personalizadores y desarrolladores crean, empaquetan y mantienen unidades de software que amplían Common Data Service for Apps. Los desarrolladores y personalizadores distribuyen soluciones para que las organizaciones puedan usar Common Data Service for Apps para instalar y desinstalar la funcionalidad empresarial definida por la solución.

Todas las personalizaciones que se realicen en Common Data Service for Apps forman parte de una solución. Se realiza el seguimiento de todos los cambios que se apliquen y las dependencias se pueden calcular. Cuando se exporta una solución administrada, contiene todos los cambios que se han aplicado para esa solución en un archivo que, después, se puede importar en otro entorno de Common Data Service for Apps.

Si tiene previsto transportar las personalizaciones o extensiones entre otros entornos de Common Data Service for Apps o distribuir las soluciones mediante AppSource, debe entender el marco de trabajo de la solución.

## <a name="unmanaged-and-managed-solutions"></a>Soluciones administradas y no administradas

Hay dos tipos de soluciones: *administradas* y *no administradas*.

Una solución **administrada** es una solución completa que está pensada para su distribución e instalación. 
- Los componentes de una solución administrada no se pueden editar.
- Una solución administrada no se puede exportar.
- Se pueden agregar personalizaciones no administradas a los componentes de una solución administrada. Al hacerlo, se crea una dependencia entre las personalizaciones no administradas y la solución administrada. Cuando existe una dependencia, la solución administrada no se puede desinstalar hasta que se quite la dependencia.
- Cuando se elimina una solución administrada (se desinstala), se quitan todas las personalizaciones y extensiones incluidas con ella.

 > [!IMPORTANT]
 > Cuando se desinstala una solución administrada, se pierden los datos siguientes: los datos almacenados en las entidades personalizadas que forman parte de la solución administrada y los almacenados en los atributos personalizados que forman parte de la solución administrada en otras entidades que no forman parte de la solución administrada.

Una solución **no administrada** es la que todavía se está desarrollando o no está diseñada para ser distribuida. 
- Mientras que una solución es no administrada, se pueden seguir agregando y quitando componentes. 
- Una solución no administrada se puede exportar para transportar personalizaciones no administradas de un entorno a otro.
- Cuando se elimina una solución no administrada, solo se elimina el contenedor de solución de las personalizaciones que incluya. Todas las personalizaciones no administradas siguen en vigor y pertenecen a la solución predeterminada. 
- Cuando se completa la solución no administrada y se quiere distribuir, se exporta como una solución administrada.

 > [!NOTE]
 > No se puede importar una solución administrada al mismo entorno que contiene la solución no administrada de origen. Para probar una solución administrada, se necesita un entorno independiente al que importarla.

## <a name="solution-publishers"></a>Editores de soluciones
Cada solución se vincula a un editor de soluciones. El editor de soluciones proporciona información sobre cómo ponerse en contacto con el editor y también un valor de prefijo de personalización. El valor predeterminado es `new`.

Cuando se incluyen cambios de esquema como parte de una solución, el prefijo de personalización del editor de soluciones se antepone al nombre de los elementos de esquema. Este valor también se anexa a todas las acciones personalizadas. Esto es útil porque permite que sea fácil reconocer qué solución agregó el elemento de esquema o la acción personalizada. No es necesario que todos los elementos de esquema y las acciones personalizadas de una solución usen el mismo prefijo de personalización, pero se recomienda encarecidamente.

> [!IMPORTANT]
> Antes de empezar a crear una solución, se debe crear un registro de editor de soluciones y una solución vinculada a él. Debe asegurarse de que el prefijo de personalización representa un valor que tenga sentido para usted. 

La elección del editor de soluciones es importante en caso de que se quiera publicar una actualización de una solución que se ha enviado. Solo se puede aplicar una actualización a una solución administrada con el mismo editor que la solución administrada original. 

Más información: [Mantener soluciones administradas (Guía para desarrolladores de Dynamics 365 Customer Engagement) > Crear actualizaciones de solución administrada](/dynamics365/customer-engagement/developer/maintain-managed-solutions#create-managed-solution-updates)

## <a name="create-a-solution-publisher-and-solution"></a>Crear un editor de soluciones y una solución 

Para crear un editor de soluciones y una solución, hay que navegar hasta el área de personalización de Dynamics 365.

Desde [powerapps.com](https://web.powerapps.com)

1. Haga clic en el icono de *gofre* situado en la esquina superior izquierda.
2. En el control flotante, seleccione **Todas las aplicaciones**.
3. Busque**Dynamics 365: aplicación personalizada**.
 Puede hacer clic en los puntos suspensivos (...) y elegir **Pin this app** (Anclar esta aplicación) para que la próxima vez sea más fácil navegar hasta ella.
4. Haga clic en la aplicación **Dynamics 365: aplicación personalizada** y selecciónela.
5. Vaya a **Configuración** > **Personalización** > **Personalizaciones**.

Desde [home.dynamics.com](http://home.dynamics.com/)

1. Busque el icono **Dynamics 365: personalizado** y haga clic en él.
2. Vaya a **Configuración** > **Personalización** > **Personalizaciones**.

### <a name="create-a-solution-publisher"></a>Crear un editor de soluciones

1. En el área de personalizaciones, seleccione **Editores**.
2. Haga clic en **Nuevo**.
3. En el formulario de editor especifique un **Nombre para mostrar**. Se generará un valor **Nombre** en función del nombre para mostrar. Puede aceptar el valor generado o especificar uno nuevo.
4. En el campo **prefijo**, especifique el prefijo de personalización que se debe anexar a los elementos de esquema personalizados que se agreguen al desarrollar la solución. El valor predeterminado es `new`. Elija un valor que represente a la organización y permita a los usuarios identificar qué componentes instalados en su sistema proceden de la solución.
5. Se generará un valor **Prefijo de valor de opción** en función del prefijo de personalización elegido. Se trata de un valor que se anexará a los valores de las opciones de conjunto de opciones que se agreguen a los atributos de la solución. Este valor ayudará a identificar todas las opciones que se agreguen a la solución.
6. En la sección **Detalles de contacto** del formulario, se puede agregar cualquier información de contacto que se quiera proporcionar a los usuarios que instalen la solución.
7. Haga clic en **Guardar y cerrar** cuando haya terminado.

### <a name="create-a-solution"></a>Crear una solución

1. En el área de personalizaciones, seleccione **Soluciones**.
2. Haga clic en **Nuevo**.
3. En el formulario de la solución, escriba un **Nombre para mostrar**. Se generará un valor **Nombre** en función del nombre para mostrar. Puede aceptar el valor generado o especificar uno nuevo.
4. En el campo **Editor**, busque el editor que creó en [Crear un editor de soluciones](#create-a-solution-publisher)
5. En el campo **Versión**, seleccione una versión adecuada para la solución, por ejemplo, 1.0.0.0.
6. Haga clic en **Guardar** cuando haya terminado.

> [!IMPORTANT]
> Siempre que se crea un componente de solución que se va a incluir en esta solución, use esta solución, o bien otra asociada con el mismo editor de soluciones para agregarlo.
> Los componentes de solución creados en el contexto de una solución asociada a otro editor de soluciones se pueden agregar a esta solución, pero pueden tener valores de prefijo de personalización incoherentes establecidos.

## <a name="solution-layering"></a>Disposición en capas de la solución

Se pueden instalar dos soluciones administradas que se contradigan entre sí o, para ciertas personalizaciones, que se apliquen al entorno para invalidar una solución administrada. ¿Cómo funciona esto?

Funciona porque Common Data Service for Apps evalúa las soluciones administradas en el orden en el que se instalan y cualquier personalización que no esté en una solución administrada se evalúa en último lugar.

En el diagrama siguiente se presentan cómo interactúan las soluciones administradas y las personalizaciones no administradas para controlar qué se incluye en la aplicación en tiempo de ejecución.

![Diagrama en el que se muestra la disposición en capas de la solución](media/solution-layering.png)

En este ejemplo, el comportamiento predeterminado definido en la solución del sistema se invalida o anexa por las soluciones administradas. Después, las personalizaciones no administradas pueden invalidar o anexar las personalizaciones que son visibles en la aplicación.

Más información: [Introducción a las soluciones (Guía para desarrolladores de Dynamics 365 Customer Engagement) > Soluciones administradas y no administradas](/dynamics365/customer-engagement/developer/introduction-solutions#unmanaged-and-managed-solutions)

## <a name="managed-properties"></a>Propiedades administradas

Cuando se distribuye una solución administrada, cualquier usuario que instale la solución puede incluir en ella sus propias personalizaciones no administradas. Después, esas personalizaciones no administradas se pueden agregar a una solución que se distribuya como una solución administrada que depende de la solución. Pero, ¿qué ocurre si no quiere que los usuarios hagan esto? Como editor de la solución administrada puede usar propiedades administradas para deshabilitar personalizaciones específicas para los componentes de la solución administrada.

Más información: [Usar propiedades administradas (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/use-managed-properties)

## <a name="modular-solutions"></a>Soluciones modulares

Se puede usar el marco de trabajo de la solución para crear un conjunto discreto de componentes que proporcionan un conjunto de funcionalidades. Cada solución administrada se puede instalar y desinstalar para devolver la implementación del cliente a su estado original. Cada solución administrada que se crea se ejecuta sobre la solución del sistema y puede tener acceso a las funciones de la solución subyacente.

También se pueden compilar soluciones administradas que se ejecuten sobre otras soluciones para crear un conjunto de funcionalidades que otras soluciones puedan compartir. De esta manera, se puede crear y mantener un módulo común como una solución para admitir varias soluciones. Por este motivo, los clientes solo tendrán que instalar las soluciones que sean adecuadas para ellos y no será necesario incluir la misma funcionalidad compartida en todas las soluciones. Si hay que publicar una actualización de la solución que admita varias soluciones, solo habrá que actualizar el módulo común.

Después, los clientes, implementadores de sistemas y otros proveedores de software independientes, pueden compilar soluciones sobre las soluciones para lograr las personalizaciones específicas que necesitan.

Cuando un conjunto de funciones de negocio se compone de varias soluciones, se denominan paquetes. Puede usar el *Package Deployer* para combinar varias soluciones en una sola unidad instalable.

## <a name="deploy-solution-packages"></a>Implementar paquetes de solución

Use *Package Deployer* para crear un instalador personalizado para un paquete que puede incluir: 
- Uno o más archivos de solución.
- Archivos sin formato o archivos de datos de configuración exportados. 
- Código personalizado que se puede ejecutar antes, durante o después de implementar el paquete.
- Contenido HTML específico del paquete que se puede mostrar al principio y al final del proceso de implementación. Esto puede ser útil para proporcionar una descripción de las soluciones y los archivos que se implementan en el paquete.

Más información: [Crear paquetes para el Dynamics 365 Package Deployer (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/create-packages-package-deployer).

## <a name="team-development-of-solutions"></a>Desarrollo en equipo de soluciones

Un archivo de solución es un archivo binario único que no se presta al control de código fuente ni al desarrollo en equipo. No hay ningún medio para que varios desarrolladores puedan trabajar en los componentes personalizados de la solución.

La herramienta *SolutionPackager* resuelve el problema del control de código fuente y desarrollo en equipo de los archivos de solución. La herramienta identifica los componentes individuales del archivo de solución comprimido y los extrae en archivos individuales. La herramienta también puede volver a crear un archivo de solución empaquetando los archivos que se han extraído previamente. Esto permite que varias personas trabajen de forma independiente en una única solución y extraigan los cambios en una ubicación común. Como cada componente del archivo de solución se divide en varios archivos, es posible combinar personalizaciones sin sobrescribir los cambios anteriores. Un uso secundario de la herramienta SolutionPackager es que se puede invocar desde un proceso de compilación automatizado para generar un archivo de solución comprimido a partir de los archivos de componente extraídos previamente sin necesidad de una instancia activa de Dynamics 365.

Más información: [Herramientas de solución para el desarrollo en equipo (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/solution-tools-team-development)

### <a name="see-also"></a>Vea también

[Common Data Service for Apps Developer Overview](overview.md) (Introducción para desarrolladores de Common Data Service for Apps)