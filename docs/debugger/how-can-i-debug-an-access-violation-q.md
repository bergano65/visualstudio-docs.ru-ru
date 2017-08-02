---
title: "Как отладить нарушение доступа? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "отладка нарушений доступа"
  - "отладка [Visual Studio], нарушения доступа"
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Как отладить нарушение доступа?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Описание проблемы  
 Программа порождает нарушение доступа. Как это отладить?  
  
## Решение  
 Если вы получаете нарушение прав доступа в строке кода, которая разыменовывает несколько указателей, может быть трудно определить указатель, который вызвал нарушение прав доступа. Начиная с Visual Studio 2015 с обновлением 1 диалоговое окно исключения теперь явно называет указатель, который вызвал нарушение прав доступа.  
  
 Например, если имеется следующий код, вы должны получить нарушение прав доступа:  
  
```cpp  
#include <iostream> using namespace std; class ClassB { public: ClassC* C; ClassB() { C = new ClassC(); } void printHello() { cout << "hello world"; } }; class ClassA { public: ClassB* B; ClassA() { B = nullptr; } }; int main() { ClassA* A = new ClassA(); A->B->printHello(); }  
```  
  
 При выполнении этого кода в Visual Studio 2015 с обновлением 1 вы увидите следующее диалоговое окно исключения:  
  
 ![AccessViolationCPlus](~/docs/debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Если не удается определить, почему указатель вызвал нарушение прав доступа, выполните трассировку кода, чтобы проверить правильность назначения указателя, ставшего причиной проблемы.  Если он передается как параметр, убедитесь, что он передается правильно и вы не создаете случайно [неполную копию](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Затем проверьте, не изменяются ли непреднамеренно значения где\-нибудь в программе путем создания точки останова по данным для рассматриваемого указателя, чтобы убедиться, что он не изменяется в другом месте программы. Дополнительные сведения о точках останова по данным см. в разделе, посвященном точкам останова по данным, в статье [Использование точек останова](../debugger/using-breakpoints.md).  
  
## См. также  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)