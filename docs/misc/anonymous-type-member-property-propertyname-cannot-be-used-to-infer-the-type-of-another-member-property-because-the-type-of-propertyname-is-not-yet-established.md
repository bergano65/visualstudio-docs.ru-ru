---
title: "Свойство члена анонимного типа &quot;&lt;имя_свойства&gt;&quot; не может использоваться для определения типа другого свойства члена, так как тип &quot;&lt;имя_свойства&gt;&quot; еще не установлен. | Microsoft Docs"
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
  - "vbc36559"
  - "bc36559"
helpviewer_keywords: 
  - "BC36559"
ms.assetid: 58ab8d35-9d85-4aca-8b4e-f232d7e4af61
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство члена анонимного типа &quot;&lt;имя_свойства&gt;&quot; не может использоваться для определения типа другого свойства члена, так как тип &quot;&lt;имя_свойства&gt;&quot; еще не установлен.
Пока тип свойства анонимного типа не установлен, он не может использоваться для установки типа другого свойства. Например, в следующем объявлении `.IDName = .LastName` недопустимо, поскольку еще не выполнена инициализация `.LastName`.  
  
```  
' Not valid.   
' Dim anon1 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}   
```  
  
 **Идентификатор ошибки:** BC36559  
  
### Исправление ошибки  
  
-   Установите тип свойства перед его использованием для инициализации другого свойства.  
  
    ```  
    Dim anon2 = New With {Key .LastName = "Jones", Key .IDName = .LastName}  
    ```  
  
## См. также  
 [Анонимные типы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)