---
title: "&quot;&lt;имя_производного_типа&gt;&quot; не может наследовать от &lt;тип&gt; &quot;&lt;имя_сконструированного_базового_типа&gt;&quot;, поскольку он расширяет доступ к типу &quot;&lt;имя_внутреннего_типа&gt;&quot; за пределы данной сборки | Microsoft Docs"
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
  - "BC30922"
  - "vbc30922"
helpviewer_keywords: 
  - "BC30922"
ms.assetid: 81909654-7e67-4b89-81a3-25ae57f678f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_производного_типа&gt;&quot; не может наследовать от &lt;тип&gt; &quot;&lt;имя_сконструированного_базового_типа&gt;&quot;, поскольку он расширяет доступ к типу &quot;&lt;имя_внутреннего_типа&gt;&quot; за пределы данной сборки
Производный класс или интерфейс пытается расширить уровень доступа ограниченного типа, используя его как аргумент типа для базового класса или интерфейса.  
  
 Приведенный ниже код может вызвать эту ошибку.  
  
```  
Public Class baseClass(Of t)  
End Class  
Public Class derivedClass  
    Inherits baseClass(Of restrictedStructure)  
End Class  
Friend Structure restrictedStructure  
    Dim firstMember As Integer  
End Structure  
```  
  
 Коду вне сборки не разрешен доступ к `restrictedStructure`. Однако доступ к `derivedClass` может осуществляться из любого кода, который может на него ссылаться. Таким образом, `derivedClass` не может наследовать `baseClass`, если он использует `restrictedStructure` в качестве аргумента типа, так как это может предоставить доступ к `restrictedStructure` коду в любой сборке.  
  
 **Идентификатор ошибки:** BC30922  
  
### Исправление ошибки  
  
-   Настройте уровни доступа классов или интерфейсов таким образом, чтобы производный тип не расширял уровень доступа ограниченного типа.  
  
     \-или\-  
  
-   Если не удается настроить уровни доступа, не используйте ограниченный тип в качестве аргумента типа при создании базового класса или интерфейса.  
  
## См. также  
 [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Уровни доступа в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)