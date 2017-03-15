---
title: "ReDim не может изменять размерность | Microsoft Docs"
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
  - "vbrArray_RankMismatch"
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReDim не может изменять размерность
Предпринята попытка использования оператора `ReDim` для изменения ранга \(размерности\) массива. Оператор `ReDim` может изменять размер одного или нескольких измерений массива, который уже был формально объявлен, но он не может изменить ранг массива.  
  
### Исправление ошибки  
  
-   Убедитесь, что требуется изменить ранг, а не размеры массива, и по возможности используйте `Dim` для объявления нового массива с нужным рангом.  
  
## См. также  
 [НЕ В СБОРКЕ. Обзор массивов в Visual Basic](http://msdn.microsoft.com/ru-ru/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [НЕ В СБОРКЕ. Многомерные массивы в Visual Basic](http://msdn.microsoft.com/ru-ru/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [Оператор ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)