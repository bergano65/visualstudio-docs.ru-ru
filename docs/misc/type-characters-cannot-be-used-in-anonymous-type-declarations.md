---
title: "Не удается использоваться символы типа в объявлениях анонимного типа | Microsoft Docs"
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
  - "bc36560"
  - "vbc36560"
helpviewer_keywords: 
  - "BC36560"
ms.assetid: 70eee559-d6fc-409b-b835-2c84511b160e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается использоваться символы типа в объявлениях анонимного типа
Нельзя использовать символ типа для имени свойства при объявлении экземпляра анонимного типа. Тип данных свойства выводится из присвоенного значения. Например, ниже приведены недопустимые объявления.  
  
```vb#  
'' Not valid. 'Dim anon1 = New With {.ID$ = "abc"} 'Dim anon2 = New With {.ID$ = 42}  
```  
  
 **Идентификатор ошибки:** BC36560  
  
### Исправление ошибки  
  
-   Удалите символ типа из списка инициализаторов. Вы можете явным образом преобразовать присвоенное значение, если это необходимо для задания типа данных для свойства.  
  
    ```vb#  
    ' Valid. Dim anon1 = New With {.ID = "abc"} Dim anon2 = New With {.ID = CStr(42)}  
    ```  
  
## См. также  
 [Анонимные типы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)   
 [Явные и неявные преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)