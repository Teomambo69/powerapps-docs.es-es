---
title: Entidades complejas que requieren licencias del plan 2 de PowerApps | Microsoft Docs
description: Lista de entidades complejas de Common Data Service (CDS) for Apps que requieren una licencia del plan 2 de PowerApps.
author: clwesene
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 07/17/2018
ms.author: clwesene
ms.openlocfilehash: 76c101f35e236ac6bf037d2b5b748ca1b943d61d
ms.sourcegitcommit: efea7ed5ad8e80c87ba423fb094fa94b4e864d75
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39266278"
---
# <a name="complex-entities-and-licensing"></a>Entidades complejas y licencias
Las entidades que incluyen la siguiente lógica compleja del lado servidor requieren que los usuarios de una aplicación o flujo en el que se usen estas entidades tengan una licencia del Plan 2 de PowerApps o del Plan 2 de Microsoft Flow:

* Complementos de código. Más información: [Desarrollo de complementos](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development))
* Flujos de trabajo en tiempo real. Más información: [Procesos de flujo de trabajo](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes))

    > [!IMPORTANT]
    >  Solo los flujos de trabajo que se convierten en un flujo de trabajo en tiempo real se consideran de tiempo real y sincrónicos. Los flujos de trabajo que se ejecutan en segundo plano se pueden seguir usando con el plan de PowerApps adecuado y no requieren licencias adicionales.

Para saber si ha agregado o no lógica de negocios compleja a las entidades, revise la lista de ensamblados de complementos y flujos de trabajo configurados en el entorno.

## <a name="complex-entities-installed-with-dynamics-365"></a>Entidades complejas instaladas con Dynamics 365
En la tabla que hay a continuación se enumeran las entidades que contienen una lógica compleja estándar del lado servidor como parte de la instalación de una aplicación de Dynamics 365. Esta lista está pensada para utilizarse como guía. La lista de entidades complejas puede variar en función de las aplicaciones y versiones de Dynamics 365 que estén instaladas en su entorno.

> [!NOTE]
>  Si usa Common Data Service y no ha instalado ninguna aplicación de Dynamics 365 o solución de terceros, su entorno no tendrá ninguna entidad que contenga una lógica compleja del lado servidor.

* Cuenta
* Acuerdo
* Fecha de reserva del acuerdo
* Incidente de reserva del acuerdo
* Producto de reserva del acuerdo
* Servicio de reserva del acuerdo
* Tarea de servicio de reserva del acuerdo
* Configuración de reserva del acuerdo
* Fecha de factura del acuerdo
* Producto de factura del acuerdo
* Configuración de factura del acuerdo
* Subestado del acuerdo
* Recurso reservable
* Reserva del recurso reservable
* Encabezado de reserva del recurso reservable
* Categoría del recurso reservable
* Asociación de categoría del recurso reservable
* Característica del recurso reservable
* Grupo de recursos reservables
* Alerta de reserva
* Estado de la alerta de reserva
* Estado de reserva
* Case
* Característica
* Requisito de competencia (en desuso)
* Competidor
* Contacto
* Recurso de cliente
* Delegación
* Gasto
* Cálculo de campos
* Elemento de lista de precios de servicio de campo
* Filtro
* Seguir
* Tipo de incidente
* Producto del tipo de incidente
* Servicio del tipo de incidente
* Tarea de servicio del tipo de incidente
* Trabajo de integración
* Detalles del trabajo de integración
* Ajuste de inventario
* Producto del ajuste de inventario
* Transferencia de inventario
* Factura
* Frecuencia de la factura
* Línea de factura
* Detalles de la línea de factura
* Diario
* Línea de diario
* Lead
* Nota
* Origen de datos de OData v4
* Opportunity
* Línea de oportunidad
* Detalles de la línea de oportunidad
* Pedido
* Producto de facturación del pedido
* Configuración del producto de facturación del pedido
* Línea de pedido
* Pago
* Detalles del pago
* Configuración de publicación
* Configuración de reglas de publicación
* Código postal
* Lista de precios
* Elemento de lista de precios
* Product
* Proyecto
* Aprobación del proyecto
* Detalles de la línea de contrato de proyecto
* Hito de la línea de contrato de proyecto
* Categoría de recurso de la línea de contrato de proyecto
* Categoría de transacción de la línea de contrato de proyecto
* Parámetro de proyecto
* Fases del proyecto
* Usuario del estado de la tarea de proyecto
* Registro de miembro del equipo de proyecto
* Purchase Order
* Factura del pedido de compra
* Producto del pedido de compra
* Recibo del pedido de compra
* Producto de recibo del pedido de compra
* Subestado del pedido de compra
* Elemento de cola
* Oferta
* Incidente de reserva de la oferta
* Producto de reserva de la oferta
* Servicio de reserva de la oferta
* Tarea de servicio de la reserva de la oferta
* Configuración de reserva de la oferta
* Producto de facturación de la oferta
* Configuración de facturación de la oferta
* Línea de oferta
* Detalles de la línea de oferta
* Hito de la línea de oferta
* Categoría de recurso de la línea de oferta
* Categoría de transacción de la línea de oferta
* Lista de precios del proyecto de oferta
* Modelo de clasificación
* Valor de clasificación
* Característica de requisito
* Categoría de recurso de requisito
* Preferencia de recurso de requisito
* Estado de requisito
* Solicitud de recurso
* Requisito de recurso
* Detalles del requisito de recurso
* RMA
* Producto de RMA
* Recibo de RMA
* Producto del recibo de RMA
* Subestado de RMA
* Requisito de competencia de rol
* Precio de rol
* RTV
* Producto de RTV
* Subestado de RTV
* Código impositivo
* Detalles del código impositivo
* Horas trabajadas
* Grupo de horarios
* Detalles del grupo de horarios
* Solicitud de permiso
* Precio de la categoría de transacción
* Usuario
* Ver
* Vista de centro comercial
* Almacén
* Orden de trabajo
* Incidente de orden de trabajo
* Producto de orden de trabajo
* Servicio de orden de trabajo
* Tarea de servicio de orden de trabajo
* Subestado de orden de trabajo
* Plantilla de trabajo


## <a name="licensing"></a>Licencias
Para obtener más información sobre las licencias de PowerApps y Dynamics 365, vea la página [Introducción a las licencias](../../administrator/pricing-billing-skus.md).

