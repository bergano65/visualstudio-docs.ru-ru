---
title: "IDebugPendingBreakpoint2::Virtualize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Virtualize"
helpviewer_keywords: 
  - "Метод виртуализации"
  - "Метод IDebugPendingBreakpoint2::Virtualize"
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::Virtualize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Переключает состояние ожидающих virtualized этой точки останова.  Если ожидается точка останова будет virtualized, отладчик пытается привязать его загрузки каждого кода времени новых в программу.  
  
## Синтаксис  
  
```cpp#  
HRESULT Virtualize(   
   BOOL fVirtualize  
);  
```  
  
```cpp#  
int Virtualize(   
   int fVirtualize  
);  
```  
  
#### Параметры  
 `fVirtualize`  
 \[in\] набор \(как значение`TRUE`ожидается\) virtualize точка останова или ноль \(`FALSE`отключить виртуализация\).  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_BP_DELETED` если точка останова удалена.  
  
## Заметки  
 Virtualized точка останова привязана каждому код времени загружена.  
  
## Пример  
 В следующем примере показано, как реализовать этот метод для простого `CPendingBreakpoint` объект, предоставляющий  [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейс.  
  
```cpp#  
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      if (fVirtualize)    
      {    
         // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         SetFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      else    
      {    
         // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## См. также  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)