---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1442297fcacb3a9464f9ea67489c91c8ab64ad78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Этот метод совместно создает класс, идентификатор которого передается с помощью `rclsid` с помощью `dwClsContext`. Это аналогично тому, как [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) работает, за исключением того, что в случае `CreateObjectWithSiteAtWebApp` объект создается асинхронно в потоке пользовательского интерфейса веб-приложения. Объект, заданный Идентификатором класса следует реализовать [iwebappdiagnosticsobjectinitialization — интерфейс](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). После создания объекта [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) вызывается со ссылкой на приложение отладки PDM и `hPassToObject` параметр `CreateObjectWithSiteAtWebApp`. Этот метод можно использовать для передачи в приложение дескриптор анонимного канала, скопированный с помощью [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [Iwebappdiagnosticssetup — интерфейс](../../winscript/reference/iwebappdiagnosticssetup-interface.md) — реализованный PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `rclsid`  
 Идентификатор класса для создания класса.  
  
 `dwClsContext`  
 Контекст, в котором будет выполняться код. В большинстве случаев это CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Не используется.  
  
 `hPassToObject`  
 Значение, которое будет передано в объект после его создания в потоке пользовательского интерфейса, если объект реализует [iwebappdiagnosticsobjectinitialization — интерфейс](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).