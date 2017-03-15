---
title: "EVENTATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENTATTRIBUTES"
helpviewer_keywords: 
  - "Перечисления EVENTATTRIBUTES"
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет атрибуты события.  
  
## Синтаксис  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## Члены  
 EVENT\_ASYNCHRONOUS  
 Указывает, что событие асинхронно и ответ на событие.  
  
 EVENT\_SYNCHRONOUS  
 Указывает, что события синхронно. ответ посредством [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md).  
  
 EVENT\_STOPPING  
 Это событие указывает на то, что остановки.  Быть совмещено с этим `EVENT_ASYNCHRONOUS` OR  `EVENT_SYNCHRONOUS`.  
  
 EVENT\_ASYNC\_STOP  
 Указывает асинхронное при остановке событие.  В данный момент такое событие.  Этот пометить только заполнителем.  
  
 EVENT\_SYNC\_STOP  
 Указывает событие \(сочетание выполняются при остановке `EVENT_SYNCHRONOUS` и  `EVENT_STOPPING`\).  Это значение используется обработчиком отладки \(DE\), когда оно отправляет при остановке событие.  Ответ выполняется посредством вызова [Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md)"  [Шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md)или  [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT\_IMMEDIATE  
 Указывает событие, отправляются немедленно и одновременно в интегрированной среде разработки.  Этот пометить объединяется с другими флагами как `EVENT_ASYNCHRONOUS`"  `EVENT_SYNCHRONOUS`или  `EVENT_SYNC_STOP` указывает тип события и fact этого механизм ответа \(если есть\), то известно, что.  
  
 EVENT\_EXPRESSION\_EVALUATION  
 Событие результат оценки выражений.  
  
## Заметки  
 Эти значения передаются в `dwAttrib` параметр   [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) метод.  
  
 Эти значения могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)