---
title: "Операнд &quot;IsNot&quot; типа &quot;&lt;имя_параметра_типа&gt;&quot; можно сравнивать только с &quot;Nothing&quot;, поскольку &quot;&lt;имя_параметра_типа&gt;&quot; является параметром типа без ограничения класса | Microsoft Docs"
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
  - "vbc32097"
  - "bc32097"
helpviewer_keywords: 
  - "BC32097"
ms.assetid: 50283a4b-70e3-4e59-9b9b-65e7cacf5ce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операнд &quot;IsNot&quot; типа &quot;&lt;имя_параметра_типа&gt;&quot; можно сравнивать только с &quot;Nothing&quot;, поскольку &quot;&lt;имя_параметра_типа&gt;&quot; является параметром типа без ограничения класса
Параметр типа используется в качестве операнда для [Оператор IsNot](/dotnet/visual-basic/language-reference/operators/isnot-operator), если параметр типа определен без ключевого слова [Class \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7), или конкретного имени класса в его списке ограничений.  
  
 Оператор `IsNot` сравнивает два ссылочных типа, чтобы определить, указывают ли они на разные экземпляры объекта в памяти. Он не может принимать операнд, который не является ссылочным типом, если только в качестве другого операнда не используется [Nothing](/dotnet/visual-basic/language-reference/nothing).  
  
 **Идентификатор ошибки:** BC32097  
  
### Исправление ошибки  
  
-   Если можно потребовать, чтобы аргумент типа, предоставленный для данного параметра типа, всегда был ссылочным типом, добавьте ключевое слово `Class` или укажите определенное имя класса в списке ограничений для параметра типа.  
  
-   Если не требуется, чтобы аргумент типа, предоставленный для данного параметра типа, всегда был ссылочным типом, удалите его из выражения `IsNot`. Его нельзя сравнивать с другими ссылочными типами с помощью оператора `IsNot`.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Операторы сравнения в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)