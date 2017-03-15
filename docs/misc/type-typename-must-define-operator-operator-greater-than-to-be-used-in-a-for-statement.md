---
title: "Тип &quot;&lt;typename&gt;&quot; должен определять оператор &quot;&lt;operator&gt;&quot;, чтобы использовать его в инструкции For. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33038"
  - "BC33038"
helpviewer_keywords: 
  - "BC33038"
ms.assetid: b1c9d87f-80f9-4c8c-8908-f8400b9fe4c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;typename&gt;&quot; должен определять оператор &quot;&lt;operator&gt;&quot;, чтобы использовать его в инструкции For.
Цикл `For` задает переменную счетчика с типом, который не поддерживает нужный оператор.  
  
 Переменная счетчика в цикле `For` может быть любого типа данных, поддерживающего все следующие операторы:  
  
-   больше или равно \(`>=`\);  
  
-   меньше или равно \(`<=`\);  
  
-   сложения \(`+`\);  
  
-   вычитания \(`-`\).  
  
 Если для переменной счетчика используется числовой тип данных, все перечисленные выше операторы поддерживаются. При использовании пользовательского класса или структуры необходимо определить все перечисленные выше операторы для этого класса или структуры.  
  
 Также обратите внимание, что типы данных выражений `start`, `end` и `step` в инструкции `For` необходимо расширить в тип данных переменной счетчика. Если переменная счетчика является определяемым пользователем классом или структурой и выражение `start`, `end` или `step` имеет другой тип, необходимо определить оператор преобразования `CType`, чтобы выполнить необходимые преобразования.  
  
 **Идентификатор ошибки:** BC33038  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания типа данных переменной счетчика.  
  
2.  При использовании для переменной счетчика пользовательского класса или структуры определите все необходимые операторы для этого класса или структуры.  
  
3.  В зависимости от типов данных выражений `start`, `end` и `step` может потребоваться определить один или несколько операторов преобразования `CType` для преобразования их в тип данных переменной счетчика.  
  
## См. также  
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Функция CType](/dotnet/visual-basic/language-reference/functions/ctype-function)