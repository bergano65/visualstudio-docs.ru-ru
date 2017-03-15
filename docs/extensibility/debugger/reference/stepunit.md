---
title: "STEPUNIT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STEPUNIT"
helpviewer_keywords: 
  - "Перечисление STEPUNIT"
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# STEPUNIT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет единицу измерения для пошагового выполнения этапа.  
  
## Синтаксис  
  
```cpp#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```c#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## Члены  
 STEP\_STATEMENT  
 Шаги выпиской.  
  
 STEP\_LINE  
 Шаги линией.  
  
 STEP\_INSTRUCTION  
 Шаги инструкцией.  
  
## Заметки  
 Передается в качестве аргумента [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md) метод.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)