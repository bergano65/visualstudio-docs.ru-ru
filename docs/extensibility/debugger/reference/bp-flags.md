---
title: "BP_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_FLAGS"
helpviewer_keywords: 
  - "Перечисление BP_FLAGS"
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Предоставляет дополнительные флаги, которые могут быть использованы для определения дополнительных сведений при установке точки останова.  
  
## Синтаксис  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```c#  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## Члены  
 BP\_FLAG\_NONE  
 Не задает ни пометить точки останова.  
  
 BP\_FLAG\_MAP\_DOCPOSITION  
 Указывает, что отладчик \(DE\) должен сопоставить точки останова, используя позицию документа.  Это применимо только к точкам останова, заданных в скрипт\-ориентированные исходных файлов, например active server pages \(ASP\).  
  
 \_STOP НЕ BP\_FLAG\_DO  
 Указывает, что точка останова должна обрабатываться службами отладки, но в конечном счете, что отладчик не должен остановиться у \(т е IDebugBreakpointEvent2 объект события не должен быть отправлен\).  Этот пометить предназначен для использования главным образом с точками трассировки.  
  
## Заметки  
 Используется для `dwFlags` элемент  [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и  [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 Эти значения могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)