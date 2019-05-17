---
title: Usar Upsert para insertar o actualizar un registro (Common Data Service) | Microsoft Docs
description: El mensaje UpsertRequest (actualizar o insertar) le ayuda a simplificar varios escenarios de integración de datos en los que no sabe si ya existe un registro en Dynamics 365. En tales casos no sabrá si debe llamar a una operación UpdateRequest o CreateRequest. Esto da lugar a que consulte el registro primero para determinar si existe antes de realizar la operación adecuada. El mensaje UpsertRequest le ayuda a solucionar este problema
ms.custom: ''
ms.date: 02/23/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-upsert-to-insert-or-update-a-record"></a>Use Upsert para insertar o actualizar un registro

Puede reducir la complejidad que caracteriza a los escenarios de integración de datos mediante el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest>. Al cargar datos en Common Data Service desde un sistema externo, por ejemplo en un escenario de integración de datos en masa, quizá no sepa si ya existe un registro en Common Data Service. En tales casos no sabrá si debe llamar a una operación <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> o <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>. Esto da lugar a que consulte el registro primero para determinar si existe antes de realizar la operación adecuada. Ahora puede reducir esta complejidad y cargar los datos en Common Data Service más eficazmente utilizando el nuevo mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> (Actualizar o Insertar).  
  
<a name="BKMK_UsingUpsert"></a>   
## <a name="using-upsert"></a>Mediante Upsert  
 Es mejor usar <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> solo si no está seguro de si existe el registro. Es decir, cuando no está seguro si debe llamar a una operación <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> o <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>. Hay una disminución del rendimiento con <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> en lugar de usar <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>. Si está seguro de que el registro no existe, use <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>.  
  
 La <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> incluye una propiedad llamada <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest.Target>. Esta propiedad contiene la definición de entidad que se usará en una operación <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> o <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>. También incluye todos los atributos requeridos por la <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> para el tipo de entidad de destino para poder crear el registro si no existe.  
  
 Puede inspeccionar <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> para determinar si se creó el registro. <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> será true si el registro no existió y se creó. Será false si el registro ya existía y se actualizó. <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.Target> será una `EntityReference` al registro que existía o el registro que se creó.  
  
 Para comprender cómo funciona <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest>, vea la siguiente sección.  
  
<a name="BKMK_upsert"></a>   
## <a name="understanding-the-upsert-process"></a>Descripción del proceso de Upsert  
 Los siguientes pasos describen la lógica de procesamiento cuando se recibe una <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest>:  
  
1. Envíe <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> con suficientes datos para crear una operación de creación o inserción.  
  
2. Common Data Service consultará el registro objetivo de la entidad de destino.  
  
3. Si existe el registro:  
  
   1.  Establezca la propiedad Id. de la entidad de destino con el identificador del registro encontrado.  
  
   2.  Llame a Actualizar.  
  
   3.  Establezca la <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> como `false`.  
  
   4.  Cree un <xref:Microsoft.Xrm.Sdk.EntityReference> de la entidad de destino de la actualización como valor para <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.Target>.  
  
   5.  Devuelva la <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse>.  
  
4. Si el registro no existe:  
  
   1.  Copie los valores de clave alternativa en los atributos de entidad de destino.  
  
   2.  Llame a `Create`.  
  
   3.  Establezca la <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> como `true`.  
  
   4.  Cree una <xref:Microsoft.Xrm.Sdk.EntityReference> desde el tipo de entidad de destino y el resultado de Id. de la solicitud `Create` como valor para <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.Target>.  
  
   5.  Devuelva la <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse>.  
  
   El siguiente ejemplo muestra el proceso que revela cuándo se recibe una <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest>.  
  
   ![flujo del proceso de upsert](media/upsert-flowchart-dynamics-crm-2015.png "flujo del proceso de upsert")  
  
<a name="BKMK_SampleCode"></a>   
## <a name="sample-code"></a>Código de ejemplo  
 La operación de [Insertar o actualizar un registro mediante Upsert](http://go.microsoft.com/fwlink/p/?LinkId=532924) El archivo [ProductUpsertSample.cs](https://code.msdn.microsoft.com/Insert-or-update-a-record-aa160870/sourcecode?fileId=136218&pathId=1243320355) de ejemplo contiene el siguiente método `ProcessUpsert` para aplicar el mensaje de `UpsertRequest` sobre el contenido de un archivo XML para crear nuevos registros o actualizar los existentes.  
  
```csharp
public void ProcessUpsert(String Filename)
{
    Console.WriteLine("Executing upsert operation.....");
    XmlTextReader tr = new XmlTextReader(Filename);
    XmlDocument xdoc = new XmlDocument();
    xdoc.Load(tr);
    XmlNodeList xnlNodes = xdoc.DocumentElement.SelectNodes("/products/product");

    foreach (XmlNode xndNode in xnlNodes)
    {
        String productCode = xndNode.SelectSingleNode("Code").InnerText;
        String productName = xndNode.SelectSingleNode("Name").InnerText;
        String productCategory = xndNode.SelectSingleNode("Category").InnerText;
        String productMake = xndNode.SelectSingleNode("Make").InnerText;

        //use alternate key for product
        Entity productToCreate = new Entity("sample_product", "sample_productcode", productCode);

        productToCreate["sample_name"] = productName;
        productToCreate["sample_category"] = productCategory;
        productToCreate["sample_make"] = productMake;
        UpsertRequest request = new UpsertRequest()
        {
            Target = productToCreate
        };

        try
        {
            // Execute UpsertRequest and obtain UpsertResponse. 
            UpsertResponse response = (UpsertResponse)_serviceProxy.Execute(request);
            if (response.RecordCreated)
                Console.WriteLine("New record {0} is created!", productName);
            else
                Console.WriteLine("Existing record {0} is updated!", productName);
        }

        // Catch any service fault exceptions that Microsoft Dynamics CRM throws.
        catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>)
        {
            throw;
        }

    }
    // Prompts to view the sample_product entity records.
    // If you choose "y", IE will be launched to display the new or updated records.
    if (PromptForView())
    {
        ViewEntityListInBrowser();
    }

}
```
  
### <a name="see-also"></a>Vea también  
 [Uso del seguimiento de cambios para sincronizar los datos con sistemas externos](use-change-tracking-synchronize-data-external-systems.md)   
 [Defina claves alternativas para una entidad](define-alternate-keys-entity.md)   
 [Uso de claves alternativas](use-alternate-key-create-record.md)
