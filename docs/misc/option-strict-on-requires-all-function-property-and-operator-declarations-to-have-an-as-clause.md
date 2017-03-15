---
title: "Для Option Strict On при объявлении функций и свойств обязательно применение конструкции As. | Microsoft Docs"
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
  - "vbc30210"
  - "bc30210"
helpviewer_keywords: 
  - "BC30210"
ms.assetid: 4d217e56-0eac-4834-bcad-234a69809390
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для Option Strict On при объявлении функций и свойств обязательно применение конструкции As.
Объявление содержит объявленное свойство или возвращаемое значение функции без предложения `As`. Когда директива `Option Strict` имеет значение `On`, все переменные, свойства, аргументы процедур и возвращаемые значения функций должны быть объявлены с предложением `As`, чтобы указать тип данных. Например: `Dim MyNum As Short`.  
  
 **Идентификатор ошибки:** BC30210  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания ключевого слова `As`.  
  
2.  Укажите предложение `As` для объявленного свойства или возвращаемого значения функции или включите `Option Strict Off`.  
  
## См. также  
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Процедуры Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)