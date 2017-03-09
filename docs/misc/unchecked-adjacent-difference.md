---
title: "unchecked_adjacent_difference | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_adjacent_difference"
  - "std::unchecked_adjacent_difference"
  - "unchecked_adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_adjacent_difference - функция"
ms.assetid: 3a6b0b49-a84b-40b1-bcd5-3bf76c6ef7d7
caps.latest.revision: 14
caps.handback.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_adjacent_difference
То же, что [adjacent\_difference](../Topic/adjacent_difference.md), но позволяет использовать непроверенный итератор как итератор вывода при \_SECURE\_SCL \= 1 определен.`unchecked_adjacent_difference` определяется в `stdext` пространства имен.  
  
> [!NOTE]
>  Этот алгоритм является предоставляемым Microsoft расширением стандартной библиотеки C\+\+. Код, реализованный с помощью этого алгоритма, не будет переносимым.  
  
## Синтаксис  
  
```  
template<class InputIterator, class OutIterator>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result   
   );  
  
template<class InputIterator, class OutputIterator, class BinaryOperation>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result,   
      BinaryOperation _Binary_op  
   );  
```  
  
#### Параметры  
 `_First`  
 Итератор ввода, обращающийся к первому элементу в диапазоне ввода, элементы которого необходимо отличить от соответствующих им предшественников или где с парой значений должна быть выполнена другая заданная бинарная операция.  
  
 `_Last`  
 Итератор ввода, обращающийся к последнему элементу в диапазоне ввода, элементы которого необходимо отличить от соответствующих им предшественников или где с парой значений должна быть выполнена другая заданная бинарная операция.  
  
 `_Result`  
 Итератор вывода, обращающийся к первому элементу в диапазоне назначения, где необходимо сохранить ряд различий или результаты определенной операции.  
  
 `_Binary_op`  
 Бинарная операция, которую необходимо применить в обобщенной операции с заменой операции вычитания в процедуре дифференцирования.  
  
## Возвращаемое значение  
 Выходной итератор, обращающийся к концу диапазона назначения: `_Result` \+ \(`_Last` \- `_First`\).  
  
## Заметки  
 В разделе [adjacent\_difference](../Topic/adjacent_difference.md) образец кода.  
  
 Дополнительные сведения о проверенных итераторах см. в разделе [Проверяемые итераторы](/visual-cpp/standard-library/checked-iterators).  
  
## Требования  
 **Заголовок:** \<numeric\>  
  
 **Пространство имен:** stdext  
  
## См. также  
 [Библиотека стандартных шаблонов](../misc/standard-template-library.md)