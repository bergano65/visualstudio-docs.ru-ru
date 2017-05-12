---
title: "IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionExit
Уведомляет объект профилировщика этот обработчик скриптов завершено выполнение вызова функции, не вызова в объектной модели документов \(DOM\).  
  
## Синтаксис  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### Параметры  
 `scriptId`  
 \[in\] уникальный идентификатор скрипта, что функция является частью.  Это идентификатор присвоитьо обработчиком скриптов.  
  
 `functionId`  
 \[in\] уникальный идентификатор функции.  Это идентификатор присвоитьо обработчиком скриптов.  
  
## Возвращаемое значение  
 Возвращаемое значение этого метода игнорироватьо обработчиком скриптов.  
  
## Заметки  
 Для вызовов DOM, обработчик скриптов вызывает [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) вместо `IActiveScriptProfilerCallback::OnFunctionExit`.  Это должно к наибольшему количеством уникальных методов и свойств в модели DOM.  
  
## См. также  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)