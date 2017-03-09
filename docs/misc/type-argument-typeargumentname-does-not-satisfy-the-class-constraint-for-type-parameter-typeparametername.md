---
title: "Аргумент типа &quot;&lt;имя_аргумента_типа&gt;&quot; не удовлетворяет ограничению &quot;Class&quot; для параметра типа &quot;&lt;имя_параметра_типа&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32106"
  - "bc32106"
helpviewer_keywords: 
  - "BC32106"
ms.assetid: 1bac1dd6-f86b-4e98-ba2d-57d1936e3658
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргумент типа &quot;&lt;имя_аргумента_типа&gt;&quot; не удовлетворяет ограничению &quot;Class&quot; для параметра типа &quot;&lt;имя_параметра_типа&gt;&quot;
Аргумент типа, предоставленный в универсальный тип, не удовлетворяет ограничению ссылочного типа в соответствующем параметре типа.  
  
 Список ограничений налагает требования на аргумент типа, передаваемый в параметр типа. Если не включать определенный класс или интерфейс в список ограничений, то можно наложить общее требование, указав одно из приведенных ниже ограничений.  
  
-   Аргумент типа должен быть типом значения \(включая ограничение [Structure \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\).  
  
-   Аргумент типа должен быть ссылочным типом \(включая ограничение [Class \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\).  
  
 Нельзя указывать оба ограничения, `Structure` и `Class`, для одного и того же параметра типа, а также указывать какое\-либо из них более одного раза.  
  
 **Идентификатор ошибки:** BC32106  
  
### Исправление ошибки  
  
-   Выберите аргумент типа любого ссылочного типа.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Практическое руководство. Использование универсального класса](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)