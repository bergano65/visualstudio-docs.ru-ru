---
title: "IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::FunctionCompiled
Уведомляет профилировщик о том, что объект обработчика сценариев обнаружил функция при компилировании скрипт.  
  
## Синтаксис  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Параметры  
 `functionId`  
 \[in\] уникальный идентификатор функции.  Это идентификатор присвоитьо обработчиком скриптов.  
  
 `scriptId`  
 \[in\] уникальный идентификатор скрипта, что функция является частью.  
  
 `pwszFunctionName`  
 \[in\] имя функции или значение null для анонимной функции.  
  
 `pwszFunctionNameHint`  
 \[in\] выводится имя функции или значение null, если обработчик скриптов вывести имя.  
  
 `pIDebugDocumentContext`  
 \[in\] если возможно\), указатель на интерфейс, `IUnknown`, профилировщик должен запросить для указателя [Интерфейс IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md).  В противном случае — значение NULL.  
  
## Возвращаемое значение  
 Возвращаемое значение этого метода игнорироватьо обработчиком скриптов.  
  
## Заметки  
 Обработчик скриптов может предоставить контекст рисования, только если это поддерживается основным приложением.  
  
## См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)