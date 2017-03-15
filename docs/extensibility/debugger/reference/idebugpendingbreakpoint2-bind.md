---
title: "IDebugPendingBreakpoint2::Bind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Bind"
helpviewer_keywords: 
  - "Bind - метод"
  - "Метод IDebugPendingBreakpoint2::Bind"
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Эта привязка ожидается точка останова с одним или несколькими места кода.  
  
## Синтаксис  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```c#  
int Bind();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_BP_DELETED` если точка останова удалена.  
  
## Заметки  
 Если этот метод вызывается обработчик отладки \(DE\) должен попытаться привязать эта отложенную точка останова ко всем места кода, которые соответствуют.  
  
 После этого метод возвращает вызывающий объект должен ожидать события, указывающий на то, что ожидается точка останова привязала или ошибке, прежде чем при условии, что вызовы [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) OR  [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md).methods перечислены все точки останова границ или ошибки, соответственно.  
  
## См. также  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)