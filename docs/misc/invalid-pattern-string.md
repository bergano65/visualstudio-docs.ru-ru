---
title: "Недопустимая строка шаблона | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Недопустимая строка шаблона
Строка шаблона, указанная в операции поиска `Like`, является недопустимой.  
  
### Исправление ошибки  
  
1.  Просмотрите допустимые символы для выражений списка.  
  
2.  В диапазоне шаблона убедитесь, что знак в начале диапазона меньше знака в конце диапазона, как в `[a-z]`.  
  
3.  В диапазоне шаблона убедитесь, что не отсутствуют дефисы, указанные рядом друг с другом, как в `[a--z]`.  
  
4.  Завершите диапазон шаблона закрывающей скобкой.  
  
## См. также  
 [Оператор Like](/dotnet/visual-basic/language-reference/operators/like-operator)