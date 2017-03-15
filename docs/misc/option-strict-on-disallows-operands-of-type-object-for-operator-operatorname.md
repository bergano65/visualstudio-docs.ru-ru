---
title: "Option Strict On запрещает использование с оператором &quot;&lt;имя_оператора&gt;&quot; операндов типа Object | Microsoft Docs"
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
  - "bc32013"
  - "vbc32013"
helpviewer_keywords: 
  - "BC32013"
ms.assetid: cd197da8-2676-453b-884b-3231fb6f909d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On запрещает использование с оператором &quot;&lt;имя_оператора&gt;&quot; операндов типа Object
Option Strict On запрещает использование с оператором "\<имя\_оператора\>" операндов типа Object. Для проверки тождества объектов используйте оператор Is.  
  
 Оператор арифметического сравнения, такой как `=`, используется с одной или несколькими объектными переменными в то время, когда параметр `Option Strict` установлен в значение `On`.  
  
 **Идентификатор ошибки:** BC32013  
  
### Исправление ошибки  
  
1.  Установите значение `Option Strict Off`, если в объектной переменной содержатся числовые значения и необходимо выполнить арифметическое сравнение.  
  
2.  Для проверки тождества объектов используйте оператор `Is`.  
  
## См. также  
 [Операторы сравнения](/dotnet/visual-basic/language-reference/operators/comparison-operators)   
 [Оператор Is](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)