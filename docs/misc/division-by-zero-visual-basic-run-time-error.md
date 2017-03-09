---
title: "Деление на ноль (ошибка времени выполнения Visual Basic) | Microsoft Docs"
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
  - "vbrID11"
ms.assetid: 5b9bc5d6-792e-48bc-a974-012e07ad95f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Деление на ноль (ошибка времени выполнения Visual Basic)
Выражение, используемое в качестве делителя, имеет нулевое значение.  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания переменных в выражении. Неправильно написанное имя переменной может привести к неявному созданию числовой переменной, которая инициализируется нулевым значением.  
  
2.  Проверьте предыдущие операции с переменными в выражении, в особенности те, которые передавались в процедуру как аргументы из других процедур.  
  
## См. также  
 [Передача аргументов по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Parameter Passing Mechanism Changes in Visual Basic](http://msdn.microsoft.com/ru-ru/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)