---
title: "Невозможно завершить операцию: конечный каталог находится внутри исходного | Microsoft Docs"
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
  - "vbrIO_CyclicOperation"
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно завершить операцию: конечный каталог находится внутри исходного
Циклическая операция не удалась. Циклические операции являются бесконечными циклами и поэтому не могут завершиться. Например, объект A может попытаться наследоваться от объекта B, который в свою очередь наследуется от объекта A.  
  
### Исправление ошибки  
  
-   При наследовании убедитесь в отсутствии циклических ссылок.  
  
## См. также  
 [Типы ошибок](/dotnet/visual-basic/programming-guide/language-features/error-types)   
 [Debugging Basics: Breakpoints](http://msdn.microsoft.com/ru-ru/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)