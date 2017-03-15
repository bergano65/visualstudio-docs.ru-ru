---
title: "Требуется символ &quot;{&quot; | Microsoft Docs"
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
  - "vbc30987"
  - "bc30987"
helpviewer_keywords: 
  - "BC30987"
ms.assetid: 3d1552b6-338a-47cf-84d5-77b59209e0d3
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется символ &quot;{&quot;
Чтобы объявить экземпляр именованного или анонимного типа с помощью инициализатора объектов, необходимо заключить список полей или свойств и их начальные значения в фигурные скобки \({ }\).  
  
```  
Dim client As New Customer() With {.Name = "Microsoft", .City = "Seattle"}  
Dim emp = New Employee() With {.Name = "Rob Young", .ID = 55555}  
Dim anon = New With {.ID = 123456}  
```  
  
 **Идентификатор ошибки:** BC30987  
  
### Исправление ошибки  
  
-   Включите список инициализации, заключенный в фигурные скобки, после `With`.  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Процедуры свойств и Поля](http://msdn.microsoft.com/ru-ru/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)   
 [Анонимные типы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)