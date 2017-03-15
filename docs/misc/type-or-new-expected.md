---
title: "Ожидается тип или New | Microsoft Docs"
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
  - "vbc32092"
  - "bc32092"
helpviewer_keywords: 
  - "BC32092"
ms.assetid: b3041c1d-837c-4d58-bbb4-5c46f227b66d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ожидается тип или New
Параметр типа в объявлении универсального типа представляет список ограничений с ключевым словом `As`, но не задает допустимое ограничение.  
  
 Ограничение в параметре типа должно быть допустимым классом или интерфейсом или одним из ключевых слов `Class`, `Structure` или `New`. Если задано недопустимое ограничение или вообще не заданы никакие ограничения, компилятор создает эту ошибку.  
  
 **Идентификатор ошибки:** BC32092  
  
### Исправление ошибки  
  
1.  Определите, как параметр типа должен быть ограничен, и задайте соответствующее ограничение в списке ограничений.  
  
2.  Если вы хотите ограничить параметр типа с помощью класса или интерфейса, убедитесь, что в ограничении он записан правильно.  
  
3.  Не забудьте разделять несколько ограничений для одного параметра типа запятыми и заключать список ограничений в фигурные скобки \(`{ }`\).  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Класс \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Структура \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)