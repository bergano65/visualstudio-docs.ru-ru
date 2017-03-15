---
title: "Тип &quot;&lt;имя_типа&gt;&quot; является универсальным и требует аргументов типа. | Microsoft Docs"
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
  - "BC32076"
  - "vbc32076"
helpviewer_keywords: 
  - "BC32076"
ms.assetid: 57f63727-c544-4012-8f03-5d77fbdd1135
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_типа&gt;&quot; является универсальным и требует аргументов типа.
Переменная, параметр процедуры или возвращаемое значение функции объявлены с типом универсального класса или структуры, но это объявление не предоставляет никакие аргументы типа.  
  
 По своей природе каждый универсальный класс и структура определяется по крайней мере с одним параметром типа. При использовании универсального типа для объявления сформированного класса или структуры вы должны указать аргумент типа для каждого параметра типа, определенного универсальным типом.  
  
 **Идентификатор ошибки:** BC32076  
  
### Исправление ошибки  
  
-   Добавьте в объявление список типов, заключенный в круглые скобки и начинающийся с ключевого слова `Of`.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)