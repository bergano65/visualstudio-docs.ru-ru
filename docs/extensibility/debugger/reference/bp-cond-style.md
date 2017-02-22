---
title: "BP_COND_STYLE | Microsoft Docs"
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
  - "BP_COND_STYLE"
helpviewer_keywords: 
  - "Перечисление BP_COND_STYLE"
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает стиль условия точки останова, ожидающих и связанных точек останова.  
  
## Синтаксис  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## Члены  
 BP\_COND\_NONE  
 Создает точку останова, если позиция точки останова.  Отсутствие заданного условия точки останова.  
  
 BP\_COND\_WHEN\_TRUE  
 Создает точку останова, только если условное выражение, связанное с точкой останова равно `true`.  
  
 BP\_COND\_WHEN\_CHANGED  
 Создает точку останова, только если значение условного выражения, связанного с точкой останова изменилось из предыдущей оценки.  
  
## Заметки  
 Используется для `styleCondition` элемент  [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) структура.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)