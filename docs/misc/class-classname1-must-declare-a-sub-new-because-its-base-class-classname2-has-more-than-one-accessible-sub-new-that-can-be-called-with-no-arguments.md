---
title: "Класс &quot;&lt;classname1&gt;&quot; должен объявить Sub New, так как его базовый класс &quot;&lt;classname2&gt;&quot; имеет более чем один доступный Sub New, который может быть вызван без аргументов. | Microsoft Docs"
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
  - "bc32036"
  - "vbc32036"
helpviewer_keywords: 
  - "BC32036"
ms.assetid: 9b96387e-337e-4b2a-b49f-783c7e13811a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Класс &quot;&lt;classname1&gt;&quot; должен объявить Sub New, так как его базовый класс &quot;&lt;classname2&gt;&quot; имеет более чем один доступный Sub New, который может быть вызван без аргументов.
Производный класс не объявляет конструктор, и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может создать его, так как он не может определить, какой конструктор базового класса следует вызвать.  
  
 Когда производный класс не объявляет конструктор, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] пытается создать неявный конструктор без параметров, который вызывает `MyBase.New()`. Если нет доступного конструктора в базовом классе, который можно вызвать без аргументов, или если есть несколько конструкторов, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может создать неявный конструктор.  
  
 Эта ситуация может возникнуть, например, если один конструктор базового класса содержит один аргумент `Optional`, а другой — один аргумент `ParamArray`. Каждый из них можно вызвать без аргументов.  
  
 **Идентификатор ошибки:** BC32036  
  
### Исправление ошибки  
  
1.  Объявите и реализуйте по крайней мере один конструктор `Sub New` где\-нибудь в производном классе.  
  
2.  Добавьте вызов в конструктор базового класса `MyBase.New()` в качестве первой строки каждого `Sub New`.  
  
## См. также  
 [Время существования: создание и уничтожение объектов](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Необязательные параметры](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)   
 [Массивы параметров](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)