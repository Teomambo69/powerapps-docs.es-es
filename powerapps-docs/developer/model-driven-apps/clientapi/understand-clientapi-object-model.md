---
title: Comprender el modelo de objeto de API de cleinte en aplicaciones basadas en modelos| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3335aec5-6b48-4ef6-8d49-2833b177f318
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="understand-the-client-api-object-model"></a>Comprender el modelo de objetos de la API del cliente



El modelo de objetos de la API del cliente para aplicaciones basadas en modelos proporciona objetos y métodos que puede usar para aplicar la lógica de negocio personalizada en aplicaciones basadas en modelos con JavaScript, como:
- Obtener o establecer valores de atributo.
- Ocultar o mostrar elementos de la interfaz de usuario.
- Hacer referencia a varios controles por atributo.
- Tener acceso a varios formularios por entidad.
- Manipular elementos de navegación del formulario.
- Interactuar con el control de flujo de proceso de negocio.

Es importante que comprenda el modelo de objetos de la API del cliente de aplicaciones basadas en modelos para escribir y usar el código JavaScript con eficacia en Customer Engagement.

## <a name="root-objects-in-the-client-api-object-model"></a>Objetos raíz en el modelo de objetos de la API del cliente

En la raíz del modelo de objetos de la API del cliente están los siguientes contextos y el objeto Xrm:

|Objeto|Descripción|
|--|--|
|**executionContext**|Representa el contexto de ejecución para un evento en los formularios y cuadrículas de aplicaciones basadas en modelos.<br/>Más información: [Contexto de ejecución de la API del cliente](clientapi-execution-context.md)|
|**formContext** |Proporciona una referencia a un formulario o un elemento en el formulario con respecto al que se ejecuta el código actual. Para obtener el objeto **formContext**, utilice el método **executionContext**.[getFormContext](reference/executioncontext/getFormContext.md).<br/>Más información: [Contexto de ejecución de la API del cliente](clientapi-form-context.md)|
|**gridContext** |Proporciona una referencia a un formulario o un elemento en el formulario con respecto al que se ejecuta el código actual.<br/>Más información: [Contexto de cuadrícula de la API del cliente](clientapi-form-context.md)|
|**Xrm**| Proporciona un objeto global para realizar las operaciones que no afectan directamente a los datos y la interfaz de usuario en formularios, cuadrículas, subcuadrículas, controles o atributos. Por ejemplo, vaya a formularios, cree y administre registros mediante la API web.<br/>Más información: [Objeto Xrm de API de cliente](clientapi-xrm.md)|

### <a name="related-topics"></a>Temas relacionados

[Contexto global de API del cliente](clientapi-xrm.md#client-api-global-context)<br/>
[Referencia de API de cliente](reference.md)








