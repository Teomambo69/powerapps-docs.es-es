---
title: Evento de atributo OnChange en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="attribute-onchange-event-client-api-reference"></a>Evento de atributo OnChange (referencia de la API de cliente)



El evento `OnChange` se produce en las siguientes situaciones:
- Los datos de un campo de formulario han cambiado y se pierde el foco. Hay una excepción a este comportamiento que se aplica a los campos de dos opciones (booleanos) que tiene el formato para usar botones de opción o casillas. En estos casos, el evento se produce inmediatamente.
- Los cambios de los datos del servidor se recuperan para actualizar un campo cuando se actualiza el formulario, como después de guardar un registro.
- Se usa el método attribute.[fireOnchange](../attributes/fireOnChange.md).

Todos los campos admiten el evento `OnChange`. Los datos del campo se validan antes y después del evento `OnChange`.

El evento `OnChange` no se produce si el campo se cambia mediante programación usando el método attribute.[setValue](../attributes/setValue.md). Si desea que los controladores de eventos para el evento `OnChange` se ejecuten después de configurar el valor, debe usar el método `formContext.data.entity attribute.`[fireOnchange.](../attributes/fireOnChange.md) en el código. 

> [!NOTE]
> Aunque el campo de **Status** admite el evento `OnChange`, el campo es de solo lectura en el formulario para que el evento no se pueda producir con la interacción del usuario. Otro script podría producir la aparición de este mediante el método [fireOnchange](../attributes/fireOnChange.md) en el campo.

## <a name="methods-supported-for-this-event"></a>Métodos admitidos para este evento
Hay tres métodos que puede usar para trabajar con el evento `OnChange` para un atributo:
- [addOnChange](../attributes/addOnChange.md)
- [fireOnChange](../attributes/fireOnChange.md)
- [removeOnChange](../attributes/removeOnChange.md)

### <a name="related-topics"></a>Temas relacionados
[Atributos (referencia de la API de cliente)](../attributes.md)
 



