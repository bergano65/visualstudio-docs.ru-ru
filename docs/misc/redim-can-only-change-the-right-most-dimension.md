---
title: "&quot;ReDim&quot; может изменять только крайнее правое измерение | Microsoft Docs"
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
  - "vbrArray_TypeMismatch"
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;ReDim&quot; может изменять только крайнее правое измерение
В операторе `ReDim` ключевое слово `Preserve` используется для изменения измерения массива, которое не является его последним измерением. При использовании `Preserve` можно изменять размер только последнего измерения массива. Для всех других измерений необходимо указать тот же размер, что и для существующего массива.  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Preserve`.  
  
## См. также  
 [НЕ В СБОРКЕ. Обзор массивов в Visual Basic](http://msdn.microsoft.com/ru-ru/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [НЕ В СБОРКЕ. Многомерные массивы в Visual Basic](http://msdn.microsoft.com/ru-ru/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [Оператор ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Preserve — удалено](http://msdn.microsoft.com/ru-ru/91badeab-b4e0-48b6-92c9-9f0c8f995d81)