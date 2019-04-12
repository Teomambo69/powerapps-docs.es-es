---
title: Administrar excepciones en el código (Common Data Service) | Microsoft Docs
description: Este artículo analiza las excepciones que se devuelven desde una llamada al método de servicio web de Dynamics 365 Customer Engagement. El ejemplo de este artículo resalta los errores y las excepciones comunes que el diseño de su aplicación debe controlar.
ms.custom: ''
ms.date: 10/31/2018
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
# <a name="handle-exceptions-in-your-code"></a>Administrar las excepciones en su código

Existe un número de excepciones que se pueden obtener de una llamada al método de servicio web de Common Data Service. El diseño de su aplicación debe respetar y manejar de manera adecuada estas excepciones. En los ensamblados de SDK.NET, todas las llamadas al método de servicio web usan un canal de comunicaciones al servidor basado en la tecnología de Windows Communication Foundation. En términos de WCF, las excepciones obtenidas del canal reciben el nombre de *errores*.  

<a name="BKMK_Common"></a>   

## <a name="common-exceptions-and-faults"></a>Excepciones y errores comunes  

 El siguiente código se usa en la mayoría de los ejemplos de servicios web de Common Data Service. Resalta los errores y las excepciones comunes que debe manejar el diseño de su aplicación.  
  
```csharp
catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)
{
    Console.WriteLine("The application terminated with an error.");
    Console.WriteLine("Timestamp: {0}", ex.Detail.Timestamp);
    Console.WriteLine("Code: {0}", ex.Detail.ErrorCode);
    Console.WriteLine("Message: {0}", ex.Detail.Message);
    Console.WriteLine("Inner Fault: {0}",
        null == ex.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");
}
catch (System.TimeoutException ex)
{
    Console.WriteLine("The application terminated with an error.");
    Console.WriteLine("Message: {0}", ex.Message);
    Console.WriteLine("Stack Trace: {0}", ex.StackTrace);
    Console.WriteLine("Inner Fault: {0}",
        null == ex.InnerException.Message ? "No Inner Fault" : ex.InnerException.Message);
}
catch (System.Exception ex)
{
    Console.WriteLine("The application terminated with an error.");
    Console.WriteLine(ex.Message);

    // Display the details of the inner exception.
    if (ex.InnerException != null)
    {
        Console.WriteLine(ex.InnerException.Message);

        FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> fe = ex.InnerException
            as FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>;
        if (fe != null)
        {
            Console.WriteLine("Timestamp: {0}", fe.Detail.Timestamp);
            Console.WriteLine("Code: {0}", fe.Detail.ErrorCode);
            Console.WriteLine("Message: {0}", fe.Detail.Message);
            Console.WriteLine("Trace: {0}", fe.Detail.TraceText);
            Console.WriteLine("Inner Fault: {0}",
                null == fe.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");
        }
    }
}
```
  
> [!NOTE]
>  Si está accediendo al servicio web de detección, su código deberá obtener <xref:Microsoft.Xrm.Sdk.DiscoveryServiceFault> en lugar del fallo <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault> mostrado anteriormente.  
  
 Además de estas excepciones y errores, el código debe administrar las siguientes excepciones:  
  
