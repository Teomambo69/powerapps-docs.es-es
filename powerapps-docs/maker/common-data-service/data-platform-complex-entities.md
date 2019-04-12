---
title: Entidades complejas que requieren licencias de Plan 2 de PowerApps | Microsoft Docs
description: Una lista de entidades complejas en Common Data Service que requieren una licencia de Plan 2 de PowerApps.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 07/17/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="complex-entities-and-licensing"></a>Entidades y licencias complejas
Las entidades que incluyen la siguiente lógica compleja de servidor requieren que los usuarios de una aplicación o flujo en el que se usen estas entidades tengan una licencia de Plan 2 de PowerApps o de Plan 2 de Microsoft Flow:

* Complementos de código. Más información: [Desarrollo de complementos](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development)
* Flujos de trabajo en tiempo real. Más información: [Procesos de flujo de trabajo](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)

    > [!IMPORTANT]
    >  Solo los flujos de trabajo que se convierten a un flujo de trabajo en tiempo real se consideran en tiempo real y sincrónicos. Los flujos de trabajo que se ejecutan en segundo plano pueden usarse con el plan adecuado de PowerApps y no requieren licencias adicionales.

Para saber si ha agregado lógica de negocios compleja a las entidades, revise la lista de ensamblados de complementos y de flujos de trabajo configurados en el entorno.

## <a name="complex-entities-installed-with-dynamics-365"></a>Entidades complejas instaladas con Dynamics 365
En la tabla siguiente se muestran las entidades que contienen lógica compleja de servidor lista para usar como parte de la instalación de una aplicación de Dynamics 365. Esta lista está diseñada como referencia. Según las aplicaciones y versiones de Dynamics 365 en las que estén instaladas en su entorno, la lista de entidades complejas puede variar.

> [!NOTE]
>  Si está usando Common Data Service y no ha instalado una aplicación o una solución de terceros de Dynamics 365, el entorno no tendrá entidades que contengan lógica compleja de servidor.

* Cuenta
* Acuerdo
* Fecha de reserva del acuerdo
* Incidente de reserva del acuerdo
* Producto de reserva del acuerdo
* Servicio de reserva del acuerdo
* Tarea de servicio de reserva del acuerdo
* Configuración de reserva del acuerdo
* Fecha de factura del acuerdo
* Producto de la factura del acuerdo
* Configuración de factura del acuerdo
* Subestado del acuerdo
* Recurso que se puede reservar
* Reserva de recursos que se pueden reservar
* Encabezado de reserva de recursos que se pueden reservar
* Categoría de recurso que se puede reservar
* Asociación de categoría de recurso que se puede reservar
* Característica del recurso que se puede reservar
* Grupo de recursos que se pueden reservar
* Alerta de reserva
* Estado de alerta de reserva
* Estado de reserva
* Característica
* Requisito de competencia (Obsoleto)
* Competidor
* Contacto
* Activo del cliente
* Delegación
* Gasto
* Cálculo de campo
* Elemento de lista de precios de Field Service
* Filtro
* Seguir
* Tipo de incidente
* Producto de tipo de incidente
* Servicio de tipo de incidente
* Tarea de servicio de tipo de incidente
* Trabajo de integración
* Detalle del trabajo de integración
* Ajuste de inventario
* Producto de ajuste de inventario
* Transferencia de inventario
* Factura
* Frecuencia de factura
* Línea de factura
* Detalle de línea de factura
* Diario
* Línea del diario
* Cliente potencial
* Nota
* Origen de datos de OData v4
* Oportunidad
* Línea de oportunidad
* Detalle de línea de oportunidad
* Pedido
* Producto de facturación de pedidos
* Configuración de facturación de pedidos
* Línea de pedido
* Pago
* Detalle de pago
* Configuración de publicación
* Configuración de regla de publicación
* Código postal
* Lista de precios
* Elemento de lista de precios
* Producto
* Proyecto
* Aprobación de proyecto
* Detalle de línea de contrato de proyecto
* Hito de línea de contrato de proyecto
* Categoría de recursos de línea de contrato de proyecto
* Categoría de transacciones de línea de contrato de proyecto
* Parámetro de proyecto
* Fases del proyecto
* Usuario de estado de tareas de proyecto
* Inscripción como miembro del equipo del proyecto
* Pedido de compra
* Factura de pedido de compra
* Producto de pedido de compra
* Recibo de pedido de compra
* Producto de recibo de pedido de compra
* Subestado del pedido de compra
* Elemento de cola
* Oferta
* Incidente de reserva de la oferta
* Producto de reserva de la oferta
* Servicio de reserva de la oferta
* Tarea de servicio de reserva de la oferta
* Configuración de reservas de oferta
* Producto de facturación de la oferta
* Configuración de facturación de la oferta
* Línea de oferta
* Detalle de línea de oferta
* Hito de línea de oferta
* Categoría de recursos de línea de oferta
* Categoría de transacciones de línea de oferta
* Lista de precios de proyecto de oferta
* Modelo de clasificación
* Valor de la clasificación
* Característica de requisito
* Categoría de recursos de requisito
* Preferencia de recursos de requisito
* Estado de requisito
* Solicitud de recursos
* Requisito de recursos
* Detalle de requisitos de recursos
* RMA
* Producto de RMA
* Recibo de RMA
* Producto de recibo de RMA
* Subestado de RMA
* Requisito de competencia de rol
* Precio de rol
* RTV
* Producto de RTV
* Subestado de RTV
* Código impositivo
* Detalle de código impositivo
* Entrada de tiempo
* Grupo de horarios
* Detalle de grupo de horarios
* Solicitud de indisponibilidad
* Precio de categoría de transacciones
* Usuario
* Vista
* Vista de muro
* Almacén
* Orden de trabajo
* Incidente de orden de trabajo
* Producto de orden de trabajo
* Servicio de orden de trabajo
* Tarea de servicio de orden de trabajo
* Subestado de la orden de trabajo
* Plantilla de trabajo


## <a name="licensing"></a>Licencias
Para obtener más información acerca de las licencias de PowerApps y Dynamics 365, consulte la página [Información general de las licencias](../../administrator/pricing-billing-skus.md).

