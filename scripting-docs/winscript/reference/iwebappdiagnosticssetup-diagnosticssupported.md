---
title: "IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::DiagnosticsSupported"
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::DiagnosticsSupported
Устранение неполадок указывает, поддерживаются ли в данном приложении.  Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) вызывается на объекте, реализующий этот интерфейс, отличными от NULL, и значение [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает `true`.  Если нет, то он возвращает `false` и вызовы [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) завершаются с ошибкой.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup — интерфейс](../../winscript/reference/iwebappdiagnosticssetup-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.  
  
## Синтаксис  
  
```cpp  
HRESULT DiagnosticsSupported(  
        [out, retval] VARIANT_BOOL* pRetVal  
        );  
```  
  
#### Параметры  
 `pRetVal`  
 Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) вызывается на объекте, реализующий этот интерфейс, отличными от NULL, и значение [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает `true`.  Если нет, то он возвращает `false` и вызовы [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) завершаются с ошибкой.