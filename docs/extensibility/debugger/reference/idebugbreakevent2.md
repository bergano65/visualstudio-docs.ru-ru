---
title: "IDebugBreakEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakEvent2"
helpviewer_keywords: 
  - "Интерфейс IDebugBreakEvent2"
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс определяет сеанс отладки \(SDM\), диспетчер асинхронных перерыву успешно завершено.  
  
## Синтаксис  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, чтобы поддерживать время ожидания пользователя в программе.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован в одном объекте, как этот интерфейс \(SDM использует  [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс\).  
  
## Замечания для вызывающих объектов  
 Вызовы SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) когда пользователь запросил отлаживаемой программы для приостановки.  Когда программа отправляет успешно приостановлен, DE `IDebugBreakEvent2` событие.  Это событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставляемая SDM, когда он вложен в отлаживаемом программе.  
  
## Заметки  
 Например, пользователь может выбирать **Прервать все** команда на  **Отладка** меню, который необходимо переключиться из программы, которая запускает бесконечный цикл.  SDM указывает, что программа останавливает путем вызова [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md).  DE отправляет `IDebugBreakEvent2` наконец, когда программа останавливается.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)