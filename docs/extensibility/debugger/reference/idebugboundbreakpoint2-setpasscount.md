---
title: "IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs"
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
  - "IDebugBoundBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "Метод SetPassCount"
  - "Метод IDebugBoundBreakpoint2::SetPassCount"
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает или изменения объем передачи, связанный с данной связанной точкой останова.  
  
## Синтаксис  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### Параметры  
 `bpPassCount`  
 \[in\] [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структура, которая определяет объем передачи.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_BP_DELETED` если состояние связанного объекта точки останова равно  `BPS_DELETED` \(часть   [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисление\).  
  
## Заметки  
 Объем передачи указывает, когда точка останова была предоставлена.  Текущие pass или число вариантов могут быть получены путем вызова [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) метод.  
  
 Любой объем передачи, который ранее был связан с этой точки останова потерян.  
  
## См. также  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)