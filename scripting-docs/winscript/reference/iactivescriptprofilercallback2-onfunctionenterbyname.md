---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionEnterByName"
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerCallback2::OnFunctionEnterByName
Уведомляет профилировщик о том, что объект обработчика сценариев будет выполнять вызов функции DOM.  
  
## Синтаксис  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### Параметры  
 `pwszFunctionName`  
 \[in\] имя функции обработчика скриптов, которая будет выполняться.  
  
 `scriptType`  
 \[in\] тип функции.  Описание допустимых значений см. в разделе [Перечисление PROFILER\_SCRIPT\_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Возвращаемое значение  
 Возвращаемое значение этого метода игнорироватьо обработчиком скриптов.  
  
## Заметки  
 Для вызовов DOM, обработчик скриптов вызывает этот метод, а не вызывать [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md).  Это должно к наибольшему количеством уникальных методов и свойств в модели DOM.  
  
## См. также  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [Интерфейс IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)