---
title: "Операнд Preserve ReDim не может быть Nothing. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b857f313-3fc2-4262-a577-88df1718b811
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операнд Preserve ReDim не может быть Nothing.
Оператор `ReDim` пытается использовать ключевое слово `Preserve` для изменения измерения массива, которое не является последним измерением, но не предоставляет допустимое значение для своего операнда.  
  
### Исправление ошибки  
  
-   Измените операнд `Preserve`, чтобы он имел допустимое значение.  
  
## См. также  
 [НЕ В СБОРКЕ. Обзор массивов в Visual Basic](http://msdn.microsoft.com/ru-ru/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [НЕ В СБОРКЕ. Многомерные массивы в Visual Basic](http://msdn.microsoft.com/ru-ru/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [Оператор ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Preserve — удалить](http://msdn.microsoft.com/ru-ru/91badeab-b4e0-48b6-92c9-9f0c8f995d81)