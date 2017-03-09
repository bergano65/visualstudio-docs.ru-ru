---
title: "При использовании директивы Option Strict On все объявления переменных должны иметь предложение As | Microsoft Docs"
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
  - "bc30209"
  - "vbc30209"
helpviewer_keywords: 
  - "BC30209"
ms.assetid: 69c2e32a-86aa-4075-a142-440605a7063a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# При использовании директивы Option Strict On все объявления переменных должны иметь предложение As
Объявление содержит объявленную переменную без предложения `As`. Когда директива `Option Strict` имеет значение `On`, все переменные, свойства, аргументы процедур и возвращаемые значения функций должны быть объявлены с предложением `As`, чтобы указать тип данных. Например: `Dim MyNum As Short`.  
  
 **Идентификатор ошибки:** BC30209  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания ключевого слова `As`.  
  
2.  Укажите предложение `As` для объявленной переменной или укажите директиву `Option Strict Off`.  
  
## См. также  
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Объявление переменной](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)