---
title: "&quot;ReDim&quot; не может изменять размерность массива. | Microsoft Docs"
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
  - "vbc30415"
  - "bc30415"
helpviewer_keywords: 
  - "BC30415"
ms.assetid: 8ce97188-ff96-4e8c-917c-efc2f94173a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;ReDim&quot; не может изменять размерность массива.
Предпринята попытка использования `ReDim` для изменения ранга \(размерности\) массива. Оператор `ReDim` может использоваться для изменения размера одного или нескольких измерений массива, который уже был формально объявлен, но он не может изменить ранг массива.  
  
 **Идентификатор ошибки:** BC30415  
  
### Исправление ошибки  
  
-   Убедитесь, что требуется изменить ранг, а не размеры массива, и по возможности используйте `Dim` для объявления нового массива с нужным рангом.  
  
## См. также  
 [Оператор ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [НЕ В СБОРКЕ. Обзор массивов в Visual Basic](http://msdn.microsoft.com/ru-ru/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)