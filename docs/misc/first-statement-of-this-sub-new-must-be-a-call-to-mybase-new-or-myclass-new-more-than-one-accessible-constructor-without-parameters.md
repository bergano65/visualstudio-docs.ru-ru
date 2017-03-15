---
title: "Первая инструкция этого Sub New должна быть вызовом MyBase.New или MyClass.New (несколько доступных конструкторов без параметров). | Microsoft Docs"
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
  - "vbc32038"
  - "bc32038"
helpviewer_keywords: 
  - "BC32038"
ms.assetid: 52e4e9df-a85b-46ae-a0cc-7d8fa377fe95
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Первая инструкция этого Sub New должна быть вызовом MyBase.New или MyClass.New (несколько доступных конструкторов без параметров).
Первая инструкция в этом Sub New должна быть вызовом MyBase.New или MyClass.New, так как базовый класс "\<базовый\>" класса "\<производный\>" имеет несколько доступных Sub New, которые могут вызываться без аргументов.  
  
 Конструктор класса не поддерживает вызов конструктора базового класса, и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может предоставить неявный вызов, так невозможно определить, какой именно конструктор базового класса следует вызывать.  
  
 **Идентификатор ошибки:** BC32038  
  
### Исправление ошибки  
  
-   Добавьте вызов конструктора базового класса `MyBase.New()` или другого конструктора этого класса с помощью `MyClass.New()` или `Me.New()` в качестве первой строки этого конструктора.  
  
## См. также  
 [Время существования: создание и уничтожение объектов](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [MyBase — удалить](http://msdn.microsoft.com/ru-ru/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)