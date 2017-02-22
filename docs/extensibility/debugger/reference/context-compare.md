---
title: "CONTEXT_COMPARE | Microsoft Docs"
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
  - "CONTEXT_COMPARE"
helpviewer_keywords: 
  - "Перечисление CONTEXT_COMPARE"
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает условие для сравнения 2 контекста памяти.  
  
## Синтаксис  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```c#  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## Члены  
 CONTEXT\_EQUAL  
 Найдите первый контекст памяти в списке, равный контексту памяти целевого объекта.  
  
 CONTEXT\_LESS\_THAN  
 Найдите первый контекст памяти в списке, чем контекст памяти целевого объекта.  
  
 CONTEXT\_GREATER\_THAN  
 Найдите первый контекст памяти в списке, больше контекст памяти целевого объекта.  
  
 CONTEXT\_LESS\_THAN\_OR\_EQUAL  
 Найдите первый контекст памяти в списке, меньшее или равное контексту памяти целевого объекта.  
  
 CONTEXT\_GREATER\_THAN\_OR\_EQUAL  
 Найдите первый контекст памяти в списке, больше или равно контексту памяти целевого объекта.  
  
 CONTEXT\_SAME\_SCOPE  
 Найдите первый контекст памяти в списке, в одной области в качестве контекста памяти целевого объекта.  
  
 CONTEXT\_SAME\_FUNCTION  
 Найдите первый контекст памяти в списке, в одной и той же функции, такие как область целевого объекта.  
  
 CONTEXT\_SAME\_MODULE  
 Найдите первый контекст памяти в списке, в одном модуле, как контекст памяти целевого объекта.  
  
 CONTEXT\_SAME\_PROCESS  
 Найдите первый контекст памяти в списке, в том же процессе, что контекст памяти целевого объекта.  
  
## Заметки  
 Передается в качестве аргумента [Сравнение](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) метод.  
  
 Эти значения используются для поиска первый контекст памяти в списке, удовлетворяющий, определенные условия сравнения.  Получает контекст памяти список контекстов памяти для сравнения с посредством `IDebugMemoryContext2::Compare` метод.  Первый контекст памяти в списке, для которого оператор сравнения `true` затем возвращается.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Сравнение](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)