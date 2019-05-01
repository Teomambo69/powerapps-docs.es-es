---
ms.openlocfilehash: 252f09737dbf55309a64ef5d02d479fde0e61c0e
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61585227"
---
Al habilitar Interacción por correo electrónico, una característica de Inteligencia integrada, cuando un correo electrónico marcado con la configuración **Follow** (Seguir) se envía desde [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], la información sobre las interacciones de los destinatarios con el correo electrónico se recopilará y almacenará en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] con el fin de calcular los KPI de actividad de destinatario y la interacciones en los correos electrónicos "seguidos".  
  
 Un administrador del sistema habilita Interacción por correo electrónico al aprovisionar la característica desde la pestaña **Interacción por correo electrónico** dentro de Inteligencia integrada. Posteriormente, los administradores pueden deshabilitar Interacción por correo electrónico en la organización desde el nodo **Configuración de inteligencia** en **Configuración**.  
  
 Cuando se deshabilita la característica, los correos electrónicos enviados desde [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] no se podrán seguir, ya sea desde la interfaz de usuario o mediante programación. Además, ya no se recopilarán los datos de interacción de los destinatarios en los correos electrónicos que estaban marcados con la configuración **Follow** (Seguir). Todos los datos recopilados anteriormente permanecerán en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y volverán a estar disponibles si la característica se habilita nuevamente en la organización. Los datos se conservan durante 90 días después de que los clientes terminan la suscripción con Microsoft. Los usuarios de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] también pueden deshabilitar la funcionalidad Interacción por correo electrónico de Inteligencia integrada, ya sea por contacto o por cliente potencial, si cambian la configuración **Follow Email** (Seguir correo electrónico) en **Preferencias de contacto**.  
  
 En las siguientes secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] que participan en la funcionalidad Interacción de correo electrónico.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]**  
  
 La característica Interacción por correo electrónico usa [!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)] para almacenar temporalmente los blobs de interacción por correo electrónico.