---
title: "IDebugProcess3::GetDebugReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetDebugReason"
helpviewer_keywords: 
  - "IDebugProcess3::GetDebugReason"
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::GetDebugReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает причину, что процесс запущен для отладки.  
  
## Синтаксис  
  
```cpp  
HRESULT GetDebugReason(  
   DEBUG_REASON* pReason  
);  
```  
  
```c#  
int GetDebugReason(  
   out enum_DEBUG_REASON pReason  
);  
```  
  
#### Параметры  
 `pReason`  
 \[out\] возвращает значение [DEBUG\_REASON](../../../extensibility/debugger/reference/debug-reason.md) перечисление.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DEBUG\_REASON](../../../extensibility/debugger/reference/debug-reason.md)