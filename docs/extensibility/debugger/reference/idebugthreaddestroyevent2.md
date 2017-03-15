---
title: "IDebugThreadDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThreadDestroyEvent2"
helpviewer_keywords: 
  - "IDebugThreadDestroyEvent2"
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugThreadDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс передается с помощью обработчика отладки \(DE\) к сеансу отладки \(SDM\) диспетчер если поток выполняется до завершения.  
  
## Синтаксис  
  
```  
IDebugThreadDestroyEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализует этот интерфейс для оповещения о том, что поток.   IDebugEvent2 интерфейс должен быть реализован в одном объекте, как этот интерфейс.  SDM использует [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс.  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события для оповещения о том, что поток.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставленные SDM, когда он вложенно для отлаживаемой программы.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugThreadDestroyEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|Возвращает код завершения потока.|  
  
## Заметки  
 Visual Studio использует это событие для обновления **потоки** окна.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)