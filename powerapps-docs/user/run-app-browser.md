---
title: 在網頁瀏覽器中執行應用程式 | Microsoft Docs
description: 在本主題中，您將了解如何在網頁瀏覽器中執行應用程式
author: mduelae
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 12/05/2019
ms.author: mkaur
manager: kvivek
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8ce6cfe213817cd603857bb5ea2735b188f8cb6c
ms.sourcegitcommit: 15c6b26ff085928459ad9b3f52fb607fae4a997d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74956793"
---
# <a name="run-an-app-in-a-web-browser"></a>在網頁瀏覽器中執行應用程式
Cuando se crea una aplicación o alguien comparte una aplicación con usted, puede ejecutarla en la aplicación móvil Dynamics 365 o en un explorador Web en una tableta. En este tema, aprenderá a ejecutar una aplicación de lienzo o controlada por modelos en un explorador Web en una tableta desde la [Página principal de Dynamics 365](https://home.dynamics.com).

Para obtener una funcionalidad completa y una experiencia optimizada, recomendamos encarecidamente que use la aplicación móvil Dynamics 365 para teléfonos y tabletas. Si no tiene la aplicación Dynamics 365 para teléfonos y tabletas instalada, todavía puede usar el explorador Web en la tableta, siempre que el dispositivo tenga una resolución de pantalla suficientemente alta. Para obtener más información: [lo que se admite](https://docs.microsoft.com/dynamics365/mobile-app/support-phones-tablets#supported-devices-for-the-mobile-app).

> [!NOTE]
> No se admite el uso del explorador Web en el teléfono para ejecutar aplicaciones controladas por modelos; debe usar la aplicación Dynamics 365 para teléfonos.

若要遵循本快速入門，您需要：
- Una licencia de Power apps. Esto está disponible con un plan de Power Apps, como la [evaluación de Power apps plan 2](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps), o cualquiera de los planes [Microsoft Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) o [Dynamics 365](https://dynamics.microsoft.com/pricing/) que incluyen Power apps. 
- 存取您建置的應用程式，或是其他人建置並與您共用的應用程式。
- 存取支援的網頁瀏覽器和作業系統。
   - 針對畫布應用程式，請參閱[系統需求、限制和設定值](../maker/canvas-apps/limits-and-config.md)
   - 針對模型驅動應用程式，請參閱[支援的網頁瀏覽器和行動裝置](https://docs.microsoft.com/dynamics365/customer-engagement/admin/supported-web-browsers-and-mobile-devices)


## <a name="sign-in-to-dynamics-365"></a>登入 Dynamics 365
登入 Dynamics 365 (網址為 [https://home.dynamics.com](https://home.dynamics.com))。

## <a name="find-an-app-on-the-home-page"></a>在首頁上尋找應用程式
首頁可能會顯示數種類型的商務應用程式，但您可以在搜尋方塊中輸入部分名稱來尋找特定的應用程式。 También puede filtrar la lista para mostrar solo las aplicaciones creadas por un origen específico, como Power apps. Para ello, seleccione **filtrar** y, a continuación, seleccione el origen.

如果您最近剛安裝應用程式，可能不會立即出現在應用程式清單中。 Seleccione **sincronizar** para mostrar todas las aplicaciones. 此程序可能需要最多 1 分鐘的時間。

![](./media/run-app-browser/dynamics-365-home.png)


## <a name="run-an-app-from-a-url"></a>從 URL 執行應用程式
Puede guardar la dirección URL de una aplicación como un marcador en el explorador de la tableta y ejecutarla seleccionando el marcador, o bien puede enviar una dirección URL como un vínculo por correo electrónico. Si otro usuario creó una aplicación y la compartió con usted en un correo electrónico, puede ejecutar la aplicación seleccionando el vínculo en el correo electrónico. 使用 URL 執行應用程式時，系統可能會提示您使用 Azure Active Directory 認證登入。

![](./media/run-app-browser/web-login.png)

## <a name="connect-to-data"></a>連接到資料
如果應用程式必須連接至資料來源，或是需要權限才能使用裝置的功能 (例如相機或位置服務)，則必須經過您的同意，您才能使用應用程式。 一般而言，系統只會在首次使用時提示您。

![Connection](./media/run-app-browser/app-connection.png)

## <a name="close-an-app"></a>關閉應用程式
若要關閉應用程式，請登出 Dynamics 365 首頁，或開啟另一個應用程式。

## <a name="next-steps"></a>後續步驟
在本主題中，您已了解如何在網頁瀏覽器中執行畫布或模型驅動應用程式。 Para obtener información sobre cómo:
- ejecutar una aplicación de lienzo en un dispositivo móvil, consulte [ejecutar una aplicación de lienzo en un dispositivo móvil](run-app-client.md)
- ejecutar una aplicación controlada por modelos en un dispositivo móvil, consulte [ejecutar una aplicación controlada por modelos en un dispositivo móvil](run-app-client-model-driven.md)
- usar una aplicación controlada por modelos, consulte [uso de aplicaciones controladas por](use-model-driven-apps.md) modelos

