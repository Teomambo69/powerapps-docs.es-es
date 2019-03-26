---
title: Utilizar InvalidPluginExecutionException en actividades de complementos y de flujo de trabajo | MicrosoftDocs
description: Use InvalidPluginExecutionException al publicar errores en el contexto de las actividades de complemento o de flujo de trabajo.
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
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-invalidpluginexecutionexception-in-plug-ins-and-workflow-activities"></a>Utilizar InvalidPluginExecutionException en actividades de complementos y de flujo de trabajo

**Categoría**: mantenimiento, uso

**Potencial de impacto**: medio

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Si un complementos sincrónico devuelve a la plataforma una excepción que no sea <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>, el cuadro de diálogo de error se muestra al usuario con el mensaje de excepción <xref:System.Exception.Message> y el seguimiento de la pila. Esto proporciona una experiencia hostil de usuario ya que es probable que ya sea una situación de frustración.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Se recomienda que los complementos devuelven solo <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> a la plataforma por las siguientes razones:

- Aparece un mensaje descriptivo para el usuario
- Se evita que aumente el archivo de seguimiento/registro de eventos

Las excepciones no controladas de otros tipos deben producirse solo cuando los errores inesperados se encuentran en tiempo de ejecución. Los siguientes son ejemplos de métodos válidos.

- Generar InvalidPluginExecutionException sin vigilar

    ```csharp
    public void Execute(IServiceProvider serviceProvider)
    {
        // Invocation of a valid scenario that throws an appropriate exception type
        ThrowPluginException();
    }
    
    private void ThrowPluginException()
    {
        throw new InvalidPluginExecutionException("Throwing a plug-in exception in a member method body");
    }
    ```

- Las excepciones sin vigilar administradas o generadas como una nueva InvalidPluginExecutionException

    ```csharp
    public void Execute(IServiceProvider serviceProvider)
    {
        try
        {
            ThrowGuardedMemberException();
        }
        catch (CustomException ex)
        {
            throw new InvalidPluginExecutionException("Unable to save the contact. This is likely caused by..."), ex);
        }
    
        // Invocation of a valid scenario in a member method
        HandleMemberException();
    }
    
    private void HandleMemberException()
    {
        try
        {
            // Invocation of a scenario where CustomException is thrown
            ThrowGuardedMemberException();
        }
        catch (CustomException ex)
        {
            // Handle the exception.
            // Note - Debug.WriteLine is likely not the appropriate way to handle the exception. This is for demonstration purposes only
            Debug.WriteLine(ex.Message);
        }
    }
    
    private void ThrowGuardedMemberException()
    {
        throw new CustomException("Throwing a custom exception in a guarded member");
    }
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

> [!WARNING]
> Estos patrones deben evitarse.

- Generación de excepciones sin vigilar

    ```csharp
    public void Execute(IServiceProvider serviceProvider)
    {
        // Invocation of a scenario where violation occurs during an unguarded throw
        UnguardedMemberThrowException();
    }
    
    private void UnguardedMemberThrowException()
    {
        throw new CustomException("Throwing an unguarded custom exception in a member method body");
    }
    ```

- Excepción vigilada que se vuelve a generar sin vigilancia

    ```csharp
    public void Execute(IServiceProvider serviceProvider)
    {
        // Invocation of a scenario where violation occurs during an unguarded rethrow
        UnguardedMemberRethrowException();
    }
    
    private void UnguardedMemberRethrowException()
    {
        try
        {
            // Guarded invoking of a method member that throws a custom exception
            GuardedMemberThrowException();
        }
        catch (CustomException ex)
        {
            // Handle and rethrow
            Debug.WriteLine(ex.Message);
    
            // This is where the issue occurs
            throw;
        }
    }
    
    private void GuardedMemberThrowException()
    {
        throw new CustomException("Throwing a guarded custom exception in a member method body");
    }
    ```

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Cancelación de una operación](../../handle-exceptions.md#cancelling-an-operation)<br/>
[Depurar actividades de flujo de trabajo personalizadas](../../workflow/workflow-extensions.md#debug-workflow-activities)<br/>