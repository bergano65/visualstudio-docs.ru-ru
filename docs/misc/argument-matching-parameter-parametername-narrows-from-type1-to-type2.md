---
title: "Соответствующий параметру &quot;&lt;имя_параметра&gt;&quot; аргумент сужает диапазон возможных значений при преобразовании из &quot;&lt;тип1&gt;&quot; в &quot;&lt;тип2&gt;&quot; | Microsoft Docs"
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
  - "vbc30520"
  - "bc30520"
helpviewer_keywords: 
  - "BC30520"
ms.assetid: 652ff70b-156d-4d1c-af19-fa1c53e2d0b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Соответствующий параметру &quot;&lt;имя_параметра&gt;&quot; аргумент сужает диапазон возможных значений при преобразовании из &quot;&lt;тип1&gt;&quot; в &quot;&lt;тип2&gt;&quot;
Вы выполнили вызов перегруженного метода, но компилятор не может найти метод, который можно вызывать без преобразования сужения. Преобразование сужения изменяет тип данных значения на тип, который не сможет точно содержать возможные значения.  
  
 **Идентификатор ошибки:** BC30520  
  
### Исправление ошибки  
  
-   Укажите директиву `Option Strict Off`.  
  
## См. также  
 [Перегруженные свойства и методы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)