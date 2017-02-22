---
title: "BP_PASSCOUNT_STYLE | Microsoft Docs"
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
  - "BP_PASSCOUNT_STYLE"
helpviewer_keywords: 
  - "Структура BP_PASSCOUNT_STYLE"
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает условие, связанное с количеством передачи точки останова, который вызывает создать точку останова.  
  
## Синтаксис  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## Члены  
 BP\_PASSCOUNT\_NONE  
 Не задает ни один стиль количества передачи точки останова.  
  
 BP\_PASSCOUNT\_EQUAL  
 Задает стиль количества передачи точки останова равно значению выражения.  Срабатывает точки останова, когда количество проходов равно попадания объем передачи.  
  
 BP\_PASSCOUNT\_EQUAL\_OR\_GREATER  
 Задает стиль количества передачи точки останова равным или больше него.  Срабатывает точки останова, когда количество проходов выполненная строка, равно или больше, чем объем передачи.  
  
 BP\_PASSCOUNT\_MOD  
 Указывает объем передачи остатка от деления.  Например, если объем передачи типа `BP_PASSCOUNT_MOD` положительный и значение числа 4, срабатывает каждый раз, когда количество обращений точки останова кратной 4.  
  
## Заметки  
 Используется для `stylePassCount` элемент  [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структура, которая, в свою очередь, элемент  [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и  [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)