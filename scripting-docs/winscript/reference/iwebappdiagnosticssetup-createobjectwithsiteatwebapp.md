---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp"
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Этот метод co\- создает класс, идентификатор которого передан с `rclsid` с помощью `dwClsContext`.  Это аналогично переходу [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) работает, за исключением того, что в случае `CreateObjectWithSiteAtWebApp` объект создать асинхронно в потоке пользовательского интерфейса веб\-приложения.  Объект, определенный идентификатор класса, должен реализовывать [IWebAppDiagnosticsObjectInitialization — интерфейс](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).  После того как объект был создания, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) Позвонитьо со ссылкой на PDM отладку приложения и параметр `hPassToObject``CreateObjectWithSiteAtWebApp`.  Этот метод можно использовать для передачи приложению дескриптор анонимного канала, который был скопирован с помощью [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup — интерфейс](../../winscript/reference/iwebappdiagnosticssetup-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(  
        [in] REFCLSID rclsid,   
        [in] DWORD dwClsContext,   
        [in] REFIID riid,   
        [in] DWORD_PTR hPassToObject  
        );  
  
```  
  
#### Параметры  
 `rclsid`  
 Идентификатор класса, который требуется создать.  
  
 `dwClsContext`  
 Контекст, в котором выполняется код.  В большинстве случаев это CLSCTX\_INPROC\_SERVER.  
  
 `riid`  
 Не используется.  
  
 `hPassToObject`  
 Значение, которое будет передано объекту раз, когда он создатьо в потоке пользовательского интерфейса, если объект реализует [IWebAppDiagnosticsObjectInitialization — интерфейс](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).