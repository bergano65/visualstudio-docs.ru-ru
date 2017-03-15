---
title: "IDebugBoundBreakpoint2::SetCondition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetCondition"
helpviewer_keywords: 
  - "Метод SetCondition"
  - "Метод IDebugBoundBreakpoint2::SetCondition"
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает или изменения условие, связанное с данной связанной точкой останова.  
  
## Синтаксис  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```c#  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### Параметры  
 `bpCondition`  
 \[in\] значение из [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) перечисление, которое описывает условие.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_BP_DELETED` если состояние связанного объекта точки останова равно  `BPS_DELETED` \(часть   [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисление\).  
  
## Заметки  
 Любое условие, который ранее был связан с этой точки останова потеряно.  
  
## См. также  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)