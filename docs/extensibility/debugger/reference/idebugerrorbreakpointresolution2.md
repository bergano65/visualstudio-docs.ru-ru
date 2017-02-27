---
title: "IDebugErrorBreakpointResolution2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorBreakpointResolution2"
helpviewer_keywords: 
  - "IDebugErrorBreakpointResolution2"
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugErrorBreakpointResolution2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет разрешение ошибок точки останова.  
  
## Синтаксис  
  
```  
IDebugErrorBreakpointResolution2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик реализует этот интерфейс в процессе поддержки для точек останова.  Этот интерфейс используется, чтобы информировать где точка останова не удалось выполнить привязку.  
  
## Замечания для вызывающих объектов  
 Вызов [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) возвращает этот интерфейс, чтобы предоставить сведения о том, где точка останова не удалось выполнить привязку.  [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) метод возвращает  [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugErrorBreakpointResolution2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Возвращает тип точки останова.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешениях точки останова.|  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)