---
title: "Ожидается &quot;=&quot; (инициализатор объекта) | Microsoft Docs"
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
  - "vbc30984"
  - "bc30984"
helpviewer_keywords: 
  - "BC30984"
ms.assetid: 9cae8d32-775a-414f-9e51-0469974b6aab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ожидается &quot;=&quot; (инициализатор объекта)
Чтобы установить начальное значение для поля или свойства в объявлении инициализатора объекта, необходимо использовать знак равенства. Например, приведенное ниже объявление назначает Microsoft в качестве начального значения для свойства `Name` объекта `client`.  
  
```  
Dim client As New Customer { .Name = "Microsoft" }  
```  
  
 **Идентификатор ошибки:** BC30984  
  
### Исправление ошибки  
  
-   Добавьте знак равенства в позицию, показанную в предыдущем примере.  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Свойства и процедуры свойств](http://msdn.microsoft.com/ru-ru/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [НЕ В СБОРКЕ. Процедуры свойств и Поля](http://msdn.microsoft.com/ru-ru/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)