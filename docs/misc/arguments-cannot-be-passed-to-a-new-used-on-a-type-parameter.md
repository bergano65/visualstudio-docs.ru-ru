---
title: "Аргументы нельзя передать в ограничение New для параметра-типа | Microsoft Docs"
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
  - "BC32085"
  - "vbc32085"
helpviewer_keywords: 
  - "BC32085"
ms.assetid: a60bf62d-2b2e-4621-b8db-e67720b918fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргументы нельзя передать в ограничение New для параметра-типа
Оператор объявления или присваивания вызывает универсальный тип и предоставляет аргументы конструктора для параметра типа, имеющего ограничение [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator).  
  
 Список ограничений для параметра типа может указывать, что аргумент типа, переданный параметру типа, должен предоставлять конструктор без параметров, к которому имеет доступ создающий код. Параметру типа не требуется конструктор, который принимает параметры, а параметр типа с ограничением `New` не может принять такой конструктор.  
  
 **Идентификатор ошибки:** BC32085  
  
### Исправление ошибки  
  
-   Удалите список аргументов следующего аргумента типа в операторе вызова универсального типа. Нельзя передать аргументы конструктора соответствующему параметру типа.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)