---
title: "IDebugPendingBreakpoint2 | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2"
helpviewer_keywords: 
  - "Интерфейс IDebugPendingBreakpoint2"
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет собой точку останова, готовы привязать к местоположению кода.  
  
## Синтаксис  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс в процессе поддержки для точек останова.  
  
## Замечания для вызывающих объектов  
 Вызов [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) создает ожидается точка останова из  [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) интерфейс.  Вызов [Привязка](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создание  `IDebugBreakpoint2` интерфейс, представляющий связанную точку останова в программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugPendingBreakpoint2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, является ли данная ожидается точка останова может привязать к местоположению кода.|  
|[Привязка](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Эта привязка ожидается точка останова с одним или несколькими места кода.|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|Получает состояние ожидающих этой точки останова.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Возвращает запрос точки останова, который использовался для создания данной ожидается точка останова.|  
|[Виртуализация](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Переключает состояние ожидающих virtualized этой точки останова.|  
|[Включить](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает включенное состояние ожидающих этой точки останова.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Задает или изменения условие, связанное с данной, ожидающих точкой останова.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Задает или изменения количество ожидающих передачи, связанного с данной точкой останова.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки останова из ожидающих привязанные этой точки останова.|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|Перечисляет все точки останова, которые привели к этой ошибки из ожидающих точки останова.|  
|[Удаление](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Ожидается удаление эта точка останова и все точки останова привязанные из нее.|  
  
## Заметки  
 `IDebugPendingBreakpoint2` можно рассматривать в качестве поставщика всего необходимые сведения, необходимого для привязки точки останова в коде, можно применять одно или несколько программ.  
  
 Ожидается точка останова потенциально может создавать несколько связанную точку останова.  Например, точка останова в шаблоне c \+\+\-style может создавать связанную точку останова для каждого уникального экземпляра этого шаблона.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)