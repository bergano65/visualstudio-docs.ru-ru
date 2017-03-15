---
title: "Значение аргумента &quot;&lt;имя_аргумента&gt;&quot; должно находиться в диапазоне от 1 до 255 | Microsoft Docs"
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
  - "vbrArgument_Range1toFF1"
ms.assetid: a447f9a6-1c90-4c71-abff-81170331e4c5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Значение аргумента &quot;&lt;имя_аргумента&gt;&quot; должно находиться в диапазоне от 1 до 255
Аргумент недопустим, так как его значение не попадает в диапазон от 0 до 255.  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания аргументов в выражении. Неправильно написанное имя переменной может привести к неявному созданию числовой переменной, которая инициализируется нулевым значением.  
  
2.  Проверьте предыдущие операции с переменными в выражении, в особенности те, которые передавались в процедуру как аргументы из других процедур.  
  
## См. также  
 [Передача аргументов по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)