---
title: "Объявления массивов не могут задавать нижние границы | Microsoft Docs"
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
  - "vbc30805"
  - "bc30805"
helpviewer_keywords: 
  - "BC30805"
ms.assetid: f2055387-f4dc-4366-89fb-d752929a0258
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Объявления массивов не могут задавать нижние границы
Массивы всегда имеют нижнюю границу, равную нулю. Вы можно указать ноль в качестве нижней границы, чтобы сделать код более понятным. Однако нельзя указать для нижней границы другое значение.  
  
 **Идентификатор ошибки:** BC30805  
  
### Исправление ошибки  
  
-   Задайте размер массива на единицу меньше, чем общее число элементов массива. Например, `Dim y(6)` имеет тот же размер \(7 элементов\), что и `Dim x(3 To 9)`. Вы также можете указать `Dim y(0 To 6)`.  
  
-   Используйте смещения для имитации ненулевых значений нижних границ. Следующий пример имитирует массив с номерами элементов от 3 до 9.  
  
    ```  
    Const offset As Integer = 3 Dim arrayIndex As Integer ' arrayIndex can vary between 3 and 9. Dim y(0 To 6) ' The preceding statement allocates the same number of elements ' as Dim y(3 To 9). y(arrayIndex - offset) = value ' The preceding statement converts arrayIndex to the ' corresponding index of y.  
    ```  
  
## См. также  
 [Массивы](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Размерность массивов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/array-dimensions)   
 [НЕ В СБОРКЕ. Практическое руководство. Указание нулевой нижней границы в массиве](http://msdn.microsoft.com/ru-ru/20ffd49a-64f7-4634-8ed0-46ba1049d935)