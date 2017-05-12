---
title: "IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::ScriptCompiled
Уведомляет профилировщик о том, что объект обработчика сценариев компилировал скрипт.  Этот метод вызывается для каждого сценария, компилировать.  
  
## Синтаксис  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Параметры  
 `scriptId`  
 \[in\] уникальный идентификатор скрипта, который был компилировать.  Это идентификатор присвоитьо обработчиком скриптов.  
  
 `type`  
 \[in\] тип скрипта, который был компилировать.  Значения определяются в [Перечисление PROFILER\_SCRIPT\_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 \[in\] если возможно\), указатель на интерфейс, `IUnknown`, профилировщик должен запросить для указателя [Интерфейс IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md).  В противном случае это будет равно null.  
  
## Возвращаемое значение  
 Возвращаемое значение этого метода игнорироватьо обработчиком скриптов.  
  
## Заметки  
 Обработчик скриптов может предоставить контекст рисования, только если это поддерживается основным приложением.  
  
## См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)