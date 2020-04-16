---
title: Crear extensiones para la herramienta de generación de código (Common Data Service) | Microsoft Docs
description: El paquete de descarga del SDK incluye una extensión a la herramienta de generación de código CrmSvcUtil que puede usar para generar enumeraciones para todos los valores del conjunto de opciones incluidos los conjuntos de opciones globales, la lista desplegable, el estado y los valores de estado.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ebc09cf522fa7847f087dc772bf23fed0ddb27fb
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156056"
---
# <a name="create-extensions-for-the-code-generation-tool"></a>Crear extensiones para la herramienta de generación de código

Puede ampliar la funcionalidad de la herramienta de generación de código especificando parámetros de línea de comandos y valores de parámetros adicionales. Para especificar un parámetro, agregue lo siguiente a la línea de comandos: /\<*nombre de parámetro*>:\<*nombre de clase*>,\<*nombre de ensamblado*>. Tenga en cuenta que el nombre del ensamblado no incluye la extensión .dll. Como alternativa, también puede agregar el valor equivalente al archivo de configuración con el formato “<add key=”\<*nombre de parámetro*>” value=”\<*nombre de clase*>,\<*nombre de ensamblado*>” />”.  

En la siguiente tabla se muestran los parámetros que puede usar.  

|Nombre del parámetro|Nombre de la interfaz|Descripción|  
|--------------------|--------------------|-----------------|  
|/codecustomization|ICustomizeCodeDomService|Se llama una vez finalizada la generación de CodeDOM, suponiendo que se trata de la instancia predeterminada de `ICodeGenerationService`. Es útil para generar clases adicionales, como las constantes de las listas desplegables.|  
|/codewriterfilter|ICodeWriterFilterService|Se llama durante el proceso de generación de CodeDOM, suponiendo que se trata de la instancia predeterminada de `ICodeGenerationService`, para determinar si debe generarse una propiedad o un objeto específico.|  
|/codewritermessagefilter|ICodeWriterMessageFilterService|Se llama durante el proceso de generación de CodeDOM, suponiendo que se trata de la instancia predeterminada de `ICodeGenerationService`, para determinar si debe generarse un mensaje específico. Esto no se recomienda para las solicitudes y respuestas pues ya se generan en Microsoft.Crm.Sdk.Proxy.dll y Microsoft.Xrm.Sdk.dll.|  
|/metadataproviderservice|IMetadataProviderService|Se le llama para recuperar los metadatos del servidor. La llamada puede realizarse varias veces durante el proceso de generación, por lo que los datos se deben almacenar en caché.|  
|/codegenerationservice|ICodeGenerationService|Implementación principal de la generación de CodeDOM. Si se cambia, las otras extensiones pueden no comportarse de la manera descrita.|  
|/namingservice|INamingService|Se llama durante la generación de CodeDOM para determinar el nombre de los objetos, suponiendo que se trata de la implementación predeterminada.|

La implementación de estas interfaces debe tener uno de los constructores siguientes:

`MyNamingService`()<br />
`MyNamingService`(`INamingService``defaultService`)<br />
`MyNamingService`(`IDictionary`<`string`, `string`> `parameters`)<br />
`MyNamingService`(`INamingService``defaultService`, `IDictionary`<`string`, `string`> `parameters`)

El espacio de nombres `Microsoft.Crm.Services.Utility` se define en CrmSvcUtil.exe. Agregue una referencia a CrmSvcUtil.exe en los proyectos de extensión de la herramienta de generación de código de Visual Studio.

<a name="Generate_Enums"></a>

## <a name="sample-extension-to-generate-enumerations-for-option-sets"></a>Ejemplo de extensión para generar enumeraciones para los conjuntos de opciones

El siguiente código de ejemplo muestra cómo escribir una extensión.  

```csharp
using System;

using Microsoft.Crm.Services.Utility;
using Microsoft.Xrm.Sdk.Metadata;

/// <summary>
/// Sample extension for the CrmSvcUtil.exe tool that generates early-bound
/// classes for custom entities.
/// </summary>
public sealed class BasicFilteringService : ICodeWriterFilterService
{
    public BasicFilteringService(ICodeWriterFilterService defaultService)
    {
        this.DefaultService = defaultService;
    }

    private ICodeWriterFilterService DefaultService { get; set; }

    bool ICodeWriterFilterService.GenerateAttribute(AttributeMetadata attributeMetadata, IServiceProvider services)
    {
        return this.DefaultService.GenerateAttribute(attributeMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateEntity(EntityMetadata entityMetadata, IServiceProvider services)
    {
        if (!entityMetadata.IsCustomEntity.GetValueOrDefault()) { return false; }
        return this.DefaultService.GenerateEntity(entityMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateOption(OptionMetadata optionMetadata, IServiceProvider services)
    {
        return this.DefaultService.GenerateOption(optionMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateOptionSet(OptionSetMetadataBase optionSetMetadata, IServiceProvider services)
    {
        return this.DefaultService.GenerateOptionSet(optionSetMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateRelationship(RelationshipMetadataBase relationshipMetadata, EntityMetadata otherEntityMetadata,
    IServiceProvider services)
    {
        return this.DefaultService.GenerateRelationship(relationshipMetadata, otherEntityMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateServiceContext(IServiceProvider services)
    {
        return this.DefaultService.GenerateServiceContext(services);
    }
}

```

Descargue el ejemplo [CrmSvcUtilExtensions](https://code.msdn.microsoft.com/Create-extensions-for-the-b8b24d1d) y [GeneratePickListEnums](https://code.msdn.microsoft.com/Create-extensions-for-the-3dd56a27). 

La extensión de ejemplo **GeneratePicklistEnums** crea un archivo de código fuente que contiene enumeraciones para todos los conjuntos de opciones y códigos de estado. Para obtener un ejemplo de cómo usar estas enumeraciones, vea el ejemplo de `SampleCode\CS\QuickStart`.  

Además, incluye un archivo de código auxiliar que contiene las enumeraciones generadas por todos los valores estándar. Estas enumeraciones se pueden usar en el código agregando el archivo `SampleCode\CS\HelperCode\OptionSets.cs` o `SampleCode\VB\HelperCode\OptionSets.vb` al proyecto.

Cada enumeración se pueda usar para probar o establecer el valor de una propiedad. Esta propiedad es normalmente un atributo de entidad pero algunos que se usan para otras propiedades.

### <a name="usage-example"></a>Ejemplo de uso

El ejemplo siguiente muestra cómo usar una de estas enumeraciones para establecer un valor en la entidad `Account`.

```csharp
// Instantiate an account object. Note the use of the option set enumerations defined
// in OptionSets.cs.
Account account = new Account { Name = "Fourth Coffee" };
account.AccountCategoryCode = new OptionSetValue((int)AccountAccountCategoryCode.PreferredCustomer);
account.CustomerTypeCode = new OptionSetValue((int)AccountCustomerTypeCode.Investor);

// Create an account record named Fourth Coffee.
// Save the record reference so we can delete it during cleanup later.
Guid accountId = service.Create(account);
```

### <a name="see-also"></a>Vea también

 [Crear clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/create-early-bound-entity-classes-code-generation-tool)<br />
 [Usar las clases de entidad con enlace en tiempo de compilación para crear, actualizar y eliminar](/dynamics365/customer-engagement/developer/use-entity-class-create-update-delete)<br />
 [Ejecución un programa sencillo mediante los servicios web](/dynamics365/customer-engagement/developer/simple-program-web-services)
