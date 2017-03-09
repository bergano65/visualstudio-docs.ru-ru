---
title: "Sub New не может объявляться в интерфейсе | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30363"
  - "vbc30363"
helpviewer_keywords: 
  - "BC30363"
ms.assetid: 371d9aa8-a935-48ce-ada2-0a69ba20e070
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub New не может объявляться в интерфейсе
Предпринята попытка объявления `Sub New` в интерфейсе. Так как это конструктор, `Sub New` можно запустить только один раз при создании класса. Его нельзя вызвать явным образом нигде, кроме первой строки кода другого конструктора этого же класса или производного класса.  
  
 **Идентификатор ошибки:** BC30363  
  
### Исправление ошибки  
  
-   Удалите конструктор `Sub New` или переместите его в соответствующее место кода.  
  
## См. также  
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)