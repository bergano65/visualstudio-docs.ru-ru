---
title: "Конструкторы не могут реализовывать методы интерфейсов | Microsoft Docs"
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
  - "bc30550"
  - "vbc30550"
helpviewer_keywords: 
  - "BC30550"
ms.assetid: 982a767d-9174-408e-bdcf-ae0d96f88cef
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Конструкторы не могут реализовывать методы интерфейсов
Вы попытались использовать ключевое слово `New` для реализации метода интерфейса, что недопустимо.  
  
 **Идентификатор ошибки:** BC30550  
  
### Исправление ошибки  
  
-   Реализуйте интерфейсы с ключевым словом `Implements`.  
  
## См. также  
 [Оператор Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [НЕ В СБОРКЕ. Общие сведения об интерфейсах](http://msdn.microsoft.com/ru-ru/f96bb470-c1b8-4c73-89bc-6f536b798da1)