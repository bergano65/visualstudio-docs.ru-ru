---
title: "IActiveScriptProfilerCallback::Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback::Shutdown
Вызываемый для оповещения профилировщика, когда объект профилирования остановки в обработчике скриптов.  В этом случае объект профилировщика может вызвать его процедуры очистки, если это необходимо.  Этот метод также вызывается обработчиком скриптов, когда обработчик скриптов завершает работу или в случаях, когда вызов [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) завершится ошибкой.  
  
## Синтаксис  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### Параметры  
 `hrReason`  
 \[in\] причина завершения работы.  Если обработчик скриптов завершает работу, `S_ОК` передаются.  Если вызов [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) возвращает сбой HRESULT, то значение HRESULT передаются.  В противном случае это значение восстановитьо из [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## Возвращаемое значение  
 Возвращаемое значение этого метода игнорироватьо обработчиком скриптов.  
  
## См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)