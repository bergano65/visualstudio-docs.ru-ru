---
title: "BP_CONDITION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_CONDITION"
helpviewer_keywords: 
  - "Структура BP_CONDITION"
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_CONDITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает условия, при которых точка останова запускает.  
  
## Синтаксис  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```c#  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## Члены  
 `pThread`  
 IDebugThread2 объект, представляющий активный поток для приложения, содержащей точку останова.  
  
 `styleCondition`  
 Значение [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) перечисление, описывающее стиль данного условия точки останова.  
  
 `bstrContext`  
 Местоположение точки останова.  
  
 `bstrCondition`  
 Условие включения точки останова.  
  
 `nRadix`  
 Корневой каталог, используемый при оценке любое числовое сведения.  
  
## Заметки  
 Эта структура элемент [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и  [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 Эта структура также передается как параметр [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) и  [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) методы.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)