---
title: "Переменные с ключевым словом WithEvents не могут быть типизированы как массивы | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30476"
  - "vbc30476"
helpviewer_keywords: 
  - "BC30476"
ms.assetid: 29bed445-a247-4c88-a1eb-115535900377
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменные с ключевым словом WithEvents не могут быть типизированы как массивы
Предпринята попытка объявить массив с помощью `WithEvents`. Вы можете объявлять сколько угодно отдельных переменных с помощью `WithEvents`, но таким образом нельзя объявлять массивы.  
  
 **Идентификатор ошибки:** BC30476  
  
### Исправление ошибки  
  
1.  Объявите переменные по отдельности.  
  
## См. также  
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [НЕ В СБОРКЕ. Оператор WithEvents и предложение Handles](http://msdn.microsoft.com/ru-ru/072b9cf6-6298-46f1-849e-4edc1631564c)