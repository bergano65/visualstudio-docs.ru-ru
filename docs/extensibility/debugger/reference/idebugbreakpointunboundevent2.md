---
title: "IDebugBreakpointUnboundEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointUnboundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2"
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointUnboundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс определяет сеанс отладки \(SDM\), диспетчер связанной точке останова из несвязанных загружаемой программы.  
  
## Синтаксис  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс в процессе поддержки для точек останова.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован в одном объекте, как этот интерфейс \(SDM использует  [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс\).  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события, когда связанная точка останова была отменена привязка.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставляемая SDM, когда он вложен в отлаживаемом программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugBreakpointUnboundEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Получает точку останова, которая стала доступной несвязанный.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Возвращает причину точка останова была отменена привязка.|  
  
## Заметки  
 Если библиотека DLL или класс обработчика отладки выгрузить все точки останова, которые были привязанны к коду в этом модуле должен быть отменена привязка от отлаживанными программы.  `IDebugBreakpointUnboundEvent2` отправляет для каждой непривязанные точки останова.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)