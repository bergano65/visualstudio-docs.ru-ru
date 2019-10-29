---
title: 'Ивебаппдиагностикссетуп:: Креатеобжектвисситеатвебапп | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984609"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Этот метод совместно создает класс, идентификатор которого передается `rclsid` с помощью `dwClsContext`. Это аналогично тому, как работает [IRemoteDebugApplication:: креатеинстанцеатаппликатион](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) , за исключением того, что в случае `CreateObjectWithSiteAtWebApp` объект создается асинхронно в ПОТОКЕ пользовательского интерфейса веб-приложения. Объект, заданный ИДЕНТИФИКАТОРом класса, должен реализовывать [интерфейс ивебаппдиагностиксобжектинитиализатион](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). После создания объекта метод [ивебаппдиагностиксобжектинитиализатион:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) вызывается со ссылкой на приложение отладки PDM и параметр `hPassToObject` `CreateObjectWithSiteAtWebApp`. Этот метод можно использовать для передачи в приложение обработчика в анонимный канал, скопированный с помощью [дупликатехандле](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle).  
  
> [!IMPORTANT]
> [Интерфейс ивебаппдиагностикссетуп](../../winscript/reference/iwebappdiagnosticssetup-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `rclsid`  
 Идентификатор класса для создания.  
  
 `dwClsContext`  
 Контекст, в котором будет выполняться код. В большинстве случаев это CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Не используется.  
  
 `hPassToObject`  
 Значение, которое будет передано объекту после его создания в потоке пользовательского интерфейса, если объект реализует [интерфейс ивебаппдиагностиксобжектинитиализатион](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).