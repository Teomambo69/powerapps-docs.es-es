---
title: Entidad Divisa de la transacción (divisa) (Common Data Service) | Microsoft Docs
description: 'Obtenga más información sobre la divisa de la transacción, que es una función multidivisa que permite a los usuarios realizar transacciones financieras en varias monedas. Es posible agregar, comparar o analizar varios registros en diferentes monedas de transacción con respecto a una moneda única utilizando la moneda base.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="transaction-currency-currency-entity"></a>Entidad de divisa de la transacción (divisa)

Common Data Service es un sistema multidivisa, en el que cada registro se puede asociar con su propia divisa. Esta divisa se denomina la divisa de la *transacción*. Las características de multidivisa permiten a los usuarios realizar transacciones financieras, como oportunidades, ofertas, pedidos y facturas en varias divisas. Esta característica también ofrece al usuario final una opción de divisa cuando se produce una transacción financiera.  
  
 Se pueden agregar, comparar o analizar varios registros en distintas divisas de la transacción en relación con una sola divisa, mediante el uso de un tipo de cambio. Esto se conoce como la *divisa base*. Primero se define una divisa base de la organización y después se definen los tipos de cambios para asociar la divisa base con las divisas de la transacción. La divisa base es la divisa con la que se cotizan otras divisas. El tipo de cambio es el valor de una divisa de la transacción equivalente a una divisa base.  
  
 Al usar las propiedades de la divisa de la transacción, puede realizar las siguientes acciones:  
  
- Seleccionar la divisa con la que desea definir y realizar las transacciones de oportunidades, ofertas, pedidos y facturas.  
  
- Definir los tipos de cambio de la divisa en relación con la divisa base.  
  
- Definir las divisas de la transacción y definir un tipo de cambio para asociar la divisa base con la divisa de la transacción.  
  
- Capturar el valor de la transacción en la divisa base y la divisa de la transacción en todas las transacciones financieras.  
  
- Definir listas de precios de productos para cada divisa.  
  
Para usar varias divisas, la divisa base de una organización se debe definir durante la instalación del servidor y la configuración de la organización. Una vez configurada la divisa base de una organización, no es posible cambiarla. Este valor se almacena en el atributo `Organization.BaseCurrencyID`.  
  
Las divisas de la transacción se definen como parte de la configuración del sistema. Se puede definir un número ilimitado de divisas de la transacción. Las divisas de la transacción se relacionan con la divisa base con la definición de un tipo de cambio de la divisa.  
  
Después de definir la divisa base y la divisa de la transacción, se deben definir las listas de precios. Una organización puede tener varias listas de precios, que también se definen normalmente para un mercado geográfico de destino en la divisa local.  
  
Todas las entidades que participan en transacciones financieras admiten la divisa de la transacción. Por lo general, la divisa se hereda de la entidad de cuenta, oportunidad, etc., pero se puede cambiar según sea necesario.  
  
Para especificar la precisión decimal de la divisa de la transacción, puede usar el atributo `TransactionCurrency.CurrencyPrecision`. Para especificar el origen de la precisión para los atributos del tipo dinero, use el atributo <xref:Microsoft.Xrm.Sdk.Metadata.MoneyAttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.MoneyAttributeMetadata.PrecisionSource> Atributo:  
  
Todas las propiedades monetarias de un registro comparten la misma divisa de la transacción; por ejemplo, vea el atributo `Account.CreditLimit`. Para cada atributo monetario de una entidad, Common Data Service crea automáticamente un atributo monetario correspondiente, de solo lectura y calculado por el sistema que se denomina "base". Este es un atributo monetario que guarda el valor del atributo correspondiente en una divisa base equivalente; por ejemplo, vea el atributo `Account.CreditLimit_Base`.  
  
La fórmula siguiente se usa para calcular el valor base:  
  
```csharp  
creditlimit_base = creditlimit / exchangerate  
```  
  
Las siguientes son las entidades para las que se puede definir la divisa de la transacción.  
  
-   Cuenta  
  
-   AnnualFiscalCalendar  
  
-   Campaña  
  
-   CampaignActivity  
  
-   Competidor  
  
-   Contacto  
  
-   Contrato  
  
-   ContractDetail  
  
-   Descuento  
  
-   DiscountType  
  
-   FixedMonthlyFiscalCalendar  
  
-   Factura  
  
-   InvoiceDetail  
  
-   Cliente potencial  
  
-   Enumerar  
  
-   MonthlyFiscalCalendar  
  
-   Oportunidad  
  
-   OpportunityClose  
  
-   Producto de oportunidad  
  
-   Nivel de precios  
  
-   Producto  
  
-   ProductPriceLevel  
  
-   QuarterlyFiscalCalendar  
  
-   Oferta  
  
-   QuoteDetail  
  
-   Pedido de venta  
  
-   SalesOrderDetail  
  
-   SemiAnnualFiscalCalendar  
  
-   UserSettings  
  
### <a name="see-also"></a>Vea también  
 [Entidad TransactionCurrency](reference/entities/transactioncurrency.md)   
 [Ejemplo: recuperar el tipo de cambio de divisas](org-service/samples/retrieve-currency-exchange-rate.md)   
 [Entidades de administración de empresas](/dynamics365/customer-engagement/developer/business-management-entities)