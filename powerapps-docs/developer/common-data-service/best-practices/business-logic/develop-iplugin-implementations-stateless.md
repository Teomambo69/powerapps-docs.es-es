---
title: Desarrollar implementaciones de IPlugin como sin estado | MicrosoftDocs
description: Los miembros de clases que implementan IPlugin se exponen a problemas potenciales de seguridad de los subprocesos que pueden llevar a incoherencia o problemas de rendimiento.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 9/05/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9a0a91420cf29a2f44e8d1f32520e7fb529e07eb
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753064"
---
# <a name="develop-iplugin-implementations-as-stateless"></a>Desarrollar implementaciones de IPlugin como sin estado

**Categoría**: diseño, rendimiento

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Los miembros de clases que implementan <xref href="Microsoft.Xrm.Sdk.IPlugin?text=IPlugin interface" /> se exponen a problemas potenciales de seguridad de los subprocesos que pueden llevar a:

- Incoherencias de datos
- Ejecuciones de complementos más lentas

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Cuando implemente <xref:Microsoft.Xrm.Sdk.IPlugin>, no utilice los campos y las propiedades del miembro y escriba el método <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*> como una operación sin estado.  Se debe acceder a toda la información por estado de invocación a través del contexto de ejecución únicamente.  

No intente almacenar los datos de estado de ejecución en campos o propiedades de miembros para su uso durante la invocación del complemento siguiente, a menos que esos datos se hayan obtenido del parámetro de configuración proporcionado al constructor sobrecargado.

No use código que se registre en eventos AppDomain. La lógica de complementos no debe basarse en ningún evento o propiedad de AppDomain, ya que la implementación interna de la infraestructura dek complemento puede cambiar el comportamiento de la ejecución en cualquier momento. Esto puede causar errores incluso si el código funcionó en algún momento.

Los miembros de sólo lectura, estáticos y constantes son intrínsecamente seguros para los subprocesos y también pueden utilizarse de forma fiable dentro de una clase de complementos. A continuación se ofrecen algunos ejemplos sobre cómo mantener complementos seguros para los subprocesos:

- Miembros de un campo constante

    ```csharp
    public class Valid_ClassConstantMember : IPlugin
    {
        public const string validConstantMember = "Plugin registration not valid for {0} message.";

        public void Execute(IServiceProvider serviceProvider)
        {
            var context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));

            if (context.MessageName.ToLower() != "create")
                throw new InvalidPluginExecutionException(String.Format(Valid_ClassConstantMember.validConstantMember, context.MessageName));
        }
    }
    ```

- Datos de configuración de almacenamiento asignados o establecidos en el constructor de clases de complementos
    ```csharp
    public class Valid_ClassFieldConfigMember : IPlugin
    {
        private string validConfigField;

        public Valid_ClassFieldConfigMember(string unsecure, string secure)
        {
            this.validConfigField = !String.IsNullOrEmpty(secure)
                ? unsecure
                : secure;
        }

        public void Execute(IServiceProvider serviceProvider)
        {
            if (!String.IsNullOrEmpty(this.validConfigField))
            {
                var message = ValidHelperMethod();
            }
        }

        private string ValidHelperMethod()
        {
            return String.Format("{0} is the config value.", this.validConfigField);
        }
    }
    ```

- Implementación de método sin estado

    ```csharp
    public class Valid_ClassStatelessMethodMember : IPlugin
    {
        public void Execute(IServiceProvider serviceProvider)
        {
            var context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
    
            if (ValidMemberMethod(context))
            {
                //Then continue with execution
            }
        }
    
        private bool ValidMemberMethod(IPluginExecutionContext context)
        {
            if (context.MessageName.ToLower() == "create")
                return true;
            else
                return false;
        }
    }
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

> [!WARNING]
> Estos patrones deben evitarse.

- Asignación de miembros de clase de complemento durante la ejecución del complemento
 
    ```csharp
    public class Violation_ClassAssignFieldMember : IPlugin
    {
        //The instance member used in multiple violation patterns
        internal IOrganizationService service = null;
        internal IPluginExecutionContext context = null;
    
        public void Execute(IServiceProvider serviceProvider)
        {
            this.context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
            var factory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    
            //The violation
            this.service = factory.CreateOrganizationService(this.context.UserId);
    
            //Invoke another violation in method member
            AccessViolationProperties();
        }
    
        private void AccessViolationProperties()
        {
            //Accessing the context and service fields exposes this IPlugin implementation to thread-safety issues
            var entity = new Entity("task");
            entity["regardingid"] = new EntityReference(this.context.PrimaryEntityName, this.context.PrimaryEntityId);
    
            var id = this.service.Create(entity);
        }
    }
    ```

- Configuración de la propiedad de clase de complemento durante la ejecución del complemento

    ```csharp
    public class Violation_ClassAssignPropertyMember : IPlugin
    {
        //The instance member used in multiple violation patterns
        internal IOrganizationService Service { get; set; }
        internal IPluginExecutionContext Context { get; set; }
    
        public void Execute(IServiceProvider serviceProvider)
        {
            this.Context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
            var factory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    
            //The violation
            this.Service = factory.CreateOrganizationService(context.UserId);
    
            //Invoke another violation in method member
            AccessViolationProperties();
        }
    
        private void AccessViolationProperties()
        {
            //Accessing the Context and Service properties exposes this IPlugin implementation to thread-safety issues
            var entity = new Entity("task");
            entity["regardingid"] = new EntityReference(this.Context.PrimaryEntityName, this.Context.PrimaryEntityId);
    
            var id = this.Service.Create(entity);
        }
    }
    ```

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Después de Common Data Service cree una instancia de la clase del complemento, la plataforma almacena en memoria caché esa instancia del complemento por razones de rendimiento. La plataforma administra el tiempo en que la instancia del complemento se retiene en memoria caché.  Algunas operaciones, como cambiar las propiedades de registro del complemento, desencadenarán una notificación para la plataforma de actualizar la memoria caché.  En estos escenarios, el complemento se reinicializará.

Puesto que la plataforma almacena en caché instancias de la clase del complemento, no se llama al constructor para cada invocación de ejecución de complemento.  Por este motivo, las implementaciones de IPlugin no deberían depender de la temporización de las operaciones en el constructor aparte de la obtención de datos de configuración estáticos. 

Otra razón por la que IPlugins no debería tener estado es que los múltiples subprocesos del sistema pueden ejecutar la misma estancia compartida de complemento de forma simultánea.  Esto expone a los miembros de clases que implementan IPlugin a problemas potenciales de seguridad de los subprocesos que pueden llevar a incoherencia o problemas de rendimiento.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Escribir un complemento](../../write-plug-in.md)<br />
[Blog del equipo de CRM: Seguridad de los subprocesos en los complementos](https://blogs.msdn.com/b/crm/archive/2008/11/18/member-static-variable-and-thread-safety-in-plug-in-for-crm-4-0.aspx)<br />