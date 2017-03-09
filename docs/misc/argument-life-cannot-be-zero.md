---
title: "Аргумент Life не может быть равен нулю | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrFinancial_LifeNEZero"
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргумент Life не может быть равен нулю
Недопустимый аргумент для `Life`, который должен быть `Double`, указывающий срок эксплуатации актива.  
  
### Исправление ошибки  
  
-   Проверьте правильность написания аргументов в выражении. Неправильно написанное имя переменной может привести к неявному созданию числовой переменной, которая инициализируется нулевым значением.  
  
-   Проверьте предыдущие операции с переменными в выражении, в особенности те, которые передавались в процедуру как аргументы из других процедур.  
  
## См. также  
 [НЕ В СБОРКЕ. Функция DDB](http://msdn.microsoft.com/ru-ru/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [НЕ В СБОРКЕ. Функция SYD](http://msdn.microsoft.com/ru-ru/23c25672-f5dd-49ac-9893-4faa82634181)   
 [НЕ В СБОРКЕ. Функция SLN](http://msdn.microsoft.com/ru-ru/8e06130a-056e-4266-a8a9-1592b86f58d2)   
 [Передача аргументов по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)