---
title: "Требуется константное выражение. | Microsoft Docs"
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
  - "bc30059"
  - "vbc30059"
helpviewer_keywords: 
  - "BC30059"
ms.assetid: fdd5e7bb-6370-4a63-bbb6-23b15badb4c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется константное выражение.
Инструкция `Const` не инициализирует константу должным образом, или в объявлении массива используется переменная для указания числа элементов.  
  
 **Идентификатор ошибки:** BC30059  
  
### Исправление ошибки  
  
1.  Если объявление является инструкцией `Const`, убедитесь, что константа инициализируется с помощью литерала, ранее объявленной константы, члена перечисления или сочетания литералов, констант и членов перечисления, объединенных операторами.  
  
2.  Если объявление задает массив, проверьте, используется ли переменная для указания числа элементов. Если это так, замените переменную на константное выражение.  
  
## См. также  
 [Оператор Const](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [НЕ В СБОРКЕ. Переменная массива](http://msdn.microsoft.com/ru-ru/c2da78bd-6928-46ba-805f-44f819dfaf93)