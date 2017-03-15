---
title: "В соответствии с ограничением &quot;New&quot; параметра типа &quot;&lt;имя_параметра_типа2&gt;&quot;, параметр типа &quot;&lt;имя_параметра_типа1&gt;&quot; должен иметь либо ограничение New, либо Structure | Microsoft Docs"
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
  - "vbc32084"
  - "BC32084"
helpviewer_keywords: 
  - "BC32084"
ms.assetid: a7ff58d3-8c67-40e4-9fd8-92cc00524c22
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В соответствии с ограничением &quot;New&quot; параметра типа &quot;&lt;имя_параметра_типа2&gt;&quot;, параметр типа &quot;&lt;имя_параметра_типа1&gt;&quot; должен иметь либо ограничение New, либо Structure
Оператор создает универсальный тип передачи параметра типа, который не ограничен для удовлетворения ограничения `New`.  
  
 Ограничение `New` означает, что аргумент типа, предоставленный для данного параметра типа, должен предоставлять коду доступ к конструктору без параметров, который создает объекты из него. Конструкторы без параметров имеются для всех типов значений, но не для всех ссылочных типов. Поэтому ограничение `Structure` удовлетворяет ограничению `New`, а ограничение `Class` или имя класса или интерфейса — нет.  
  
 Эта ошибка может быть вызвана указанными ниже операторами.  
  
```  
Public Class c1(Of t As New) End Class Public Class c2(Of u) Public testObject As New c1(Of u) End Class  
```  
  
 Когда класс `c2` создает объект из `c1`, параметр типа `u` не удовлетворяет ограничению `New` для параметра типа `t`.  
  
 **Идентификатор ошибки:** BC32084  
  
### Исправление ошибки  
  
-   Если передаваемый в универсальный тип параметр типа может удовлетворять ограничению `Structure` или `New`, следует добавить к его определению соответствующее ограничение.  
  
    ```  
    Public Class c2(Of u As Structure)  
    ```  
  
-   Если параметр типа не удовлетворяет ограничению `Structure` или `New`, не следует передавать его в универсальный тип. Следует передать в качестве аргумента типа что\-нибудь другое.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Структура \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Класс \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)