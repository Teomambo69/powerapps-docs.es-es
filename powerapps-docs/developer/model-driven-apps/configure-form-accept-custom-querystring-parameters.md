---
title: Configure un formulario para aceptar parámetros querystring personalizados (aplicaciones basadas en modelos) | Microsoft Docs
description: Aprenda cómo configurar un formulario para aceptar parámetros querystring personalizados. Use estos parámetros para definir los valores predeterminados al crear un nuevo registro en la aplicación.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 89287d32-0d16-8f7d-e0b6-8cc208212cff
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-a-form-to-accept-custom-querystring-parameters"></a>Configurar un formulario para aceptar parámetros querystring personalizados

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/configure-form-accept-custom-querystring-parameters -->

La capacidad de transferir valores a una página web mediante cadenas de consulta representa un riesgo de seguridad. Las aplicaciones basadas en modelos aplican la práctica óptima de comparar siempre cualquier parámetro pasado como cadena de consulta con una lista de los nombres de parámetros y de tipos de datos esperados.  
  
 De forma predeterminada, las aplicaciones basadas en modelos permiten que un conjunto de parámetros de cadena de consulta especificado pase a un formulario. Use estos parámetros para definir los valores predeterminados al crear un nuevo registro en la aplicación. Cada parámetro debe usar una convención de nomenclatura estándar que incluye una referencia al nombre lógico del atributo. Para obtener más información, consulte [Establecer los valores de campo mediante parámetros que se pasan a un formulario](set-field-values-using-parameters-passed-form.md).  
  
 En sus aplicaciones, es posible que desee pasar parámetros de cadena de consulta personalizados a un formulario de entidad. Este tema proporciona información sobre cómo puede definir un conjunto de nombres de parámetros y de tipos de datos específicos que se pueden aceptar para un determinado formulario de entidad.  
  
## <a name="define-allowed-query-string-parameters"></a>Definir parámetros de cadena de consulta permitidos  
 Existen dos formas de especificar cuáles de los parámetros de la cadena de consulta serán aceptados por el formulario:  
  
-   Edición de propiedades de formularios  
  
-   Editar XML de formulario  
  
### <a name="edit-form-properties"></a>Edición de propiedades de formularios  
 Al editar un formulario de entidad, en la pestaña **Inicio**, en el grupo **Formulario**, haga clic en **Propiedades del formulario**. En el cuadro de diálogo **Propiedades del formulario**, seleccione la pestaña **Parámetros**.  
  
 Use esta pestaña para modificar los nombres y los tipos de datos que permite el formulario.  
  
### <a name="edit-formxml"></a>Editar FormXml  
 En el archivo exportado de la solución customizations.xml, inmediatamente después del elemento de pie de página, puede agregar un elemento de `<formparameters>`. En el elemento `<formparameters>` , agregue elementos de `<querystringparameter>` para especificar qué parámetros están permitidos.  
  
 A continuación se describen los atributos de los elementos de `querystringparameter`, `name` y `type`:  
  
- **nombre**. Cada atributo de nombre debe tener al menos un carácter subrayado ("\_"), pero el nombre del parámetro de cadena de la consulta no puede comenzar con un carácter subrayado. El nombre tampoco puede empezar con el “crm\_”. Se recomienda usar el prefijo de personalización del editor de soluciones como la convención de nomenclatura. Un valor de atributo válido del nombre `querystringparameter` es "myISV_contact_specialvalue".  
  
    > [!IMPORTANT]
    >  Si el nombre del elemento `querystringparameter` no es único, debe sobrescribirse con otra definición de parámetro con un tipo de datos diferente.  
  
- **Tipo**. Hacer coincidir los valores del tipo de datos con los valores de los parámetros de manera que los datos no válidos no pasen con el parámetro. Los siguientes son tipos de datos válidos:  
  
    -   Boolean  
  
    -   DateTime  
  
    -   Double  
  
    -   EntityType  
  
    -   Entero  
  
    -   Long  
  
    -   PositiveInteger  
  
        > [!NOTE]
        >  PositiveInteger incluye "0 " en el rango de valores válidos.  
  
    -   SafeString  
  
    -   UniqueId  
  
    -   UnsignedInt  
  
### <a name="see-also"></a>Vea también  
 [Establecer valores de campo usando parámetros pasados a un formulario](set-field-values-using-parameters-passed-form.md)   
 [Abrir formularios y vistas con una dirección URL](open-forms-views-dialogs-reports-url.md)
