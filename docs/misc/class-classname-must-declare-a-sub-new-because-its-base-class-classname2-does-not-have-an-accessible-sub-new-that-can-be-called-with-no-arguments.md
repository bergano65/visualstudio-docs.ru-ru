---
title: "Класс &quot;&lt;имя_класса&gt;&quot; должен объявлять Sub New, так как его базовый класс &quot;&lt;имя_класса2&gt;&quot; не имеет доступный Sub New, который может быть вызван без аргументов. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30387"
  - "bc30387"
helpviewer_keywords: 
  - "BC30387"
ms.assetid: ff587e79-fa47-4b55-9a08-24688b209e0a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Класс &quot;&lt;имя_класса&gt;&quot; должен объявлять Sub New, так как его базовый класс &quot;&lt;имя_класса2&gt;&quot; не имеет доступный Sub New, который может быть вызван без аргументов.
Производный класс не объявляет конструктор, и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может создать его, так как отсутствует конструктор базового класса, который он может вызвать.  
  
 Когда производный класс не объявляет конструктор, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] пытается создать неявный конструктор без параметров, который вызывает `MyBase.New()`. Если в базовом классе нет доступного конструктора, который можно вызвать без аргументов, или если есть несколько конструкторов, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может создать неявный конструктор.  
  
 **Идентификатор ошибки:** BC30387  
  
### Исправление ошибки  
  
1.  Объявите и реализуйте по крайней мере один конструктор `Sub New` где\-нибудь в производном классе.  
  
2.  Добавьте вызов конструктора базового класса `MyBase.New()` в качестве первой строки каждого `Sub New`.  
  
## См. также  
 [Время существования: создание и уничтожение объектов](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Необязательные параметры](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)   
 [Массивы параметров](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)