---
title: "Множественные инициализации члена &quot;&lt;имя-члена&gt;&quot; | Microsoft Docs"
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
  - "vbc30989"
  - "bc30989"
helpviewer_keywords: 
  - "BC30989"
ms.assetid: 574b6398-1e9d-43e1-ac16-6fc8687f71d9
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Множественные инициализации члена &quot;&lt;имя-члена&gt;&quot;
Множественные инициализации члена "\<имя\-члена\>". Поля и свойства могут инициализироваться только один раз в выражении инициализатора объекта.  
  
 Вы можете назначить начальное значение для каждого поля и свойства в списке инициализатора объекта только один раз. Следующее объявление является неправильным.  
  
```  
' Dim cust = New Customer() With {.Name = "Bob", .Name = "Robert"}  
```  
  
> [!NOTE]
>  Вы можете использовать одно поле или свойство в качестве начального значения для другого члена, как показано в следующем объявлении.  
  
```  
Dim cust = New Customer() With {.First = "Mike", .Last = "Nash", _ .Full = .First & " " & .Last}  
```  
  
 **Идентификатор ошибки:** BC30989  
  
### Исправление ошибки  
  
-   Удалите все лишние инициализации, оставив по одной инициализации для каждого поля или свойства в списке инициализатора объекта.  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Процедуры свойств и Поля](http://msdn.microsoft.com/ru-ru/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)