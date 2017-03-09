---
title: "Требуется тип или &quot;With&quot; | Microsoft Docs"
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
  - "vbc30988"
  - "bc30988"
helpviewer_keywords: 
  - "BC30988"
ms.assetid: ab9c0cee-9fe4-4764-a3c2-aec16e709d4c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется тип или &quot;With&quot;
При объявлении экземпляра класса за ключевым словом `New` должно следовать имя типа или `With`. Например, в следующих инструкциях объявляется `client` как экземпляр класса `Customer`. Имя типа `Customer`, следующее за `New`.  
  
```  
' Dim client As New Customer()  
' The next declaration uses an object initializer.  
Dim client As New Customer() With {.Name = "Litware, Inc."}  
```  
  
 Начиная с версии [!INCLUDE[vb_orcas_long](../misc/includes/vb_orcas_long_md.md)], вы можете объявлять объект как экземпляр анонимного типа, и в этом случае не указывать тип данных. В объявлениях анонимных типов за `New` следует ключевое слово `With`.  
  
```  
Dim person = New With {.Name ="Mike Nash", .Age = 27}  
```  
  
 **Идентификатор ошибки:** BC30988  
  
### Исправление ошибки  
  
-   Измените объявление, чтобы после `New` указывалось `With` или имя типа.  
  
## См. также  
 [Анонимные типы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [НЕ В СБОРКЕ. Инструкции объявления в Visual Basic](http://msdn.microsoft.com/ru-ru/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)