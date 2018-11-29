---
title: 'Ejemplo: Calcular una puntuación de crédito con una actividad de flujo de trabajo personalizada (Common Data Service para aplicaciones) | Microsoft Docs'
description: El ejemplo muestra una actividad de flujo de trabajo que calcula la puntuación de crédito basada en el número de la seguridad social (SSN) y el nombre.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
  - Dynamics 365 (online)
ms.assetid: 9cb7eb41-1a73-44a8-ae58-14120e84243f
caps.latest.revision: 19
author: JimDaly
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-calculate-a-credit-score-with-a-custom-workflow-activity"></a>Ejemplo: Calcular una puntuación de crédito con una actividad de flujo de trabajo personalizada

Este código de ejemplo es para Common Data Service para aplicaciones. Descargue el ejemplo completo aquí [Ejemplos de actividades de flujo de trabajo personalizadas](https://code.msdn.microsoft.com/Custom-Workflow-Activities-eee57285).

## <a name="prerequisites"></a>Requisitos previos

[!INCLUDE [sdk-prerequisite](../../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Requisitos

Las siguientes personalizaciones deben existir para que esta actividad de flujo de trabajo personalizada funcione:  

-   Nombre de esquema de entidad: `new_loanapplication`  
-   Atributo: `new_loanapplicationid` como clave principal  
-   Atributo: `new_creditscore` de tipo `int` con mínimo de 0 y máximo de 1000 (si se va a actualizar)  
-   Atributo: `new_loanamount` de tipo monetario con mínimo/máximo predeterminados  
-   Personalice el formulario para incluir el atributo `new_loanapplicantid`  
  
La entidad contacto debe tener las siguientes personalizaciones:  
  
-   Atributo: `new_ssn` como **Línea de texto única** con la longitud máxima de 15  
-   Relación de uno a varios con estas propiedades:  
    -   Nombre de esquema de definición de relación: `new_loanapplicant`  
    -   Nombre para mostrar de la entidad relacionada con la definición de relación: Aplicación de préstamo  
    -   Nombre de esquema de atributo de relación: `new_loanapplicantid`  
    -   Tipo de comportamiento de relación: Referencial  
  
## <a name="demonstrates"></a>Demostraciones

La siguiente actividad de flujo de trabajo de ejemplo calcula la puntuación de crédito basada en el número de la seguridad social (SSN) y el nombre.  
  
## <a name="example"></a>Ejemplo  

```csharp
/// <summary>
/// Calculates the credit score based on the SSN and name. 
/// </summary>
/// <remarks>
/// This depends on a custom entity called Loan Application and customizations to Contact.
/// 
/// Loan Application requires the following properties:
/// <list>
///     <item>Schema Name: new_loanapplication</item>
///     <item>Attribute: new_loanapplicationid as the primary key</item>
///     <item>Attribute: new_creditscore of type int with min of 0 and max of 1000 (if it is to be updated)</item>
///     <item>Attribute: new_loanamount of type money with default min/max</item>
///     <item>Customize the form to include the attribute new_loanapplicantid</item>
/// </list>
/// 
/// Contact Requires the following customizations
/// <list>
///     <item>Attribute: new_ssn as nvarchar with max length of 15</item>
///     <item>One-To-Many Relationship with these properties:
///         <list>
///             <item>Relationship Definition Schema Name: new_loanapplicant</item>
///             <item>Relationship Definition Related Entity Name: Loan Application</item>
///             <item>Relationship Atttribute Schema Name: new_loanapplicantid</item>
///             <item>Relationship Behavior Type: Referential</item>
///         </list>
///     </item>
/// </list>
/// 
/// The activity takes, as input, a EntityReference to the Loan Application and a boolean indicating whether new_creditscore should be updated to the credit score.
/// </remarks>
/// <exception cref=">ArgumentNullException">Thrown when LoanApplication is null</exception>
/// <exception cref=">ArgumentException">Thrown when LoanApplication is not a EntityReference to a LoanApplication entity</exception>
public sealed partial class RetrieveCreditScore : CodeActivity
{
    private const string CustomEntity = "new_loanapplication";

    protected override void Execute(CodeActivityContext executionContext)
    {
        //Check to see if the EntityReference has been set
        EntityReference loanApplication = this.LoanApplication.Get(executionContext);
        if (loanApplication == null)
        {
            throw new InvalidOperationException("Loan Application has not been specified", new ArgumentNullException("Loan Application"));
        }
        else if (loanApplication.LogicalName != CustomEntity)
        {
            throw new InvalidOperationException("Loan Application must reference a Loan Application entity",
                new ArgumentException("Loan Application must be of type Loan Application", "Loan Application"));
        }

        //Retrieve the CrmService so that we can retrieve the loan application
        IWorkflowContext context = executionContext.GetExtension<IWorkflowContext>();
        IOrganizationServiceFactory serviceFactory = executionContext.GetExtension<IOrganizationServiceFactory>();
        IOrganizationService service = serviceFactory.CreateOrganizationService(context.InitiatingUserId);

        //Retrieve the Loan Application Entity
        Entity loanEntity;
        {
            //Create a request
            RetrieveRequest retrieveRequest = new RetrieveRequest();
            retrieveRequest.ColumnSet = new ColumnSet(new string[] { "new_loanapplicationid", "new_loanapplicantid" });
            retrieveRequest.Target = loanApplication;

            //Execute the request
            RetrieveResponse retrieveResponse = (RetrieveResponse)service.Execute(retrieveRequest);

            //Retrieve the Loan Application Entity
            loanEntity = retrieveResponse.Entity as Entity;
        }

        //Retrieve the Contact Entity
        Entity contactEntity;
        {
            //Create a request
            EntityReference loanApplicantId = (EntityReference)loanEntity["new_loanapplicantid"];

            RetrieveRequest retrieveRequest = new RetrieveRequest();
            retrieveRequest.ColumnSet = new ColumnSet(new string[] { "fullname", "new_ssn", "birthdate" });
            retrieveRequest.Target = loanApplicantId;

            //Execute the request
            RetrieveResponse retrieveResponse = (RetrieveResponse)service.Execute(retrieveRequest);

            //Retrieve the Loan Application Entity
            contactEntity = retrieveResponse.Entity as Entity;
        }

        //Retrieve the needed properties
        string ssn = (string)contactEntity["new_ssn"];
        string name = (string)contactEntity[ContactAttributes.FullName];
        DateTime? birthdate = (DateTime?)contactEntity[ContactAttributes.Birthdate];
        int creditScore;

        //This is where the logic for retrieving the credit score would be inserted
        //We are simply going to return a random number
        creditScore = (new Random()).Next(0, 1000);

        //Set the credit score property
        this.CreditScore.Set(executionContext, creditScore);

        //Check to see if the credit score should be saved to the entity
        //If the value of the property has not been set or it is set to true
        if (null != this.UpdateEntity &amp;&amp; this.UpdateEntity.Get(executionContext))
        {
            //Create the entity
            Entity updateEntity = new Entity(loanApplication.LogicalName);
            updateEntity["new_loanapplicationid"] = loanEntity["new_loanapplicationid"];
            updateEntity["new_creditscore"] = this.CreditScore.Get(executionContext);

            //Update the entity
            service.Update(updateEntity);
        }
    }

    //Define the properties
    [Input("Loan Application")]
    [ReferenceTarget(CustomEntity)]
    public InArgument<EntityReference> LoanApplication { get; set; }

    [Input("Update Entity's Credit Score")]
    [Default("true")]
    public InArgument<bool> UpdateEntity { get; set; }

    [Output("Credit Score")]
    [AttributeTarget(CustomEntity, "new_creditscore")]
    public OutArgument<int> CreditScore { get; set; }
}
```
  
### <a name="see-also"></a>Vea también

[Extensiones de flujo de trabajo](workflow-extensions.md)<br />
[Tutorial: Crear extensión de flujo de trabajo](tutorial-create-workflow-extension.md)<br />
[Ejemplo: crear una actividad de flujo de trabajo personalizada](sample-create-custom-workflow-activity.md)<br />
[Ejemplo: actualizar el siguiente cumpleaños con una actividad de flujo de trabajo personalizada](sample-update-next-birthday-using-custom-workflow-activity.md)