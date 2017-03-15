---
title: "IEnumDebugBoundBreakpoints2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugBoundBreakpoints2"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2"
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет связанные точки останова, связанные с отложенной точкой останова или событием точки останова связанным.  
  
## Синтаксис  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс в процессе поддержки для точек останова.  Этот интерфейс должен быть реализован, если точки останова поддерживаются.  
  
## Замечания для вызывающих объектов  
 Вызовы Visual Studio:  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) получить этот интерфейс, представляющий список всех точек останова, которые были активированы.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) получить этот интерфейс, представляющий список всех точек останова, которые были привязанны.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) получить этот интерфейс, представляющий список всех точек останова, ожидающих привязанных к данной точке останова.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugBoundBreakpoints2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Извлекает заданное количество связанных точек останова в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Пропустить указанное количество связанных точек останова в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Возвращает количество связанных точек останова в перечислителе.|  
  
## Заметки  
 Visual Studio использует связанные точки останова, представленный этим интерфейсом, чтобы обновить отображение точек останова в интегрированной среде разработки.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)