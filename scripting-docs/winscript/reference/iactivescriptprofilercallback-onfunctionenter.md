---
title: "IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionEnter
Уведомляет профилировщик о том, что объект обработчика сценариев собирается выполнить вызов функции, не вызова в объектной модели документов \(DOM\).  
  
## Синтаксис  
  
```  
HRESULT OnFunctionEnter(  
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
 Для вызовов DOM, обработчик скриптов вызывает [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) вместо `IActiveScriptProfilerCallback::OnFunctionEnter`.  Это должно к наибольшему количеством уникальных методов и свойств в модели DOM.  
  
## См. также  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)