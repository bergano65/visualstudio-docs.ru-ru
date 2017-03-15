---
title: "IDebugProcessDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProcessDestroyEvent2"
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProcessDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс при отправке процесс завершен нетипово или наконец, будет удален из кластера.  
  
## Синтаксис  
  
```  
IDebugProcessDestroyEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) или пользовательского поставщика порта реализовать этот интерфейс, чтобы информировать, что процесс завершен.   IDebugEvent2 интерфейс должен быть реализован в одном объекте, как этот интерфейс.  SDM использует [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс.  
  
## Замечания для вызывающих объектов  
 DE или пользовательского поставщика порта создают и выполняют этот объект события для оповещения завершение процесса.  Отправляет данное событие с помощью DE IDebugEventCallback2 функция обратного вызова, предоставленные SDM, когда он вложенно для отлаживаемой программы.  Пользовательский поставщик отправляет данное событие использование порта [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) интерфейс.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)