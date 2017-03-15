---
title: "Аргумента &quot;&lt;имя_аргумента&gt;&quot; должен быть больше нуля | Microsoft Docs"
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
  - "vbrArgument_GTZero1"
ms.assetid: f9939fbd-6c4f-4871-9452-9ea0267e948e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргумента &quot;&lt;имя_аргумента&gt;&quot; должен быть больше нуля
Аргумент недопустим, так как он меньше или равен нулю.  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания аргументов в выражении. Неправильно написанное имя переменной может привести к неявному созданию числовой переменной, которая инициализируется нулевым значением.  
  
2.  Проверьте предыдущие операции с переменными в выражении, в особенности те, которые передавались в процедуру как аргументы из других процедур.  
  
## См. также  
 [Передача аргументов по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Parameter Passing Mechanism Changes in Visual Basic](http://msdn.microsoft.com/ru-ru/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)