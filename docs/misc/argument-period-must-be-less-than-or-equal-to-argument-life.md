---
title: "Аргумент &quot;Period&quot; должен быть меньше или равен аргументу &quot;Life&quot; | Microsoft Docs"
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
  - "vbrFinancial_PeriodLELife"
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргумент &quot;Period&quot; должен быть меньше или равен аргументу &quot;Life&quot;
Значение аргумента `Period`, определяющего период, для которого рассчитывается снижение стоимости актива, больше, чем значение аргумента `Life`.  
  
### Исправление ошибки  
  
-   Убедитесь в том, что значения аргументов `Life` и `Period` выражаются в одинаковых единицах измерения. Например, если `Life` измеряется в месяцах, то значение `Period` должно быть также в месяцах.  
  
## См. также  
 [НЕ В СБОРКЕ. Функция DDB](http://msdn.microsoft.com/ru-ru/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [НЕ В СБОРКЕ. Функция SYD](http://msdn.microsoft.com/ru-ru/23c25672-f5dd-49ac-9893-4faa82634181)   
 [Передача аргументов по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)