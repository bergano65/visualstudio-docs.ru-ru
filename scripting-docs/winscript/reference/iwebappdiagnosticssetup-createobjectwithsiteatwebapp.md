---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Документация Майкрософт
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
ms.openlocfilehash: 42f92cfe9245a5e3a6342c31fc996ae2db50ef70
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443696"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Этот метод создает совместно, идентификатор которого передается с помощью класса `rclsid` с помощью `dwClsContext`. Это аналогично тому, как [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) works, за исключением случаев, в случае использования `CreateObjectWithSiteAtWebApp` объект создается асинхронно в потоке пользовательского интерфейса веб-приложения. Объект, указанный с помощью идентификатора класса следует реализовать [iwebappdiagnosticsobjectinitialization — интерфейс](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). После создания объекта [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) вызывается со ссылкой на приложения отладки PDM и `hPassToObject` параметр `CreateObjectWithSiteAtWebApp`. Этот метод можно использовать для передачи в приложение дескриптора для анонимного канала, который вы скопировали с помощью [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
> [Интерфейс IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) является реализуется PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
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
 Значение, которое будет передан объект после его создания в потоке пользовательского интерфейса, если объект реализует [iwebappdiagnosticsobjectinitialization — интерфейс](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).