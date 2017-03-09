---
title: "Имя инициализируемого поля или свойства должно начинаться с точки (.). | Microsoft Docs"
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
  - "vbc30985"
  - "bc30985"
helpviewer_keywords: 
  - "BC30985"
ms.assetid: 4cb543e1-477c-429c-82df-541ebff08543
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Имя инициализируемого поля или свойства должно начинаться с точки (.).
Каждый инициализатор члена в списке инициализаторов объектов задает имя поля или свойства и его начальное значение. Имя поля или свойства должно начинаться с точки. Например, следующее объявление назначает Microsoft в качестве начального значения для свойства `Name` объекта `client`.  
  
```  
Dim client As New Customer() With { .Name = "Microsoft" }  
```  
  
 **Идентификатор ошибки:** BC30985  
  
### Исправление ошибки  
  
-   Укажите точку перед именем каждого члена.  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Процедуры свойств и Поля](http://msdn.microsoft.com/ru-ru/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)