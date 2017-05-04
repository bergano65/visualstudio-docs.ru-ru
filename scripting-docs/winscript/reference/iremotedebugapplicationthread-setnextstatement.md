---
title: "IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::SetNextStatement"
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::SetNextStatement
Вызывает принудительное выполнение, чтобы продолжить, как можно ближе к заданному контексту кода в контексте данного фрейма.  
  
## Синтаксис  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### Параметры  
 `pStackFrame`  
 \[in\] объект кадра стека.  Этот аргумент может принимать значение null, подразумевается текущий кадр стека следует использовать.  
  
 `pCodeContext`  
 \[in\] контекст кода.  Этот аргумент может принимать значение null, подразумевается текущий контекст кода должен использоваться.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод вызывает принудительное выполнение, чтобы продолжить, как можно ближе к контексту кода указанному `pCodeContext` в контексте заданного `pStackFrame` кадра.  Один из этих аргументов может быть `NULL`, представляющая текущий кадр или контекста.  
  
## См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)