---
title: "Ограничения New и Structure нельзя использовать вместе. | Microsoft Docs"
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
  - "bc32103"
  - "vbc32103"
helpviewer_keywords: 
  - "BC32103"
ms.assetid: 5418b420-a014-4006-84aa-20ddac6739e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ограничения New и Structure нельзя использовать вместе.
Список ограничений включает оба ограничения [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator) и [Structure \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0).  
  
 Список ограничений в параметре типа может указывать, что аргумент типа, переданный в этот параметр типа, должен быть типом значения \(с ограничением `Structure`\) или ссылочным типом \(с ограничением [Class \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\). Нельзя указывать оба ограничения в одном и том же параметре типа, и нельзя указывать какое\-либо из них более одного раза.  
  
 Ограничение `New` указывает, что аргумент типа должен предоставлять конструктор без параметров, к которому код создания может получить доступ. Однако структура не может иметь не являющийся общим конструктор без параметров. Таким образом, ограничения `New` и `Structure` являются конфликтующими.  
  
 **Идентификатор ошибки:** BC32103  
  
### Исправление ошибки  
  
1.  Решите, следует ли требовать тип значения или ссылочный тип для аргумента типа.  
  
2.  Если вы хотите, чтобы аргумент типа имел тип значения, удалите ключевое слово `New` из списка ограничений.  
  
3.  Если вы хотите, чтобы аргумент типа имел ссылочный тип, удалите ключевое слово `Structure` из списка ограничений.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)