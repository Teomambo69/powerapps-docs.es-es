---
title: getSaveMode (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 03e970ee-7ed3-4df2-9670-222d76a479fd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getsavemode-client-api-reference"></a>getSaveMode (referencia de la API de cliente)



[!INCLUDE[./includes/getSaveMode-description.md](./includes/getSaveMode-description.md)]

## <a name="syntax"></a>Sintaxis

`executionContext.getEventArgs().getSaveMode()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: la siguiente tabla describe los valores compatibles devueltos para detectar las distintas formas en que el usuario puede guardar los registros de entidad.

|Value |Modo Guardar |Entity|
|---|---|---|
|1|Guardar|Todas|
|2|Guardar y cerrar|Todas|
|5|Desactivar|Todas|
|6|Reactivar|Todas|
|7|Enviar|Enviar por correo electrónico|
|15|Descalificar|Cliente potencial|
|16|Calificar|Cliente potencial|
|47|Asignar|Entidades propiedad del usuario o el equipo|
|58|Guardar como completado|Actividades|
|59|Guardar y nuevo|Todas|
|70|Autoguardado|Todas|

## <a name="remarks"></a>Comentarios

Este método es esencial si desea habilitar el autoguardado para la mayoría de los formularios en una organización pero deshabilitarlo para formularios específicos.  

## <a name="example"></a>Ejemplo

El siguiente código registrado para el evento **OnSave** con el contexto de ejecución que se le ha pasado evitará las operaciones de guardar que se inicien en un autoguardado, pero permitirá todas las demás. Con el autoguardado habilitado, salir del explorador es equivalente a **Guardar y cerrar**. Este código evitará las operaciones de guardado que inicia el temporizador de 30 segundos o cuando el usuario navega fuera de un formulario con datos sin guardar.

```JavaScript
function preventAutoSave(executionContext) {
    var eventArgs = executionContext.getEventArgs();
    if (eventArgs.getSaveMode() == 70 || eventArgs.getSaveMode() == 2) {
        eventArgs.preventDefault();
    }
}
```

Para guardar un registro, el usuario debe hacer clic en el icono **Guardar** en la parte inferior del formulario o es necesario agregar un comando **Guardar** personalizado a la barra de comandos.

### <a name="related-topics"></a>Temas relacionados

[isDefaultPrevented](isDefaultPrevented.md)

[preventDefault](preventDefault.md)

