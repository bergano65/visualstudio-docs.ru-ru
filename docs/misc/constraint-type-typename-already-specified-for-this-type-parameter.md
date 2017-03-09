---
title: "Тип ограничения &quot;&lt;имя_типа&gt;&quot; уже указан для данного параметра типа | Microsoft Docs"
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
  - "BC32071"
  - "vbc32071"
helpviewer_keywords: 
  - "BC32071"
ms.assetid: 6b0e85e9-3ac8-4181-97de-ca690b95a63c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип ограничения &quot;&lt;имя_типа&gt;&quot; уже указан для данного параметра типа
Список ограничений включает ограничение класса или интерфейса более одного раза.  
  
 Список ограничений назначает требования на тип аргумента, передаваемого параметру типа. Вы можете указать приведенные ниже требования в любой комбинации.  
  
-   Аргумент типа должен реализовывать один или несколько интерфейсов  
  
-   Аргумент типа должен наследовать не больше чем из одного класса  
  
 Тип не может реализовывать один тип или наследоваться от него более одного раза; тип нельзя также указывать более одного раза в одном списке ограничений.  
  
 **Идентификатор ошибки:** BC32071  
  
### Исправление ошибки  
  
-   Удалите все избыточные спецификации класса или интерфейса. Тип должен содержаться в списке ограничений только один раз.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)