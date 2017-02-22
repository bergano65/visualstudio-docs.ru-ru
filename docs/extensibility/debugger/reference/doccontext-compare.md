---
title: "DOCCONTEXT_COMPARE | Microsoft Docs"
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
  - "DOCCONTEXT_COMPARE"
helpviewer_keywords: 
  - "Перечисление DOCCONTEXT_COMPARE"
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает условие для сравнения 2 контекста документа.  
  
## Синтаксис  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```c#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## Члены  
 DOCCONTEXT\_EQUAL  
 Найдите первый контекст рисования в списке, равный контексту документа целевого объекта.  
  
 DOCCONTEXT\_LESS\_THAN  
 Найдите первый контекст рисования в списке, чем контекст рисования целевого объекта.  
  
 DOCCONTEXT\_GREATER\_THAN  
 Найдите первый контекст рисования в списке, больше контекст рисования целевого объекта.  
  
 DOCCONTEXT\_SAME\_DOCUMENT  
 Найдите первый контекст рисования в списке, в том же документе, что контекст рисования целевого объекта.  
  
## Заметки  
 Передается в качестве аргумента [Сравнение](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) метод.  
  
 Эти значения используются для указания условия сравнения для поиска первый контекст рисования в списке.  Получает контекст рисования список контекстов документа для сравнения с посредством `IDebugDocumentContext2::Compare` метод.  Первый контекст рисования в списке, для которого оператор сравнения `true` затем возвращается.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Сравнение](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)