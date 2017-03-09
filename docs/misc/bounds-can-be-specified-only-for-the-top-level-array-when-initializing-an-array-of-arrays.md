---
title: "При инициализации массива массивов границы могут задаваться только для массива верхнего уровня. | Microsoft Docs"
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
  - "bc32014"
  - "vbc32014"
helpviewer_keywords: 
  - "BC32014"
ms.assetid: d8d7155d-82d1-4a25-b9bb-1883e1586383
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# При инициализации массива массивов границы могут задаваться только для массива верхнего уровня.
Инициализация массива для массива массивов задает начальную длину одного из нижних уровней. В операторе объявления массива можно указать длину только массива верхнего уровня.  
  
 **Идентификатор ошибки:** BC32014  
  
### Исправление ошибки  
  
1.  Удалите указание длины из всех массивов, кроме массива верхнего уровня.  
  
2.  Установите начальную границу массивов нижнего уровня в последующих операторах назначения с помощью ключевого слова `New`.  
  
## См. также  
 [НЕ В СБОРКЕ. Переменная массива](http://msdn.microsoft.com/ru-ru/c2da78bd-6928-46ba-805f-44f819dfaf93)   
 [НЕ В СБОРКЕ. Массивы массивов в Visual Basic](http://msdn.microsoft.com/ru-ru/05c12439-ee8f-4fef-ba75-b35402b67ab9)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)