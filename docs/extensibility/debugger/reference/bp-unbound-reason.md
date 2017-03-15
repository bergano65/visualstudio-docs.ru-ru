---
title: "BP_UNBOUND_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_UNBOUND_REASON"
helpviewer_keywords: 
  - "Перечисление BP_UNBOUND_REASON"
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Предоставляет причину точка останова была отменена привязка.  
  
## Синтаксис  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```c#  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## Члены  
 BPUR\_UNKNOWN  
 Причина неизвестна.  
  
 BPUR\_CODE\_UNLOADED  
 Код, в котором содержится точка останова был выгружен.  
  
 BPUR\_BREAKPOINT\_REBIND  
 Точка останова отскок в другое расположение.  Это может происходить после правка и продолжает операции, когда точка останова или точка останова перемещается привязана к файлу с путем, который больше не является допустимым.  
  
 BPUR\_ BREAKPOINT\_ERROR  
 Указываются находит точку останова в ошибке после того, как она привязана.  Это происходит в управляемый точки останова, состояние которых более не являются допустимыми.  
  
## Заметки  
 Возвращается [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) метод.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)