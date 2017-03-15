---
title: "Ограничения Class и Structure нельзя использовать вместе. | Microsoft Docs"
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
  - "vbc32104"
  - "bc32104"
helpviewer_keywords: 
  - "BC32104"
ms.assetid: f41a581b-afca-4173-bc82-b35ed49caba0
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ограничения Class и Structure нельзя использовать вместе.
Список ограничений включает оба ограничения [Class \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) и [Structure \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0).  
  
 Список ограничений в параметре типа может указывать, что аргумент типа, переданный в этот параметр типа, должен быть типом значения \(с ограничением `Structure`\) или должен быть ссылочным типом \(с ограничением `Class`\). Нельзя указывать оба ограничения в одном и том же параметре типа, и нельзя указывать какое\-либо из них более одного раза.  
  
 **Идентификатор ошибки:** BC32104  
  
### Исправление ошибки  
  
1.  Решите, следует ли требовать тип значения или ссылочный тип для аргумента типа.  
  
    -   Если вы хотите, чтобы аргумент типа имел тип значения, удалите ключевое слово `Class` из списка ограничений.  
  
    -   Если вы хотите, чтобы аргумент типа имел ссылочный тип, удалите ключевое слово `Structure` из списка ограничений.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)