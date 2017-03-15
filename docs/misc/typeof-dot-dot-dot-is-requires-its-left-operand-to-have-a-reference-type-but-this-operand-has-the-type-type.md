---
title: "Левый операнд выражения &quot;TypeOf...Is&quot; должен иметь ссылочный тип, а этот операнд имеет тип значения &quot;&lt;тип&gt;&quot; | Microsoft Docs"
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
  - "bc30021"
  - "vbc30021"
helpviewer_keywords: 
  - "BC30021"
ms.assetid: a6e76fc8-9c7f-4e55-8b68-e6e7b03a6737
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Левый операнд выражения &quot;TypeOf...Is&quot; должен иметь ссылочный тип, а этот операнд имеет тип значения &quot;&lt;тип&gt;&quot;
Выражение `TypeOf...Is` служит для проверки совместимости типа времени выполнения переменной объекта. Эта совместимость не определяется для типов значений.  
  
 **Идентификатор ошибки:** BC30021  
  
### Исправление ошибки  
  
-   Если `Option Strict` установлено в значение `Off`, используйте функцию `TypeName` или `VarType` для получения сведений о типе данных переменной.  
  
-   Если `Option Strict` установлено в значение `On`, объявление переменной определяет тип данных переменной.  
  
## См. также  
 [Операторы сравнения в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [НЕ В СБОРКЕ. Функция TypeName \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/6197bc6c-e8a6-4711-883c-0c95e94e272c)   
 [НЕ В СБОРКЕ. Функция VarType \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/e820b6fc-faa6-4de4-836a-0466032dc190)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)