-   [SecurityTokenValidationException](https://msdn.microsoft.com/library/system.identitymodel.tokens.securitytokenvalidationexception.aspx)  
  
-   [ExpiredSecurityTokenException](https://msdn.microsoft.com/library/system.servicemodel.security.expiredsecuritytokenexception.aspx)  
  
-   [SecurityAccessDeniedException](https://msdn.microsoft.com/library/system.servicemodel.security.securityaccessdeniedexception.aspx)  
  
-   [MessageSecurityException](https://msdn.microsoft.com/library/system.servicemodel.security.messagesecurityexception.aspx)  
  
-   [SecurityNegotiationException](https://msdn.microsoft.com/library/system.servicemodel.security.securitynegotiationexception.aspx)  
  
 Al conectarse a Common Data Service, es posible que se muestre una excepción `SecurityAccessDeniedException` si utiliza una cuenta Microsoft válida y su cuenta no está asociada con ninguna organización de Common Data Service. Se puede mostrar una `MessageSecurityException` si su cuenta Microsoft no es válido o se produjo un error de autenticación.  
  
<a name="BKMK_BusinessRuleErrors"></a>

## <a name="custom-errors-from-business-rules"></a>Errores personalizados de reglas de negocio
 
 Con Common Data Service, los personalizadores pueden crear reglas de negocio que se evalúan en el servidor. Los personalizadores pueden lanzar mensajes de error según las condiciones fijadas en la regla de negocio. Los programadores deben asegurarse de incluir un control de errores sólido en el código para obtener y resolver estas excepciones.  
  
 El siguiente es un ejemplo de registro de seguimiento que se produce cuando se devuelve uno de estos errores desde una regla de negocio denominada **Nombre de regla de negocio del ámbito de entidad que devuelve el error** y el mensaje de error es **mensaje de error personalizado**.  
  
```csharp
Unhandled Exception: System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]: custom error messageDetail:   
<OrganizationServiceFault xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/xrm/2011/Contracts">  
  <ErrorCode>-2147220891</ErrorCode>  
  <ErrorDetails xmlns:d2p1="http://schemas.datacontract.org/2004/07/System.Collections.Generic">  
    <KeyValuePairOfstringanyType>  
      <d2p1:key>OperationStatus</d2p1:key>  
      <d2p1:value xmlns:d4p1="http://www.w3.org/2001/XMLSchema" i:type="d4p1:string">0</d2p1:value>  
    </KeyValuePairOfstringanyType>  
    <KeyValuePairOfstringanyType>  
      <d2p1:key>SubErrorCode</d2p1:key>  
      <d2p1:value xmlns:d4p1="http://www.w3.org/2001/XMLSchema" i:type="d4p1:string">-2146233088</d2p1:value>  
    </KeyValuePairOfstringanyType>  
  </ErrorDetails>  
  <Message>custom error message</Message>  
  <Timestamp>2014-09-04T17:43:16.8197965Z</Timestamp>  
  <InnerFault i:nil="true" />  
  <TraceText>  
  
[Microsoft.Crm.ObjectModel: Microsoft.Crm.ObjectModel.SyncWorkflowExecutionPlugin]  
[cf6a25a9-5a34-e411-80b9-00155dd8c20f: ]  
Starting sync workflow 'Name of Entity Scope Business Rule returning Error', Id: c76a25a9-5a34-e411-80b9-00155dd8c20f  
Entering ConditionStep1_step:   
Entering SetMessage_step:   
Sync workflow 'Name of Entity Scope Business Rule returning Error' terminated with error 'custom error message'  
  
</TraceText>  
</OrganizationServiceFault>  
```  
  
 Más información: [Crear y editar reglas de negocio](https://technet.microsoft.com/library/dn531086.aspx)  
  
<a name="BKMK_AdditionalInfo"></a>   
## <a name="additional-information-about-exceptions"></a>Información adicional acerca de excepciones  
 Cuando se genera una excepción no detectada que contiene información confidencial que el usuario no tiene permiso para ver, la información confidencial de la excepción se oculta al usuario y se proporciona un número de referencia. Este número de referencia hace referencia a la entrada del registro de evento de servidor relacionado y a la entrada de seguimiento del servidor. El administrador del sistema puede buscar estas entradas y buscar más información sobre la excepción.  
  
### <a name="see-also"></a>Vea también  
 [Solución de problemas y control de errores](/dynamics365/customer-engagement/developer/troubleshooting-error-handling)   
 [Sugerencias para la solución de problemas](/dynamics365/customer-engagement/developer/troubleshooting-tips)   
 [Códigos de error de servicio web](web-service-error-codes.md)   
 [Administrar las excepciones en complementos](../handle-exceptions.md)   
 [Centro para desarrolladores .NET Framework](https://docs.microsoft.com/dotnet/framework/development-guide)